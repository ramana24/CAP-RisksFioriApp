# CAP-RisksFioriApp
Fiori Annotation App with CAP service
Certification Essentials – Extension Developer Certification.

Final – certifications (Recommended) 
-	SAP Certified Development Associate - SAP BTP Extension Developer
-	SAP Certified Development Associate - SAP HANA Cloud 1.0
-	SAP Certified Development Associate - SAP Integration Suite

Integration suite - https://learning.sap.com/learning-journey/developing-with-sap-integration-suite
Extension suite – Topics : 
 Cloud Application Programming Plays a role to solve business usecases
1. In App Extension : Develop Applications Running on SAP BTP Using SAP HANA Cloud
 https://learning.sap.com/learning-journey/develop-applications-running-on-sap-btp-using-sap-hana-cloud
2. Side- by Side :  Build side-by-side extensions on SAP BTP
https://learning.sap.com/learning-journey/build-side-by-side-extensions-on-sap-btp

Refresh CAP Learnings –
Samples:
https://github.com/SAP-samples/cloud-cap-samples/tree/main
install codetour extension in BAS for easy navigation.
use  npm install for all the folders , followed by cds watch
-	Hello   - hello world ex
-	Bookshop – reference one cds service (https://developers.sap.com/tutorials/cp-apm-nodejs-create-service.html#d1bd1dc9-182f-4afd-b41f-766a621af482)
-	Common – (similar to formatter – allows to define f4 /dropdown values in Fiori app )
-	Orders – (for table/list navigation/association / deep entity)
-	 Reviews – (feature of review – how to design odata using cds cap)
-	Annotations – how to automate annotations in CAP ( to be discussed ) 
(1.	Documentation :  https://cap.cloud.sap/docs/advanced/fiori   2.  Need detailed documentation -  FAQ )
-	Bookstore – (app built using vue.js and Fiori as well ) userid – alice and pwd – blank
-	Fiori – gives access to few apps generated based Fiori element- CAP annotations
Real Time Usecase –
https://learning.sap.com/learning-journey/build-side-by-side-extensions-on-sap-btp

SAP to Non-SAP:
Manufacture – exports all regions – US, Japan,india
SAP Data for US onpremise – in App extension
SAP Data for Japan onpremise

Export – Risks and mitigation App
Report App : What are the risks that can effect export ?
 Side by Side Extension  - when data from multiple regions needs to be collated in a single App for business benefit.

Internal API – sap.api.hub
External API-  how to connect to external API .



Snippets 1 :

Snippet 2: 
using RiskService from '../../srv/risk-service';
 // Risk List Report Page
 annotate RiskService.Risks with @(UI : {
    HeaderInfo : {
       TypeName : 'Risk',
       TypeNamePlural : 'Risks',
       Title : {
          $Type : 'UI.DataField',
          Value : title
       },
       Description : {
          $Type : 'UI.DataField',
            Value : descr
       }
    },
    SelectionFields : [prio],
    Identification : [{Value : title}],
    // Define the table columns
    LineItem : [
       {Value : title},
       {Value : miti_ID},
       {Value : owner},
       { 
          Value : prio,
          Criticality : criticality
       },
       {
          Value : impact,
          Criticality : criticality
       },
    ],
 });
 // Risk Object Page
 annotate RiskService.Risks with @(UI : {
     Facets : [{
        $Type : 'UI.ReferenceFacet',
        Label : 'Main',
        Target : '@UI.FieldGroup#Main',
     }],
     FieldGroup #Main : {Data : [
       {Value : miti_ID},
       {Value : owner},
       {
           Value : prio,
           Criticality : criticality
       },
       { 
           Value : impact,
           Criticality : criticality
       }
    ]},
 });








