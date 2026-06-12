---
title: "HP P1006 just stopped working for no reason [lucid]"
date: 2010-05-18
forum: General Help
---

### Post by arsenic23 on 2010-05-18
OK, I when I installed lucid it picked up my printer write away, downloaded hplip on its own and installed it.  Worked with no problem at all, and it continued to work up until this morning.  Suddenly print jobs just disappear without so much as making the printer twitch.  Every time I reboot my printer I get that little floating black notice box that informs me that Ubuntu is downloading proprietary drivers for my printer.

Also if I reboot the machine and the printer I still get 'job 11' or what-not.  I uninstalled the driver and reinstalled it. I reset cups, rebooted, ect...  Nothing.  So I did the last week or so of updates, noticing there was some printer related stuff in there, and still no go.  I did an apt-get purge of hplip and reinstall, but still the error persists.

Here's my errors, the problem the problem appears to be with my driver setup:
```
E [18/May/2010:11:47:04 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [18/May/2010:11:50:36 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [18/May/2010:11:51:24 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [18/May/2010:11:59:49 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [18/May/2010:12:45:14 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
```

-------------
EDIT
-------------
Would appear to be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/434564](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/434564)

---

### Post by arsenic23 on 2010-05-18
OK, so I decided to purge CUPS and reinstall it:
```
sudo apt-get purge cups
sudo rm /etc/cups/ -r
sudo apt-get install cups
sudo apt-get install cups cups-ppdc foomatic-db-engine foomatic-db hplip xpdf-korean xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf gutenprint-doc gutenprint-locales
```

Well now I have a completely different problem, and I have no idea what is going on now.

Whenever I print I get "**There was a problem processing document 'Test Page' (job 5)** or similar.  Then the job just stops and CUPS asks me if I want to troubleshoot.

Here is what the new errors look like, the first one is in debugging mode the second is what it looks like normally:

