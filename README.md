# SOA Software API HOOK
Put a nice company logo image here. 
Link to product documentation and product overview page
## Trello API to Google Sheets API integration
### About the API
- This integration API takes no input, but uses the users credentials to discover all the Boards owned and converts them to Google Sheets spreadsheets. The Board name becomes the name of the spreadsheet. The List names of the Board becomes the names of the worksheets, inside the spreadsheet. The name of a Card in the List becomes the values of the first cell in a row in a worksheet.

### Pre-Reqs
- This uses the following API Hooks, that must be installed:
    + Google Sheets API Hook
    + Google Drive API Hook
    + Trello API Hook

### Getting Started Instructions
#### Download and Import
- Download TrellotogoggleIntegration.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM.
    - the container key is found by going to the "Deatils Tab" of the ND cluster, or ND defined in the Policy Manager Console, then looking at the " Container Overview" tab on that page, and copying the "Container Key:" value. ![container key screenshot](https://github.com/pogo61/Google-Sheets-API-Integration/blob/master/Screen%20Shot%202015-03-18%20at%2011.24.45%20am.png "ND Container Key")
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the TrellotoGoogleIntegration.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a *Trello to Google Integration* Organisation with the requisite artefacts needed to run the API.
- you can us the API as is calling http://"URL of the Listener of your ND"/trello2Google_int/export, or you can create an API in CM and expost it.
    - if you chose to create an API in CM, you must create a Service in your CM tenant which is a Virtual Service of the Trello_to_Google_Integration VS that was created by the import. Then Go to CM and create a API from an existing Service.

#### Verify Import
- Expand the services folder in the Google to Trello Integration you imported and find Trello_to_Google_Integration VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Trello to Google Integration organisation you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- As per the listed Hooks procedures
- go to the Policies->Operational Policies->ProcessVariables policy in the Trello to Google Integration orgnisation
- click the modify link in the "XML Policy" tab
- change the values of the "auth.key" and "auth.token" elements to be those of your Tello API Hook credentials
- save the changes
- click the "Activate Policy" workflow action, on the right hand side of the policy details screen
- go to the Policies->Operational Policies->Trello API Hook Auth policy in the Trello to google Integration orgnisation
- click the "Activate Policy" workflow action, on the right hand side of the policy details screen

#### Verify Connectivity
- Using  curl http://"URL of the Listener of your ND"/trello2google_int/export
    -  the value "Test" can be replaced with the name of your google sheets spreadsheet 
-  the response should be: 
    +  {
            "status": "Success",
            "detail": "Your Trello Boards have been exported to google Drive"
        }

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

