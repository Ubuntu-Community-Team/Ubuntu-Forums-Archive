---
title: "tally erp 9"
date: 2012-09-12
forum: General Help
---

### Post by sumitgupta on 2012-09-12
Dear Friends

We are using ubuntu 12.04 & installed tally by wine.
but our accounting data is still on windows xp.
how can i link window data to tally .
please give me syntax..
for example-windows xp ip is 192.100.110.204
and tally data is shared in DATA folder.

---

### Post by prshah on 2012-09-12
> **sumitgupta said:**
> We are using ubuntu 12.04 & installed tally by wine.
..
how can i link window data to tally .
..
for example-windows xp ip is 192.100.110.204
and tally data is shared in DATA folder.

Copy your existing TALLY.INI file from your Windows machine to your linux machine's Tally directory (typically ~/.wine/drive_c/Tally).

Then, edit your TALLY.INI file and change the DATA parameter:```

#probably from DATA=c:\tally\data to
DATA = \\192.100.110.204\DATASHARE
# if sharename is not DATASHARE, or if DATASHARE share is other than 
# c:\tally\data, then please modify DATASHARE accordingly.
# eg, if DATASHARE points to c:\tally, then the above line should be
# DATA = \\192.100.110.204\DATASHARE\DATA

```

I recommend that you simply copy the TALLY.INI on an existing Windows client machine to your linux machine.

However, this means that your SMB (samba, windows client) setup should be completed; please post back if you want details on this.

---

### Post by sumitgupta on 2012-09-13
thanks ..
After replacing .ini file , the path on tally is shown.
but data is not executed.
still showing "NO COMPANY SELECTED"

---

### Post by prshah on 2012-09-13
> **sumitgupta said:**
> 
After replacing .ini file , the path on tally is shown.
but data is not executed.
still showing "NO COMPANY SELECTED"

I'm sorry, this makes no sense at all.. ie, I cannot understand what you are trying to say.

Please post your TALLY.INI file here for further inspection / troubleshooting.

---

### Post by sumitgupta on 2012-09-14
1

---

### Post by sumitgupta on 2012-09-14
> **sumitgupta said:**
> this is tally.ini file-

.....................................................................................................................................................
;;Tally.ERP 9 workstation specific parameters file
[TALLY]

;;** If you are running multi-user in client mode use TallyLicenseServer 
;; TallyLicenseServer = server : Port
Tally License Server=192.100.110.204:9099
LicTimeout=

;;** If you are running single-user - specify License Directory 
;; LicensePath = Location of License file
License Path=C:\Tally.ERP9

;;Specify location of Data files
Data=\\192.100.110.204\tally$\Data (11-12)

;;Specify list of companies to preload, 
;; ** TO STOP DEFAULT LOADING set the following line to NO
Default Companies=Yes
Load=10000

;;Specify list of TDL files for user defined reports and changes, 
;; ** TO STOP LOADING TDL FILES, set the following line to NO
User TDL=Yes

;;Specify location of TALLYSAV.tsf (saved configuration of Tally)
Config=C:\Tally.ERP9

;;Specify location of Language Files
LangPath=C:\Tally.ERP9\Lang

;;Specify location where files are created during export by default
Export Path=C:\Tally.ERP9

;;Specify Color details of local monitor
Color=Yes
Sound=Yes

Client Server=None
ServerPort=9000
Enable ODBC Server=Yes
Load Buffering=Yes
Ignore Tcp Timeout=Yes

Width=1366
Height=738
..............................................................................................................................................


My problem is that after replacing .ini file, we are unable to  access data .
Tally is not taking specified path..
pls help me.

---

### Post by prshah on 2012-09-14
> **sumitgupta said:**
> 
;;Specify location of Data files
Data=\\192.100.110.204\tally$\Data (11-12)


Is your data folder REALLY "Data (11-12)"? Or just data?

If it is actually correct, then try placing the entire path in quotes (") to allow for spaces in path.

Try to mount it manually from the Terminal (Dash-Terminal)```

sudo smbmount "\\\\192.100.110.204\\tally$\\Data (11-12)" /mnt/ -o guest
ls /mnt # if no error from above
sudo umount /mnt # to unmount

```

If the smbmount command gives you an error, please check and post relevant lines from the logfile ```
dmesg|tail
``` Also try to mount it in nautilus (Places-> Connect to server...) and post back with results.

Are you certain samba is setup correctly in your machine?

---