```
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:01 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [18/May/2010:13:46:01 -0400] Get-Jobs ipp://localhost/printers/
D [18/May/2010:13:46:01 -0400] [Job 3] Loading attributes...
D [18/May/2010:13:46:01 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:01 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [18/May/2010:13:46:01 -0400] Get-Jobs ipp://localhost/printers/
D [18/May/2010:13:46:01 -0400] [Job 1] Loading attributes...
D [18/May/2010:13:46:01 -0400] [Job 2] Loading attributes...
D [18/May/2010:13:46:01 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:01 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:01 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1
D [18/May/2010:13:46:01 -0400] Create-Printer-Subscription /
D [18/May/2010:13:46:01 -0400] cupsdCreateSubscription(con=0x7fd57bf84170(11), uri="/")
D [18/May/2010:13:46:01 -0400] pullmethod="ippget"
D [18/May/2010:13:46:01 -0400] notify-lease-duration=86400
D [18/May/2010:13:46:01 -0400] notify-time-interval=0
D [18/May/2010:13:46:01 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [18/May/2010:13:46:01 -0400] Added subscription 4 for server
D [18/May/2010:13:46:01 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:01 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [18/May/2010:13:46:01 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:02 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:02 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:02 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [18/May/2010:13:46:02 -0400] Get-Notifications /
D [18/May/2010:13:46:02 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:02 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:03 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 14 POST /printers/HP-LaserJet-P1006 HTTP/1.1
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:03 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 14 1.1 Print-Job 1
D [18/May/2010:13:46:03 -0400] Print-Job ipp://localhost/printers/HP-LaserJet-P1006
D [18/May/2010:13:46:03 -0400] [Job ???] Auto-typing file...
I [18/May/2010:13:46:03 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(----J-)
D [18/May/2010:13:46:03 -0400] add_job: requesting-user-name="ending"
D [18/May/2010:13:46:03 -0400] Adding default job-sheets values "none,none"...
I [18/May/2010:13:46:03 -0400] [Job 4] Adding start banner page "none".
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(----J-)
I [18/May/2010:13:46:03 -0400] [Job 4] Adding end banner page "none".
I [18/May/2010:13:46:03 -0400] [Job 4] File of type application/vnd.cups-banner queued by "ending".
D [18/May/2010:13:46:03 -0400] [Job 4] hold_until=0
I [18/May/2010:13:46:03 -0400] [Job 4] Queued on "HP-LaserJet-P1006" by "ending".
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(----J-)
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:03 -0400] [Job 4] job-sheets=none,none
D [18/May/2010:13:46:03 -0400] [Job 4] argv[0]="HP-LaserJet-P1006"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[1]="4"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[2]="ending"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[3]="Test Page"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[4]="1"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[5]="job-uuid=urn:uuid:9b8cf2b9-91a1-38b7-75a2-c39189c4e792 job-originating-host-name=localhost"
D [18/May/2010:13:46:03 -0400] [Job 4] argv[6]="/var/spool/cups/d00004-001"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[10]="SERVER_ADMIN=root@bigby"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.3"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[13]="TZ=US/Eastern"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[14]="USER=root"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[17]="IPP_PORT=631"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[18]="CHARSET=utf-8"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[19]="LANG=en_US.UTF-8"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[20]="PPD=/etc/cups/ppd/HP-LaserJet-P1006.ppd"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[21]="RIP_MAX_CACHE=1014279k"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[23]="DEVICE_URI=hp:/usb/HP_LaserJet_P1006?serial=AC233BA"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[24]="PRINTER_INFO=Hewlett-Packard HP LaserJet P1006"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[25]="PRINTER_LOCATION=bigby"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[26]="PRINTER=HP-LaserJet-P1006"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[27]="CUPS_FILETYPE=document"
D [18/May/2010:13:46:03 -0400] [Job 4] envp[28]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-P1006"
I [18/May/2010:13:46:03 -0400] [Job 4] Started filter /usr/lib/cups/filter/bannertops (PID 1987)
I [18/May/2010:13:46:03 -0400] [Job 4] Started filter /usr/lib/cups/filter/pstopdf (PID 1988)
I [18/May/2010:13:46:03 -0400] [Job 4] Started filter /usr/lib/cups/filter/pdftopdf (PID 1989)
I [18/May/2010:13:46:03 -0400] [Job 4] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1990)
I [18/May/2010:13:46:03 -0400] [Job 4] Started backend /usr/lib/cups/backend/hp (PID 1991)
D [18/May/2010:13:46:03 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:03 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-LaserJet-P1006) from localhost
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:03 -0400] [Job 4] Getting input from file
D [18/May/2010:13:46:03 -0400] [Job 4] foomatic-rip version 4.0.4.217 running...
D [18/May/2010:13:46:03 -0400] [Job 4] Parsing PPD file ...
D [18/May/2010:13:46:03 -0400] [Job 4] Added option Resolution
D [18/May/2010:13:46:03 -0400] [Job 4] Added option PageSize
D [18/May/2010:13:46:03 -0400] [Job 4] Added option Model
D [18/May/2010:13:46:03 -0400] [Job 4] Added option PrintoutMode
D [18/May/2010:13:46:03 -0400] [Job 4] Added option MediaType
D [18/May/2010:13:46:03 -0400] [Job 4] Added option InputSlot
D [18/May/2010:13:46:03 -0400] [Job 4] Added option Quality
D [18/May/2010:13:46:03 -0400] [Job 4] Added option ImageableArea
D [18/May/2010:13:46:03 -0400] [Job 4] Added option PaperDimension
D [18/May/2010:13:46:03 -0400] [Job 4] Added option Font
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] Parameter Summary
D [18/May/2010:13:46:03 -0400] [Job 4] -----------------
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] Spooler: cups
D [18/May/2010:13:46:03 -0400] [Job 4] Printer: HP-LaserJet-P1006
D [18/May/2010:13:46:03 -0400] [Job 4] Shell: /bin/bash
D [18/May/2010:13:46:03 -0400] [Job 4] PPD file: /etc/cups/ppd/HP-LaserJet-P1006.ppd
D [18/May/2010:13:46:03 -0400] [Job 4] ATTR file:
D [18/May/2010:13:46:03 -0400] [Job 4] Printer model: HP LaserJet p1006 hpijs, 3.10.2, requires proprietary plugin
D [18/May/2010:13:46:03 -0400] [Job 4] load_banner(filename="/var/spool/cups/d00004-001")
D [18/May/2010:13:46:03 -0400] [Job 4] Job title: Test Page
D [18/May/2010:13:46:03 -0400] [Job 4] File(s) to be printed:
D [18/May/2010:13:46:03 -0400] [Job 4] <STDIN>
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [18/May/2010:13:46:03 -0400] [Job 4] Printing system options:
D [18/May/2010:13:46:03 -0400] [Job 4] Pondering option 'job-uuid=urn:uuid:9b8cf2b9-91a1-38b7-75a2-c39189c4e792'
D [18/May/2010:13:46:03 -0400] [Job 4] Unknown option job-uuid=urn:uuid:9b8cf2b9-91a1-38b7-75a2-c39189c4e792.
D [18/May/2010:13:46:03 -0400] [Job 4] Pondering option 'job-originating-host-name=localhost'
D [18/May/2010:13:46:03 -0400] [Job 4] Unknown option job-originating-host-name=localhost.
D [18/May/2010:13:46:03 -0400] [Job 4] Options from the PPD file:
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] ================================================
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] File: <STDIN>
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] ================================================
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:03 -0400] [Job 4] Page = 612x792; 18,14 to 594,778
D [18/May/2010:13:46:03 -0400] [Job 4] pstopdf 5 args: 4 ending Test Page 1 job-uuid=urn:uuid:9b8cf2b9-91a1-38b7-75a2-c39189c4e792 job-originating-host-name=localhost
D [18/May/2010:13:46:03 -0400] [Job 4] PPD: /etc/cups/ppd/HP-LaserJet-P1006.ppd
D [18/May/2010:13:46:03 -0400] [Job 4] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [18/May/2010:13:46:03 -0400] [Job 4] PNG image: 192x128x8, color_type=2 (RGB)
D [18/May/2010:13:46:03 -0400] PID 1987 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [18/May/2010:13:46:03 -0400] [Job 4] Resolution: 600
D [18/May/2010:13:46:03 -0400] [Job 4] Page size: letter
D [18/May/2010:13:46:03 -0400] [Job 4] Width: , height: , absolute margins: 0, 0, ,
D [18/May/2010:13:46:03 -0400] [Job 4] Relative margins: , , ,
D [18/May/2010:13:46:03 -0400] [Job 4] PPD options: -r600
D [18/May/2010:13:46:03 -0400] [Job 4] PostScript to be injected:
D [18/May/2010:13:46:03 -0400] [Job 4] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r600 - -
D [18/May/2010:13:46:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:03 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [18/May/2010:13:46:03 -0400] Get-Notifications /
D [18/May/2010:13:46:03 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:03 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:03 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [18/May/2010:13:46:03 -0400] Get-Job-Attributes ipp://localhost/jobs/4
D [18/May/2010:13:46:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:03 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [18/May/2010:13:46:03 -0400] Get-Notifications /
D [18/May/2010:13:46:03 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:03 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:03 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [18/May/2010:13:46:03 -0400] cupsdCloseClient: 16
D [18/May/2010:13:46:03 -0400] PID 1988 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [18/May/2010:13:46:03 -0400] [Job 4] Filetype: PDF
D [18/May/2010:13:46:03 -0400] [Job 4] Storing temporary files in /var/spool/cups/tmp
D [18/May/2010:13:46:03 -0400] PID 1989 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [18/May/2010:13:46:03 -0400] [Job 4] File contains 1 pages
D [18/May/2010:13:46:03 -0400] [Job 4] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet P1005" -r600 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-L358x8
D [18/May/2010:13:46:03 -0400] [Job 4] Starting process "kid3" (generation 1)
D [18/May/2010:13:46:03 -0400] [Job 4] Starting process "kid4" (generation 2)
D [18/May/2010:13:46:03 -0400] [Job 4] Starting process "renderer" (generation 2)
D [18/May/2010:13:46:03 -0400] [Job 4] JCL: %-12345X@PJL
D [18/May/2010:13:46:03 -0400] [Job 4] <job data>
D [18/May/2010:13:46:03 -0400] [Job 4]
D [18/May/2010:13:46:04 -0400] [Job 4] prnt/hpijs/hpijs.cpp 638: unable to open PrintContext object err=48
D [18/May/2010:13:46:04 -0400] [Job 4] GPL Ghostscript 8.71: Can't start ijs server "hpijs"
D [18/May/2010:13:46:04 -0400] [Job 4] renderer exited with status 1
D [18/May/2010:13:46:04 -0400] [Job 4] Possible error on renderer command line or PostScript error. Check options.STATE: +connecting-to-device
D [18/May/2010:13:46:04 -0400] [Job 4] Kid3 exit status: 3
D [18/May/2010:13:46:04 -0400] PID 1990 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [18/May/2010:13:46:04 -0400] [Job 4] STATE: -connecting-to-device
D [18/May/2010:13:46:04 -0400] [Job 4] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [18/May/2010:13:46:21 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [18/May/2010:13:46:21 -0400] cupsdReadClient: 16 POST /jobs/ HTTP/1.1
D [18/May/2010:13:46:21 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:21 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:21 -0400] cupsdReadClient: 16 1.1 Cancel-Job 1
D [18/May/2010:13:46:21 -0400] Cancel-Job ipp://localhost/jobs/3
D [18/May/2010:13:46:21 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:21 -0400] cupsdMarkDirty(-----S)
I [18/May/2010:13:46:21 -0400] [Job 3] Job purged by "ending"
I [18/May/2010:13:46:21 -0400] [Job 3] Purged by "ending".
D [18/May/2010:13:46:21 -0400] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/3) from localhost
D [18/May/2010:13:46:21 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:21 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [18/May/2010:13:46:21 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [18/May/2010:13:46:21 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [18/May/2010:13:46:21 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:21 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [18/May/2010:13:46:21 -0400] Get-Notifications /
D [18/May/2010:13:46:21 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:21 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:21 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [18/May/2010:13:46:21 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [18/May/2010:13:46:21 -0400] cupsdCloseClient: 17
I [18/May/2010:13:46:24 -0400] [Job 4] ready to print
D [18/May/2010:13:46:24 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:24 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:24 -0400] PID 1991 (/usr/lib/cups/backend/hp) exited with no errors.
D [18/May/2010:13:46:24 -0400] cupsdMarkDirty(-----S)
E [18/May/2010:13:46:24 -0400] [Job 4] Job stopped due to filter errors; please consult the error_log file for details.
D [18/May/2010:13:46:24 -0400] cupsdMarkDirty(----J-)
D [18/May/2010:13:46:24 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:24 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:24 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [18/May/2010:13:46:24 -0400] Get-Notifications /
D [18/May/2010:13:46:24 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:24 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:24 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [18/May/2010:13:46:24 -0400] Get-Notifications /
D [18/May/2010:13:46:24 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:24 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:24 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:24 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [18/May/2010:13:46:24 -0400] Get-Printer-Attributes ipp://bigby:0/printers/HP-LaserJet-P1006
D [18/May/2010:13:46:24 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://bigby:0/printers/HP-LaserJet-P1006) from localhost
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:24 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [18/May/2010:13:46:24 -0400] Get-Job-Attributes ipp://localhost/jobs/4
D [18/May/2010:13:46:24 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [18/May/2010:13:46:24 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:24 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [18/May/2010:13:46:24 -0400] cupsdCloseClient: 15
D [18/May/2010:13:46:25 -0400] [Job 4] Unloading...
I [18/May/2010:13:46:27 -0400] Generating printcap /var/run/cups/printcap...
I [18/May/2010:13:46:27 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [18/May/2010:13:46:27 -0400] Saving subscriptions.conf...
D [18/May/2010:13:46:27 -0400] cupsdSetBusyState: Not busy
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Active clients
D [18/May/2010:13:46:29 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1
D [18/May/2010:13:46:29 -0400] Get-Job-Attributes ipp://localhost/jobs/4
D [18/May/2010:13:46:29 -0400] [Job 4] Loading attributes...
D [18/May/2010:13:46:29 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Not busy
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Active clients
D [18/May/2010:13:46:29 -0400] cupsdAuthorize: No authentication data provided.
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1
D [18/May/2010:13:46:29 -0400] Cancel-Subscription /
D [18/May/2010:13:46:29 -0400] cupsdIsAuthorized: requesting-user-name="ending"
D [18/May/2010:13:46:29 -0400] cupsdMarkDirty(-----S)
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:29 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Dirty files
D [18/May/2010:13:46:29 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [18/May/2010:13:46:29 -0400] cupsdCloseClient: 17
D [18/May/2010:13:46:29 -0400] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [18/May/2010:13:46:29 -0400] cupsdSetBusyState: Active clients and dirty files
D [18/May/2010:13:46:29 -0400] cupsdAuthorize: No authentication data provided.
```

