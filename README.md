[comment]: # "Auto-generated SOAR connector documentation"
# Intezer Analyze

Publisher: Domenico Perre  
Connector Version: 1\.1\.1  
Product Vendor: Intezer  
Product Name: Analyze  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.2\.7532  

This app supports the investigate actions on the Intezer platform\. Intezer's technology enables your security team to go beyond behavioral analysis\. Its solutions diagnose every piece of code quickly and accurately with DNA mapping from Intezer\-an industry first enabling your team to address real threats immediately

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Analyze asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Base URL for API request
**apiKey** |  required  | password | API Key for submitting samples

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using the supplied configuration  
[detonate file](#action-detonate-file) - Run the file in the sandbox and retrieve the analysis results  
[get report](#action-get-report) - Query for results of an already completed detonation  
[file reputation](#action-file-reputation) - Queries for file info  

## action: 'test connectivity'
Validate the asset configuration for connectivity using the supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'detonate file'
Run the file in the sandbox and retrieve the analysis results

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**vault\_id** |  required  | Vault ID of file to detonate | string |  `pe file`  `pdf`  `flash`  `apk`  `jar`  `doc`  `xls`  `ppt` 
**file\_name** |  optional  | Filename to use | string |  `file name` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.file\_name | string |  `file name` 
action\_result\.parameter\.vault\_id | string |  `pe file`  `pdf`  `flash`  `apk`  `jar`  `doc`  `xls`  `ppt` 
action\_result\.data\.\*\.result\.analysis\_id | string |  `id` 
action\_result\.data\.\*\.result\.analysis\_url | string | 
action\_result\.data\.\*\.result\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.result\.sub\_verdict | string | 
action\_result\.summary\.verdict | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get report'
Query for results of an already completed detonation

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Detonation ID to get the report of | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.id | string | 
action\_result\.data\.\*\.result\.analysis\_id | string |  `id` 
action\_result\.data\.\*\.result\.analysis\_url | string | 
action\_result\.data\.\*\.result\.family | string | 
action\_result\.data\.\*\.result\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.result\.sub\_verdict | string | 
action\_result\.summary\.verdict | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'file reputation'
Queries for file info

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**hash** |  required  | File hash to query | string |  `hash`  `sha256`  `sha1`  `md5` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.hash | string |  `hash`  `sha256`  `sha1`  `md5` 
action\_result\.data\.\*\.result\.analysis\_id | string |  `id` 
action\_result\.data\.\*\.result\.analysis\_url | string | 
action\_result\.data\.\*\.result\.family | string | 
action\_result\.data\.\*\.result\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.result\.sub\_verdict | string | 
action\_result\.summary\.verdict | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 