---
title: "Printer HP d1660 No print"
date: 2010-11-09
forum: General Help
---

### Post by TheTinyt1 on 2010-11-09
Ok; I've looked at all the threads that I can find on the HP Deskjet D1660. I am unable to print. I've also tried to manually install the hplip files with no help. The only thing that I can find says to use a driver 3.10.2 but all I can find is 3.10.6 and 3.10.6.15. But non of this is working. XP prints fine but I want Ubuntu to work fine too. This is why I bought this printer in the first place. 

I am running Ubuntu 10.10 on an emachine with a celeron micro processor and it has 2 gig memory. I have tried the usb cable in every usb slot available and ever thing else. 

When I go go print a job the hp panel shows that job is sent to printer and that the printer is printing it. Unfortunately it never get printed. I have tried even removing cups and hplip using synaptic and reinstalling them but no help.

Any help in this would be greatly appreciated...

Bright Blessings
Chuck 
TheTiny1

---

### Post by Version Dependency on 2010-11-09
My d1660 recently decided to stop printing correctly as well.  I found the following link helpful: [http://bloggervince.blogspot.com/2010/08/how-to-install-hp-d1660-in-ubuntu.html](http://bloggervince.blogspot.com/2010/08/how-to-install-hp-d1660-in-ubuntu.html)

You won't find 3.10.2 as suggested by the above link.  But choosing hpcups 3.10.6 solved the problem for me.  Hope it helps you.

---

### Post by TheTinyt1 on 2010-11-09
Thanks for the suggestions even if it doesn't work.

Already tried that one. No help. It's strange because the printer worked until the last cups update and then craped out. I have a feeling that the update is the problem but no way to go back and figure it out.

---

### Post by soad6 on 2010-12-13
Same issue here, but mines worse... The other computer a Win 7 computer recognizes this as a f4400 printer which isn't right so Ubuntu was the only way for me to print... Please someone help! And I try instructions above all that is avaliable is ver 3.10.6 --- 3.10.2 has been removed and no way to get it back

---

### Post by soad6 on 2010-12-13
Reinstalled Hpcups and Hplibcups from synaptic... also changed connection type from HP image to usb got this error from CUPS debug:

D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1
D [13/Dec/2010:18:30:28 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2010:18:30:28 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1
D [13/Dec/2010:18:30:28 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2010:18:30:28 -0500] [Job 1] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 8] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 9] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 10] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 11] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 13] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] [Job 14] Loading attributes...
D [13/Dec/2010:18:30:28 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:28 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:28 -0500] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [13/Dec/2010:18:30:28 -0500] Create-Printer-Subscription /
D [13/Dec/2010:18:30:28 -0500] cupsdCreateSubscription(con=0xb7980fb8(12), uri="/")
D [13/Dec/2010:18:30:28 -0500] pullmethod="ippget"
D [13/Dec/2010:18:30:28 -0500] notify-lease-duration=86400
D [13/Dec/2010:18:30:28 -0500] notify-time-interval=0
D [13/Dec/2010:18:30:28 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [13/Dec/2010:18:30:28 -0500] Added subscription 17 for server
D [13/Dec/2010:18:30:28 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:28 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [13/Dec/2010:18:30:28 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:30 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:30 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:30 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:30 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:30 -0500] Get-Notifications /
D [13/Dec/2010:18:30:30 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:30 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:30 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAcceptClient: 13 from localhost (Domain)
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 13 POST /printers/HP-Deskjet-D1600-series HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 13 1.1 Print-Job 1
D [13/Dec/2010:18:30:38 -0500] Print-Job ipp://localhost/printers/HP-Deskjet-D1600-series
D [13/Dec/2010:18:30:38 -0500] [Job ???] Auto-typing file...
I [13/Dec/2010:18:30:38 -0500] [Job ???] Request file type is application/vnd.cups-banner.
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(----J-)
D [13/Dec/2010:18:30:38 -0500] add_job: requesting-user-name="needlez"
D [13/Dec/2010:18:30:38 -0500] Adding default job-sheets values "none,none"...
I [13/Dec/2010:18:30:38 -0500] [Job 15] Adding start banner page "none".
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(----J-)
I [13/Dec/2010:18:30:38 -0500] [Job 15] Adding end banner page "none".
I [13/Dec/2010:18:30:38 -0500] [Job 15] File of type application/vnd.cups-banner queued by "needlez".
D [13/Dec/2010:18:30:38 -0500] [Job 15] hold_until=0
I [13/Dec/2010:18:30:38 -0500] [Job 15] Queued on "HP-Deskjet-D1600-series" by "needlez".
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(----J-)
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:38 -0500] [Job 15] job-sheets=none,none
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[0]="HP-Deskjet-D1600-series"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[1]="15"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[2]="needlez"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[3]="Test Page"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[4]="1"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[5]="job-uuid=urn:uuid:66225b08-8be7-342e-6f78-d2e614d1fd7c job-originating-host-name=localhost"
D [13/Dec/2010:18:30:38 -0500] [Job 15] argv[6]="/var/spool/cups/d00015-001"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[8]="HOME=/var/spool/cups/tmp"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[10]="SERVER_ADMIN=root@needlez-Satellite-A505"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[11]="SOFTWARE=CUPS/1.4.4"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[13]="USER=root"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[16]="IPP_PORT=631"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[17]="CHARSET=utf-8"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[18]="LANG=en_US.UTF-8"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[19]="PPD=/etc/cups/ppd/HP-Deskjet-D1600-series.ppd"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[20]="RIP_MAX_CACHE=auto"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[22]="DEVICE_URI=usb://HP/Deskjet%20D1600%20series?serial=CN02CCC2JJ05CT"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[23]="PRINTER_INFO=HP Deskjet D1600 series"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[24]="PRINTER_LOCATION=needlez-Satellite-A505"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[25]="PRINTER=HP-Deskjet-D1600-series"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[26]="CUPS_FILETYPE=document"
D [13/Dec/2010:18:30:38 -0500] [Job 15] envp[27]="FINAL_CONTENT_TYPE=printer/HP-Deskjet-D1600-series"
I [13/Dec/2010:18:30:38 -0500] [Job 15] Started filter /usr/lib/cups/filter/bannertops (PID 11475)
I [13/Dec/2010:18:30:38 -0500] [Job 15] Started filter /usr/lib/cups/filter/pstopdf (PID 11476)
I [13/Dec/2010:18:30:38 -0500] [Job 15] Started filter /usr/lib/cups/filter/pdftopdf (PID 11477)
I [13/Dec/2010:18:30:38 -0500] [Job 15] Started filter /usr/lib/cups/filter/foomatic-rip (PID 11478)
I [13/Dec/2010:18:30:38 -0500] [Job 15] Started backend /usr/lib/cups/backend/usb (PID 11479)
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-Deskjet-D1600-series) from localhost
D [13/Dec/2010:18:30:38 -0500] [Job 15] pstopdf 5 args: 15 needlez Test Page 1 job-uuid=urn:uuid:66225b08-8be7-342e-6f78-d2e614d1fd7c job-originating-host-name=localhost
D [13/Dec/2010:18:30:38 -0500] [Job 15] PPD: /etc/cups/ppd/HP-Deskjet-D1600-series.ppd
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] [Job 15] Getting input from file
D [13/Dec/2010:18:30:38 -0500] [Job 15] foomatic-rip version 4.0.5.223 running...
D [13/Dec/2010:18:30:38 -0500] [Job 15] Parsing PPD file ...
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option Resolution
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option PageSize
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option Model
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option PrintoutMode
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option InputSlot
D [13/Dec/2010:18:30:38 -0500] [Job 15] STATE: +connecting-to-device
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:38 -0500] [Job 15] Printer using device file "/dev/usblp0"...
D [13/Dec/2010:18:30:38 -0500] [Job 15] STATE: -connecting-to-device
D [13/Dec/2010:18:30:38 -0500] [Job 15] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0xb77e87f0)
D [13/Dec/2010:18:30:38 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option Duplex
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option DryTime
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option Quality
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option ImageableArea
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option PaperDimension
D [13/Dec/2010:18:30:38 -0500] [Job 15] Added option Font
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] Parameter Summary
D [13/Dec/2010:18:30:38 -0500] [Job 15] -----------------
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] Spooler: cups
D [13/Dec/2010:18:30:38 -0500] [Job 15] Printer: HP-Deskjet-D1600-series
D [13/Dec/2010:18:30:38 -0500] [Job 15] Shell: /bin/bash
D [13/Dec/2010:18:30:38 -0500] [Job 15] PPD file: /etc/cups/ppd/HP-Deskjet-D1600-series.ppd
D [13/Dec/2010:18:30:38 -0500] [Job 15] ATTR file:
D [13/Dec/2010:18:30:38 -0500] [Job 15] Printer model: HP Deskjet d1600 Series hpijs, 3.10.6
D [13/Dec/2010:18:30:38 -0500] [Job 15] Job title: Test Page
D [13/Dec/2010:18:30:38 -0500] [Job 15] File(s) to be printed:
D [13/Dec/2010:18:30:38 -0500] [Job 15] <STDIN>
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [13/Dec/2010:18:30:38 -0500] [Job 15] Printing system options:
D [13/Dec/2010:18:30:38 -0500] [Job 15] Pondering option 'job-uuid=urn:uuid:66225b08-8be7-342e-6f78-d2e614d1fd7c'
D [13/Dec/2010:18:30:38 -0500] [Job 15] Unknown option job-uuid=urn:uuid:66225b08-8be7-342e-6f78-d2e614d1fd7c.
D [13/Dec/2010:18:30:38 -0500] [Job 15] Pondering option 'job-originating-host-name=localhost'
D [13/Dec/2010:18:30:38 -0500] [Job 15] Unknown option job-originating-host-name=localhost.
D [13/Dec/2010:18:30:38 -0500] [Job 15] Options from the PPD file:
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] ================================================
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] File: <STDIN>
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] ================================================
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:38 -0500] [Job 15] load_banner(filename="/var/spool/cups/d00015-001")
D [13/Dec/2010:18:30:38 -0500] [Job 15] Page = 612x792; 18,36 to 594,783
D [13/Dec/2010:18:30:38 -0500] [Job 15] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [13/Dec/2010:18:30:38 -0500] [Job 15] PNG image: 192x128x8, color_type=2 (RGB)
D [13/Dec/2010:18:30:38 -0500] PID 11475 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [13/Dec/2010:18:30:38 -0500] [Job 15] Resolution: 600
D [13/Dec/2010:18:30:38 -0500] [Job 15] Page size: Letter
D [13/Dec/2010:18:30:38 -0500] [Job 15] Width: 612, height: 792, absolute margins: 18, 36, 594, 783
D [13/Dec/2010:18:30:38 -0500] [Job 15] Relative margins: 18, 36, 18, 9
D [13/Dec/2010:18:30:38 -0500] [Job 15] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [13/Dec/2010:18:30:38 -0500] [Job 15] PostScript to be injected:
D [13/Dec/2010:18:30:38 -0500] [Job 15] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [13/Dec/2010:18:30:38 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:38 -0500] Get-Notifications /
D [13/Dec/2010:18:30:38 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 1.1 Get-Jobs 1
D [13/Dec/2010:18:30:38 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 WAITING Closing on EOF
D [13/Dec/2010:18:30:38 -0500] cupsdCloseClient: 17
D [13/Dec/2010:18:30:38 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:38 -0500] Get-Notifications /
D [13/Dec/2010:18:30:38 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [13/Dec/2010:18:30:38 -0500] Get-Job-Attributes ipp://localhost/jobs/15
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 WAITING Closing on EOF
D [13/Dec/2010:18:30:38 -0500] cupsdCloseClient: 16
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:38 -0500] Get-Notifications /
D [13/Dec/2010:18:30:38 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Printers
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Classes
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Default
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 17 WAITING Closing on EOF
D [13/Dec/2010:18:30:38 -0500] cupsdCloseClient: 17
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Printers
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Classes
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Default
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Printers
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Classes
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Dec/2010:18:30:38 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:38 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [13/Dec/2010:18:30:38 -0500] CUPS-Get-Default
D [13/Dec/2010:18:30:38 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Dec/2010:18:30:38 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [13/Dec/2010:18:30:38 -0500] PID 11476 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [13/Dec/2010:18:30:38 -0500] [Job 15] Filetype: PDF
D [13/Dec/2010:18:30:38 -0500] [Job 15] Storing temporary files in /var/spool/cups/tmp
D [13/Dec/2010:18:30:38 -0500] PID 11477 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [13/Dec/2010:18:30:38 -0500] [Job 15] File contains 1 pages
D [13/Dec/2010:18:30:38 -0500] [Job 15] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-G9sU26
D [13/Dec/2010:18:30:38 -0500] [Job 15] Starting process "kid3" (generation 1)
D [13/Dec/2010:18:30:38 -0500] [Job 15] Starting process "kid4" (generation 2)
D [13/Dec/2010:18:30:38 -0500] [Job 15] Starting process "renderer" (generation 2)
D [13/Dec/2010:18:30:38 -0500] [Job 15] JCL: %-12345X@PJL
D [13/Dec/2010:18:30:38 -0500] [Job 15] <job data>
D [13/Dec/2010:18:30:38 -0500] [Job 15]
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] STATE: -media-empty-warning
D [13/Dec/2010:18:30:39 -0500] [Job 15] STATE: -offline-report
I [13/Dec/2010:18:30:39 -0500] [Job 15] Printer is now online.
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 8192 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] renderer exited with status 0
D [13/Dec/2010:18:30:39 -0500] [Job 15] Read 7755 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] [Job 15] kid4 exited with status 0
D [13/Dec/2010:18:30:39 -0500] [Job 15] kid3 finished
D [13/Dec/2010:18:30:39 -0500] [Job 15] Kid3 exit status: 0
D [13/Dec/2010:18:30:39 -0500] [Job 15]
D [13/Dec/2010:18:30:39 -0500] [Job 15] Closing foomatic-rip.
D [13/Dec/2010:18:30:39 -0500] [Job 15] Wrote 7755 bytes of print data...
D [13/Dec/2010:18:30:39 -0500] PID 11478 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [13/Dec/2010:18:30:39 -0500] PID 11479 (/usr/lib/cups/backend/usb) exited with no errors.
D [13/Dec/2010:18:30:39 -0500] cupsdMarkDirty(-----S)
I [13/Dec/2010:18:30:39 -0500] [Job 15] Job completed.
D [13/Dec/2010:18:30:39 -0500] cupsdMarkDirty(----J-)
D [13/Dec/2010:18:30:39 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:39 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:39 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 1.1 Get-Jobs 1
D [13/Dec/2010:18:30:39 -0500] Get-Jobs ipp://localhost/printers/
D [13/Dec/2010:18:30:39 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 17 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:39 -0500] Get-Notifications /
D [13/Dec/2010:18:30:39 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:39 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [13/Dec/2010:18:30:39 -0500] cupsdCloseClient: 15
D [13/Dec/2010:18:30:39 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:39 -0500] Get-Notifications /
D [13/Dec/2010:18:30:39 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:39 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 17 WAITING Closing on EOF
D [13/Dec/2010:18:30:39 -0500] cupsdCloseClient: 17
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [13/Dec/2010:18:30:39 -0500] Get-Notifications /
D [13/Dec/2010:18:30:39 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:39 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:39 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
E [13/Dec/2010:18:30:39 -0500] Unsupported character set "usb://HP/Deskjet%20D1600%20series?serial=CN02CCC2JJ05CT"!
D [13/Dec/2010:18:30:39 -0500] Discarding unused server-audit event...
D [13/Dec/2010:18:30:39 -0500] CUPS-Get-Printers client-error-bad-request: Unsupported character set "usb://HP/Deskjet%20D1600%20series?serial=CN02CCC2JJ05CT"!
E [13/Dec/2010:18:30:39 -0500] Returning IPP client-error-bad-request for CUPS-Get-Printers (no URI) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Dec/2010:18:30:39 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [13/Dec/2010:18:30:39 -0500] Get-Printer-Attributes ipp://needlez-Satellite-A505:0/printers/HP-Deskjet-D1600-series
D [13/Dec/2010:18:30:39 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://needlez-Satellite-A505:0/printers/HP-Deskjet-D1600-series) from localhost
D [13/Dec/2010:18:30:39 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:39 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [13/Dec/2010:18:30:39 -0500] cupsdCloseClient: 15
D [13/Dec/2010:18:30:40 -0500] [Job 15] Unloading...
I [13/Dec/2010:18:30:52 -0500] Generating printcap /var/run/cups/printcap...
I [13/Dec/2010:18:30:52 -0500] Saving job cache file "/var/cache/cups/job.cache"...
I [13/Dec/2010:18:30:52 -0500] Saving subscriptions.conf...
D [13/Dec/2010:18:30:52 -0500] cupsdSetBusyState: Not busy
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Active clients
D [13/Dec/2010:18:30:56 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [13/Dec/2010:18:30:56 -0500] Get-Job-Attributes ipp://localhost/jobs/15
D [13/Dec/2010:18:30:56 -0500] [Job 15] Loading attributes...
D [13/Dec/2010:18:30:56 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/15) from localhost
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Not busy
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Active clients
D [13/Dec/2010:18:30:56 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [13/Dec/2010:18:30:56 -0500] Cancel-Subscription /
D [13/Dec/2010:18:30:56 -0500] cupsdIsAuthorized: requesting-user-name="needlez"
D [13/Dec/2010:18:30:56 -0500] cupsdMarkDirty(-----S)
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:56 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:56 -0500] cupsdAuthorize: No authentication data provided.
D [13/Dec/2010:18:30:56 -0500] cupsdIsAuthorized: username=""
D [13/Dec/2010:18:30:56 -0500] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [13/Dec/2010:18:30:56 -0500] cupsdCloseClient: 12
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:56 -0500] cupsdAcceptClient: 12 from localhost (Domain)
D [13/Dec/2010:18:30:56 -0500] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Active clients and dirty files
D [13/Dec/2010:18:30:56 -0500] cupsdAuthorize: Authorized as needlez using PeerCred
D [13/Dec/2010:18:30:56 -0500] cupsdIsAuthorized: username="needlez"
I [13/Dec/2010:18:30:56 -0500] Installing config file "/etc/cups/cupsd.conf"...
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Dirty files
D [13/Dec/2010:18:30:56 -0500] cupsdCloseClient: 13
D [13/Dec/2010:18:30:56 -0500] cupsdCloseClient: 16
D [13/Dec/2010:18:30:56 -0500] cupsdCloseClient: 17
D [13/Dec/2010:18:30:56 -0500] cupsdCloseClient: 12
I [13/Dec/2010:18:30:56 -0500] Saving subscriptions.conf...
D [13/Dec/2010:18:30:56 -0500] cupsdSetBusyState: Not busy


Any help great appreciated!!

---

### Post by soad6 on 2010-12-13
FIXED!!!! DOWNLOAD FROM SYNAPTIC :: hplip-gui then go into hplip toolbox and test worked for me!! thanx

---

### Post by nixor01 on 2011-05-01
yep try

```
synaptic &
```

Then download the hp-gui.

In case something still goes wrong type this in the command line after the download:

```
sudo hp-setup
```

Worked for me :)

---