```
E [18/May/2010:13:50:10 -0400] [Job 5] Job stopped due to filter errors; please consult the error_log file for details.
D [18/May/2010:13:50:10 -0400] [Job 5] The following messages were recorded from 13:49:49 to 13:50:09
D [18/May/2010:13:50:10 -0400] [Job 5] Adding start banner page "none".
D [18/May/2010:13:50:10 -0400] [Job 5] Adding end banner page "none".
D [18/May/2010:13:50:10 -0400] [Job 5] File of type application/postscript queued by "ending".
D [18/May/2010:13:50:10 -0400] [Job 5] hold_until=0
D [18/May/2010:13:50:10 -0400] [Job 5] Queued on "HP-LaserJet-P1006" by "ending".
D [18/May/2010:13:50:10 -0400] [Job 5] job-sheets=none,none
D [18/May/2010:13:50:10 -0400] [Job 5] argv[0]="HP-LaserJet-P1006"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[1]="5"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[2]="ending"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[3]="Test Page"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[4]="1"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[5]="PageSize=Letter job-uuid=urn:uuid:9d9c8728-01f8-35ef-4343-03fab99cec28 job-originating-host-name=localhost"
D [18/May/2010:13:50:10 -0400] [Job 5] argv[6]="/var/spool/cups/d00005-001"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[8]="HOME=/var/spool/cups/tmp"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[10]="SERVER_ADMIN=root@bigby"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[11]="SOFTWARE=CUPS/1.4.3"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[13]="TZ=US/Eastern"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[14]="USER=root"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[17]="IPP_PORT=631"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[18]="CHARSET=utf-8"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[19]="LANG=en_US.UTF-8"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[20]="PPD=/etc/cups/ppd/HP-LaserJet-P1006.ppd"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[21]="RIP_MAX_CACHE=1014279k"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[22]="CONTENT_TYPE=application/postscript"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[23]="DEVICE_URI=hp:/usb/HP_LaserJet_P1006?serial=AC233BA"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[24]="PRINTER_INFO=Hewlett-Packard HP LaserJet P1006"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[25]="PRINTER_LOCATION=bigby"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[26]="PRINTER=HP-LaserJet-P1006"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[27]="CUPS_FILETYPE=document"
D [18/May/2010:13:50:10 -0400] [Job 5] envp[28]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-P1006"
D [18/May/2010:13:50:10 -0400] [Job 5] Started filter /usr/lib/cups/filter/pstopdf (PID 2135)
D [18/May/2010:13:50:10 -0400] [Job 5] Started filter /usr/lib/cups/filter/pdftopdf (PID 2136)
D [18/May/2010:13:50:10 -0400] [Job 5] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2137)
D [18/May/2010:13:50:10 -0400] [Job 5] Started backend /usr/lib/cups/backend/hp (PID 2138)
D [18/May/2010:13:50:10 -0400] [Job 5] pstopdf 6 args: 5 ending Test Page 1 PageSize=Letter job-uuid=urn:uuid:9d9c8728-01f8-35ef-4343-03fab99cec28 job-originating-host-name=localhost /var/spool/cups/d00005-001
D [18/May/2010:13:50:10 -0400] [Job 5] PPD: /etc/cups/ppd/HP-LaserJet-P1006.ppd
D [18/May/2010:13:50:10 -0400] [Job 5] Getting input from file 
D [18/May/2010:13:50:10 -0400] [Job 5] foomatic-rip version 4.0.4.217 running...
D [18/May/2010:13:50:10 -0400] [Job 5] Parsing PPD file ...
D [18/May/2010:13:50:10 -0400] [Job 5] Added option Resolution
D [18/May/2010:13:50:10 -0400] [Job 5] Added option PageSize
D [18/May/2010:13:50:10 -0400] [Job 5] Added option Model
D [18/May/2010:13:50:10 -0400] [Job 5] Added option PrintoutMode
D [18/May/2010:13:50:10 -0400] [Job 5] Added option MediaType
D [18/May/2010:13:50:10 -0400] [Job 5] Added option InputSlot
D [18/May/2010:13:50:10 -0400] [Job 5] Added option Quality
D [18/May/2010:13:50:10 -0400] [Job 5] Added option ImageableArea
D [18/May/2010:13:50:10 -0400] [Job 5] Added option PaperDimension
D [18/May/2010:13:50:10 -0400] [Job 5] Added option Font
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] Parameter Summary
D [18/May/2010:13:50:10 -0400] [Job 5] -----------------
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] Spooler: cups
D [18/May/2010:13:50:10 -0400] [Job 5] Printer: HP-LaserJet-P1006
D [18/May/2010:13:50:10 -0400] [Job 5] Shell: /bin/bash
D [18/May/2010:13:50:10 -0400] [Job 5] PPD file: /etc/cups/ppd/HP-LaserJet-P1006.ppd
D [18/May/2010:13:50:10 -0400] [Job 5] ATTR file: 
D [18/May/2010:13:50:10 -0400] [Job 5] Printer model: HP LaserJet p1006 hpijs, 3.10.2, requires proprietary plugin
D [18/May/2010:13:50:10 -0400] [Job 5] Job title: Test Page
D [18/May/2010:13:50:10 -0400] [Job 5] File(s) to be printed:
D [18/May/2010:13:50:10 -0400] [Job 5] <STDIN>
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [18/May/2010:13:50:10 -0400] [Job 5] Printing system options:
D [18/May/2010:13:50:10 -0400] [Job 5] Pondering option 'job-uuid=urn:uuid:9d9c8728-01f8-35ef-4343-03fab99cec28'
D [18/May/2010:13:50:10 -0400] [Job 5] Unknown option job-uuid=urn:uuid:9d9c8728-01f8-35ef-4343-03fab99cec28.
D [18/May/2010:13:50:10 -0400] [Job 5] Pondering option 'job-originating-host-name=localhost'
D [18/May/2010:13:50:10 -0400] [Job 5] Unknown option job-originating-host-name=localhost.
D [18/May/2010:13:50:10 -0400] [Job 5] Options from the PPD file:
D [18/May/2010:13:50:10 -0400] [Job 5] Pondering option 'PageSize=Letter'
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] ================================================
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] File: <STDIN>
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] ================================================
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] Resolution: 600
D [18/May/2010:13:50:10 -0400] [Job 5] Page size: Letter
D [18/May/2010:13:50:10 -0400] [Job 5] Width: 612, height: 792, absolute margins: 18, 14.39999961853, 594, 777.599975585938
D [18/May/2010:13:50:10 -0400] [Job 5] Relative margins: 18, 14.39999961853, 18, 14.400024414062
D [18/May/2010:13:50:10 -0400] [Job 5] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [18/May/2010:13:50:10 -0400] [Job 5] PostScript to be injected: 
D [18/May/2010:13:50:10 -0400] [Job 5] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [18/May/2010:13:50:10 -0400] [Job 5] Filetype: PDF
D [18/May/2010:13:50:10 -0400] [Job 5] Storing temporary files in /var/spool/cups/tmp
D [18/May/2010:13:50:10 -0400] [Job 5] File contains 1 pages
D [18/May/2010:13:50:10 -0400] [Job 5] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet P1005" -r600 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-zFxtkl 
D [18/May/2010:13:50:10 -0400] [Job 5] Starting process "kid3" (generation 1)
D [18/May/2010:13:50:10 -0400] [Job 5] Starting process "kid4" (generation 2)
D [18/May/2010:13:50:10 -0400] [Job 5] Starting process "renderer" (generation 2)
D [18/May/2010:13:50:10 -0400] [Job 5] JCL: %-12345X@PJL
D [18/May/2010:13:50:10 -0400] [Job 5] <job data> 
D [18/May/2010:13:50:10 -0400] [Job 5] 
D [18/May/2010:13:50:10 -0400] [Job 5] prnt/hpijs/hpijs.cpp 638: unable to open PrintContext object err=48
D [18/May/2010:13:50:10 -0400] [Job 5] GPL Ghostscript 8.71: Can't start ijs server "hpijs"
D [18/May/2010:13:50:10 -0400] [Job 5] renderer exited with status 1
D [18/May/2010:13:50:10 -0400] [Job 5] Possible error on renderer command line or PostScript error. Check options.STATE: +connecting-to-device
D [18/May/2010:13:50:10 -0400] [Job 5] Kid3 exit status: 3
D [18/May/2010:13:50:10 -0400] [Job 5] STATE: -connecting-to-device
D [18/May/2010:13:50:10 -0400] [Job 5] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [18/May/2010:13:50:10 -0400] [Job 5] ready to print
D [18/May/2010:13:50:10 -0400] [Job 5] End of messages
D [18/May/2010:13:50:10 -0400] [Job 5] printer-state=3(idle)
D [18/May/2010:13:50:10 -0400] [Job 5] printer-state-message="ready to print"
D [18/May/2010:13:50:10 -0400] [Job 5] printer-state-reasons=none
```

