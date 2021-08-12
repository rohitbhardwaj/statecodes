<a href="https://githubsfdeploy.herokuapp.com?owner=bigassforce&amp;repo=statecodes&amp;ref=master">
<img align="right" alt="Deploy to Salesforce" src="https://raw.githubusercontent.com/afawcett/githubsfdeploy/master/deploy.png">
</a> This tool initializes all ISO states by screen scraping the forms in setup.<br />(State and Country picklist values cannot be created any other way)

# Install

- Install the package: <a href="https://login.salesforce.com/packaging/installPackage.apexp?p0=04t4J000000tIvu">/packaging/installPackage.apexp?p0=04t4J000000tIvu</a>
- Go to Setup > Installed Packages > State Codes, then click **Configure**
- Review the included ISO state codes then click **Start Batch**

<img src="https://raw.githubusercontent.com/wiki/bigassforce/statecodes/images/states-configure.png" />

# Verify

Inspect the State and Country picklist values before, during, and after starting the batch:

<img width="625" src="https://raw.githubusercontent.com/wiki/bigassforce/statecodes/images/states-completed.png" />
<img width="625" src="https://raw.githubusercontent.com/wiki/bigassforce/statecodes/images/states-after.png" />

# Modify

After the package creates all the state codes and state names, the values must be permanently activated using Workbench or an IDE connected to the org. Use this package.xml to retrieve the states and countries metadata:

```
<?xml version="1.0" encoding="UTF-8"?>
<Package>
    <types>
        <members>Address</members>
        <name>Settings</name>
    </types>
    <version>45.0</version>
</Package>
```

1. Extract the metadata and open the Address.settings file
2. Search and replace `<active>false</active>` with `<active>true</active>`
3. Search and replace `<visible>false</visible>` with `<visible>true</visible>`
4. Zip the metadata folder with your changes and deploy it to the org using Workbench
