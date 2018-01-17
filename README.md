# abap-lcl-ftp
ABAP Local Class for Handling FTP

## SAPFTPA Config
You need to create RFC destinations for FTP communications. There is a standard report for that purpose called:
    'RSFTP005'(SAPFTP check)
instead of configuring it manually via the transaction 'SM59'(Configurations of RFC connections),it automatically creates the following two RFC destinations:
1.SAPFTP(For invoking the RFC library on the SAP GUI frontend)
2.SAPFTPA(For invoking the RFC library on the SAP Netweaver AS ABAP host)

## Installation
1. Create table ZTA_FTPCONFIG

Field | Data Type | Length
----- | --------- | ------
MANDT | CLNT | 3 
CNAME | CHAR | 30
CSYSTEM | CHAR | 20
CUSER | CHAR | 30
CPASSWORD | CHAR | 30
CHOST | CHAR | 30
IPORT | CHAR | 10
RFC_DESTINATION | CHAR | 32
CFOLDER | CHAR | 100

2. Create `Include Program` from SE38 and paste the code
3. Activate
## How to Use?
1. Create local object with reference `lcl_ftp`
2. Create object of `lcl_ftp`
3. And method on class ready

## Example 

```
DATA: lo_export_ftp TYPE REF TO lcl_ftp.

CREATE OBJECT lo_export_ftp.
lo_export_ftp->handle_connect(
        EXPORTING imw_ftp_config = lw_ftpconfig
        IMPORTING ex_hdl = lv_hdl ).
```

## License
TODO: ???