Anyone have any ideas?

---

### Post by arsenic23 on 2010-05-18
OK, I fiddle around a bit more, apt-get purging and reinstalling things and now I'm back to the original problem (mostly).

Running **hp-check -t** give me:
```
hp-check[9564]: info: :
Initializing. Please wait...
Ubuntu

10.04

scheduler is running

1.4.3

Linux bigby 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

hp-check[9564]: info: :
hp-check[9564]: info: :---------------
hp-check[9564]: info: :| SYSTEM INFO |
hp-check[9564]: info: :---------------
hp-check[9564]: info: :
hp-check[9564]: info: :Basic system information:
hp-check[9564]: info: :Linux bigby 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
hp-check[9564]: info: :
hp-check[9564]: info: :Distribution:
hp-check[9564]: info: :ubuntu 10.04
hp-check[9564]: info: :
hp-check[9564]: info: :Checking Python version...
hp-check[9564]: info: :OK, version 2.6.5 installed
hp-check[9564]: info: :
hp-check[9564]: info: :Checking PyQt 4.x version...
hp-check[9564]: info: :OK, version 4.7.2 installed.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for CUPS...
hp-check[9564]: info: :Status: scheduler is running
hp-check[9564]: info: :Version: 1.4.3
hp-check[9564]: info: :error_log is set to level: warn
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dbus/python-dbus...
hp-check[9564]: info: :dbus daemon is running.
hp-check[9564]: info: :python-dbus version: 0.83.0
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :------------------------------------
hp-check[9564]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[9564]: info: :------------------------------------
hp-check[9564]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: CUPS - Common Unix Printing System...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: CUPS devel- Common Unix Printing System development files...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libcupsimage2-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libdbus-1-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes build-essential
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libcrypto - OpenSSL cryptographic library...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libjpeg62-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libsnmp-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libpthread - POSIX threads library...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libtool
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libusb-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: make - GNU make utility to maintain groups of programs...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: PolicyKit - Administrative policy framework...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python DBus - Python bindings for DBus...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes python-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python XML libraries...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python 2.3 or greater - Required for fax functionality...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Python 2.2 or greater - Python programming language...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: Reportlab - PDF library for Python...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: SANE - Scanning library...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
hp-check[9564]: info: :To install this dependency, execute this command:
hp-check[9564]: info: :sudo aptitude install --assume-yes libsane-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: scanimage - Shell scanning program...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for dependency: xsane - Graphical scanner frontend for SANE...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :----------------------
hp-check[9564]: info: :| HPLIP INSTALLATION |
hp-check[9564]: info: :----------------------
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :Currently installed HPLIP version...
hp-check[9564]: info: :HPLIP 3.10.2 currently installed in '/usr/share/hplip'.
hp-check[9564]: info: :
hp-check[9564]: info: :Current contents of '/etc/hp/hplip.conf' file:
hp-check[9564]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.2rc1.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no

hp-check[9564]: info: :
hp-check[9564]: info: :Current contents of '/var/lib/hp/hplip.state' file:
hp-check[9564]: info: :# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0


hp-check[9564]: info: :
hp-check[9564]: info: :Current contents of '~/.hplip/hplip.conf' file:
hp-check[9564]: info: :[last_used]
device_uri = hp:/usb/HP_LaserJet_P1006?serial=AC233BA

[installation]
version = 3.10.2rc1.9
date_time = 05/18/2010 23:47:07


hp-check[9564]: info: :
hp-check[9564]: info: :--------------------------
hp-check[9564]: info: :| DISCOVERED USB DEVICES |
hp-check[9564]: info: :--------------------------
hp-check[9564]: info: :
hp-check[9564]: info: :  Device URI                                Model                
hp-check[9564]: info: :  ----------------------------------------  ---------------------
hp-check[9564]: info: :  hp:/usb/HP_LaserJet_P1006?serial=AC233BA  HP LaserJet P1006    
hp-check[9564]: info: :
hp-check[9564]: info: :---------------------------------
hp-check[9564]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[9564]: info: :---------------------------------
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :HP-LaserJet-P1006
hp-check[9564]: info: :-----------------
hp-check[9564]: info: :Type: Printer
hp-check[9564]: info: :Device URI: hp:/usb/HP_LaserJet_P1006?serial=AC233BA
hp-check[9564]: info: :PPD: /etc/cups/ppd/HP-LaserJet-P1006.ppd
hp-check[9564]: info: :PPD Description: HP LaserJet P1006 Foomatic/foo2xqx (recommended)
hp-check[9564]: info: :Printer status: printer HP-LaserJet-P1006 is idle.  enabled since Tue 18 May 2010 11:35:29 PM EDT
error: Required plug-in status: Not installed
hp-check[9564]: info: :Communication status: Good
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :----------------------
hp-check[9564]: info: :| SANE CONFIGURATION |
hp-check[9564]: info: :----------------------
hp-check[9564]: info: :
hp-check[9564]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[9564]: info: :'hpaio' in '/etc/sane.d/dll.d/hplip'...
hp-check[9564]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking output of 'scanimage -L'...
hp-check[9564]: info: :device `plustek:libusb:001:007' is a Canon CanoScan N1240U/LiDE30 flatbed scanner

hp-check[9564]: info: :
hp-check[9564]: info: :---------------------
hp-check[9564]: info: :| PYTHON EXTENSIONS |
hp-check[9564]: info: :---------------------
hp-check[9564]: info: :
hp-check[9564]: info: :Checking 'cupsext' CUPS extension...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking 'pcardext' Photocard extension...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking 'hpmudext' I/O extension...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :Checking 'scanext' SANE scanning extension...
hp-check[9564]: info: :OK, found.
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :
hp-check[9564]: info: :-----------------
hp-check[9564]: info: :| USB I/O SETUP |
hp-check[9564]: info: :-----------------
hp-check[9564]: info: :
hp-check[9564]: info: :Checking for permissions of USB attached printers...
hp-check[9564]: info: :
HP Device 0x3e17 at 001:011: 
hp-check[9564]: info: :    Device URI: hp:/usb/HP_LaserJet_P1006?serial=AC233BA
hp-check[9564]: info: :    Device node: /dev/bus/usb/001/011
hp-check[9564]: info: :    Mode: 0664
hp-check[9564]: info: :
hp-check[9564]: info: :---------------
hp-check[9564]: info: :| USER GROUPS |
hp-check[9564]: info: :---------------
hp-check[9564]: info: :
hp-check[9564]: info: :ending adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
hp-check[9564]: info: :User member of group 'lpadmin'.
hp-check[9564]: info: :
hp-check[9564]: info: :-----------
hp-check[9564]: info: :| SUMMARY |
hp-check[9564]: info: :-----------
hp-check[9564]: info: :
error: 10 errors and/or warnings.
hp-check[9564]: info: :
hp-check[9564]: info: :Summary of needed commands to run to satisfy missing dependencies:
hp-check[9564]: info: :sudo aptitude install --assume-yes libcupsimage2-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes libdbus-1-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes build-essential
hp-check[9564]: info: :sudo aptitude install --assume-yes libjpeg62-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes libsnmp-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes libtool
hp-check[9564]: info: :sudo aptitude install --assume-yes libusb-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes python-dev
hp-check[9564]: info: :sudo aptitude install --assume-yes libsane-dev
hp-check[9564]: info: :
hp-check[9564]: info: :Please refer to the installation instructions at:
hp-check[9564]: info: :http://hplip.sourceforge.net/install/index.html

hp-check[9564]: info: :
hp-check[9564]: info: :Done.
```

What seems important is this part:
```
hp-check[9564]: info: :
hp-check[9564]: info: :HP-LaserJet-P1006
hp-check[9564]: info: :-----------------
hp-check[9564]: info: :Type: Printer
hp-check[9564]: info: :Device URI: hp:/usb/HP_LaserJet_P1006?serial=AC233BA
hp-check[9564]: info: :PPD: /etc/cups/ppd/HP-LaserJet-P1006.ppd
hp-check[9564]: info: :PPD Description: HP LaserJet P1006 Foomatic/foo2xqx (recommended)
hp-check[9564]: info: :Printer status: printer HP-LaserJet-P1006 is idle.  enabled since Tue 18 May 2010 11:35:29 PM EDT
error: Required plug-in status: Not installed
hp-check[9564]: info: :Communication status: Good
hp-check[9564]: info: :
```

I notice the error is that I don't have the required plugin installed.  Well that should be hplip, right?  I most certainly do have it installed and it checks out fine.  Am I missing something?

---

### Post by arsenic23 on 2010-05-19
OK!  Problem solved.

I had to purge and reinstall cups, hpijs, and hplip.  Then I had to run hp-setup as root.  It would not download the plugin, but gave me a GUI error (no errors in the console though).  It then continued setup.

Restarting cups and then resetting my printer got me printing again, and now when I turn on or plug in my printer the little black status window no longer pops up.

Everything is working.

---

### Post by starlinq on 2011-05-03
> **arsenic23 said:**
> OK!  Problem solved.

I had to purge and reinstall cups, hpijs, and hplip.  Then I had to run hp-setup as root.  It would not download the plugin, but gave me a GUI error (no errors in the console though).  It then continued setup.

Restarting cups and then resetting my printer got me printing again, and now when I turn on or plug in my printer the little black status window no longer pops up.

Everything is working.

Hi arsenic,

Your information has helped me to solve a printing problem with Lexmark printer.

Thank you!

starlinq

---

### Post by amishtrucker on 2011-05-31
When you run HP-setup it needs to be run as root:   sudo hp-setup.

---

### Post by KutWrite on 2011-06-01
This may be similar, but I don't know enough to do "run as root" type of things w/o some instructions.  Here's my problem:

My HP 845c printer only prints text files from gedit
Won't print rtf from Libre Office
Won't print jpgs or gifs from any image handling pgm.
Won't print pdfs from Firefox w/plugin, image viewer or Acrobat
Document print status shows "stopped" - thinks it printed per brief msg on screen

When I try to print...

HPLIP Device Status box first says:
Started a print job 
(when restarting an existing job still in queue, this has a yellow triangle around a "!")
Then:
Print job is processing (name)

Then, with a yellow triangle around the "!":
! Print job has completed  (but it never printed)

New box with red " - " says:
Print Error
There was a problem processing document xxx.rtf (job xx)
Diagnose    OK "

When I click "Diagnose" & go through the Wizard:
Little box: HLIP Device status: (printer name) Idle"

In troubleshooter box:
"E [31/May/2011:21:01:25 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET 845C @ Dan-Toshiba: -2"

CUPS error: 

HP 845c USB printer
Ubuntu 11.04
latest drivers and HPLIP
tried plugging and unplugging, deleting & reinstalling printer and HPLIP
Tried running printer direcly via USB w/o HPLIP

- - - - - -

```
Error Log Messages:

E [31/May/2011:20:50:08 -0700] [Job 58] Job stopped due to filter errors; please consult the error_log file for details.
D [31/May/2011:20:50:08 -0700] [Job 58] The following messages were recorded from 20:50:00 to 20:50:08
D [31/May/2011:20:50:08 -0700] [Job 58] Adding start banner page "none".
D [31/May/2011:20:50:08 -0700] [Job 58] Adding end banner page "none".
D [31/May/2011:20:50:08 -0700] [Job 58] File of type application/vnd.cups-banner queued by "daniel".
D [31/May/2011:20:50:08 -0700] [Job 58] hold_until=0
D [31/May/2011:20:50:08 -0700] [Job 58] Queued on "DESKJET-845C" by "daniel".
D [31/May/2011:20:50:09 -0700] [Job 58] job-sheets=none,none
D [31/May/2011:20:50:09 -0700] [Job 58] argv[0]="DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[1]="58"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[2]="daniel"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[3]="Test Page"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[4]="1"
D [31/May/2011:20:50:09 -0700] [Job 58] argv[5]="job-uuid=urn:uuid:fc1d94d1-adba-3475-575b-974b28b963ad job-originating-host-name=localhost time-at-creation=1306900200 time-at-processing=1306900200 AP_D_InputSlot="
D [31/May/2011:20:50:09 -0700] [Job 58] argv[6]="/var/spool/cups/d00058-001"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[8]="HOME=/var/spool/cups/tmp"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[10]="SERVER_ADMIN=root@Dan-Toshiba"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[11]="SOFTWARE=CUPS/1.4.6"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[13]="USER=root"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[14]="CUPS_SERVER=localhost"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[16]="IPP_PORT=631"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[17]="CHARSET=utf-8"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[18]="LANG=en_US.UTF-8"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[19]="PPD=/etc/cups/ppd/DESKJET-845C.ppd"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[20]="RIP_MAX_CACHE=auto"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[22]="DEVICE_URI=hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[23]="PRINTER_INFO=HEWLETT-PACKARD DESKJET 845C"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[24]="PRINTER_LOCATION=Dan-Toshiba"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[25]="PRINTER=DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[26]="CUPS_FILETYPE=document"
D [31/May/2011:20:50:09 -0700] [Job 58] envp[27]="FINAL_CONTENT_TYPE=printer/DESKJET-845C"
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/bannertops (PID 3322)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pstopdf (PID 3323)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pdftopdf (PID 3324)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 3325)
D [31/May/2011:20:50:09 -0700] [Job 58] Started filter /usr/lib/cups/filter/hpcups (PID 3326)
D [31/May/2011:20:50:09 -0700] [Job 58] Started backend /usr/lib/cups/backend/hp (PID 3327)
D [31/May/2011:20:50:09 -0700] [Job 58] pstopdf 5 args: 58 daniel Test Page 1 job-uuid=urn:uuid:fc1d94d1-adba-3475-575b-974b28b963ad job-originating-host-name=localhost time-at-creation=1306900200 time-at-processing=1306900200 AP_D_InputSlot=
D [31/May/2011:20:50:09 -0700] [Job 58] PPD: /etc/cups/ppd/DESKJET-845C.ppd
D [31/May/2011:20:50:09 -0700] [Job 58] load_banner(filename="/var/spool/cups/d00058-001")
D [31/May/2011:20:50:09 -0700] [Job 58] Page = 612x792; 18,36 to 594,783
D [31/May/2011:20:50:09 -0700] [Job 58] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [31/May/2011:20:50:09 -0700] [Job 58] PNG image: 192x128x8, color_type=2 (RGB)
D [31/May/2011:20:50:09 -0700] [Job 58] Resolution:
D [31/May/2011:20:50:09 -0700] [Job 58] Page size: Letter
D [31/May/2011:20:50:09 -0700] [Job 58] Width: 612, height: 792, absolute margins: 18, 36, 594, 783
D [31/May/2011:20:50:09 -0700] [Job 58] Relative margins: 18, 36, 18, 9
D [31/May/2011:20:50:09 -0700] [Job 58] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [31/May/2011:20:50:09 -0700] [Job 58] PostScript to be injected:
D [31/May/2011:20:50:09 -0700] [Job 58] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [31/May/2011:20:50:09 -0700] [Job 58] mediaBox = [ 0.000000 0.000000 612.000000 792.000000 ]
D [31/May/2011:20:50:09 -0700] [Job 58] size = Letter
D [31/May/2011:20:50:09 -0700] [Job 58] STATE: +connecting-to-device
D [31/May/2011:20:50:09 -0700] [Job 58] prnt/hpcups/Pcl3Gui.cpp 75: Requested resolution not supported with requested printmodeprnt/hpcups/HPCupsFilter.cpp 420: m_Job initialization failed with error = 25STATE: -connecting-to-device
D [31/May/2011:20:50:09 -0700] [Job 58] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [31/May/2011:20:50:09 -0700] [Job 58] ready to print
D [31/May/2011:20:50:09 -0700] [Job 58] End of messages
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state=3(idle)
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state-message="ready to print"
D [31/May/2011:20:50:09 -0700] [Job 58] printer-state-reasons=none
E [31/May/2011:20:53:36 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET 845C @ Dan-Toshiba: -2

- - - - - -

Note: Near the bottom it says: 
Test Page printed = true   <------- But this statement is false


Other info:

Diagnostic Output (Advanced)
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DESKJET-845C (default)>,
 'cups_instance': None,
 'cups_queue': 'DESKJET-845C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 845C',
                       'printer-is-shared': True,
                       'printer-location': u'Dan-Toshiba',
                       'printer-make-and-model': u'HP Deskjet 845c, hpcups 3.11.5',
                       'printer-state': 3,
                       'printer-state-message': u'ready to print',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET-845C'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.11.5)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 5.2\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  agent1-ack                    False                                                     ',
                   '  agent1-desc                   Black cartridge                                           ',
                   '  agent1-dvc                    0                                                         ',
                   '  agent1-health                 0                                                         ',
                   '  agent1-health-desc            Good/OK                                                   ',
                   '  agent1-hp-ink                 False                                                     ',
                   '  agent1-id                     0                                                         ',
                   '  agent1-kind                   3                                                         ',
                   '  agent1-known                  False                                                     ',
                   '  agent1-level                  0                                                         ',
                   '  agent1-level-trigger          0                                                         ',
                   '  agent1-sku                    15 (C6615DN)                                              ',
                   '  agent1-type                   1                                                         ',
                   '  agent1-virgin                 False                                                     ',
                   '  back-end                      hp                                                        ',
                   "  cups-printers                 ['DESKJET-845C']                                          ",
                   '  cups-uri                      hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX                  ',
                   '  dev-file                                                                                ',
                   '  device-state                  1                                                         ',
                   '  device-uri                    hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX                  ',
                   '  deviceid                      MFG:HEWLETT-PACKARD;MDL:DESKJET                           ',
                   '                                845C;CMD:MLC,PCL,PML;CLASS:PRINTER;DESCRIPTION:Hewlett-Pac',
                   '                                kard DeskJet                                              ',
                   '                                845C;SERN:CN19Q1C0J9SX;VSTATUS:$HB0$AU0,ff,DN,IDLE,CUT;VP:',
                   '                                0800,FL,B0;                                               ',
                   '  duplexer                      0                                                         ',
                   '  error-state                   0                                                         ',
                   '  host                                                                                    ',
                   '  in-tray1                      0                                                         ',
                   '  in-tray2                      0                                                         ',
                   '  is-hp                         True                                                      ',
                   '  media-path                    1                                                         ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  photo-tray                    0                                                         ',
                   '  port                          1                                                         ',
                   '  r                             0                                                         ',
                   '  revision                      255                                                       ',
                   '  rg                            000                                                       ',
                   '  rr                            000000                                                    ',
                   '  rs                            000000000                                                 ',
                   '  serial                        CN19Q1C0J9SX                                              ',
                   '  status-code                   1000                                                      ',
                   '  status-desc                   Idle                                                      ',
                   '  supply-door                   0                                                         ',
                   '  top-door                      1                                                         ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    2                                                         ',
                   '  clean-type                    1                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   False                                                     ',
                   '  icon                          DESKJET_840C.png                                          ',
                   '  io-mfp-mode                   6                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         DeskJet_845C                                              ',
                   '  model-ui                      HP Deskjet 845c                                           ',
                   '  model1                        HP Deskjet 845c Printer                                   ',
                   '  model2                        HP Deskjet 845cvr Printer                                 ',
                   '  monitor-type                  0                                                         ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  plugin-reason                 0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  r0-agent1-kind                3                                                         ',
                   '  r0-agent1-sku                 15 (C6615DN)                                              ',
                   '  r0-agent1-type                1                                                         ',
                   '  r0-agent2-kind                3                                                         ',
                   '  r0-agent2-sku                 17 (C6625AN)                                              ',
                   '  r0-agent2-type                2                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   1                                                         ',
                   '  support-released              True                                                      ',
                   '  support-subtype               2202411                                                   ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   0.9.5                                                     ',
                   "  tech-class                    ['DJ8x5']                                                 ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     2                                                         ',
                   '  usb-pid                       2308                                                      ',
                   '  usb-vid                       1008                                                      ',
                   '  wifi-config                   0                                                         ',
                   '\x1b[01m',
                   'Status History (most recent first):\x1b[0m',
                   '\x1b[01m  Date/Time             Code   Status Description                        User      Job ID  \x1b[0m',
                   '  --------------------  -----  ----------------------------------------  --------  --------',
                   '  05/31/11 21:00:37     1000   Idle                                      daniel    0       ',
                   '  05/31/11 20:58:04     501    Print job has completed                   daniel    57      ',
                   '  05/31/11 20:57:56     500    Started a print job                       daniel    57      ',
                   '  05/31/11 20:50:08     501    Print job has completed                   daniel    58      ',
                   '  05/31/11 20:50:00     500    Started a print job                       daniel    58      ',
                   '  05/31/11 20:49:13     1000   Idle                                      daniel    0       ',
                   '  05/31/11 20:48:51     501    Print job has completed                   daniel    57      ',
                   '  05/31/11 20:48:42     500    Started a print job                       daniel    57      ',
                   '  05/31/11 20:16:40     1000   Idle                                      daniel    0       ',
                   '  05/31/11 17:45:07     501    Print job has completed                   daniel    56      ',
                   '  05/31/11 17:44:57     500    Started a print job                       daniel    56      ',
                   '  05/31/11 17:44:57     501    Print job has completed                   daniel    55      ',
                   '  05/31/11 17:43:46     500    Started a print job                       daniel    55      ',
                   '  05/31/11 17:43:20     501    Print job has completed                   daniel    54      ',
                   '  05/31/11 17:43:12     500    Started a print job                       daniel    54      ',
                   '  05/31/11 17:41:31     1000   Idle                                      daniel    0       ',
                   '  05/31/11 17:41:00     501    Print job has completed                   daniel    53      ',
                   '  05/31/11 17:40:51     500    Started a print job                       daniel    53      ',
                   '  05/31/11 17:38:00     501    Print job has completed                   daniel    52      ',
                   '  05/31/11 17:37:57     5021   Device is busy                            daniel    0       ',
                   '  05/31/11 17:37:50     500    Started a print job                       daniel    52      ',
                   '  05/31/11 17:37:50     1000   Idle                                      daniel    0       ',
                   '  05/31/11 17:35:22     501    Print job has completed                   daniel    50      ',
                   '  05/31/11 17:35:13     500    Started a print job                       daniel    50      ',
                   '  05/31/11 17:33:20     501    Print job has completed                   daniel    51      ',
                   '  05/31/11 17:33:02     500    Started a print job                       daniel    51      ',
                   '  05/31/11 17:31:27     501    Print job has completed                   daniel    50      ',
                   '  05/31/11 17:31:17     500    Started a print job                       daniel    50      ',
                   '  05/31/11 17:30:30     1000   Idle                                      daniel    0       ',
                   '  05/31/11 17:30:02     501    Print job has completed                   daniel    49      ',
                   '  05/31/11 17:29:53     500    Started a print job                       daniel    49      ',
                   '  05/31/11 17:29:15     1000   Idle                                      daniel    0       ',
                   '  05/31/11 17:29:04     501    Print job has completed                   daniel    49      ',
                   '  05/31/11 17:28:54     500    Started a print job                       daniel    49      ',
                   '  05/31/11 17:28:45     501    Print job has completed                   daniel    49      ',
                   '  05/31/11 17:28:35     500    Started a print job                       daniel    49      ',
                   '  05/31/11 17:24:32     501    Print job has completed                   daniel    48      ',
                   '  05/31/11 17:23:43     500    Started a print job                       daniel    48      ',
                   '  05/31/11 17:21:00     501    Print job has completed                   daniel    47      ',
                   '  05/31/11 17:20:14     500    Started a print job                       daniel    47      ',
                   '',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   ''],
                  0),
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.6',
                                 'device-uri': u'hp:/usb/DeskJet_845C?serial=CN19Q1C0J9SX',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [1270],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-left-margin-supported': [635, 317],
                                 'media-right-margin-supported': [635, 317],
                                 'media-source-supported': [u'auto',
                                                            u'photo',
                                                            u'top',
                                                            u'bottom',
                                                            u'envelope',
                                                            u'large-capacity',
                                                            u'manual',
                                                            u'alternate'],
                                 'media-supported': [u'oe_card3x5_3x5in',
                                                     u'om_hagaki_100.18x148.16mm',
                                                     u'oe_photo4x6_4x6in',
                                                     u'iso_a6_105x148mm',
                                                     u'oe_photo5x7_5x7in',
                                                     u'oe_card5x8_5x8in',
                                                     u'om_oufuku_200.02x148.16mm',
                                                     u'iso_a5_148x210mm',
                                                     u'jis_b5_182x257mm',
                                                     u'om_jb5_182.11x257.04mm',
                                                     u'na_executive_7.25x10.5in',
                                                     u'oe_16k_7.75x10.75in',
                                                     u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_legal_8.5x14in',
                                                     u'om_env-a2_110.99x146.05mm',
                                                     u'iso_c6_114x162mm',
                                                     u'jpn_chou4_90x205mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'jpn_chou3_120x235mm',
                                                     u'iso_c5_162x229mm',
                                                     u'om_env-b5_176.03x250.11mm',
                                                     u'custom_min_1x4in',
                                                     u'custom_max_8.5x14in'],
                                 'media-top-margin-supported': [317],
                                 'media-type-supported': [u'stationery',
                                                          u'photographic-glossy'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'output-mode-default': u'color',
                                 'output-mode-supported': [u'monochrome',
                                                           u'color'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pages-per-minute-color': 1,
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/DESKJET-845C.png',
                                 'printer-info': u'HEWLETT-PACKARD DESKJET 845C',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'Dan-Toshiba',
                                 'printer-make-and-model': u'HP Deskjet 845c, hpcups 3.11.5',
                                 'printer-more-info': u'http://localhost:631/printers/DESKJET-845C',
                                 'printer-name': u'DESKJET-845C',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': '(unknown IPP tag)',
                                 'printer-resolution-supported': '(unknown IPP tag)',
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1306900684,
                                 'printer-state-message': u'ready to print',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 167948,
                                 'printer-up-time': 1306900837,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/DESKJET-845C'],
                                 'queued-job-count': 2,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'InputSlot': u'Auto',
                                            u'MediaType': u'Plain',
                                            u'OutputMode': u'NormalGray',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Hewlett-Packard;MDL:DeskJet 845C;CLS:PRINTER;DES:DeskJet 845C;SN:CN19Q1C0J9SX;',
                      'device-info': u'HP DeskJet 845C USB CN19Q1C0J9SX HPLIP',
                      'device-location': u'',
                      'device-make-and-model': u'HP DeskJet 845C'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseAddress': '@LOCAL',
                          'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseOrder': 'allow,deny',
                          'BrowseRemoteProtocols': '',
                          'Browsing': 'On',
                          'DefaultAuthType': 'Basic',
                          'LogLevel': 'warn',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 222012L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_job_status': [(True,
                           57,
                           'DESKJET-845C',
                           'MiscInfo',
                           'Stopped',
                           {'PageSize': u'Letter',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 57,
                            'job-k-octets': 262,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/57',
                            'job-name': u'MiscInfo',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'daniel',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/hpcups failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1306900885,
                            'job-printer-uri': u'ipp://Dan-Toshiba:631/printers/DESKJET-845C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/57',
                            'job-uuid': u'urn:uuid:87ee4a99-55a7-3ddd-5744-de794cfad96f',
                            'printer-uri': u'ipp://localhost:631/printers/DESKJET-845C',
                            'time-at-completed': None,
                            'time-at-creation': 1306900122,
                            'time-at-processing': 1306900676}),
                          (False,
                           58,
                           'DESKJET-845C',
                           'Test Page',
                           'Stopped',
                           None)],
 'test_page_successful': True}
Page 9 (Error log fetch):
{'error_log': ['E [31/May/2011:21:01:25 -0700] Failed to update TXT record for HEWLETT-PACKARD DESKJET 845C @ Dan-Toshiba: -2'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'job_page_size': u'Letter',
 'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

---

### Post by genosse23 on 2012-11-03
Hi, 

I tried to purge and reinstall cups, hijs and hplip as suggested above, but when I start hp-setup as root, it is downloading files from hp, but then says: error: Plug-in file does not match ints dgital signature. File may have been corrupten or altered. Error code: 2. Exactly the same I have to reaad when I just plug-in the printer and the computer tries to download the driver automatically. What do I have to do?

Thanks for your help, Chris

---

