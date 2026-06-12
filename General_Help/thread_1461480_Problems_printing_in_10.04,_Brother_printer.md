---
title: "Problems printing in 10.04, Brother printer"
date: 2010-04-24
forum: General Help
---

### Post by iceman2048 on 2010-04-24
Hey all,

As of yesterday I was unable to print on my test machine using 10.04 and a Brother HL 2140 laser printer. Before that, it was printing beautifully. I tried using the "Diagnose" button from the print error box and it spat out this log:

D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [24/Apr/2010:08:35:32 -0400] Get-Jobs ipp://localhost/printers/
D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [24/Apr/2010:08:35:32 -0400] Get-Jobs ipp://localhost/printers/
D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1
D [24/Apr/2010:08:35:32 -0400] Create-Printer-Subscription /
D [24/Apr/2010:08:35:32 -0400] cupsdCreateSubscription(con=0x7f94f342af70(11), uri="/")
D [24/Apr/2010:08:35:32 -0400] pullmethod="ippget"
D [24/Apr/2010:08:35:32 -0400] notify-lease-duration=86400
D [24/Apr/2010:08:35:32 -0400] notify-time-interval=0
D [24/Apr/2010:08:35:32 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Apr/2010:08:35:32 -0400] Added subscription 21 for server
D [24/Apr/2010:08:35:32 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:34 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:34 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:34 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:34 -0400] Get-Notifications /
D [24/Apr/2010:08:35:34 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:34 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:34 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 13 POST /printers/HL-2140-series HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 13 1.1 Print-Job 1
D [24/Apr/2010:08:35:37 -0400] Print-Job ipp://localhost/printers/HL-2140-series
D [24/Apr/2010:08:35:37 -0400] [Job ???] Auto-typing file...
I [24/Apr/2010:08:35:37 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)
D [24/Apr/2010:08:35:37 -0400] add_job: requesting-user-name="iceman"
D [24/Apr/2010:08:35:37 -0400] Adding default job-sheets values "none,none"...
I [24/Apr/2010:08:35:37 -0400] [Job 21] Adding start banner page "none".
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)
I [24/Apr/2010:08:35:37 -0400] [Job 21] Adding end banner page "none".
I [24/Apr/2010:08:35:37 -0400] [Job 21] File of type application/vnd.cups-banner queued by "iceman".
D [24/Apr/2010:08:35:37 -0400] [Job 21] hold_until=0
I [24/Apr/2010:08:35:37 -0400] [Job 21] Queued on "HL-2140-series" by "iceman".
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:37 -0400] [Job 21] job-sheets=none,none
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[0]="HL-2140-series"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[1]="21"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[2]="iceman"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[3]="Test Page"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[4]="1"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[5]="job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9 fitplot orientation-requested=3 job-originating-host-name=localhost"
D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[6]="/var/spool/cups/d00021-001"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[8]="HOME=/var/spool/cups/tmp"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[10]="SERVER_ADMIN=root@iceman-desktop"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[11]="SOFTWARE=CUPS/1.4.3"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[13]="TZ=America/New_York"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[14]="USER=root"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[17]="IPP_PORT=631"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[18]="CHARSET=utf-8"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[19]="LANG=en_US.UTF-8"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[20]="PPD=/etc/cups/ppd/HL-2140-series.ppd"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[21]="RIP_MAX_CACHE=514506k"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[23]="DEVICE_URI=usb://Brother/HL-2140%20series"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[24]="PRINTER_INFO=Brother HL-2140 series"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[25]="PRINTER_LOCATION=iceman-desktop"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[26]="PRINTER=HL-2140-series"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[27]="CUPS_FILETYPE=document"
D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[28]="FINAL_CONTENT_TYPE=printer/HL-2140-series"
I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/bannertops (PID 1838)
I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/pstopdf (PID 1839)
I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/pdftopdf (PID 1840)
I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1841)
I [24/Apr/2010:08:35:37 -0400] [Job 21] Started backend /usr/lib/cups/backend/usb (PID 1842)
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HL-2140-series) from localhost
D [24/Apr/2010:08:35:37 -0400] [Job 21] pstopdf 5 args: 21 iceman Test Page 1 job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9 fitplot orientation-requested=3 job-originating-host-name=localhost
D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD: /etc/cups/ppd/HL-2140-series.ppd
D [24/Apr/2010:08:35:37 -0400] [Job 21] STATE: +connecting-to-device
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] [Job 21] Getting input from file
D [24/Apr/2010:08:35:37 -0400] [Job 21] foomatic-rip version 4.0.4.217 running...
D [24/Apr/2010:08:35:37 -0400] [Job 21] Parsing PPD file ...
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Resolution
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PageSize
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PrintoutMode
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option InputSlot
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option ImageableArea
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PaperDimension
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Duplex
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Quality
D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Font
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] Parameter Summary
D [24/Apr/2010:08:35:37 -0400] [Job 21] -----------------
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] Spooler: cups
D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer: HL-2140-series
D [24/Apr/2010:08:35:37 -0400] [Job 21] Shell: /bin/bash
D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD file: /etc/cups/ppd/HL-2140-series.ppd
D [24/Apr/2010:08:35:37 -0400] [Job 21] ATTR file:
D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer model: Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)
D [24/Apr/2010:08:35:37 -0400] [Job 21] Job title: Test Page
D [24/Apr/2010:08:35:37 -0400] [Job 21] File(s) to be printed:
D [24/Apr/2010:08:35:37 -0400] [Job 21] <STDIN>
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [24/Apr/2010:08:35:37 -0400] [Job 21] Printing system options:
D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9'
D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9.
D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'fitplot'
D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown boolean option "fitplot".
D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'orientation-requested=3'
D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option orientation-requested=3.
D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'job-originating-host-name=localhost'
D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option job-originating-host-name=localhost.
D [24/Apr/2010:08:35:37 -0400] [Job 21] Options from the PPD file:
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] ================================================
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] File: <STDIN>
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] ================================================
D [24/Apr/2010:08:35:37 -0400] [Job 21]
D [24/Apr/2010:08:35:37 -0400] [Job 21] load_banner(filename="/var/spool/cups/d00021-001")
D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer using device file "/dev/usblp1"...
D [24/Apr/2010:08:35:37 -0400] [Job 21] STATE: -connecting-to-device
D [24/Apr/2010:08:35:37 -0400] [Job 21] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x7febf9a7c6a0)
D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:37 -0400] [Job 21] Page = 612x792; 18,14 to 594,778
D [24/Apr/2010:08:35:37 -0400] [Job 21] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [24/Apr/2010:08:35:37 -0400] [Job 21] PNG image: 192x128x8, color_type=2 (RGB)
D [24/Apr/2010:08:35:37 -0400] PID 1838 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [24/Apr/2010:08:35:37 -0400] [Job 21] Resolution: 600
D [24/Apr/2010:08:35:37 -0400] [Job 21] Page size: Letter
D [24/Apr/2010:08:35:37 -0400] [Job 21] Width: 612, height: 792, absolute margins: 18, 14.40, 594, 777.60
D [24/Apr/2010:08:35:37 -0400] [Job 21] Relative margins: 18, 14.40, 18, 14.40
D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [24/Apr/2010:08:35:37 -0400] [Job 21] PostScript to be injected:
D [24/Apr/2010:08:35:37 -0400] [Job 21] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:37 -0400] Get-Notifications /
D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 16
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [24/Apr/2010:08:35:37 -0400] Get-Jobs ipp://localhost/printers/
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 17
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:37 -0400] Get-Notifications /
D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [24/Apr/2010:08:35:37 -0400] Get-Job-Attributes ipp://localhost/jobs/21
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Apr/2010:08:35:37 -0400] Get-Printer-Attributes ipp://iceman-desktop:631/printers/HL-2140-series
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://iceman-desktop:631/printers/HL-2140-series) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 17
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:37 -0400] Get-Notifications /
D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 18
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default
D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [24/Apr/2010:08:35:37 -0400] PID 1839 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [24/Apr/2010:08:35:37 -0400] [Job 21] Filetype: PDF
D [24/Apr/2010:08:35:37 -0400] [Job 21] Storing temporary files in /var/spool/cups/tmp
D [24/Apr/2010:08:35:37 -0400] PID 1840 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Apr/2010:08:35:38 -0400] [Job 21] File contains 1 pages
D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-qaqiH2
D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "kid3" (generation 1)
D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "kid4" (generation 2)
D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "renderer" (generation 2)
D [24/Apr/2010:08:35:38 -0400] [Job 21] JCL: %-12345X@PJL
D [24/Apr/2010:08:35:38 -0400] [Job 21] <job data>
D [24/Apr/2010:08:35:38 -0400] [Job 21]
D [24/Apr/2010:08:35:38 -0400] [Job 21] sh: hpijs: not found
D [24/Apr/2010:08:35:38 -0400] [Job 21] GPL Ghostscript 8.71: Can't start ijs server "hpijs"
D [24/Apr/2010:08:35:38 -0400] [Job 21] renderer exited with status 1
D [24/Apr/2010:08:35:38 -0400] [Job 21] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [24/Apr/2010:08:35:38 -0400] [Job 21] Read 50 bytes of print data...
D [24/Apr/2010:08:35:38 -0400] PID 1841 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [24/Apr/2010:08:35:38 -0400] [Job 21] STATE: -media-empty-warning
D [24/Apr/2010:08:35:38 -0400] [Job 21] STATE: -offline-report
I [24/Apr/2010:08:35:38 -0400] [Job 21] Printer is now online.
D [24/Apr/2010:08:35:38 -0400] [Job 21] Wrote 50 bytes of print data...
D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:38 -0400] PID 1842 (/usr/lib/cups/backend/usb) exited with no errors.
D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)
E [24/Apr/2010:08:35:38 -0400] [Job 21] Job stopped due to filter errors; please consult the error_log file for details.
D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(----J-)
D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:38 -0400] Get-Notifications /
D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 14
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [24/Apr/2010:08:35:38 -0400] Get-Jobs ipp://localhost/printers/
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Printers
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 17
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:38 -0400] Get-Notifications /
D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Classes
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Default
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [24/Apr/2010:08:35:38 -0400] Get-Notifications /
D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Printers
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Classes
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1
D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Default
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 13 WAITING Closing on EOF
D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 13
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [24/Apr/2010:08:35:38 -0400] Get-Printer-Attributes ipp://iceman-desktop:631/printers/HL-2140-series
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://iceman-desktop:631/printers/HL-2140-series) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [24/Apr/2010:08:35:38 -0400] Get-Job-Attributes ipp://localhost/jobs/21
D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost
D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 14
D [24/Apr/2010:08:35:39 -0400] [Job 21] Unloading...
D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1
D [24/Apr/2010:08:35:41 -0400] Get-Job-Attributes ipp://localhost/jobs/21
D [24/Apr/2010:08:35:41 -0400] [Job 21] Loading attributes...
D [24/Apr/2010:08:35:41 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost
D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.
D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1
D [24/Apr/2010:08:35:41 -0400] Cancel-Subscription /
D [24/Apr/2010:08:35:41 -0400] cupsdIsAuthorized: requesting-user-name="iceman"
D [24/Apr/2010:08:35:41 -0400] cupsdMarkDirty(-----S)
D [24/Apr/2010:08:35:41 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Dirty files
D [24/Apr/2010:08:35:41 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1
D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.

Here is the "advanced log" it gave:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest HL-2140-series (default)>,
 'cups_instance': None,
 'cups_queue': 'HL-2140-series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/HL-2140%20series',
                       'printer-info': u'Brother HL-2140 series',
                       'printer-is-shared': True,
                       'printer-location': u'iceman-desktop',
                       'printer-make-and-model': u'Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8564756,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HL-2140-series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'usb://Brother/HL-2140%20series',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
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
                                 'fitplot-default': True,
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
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
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
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
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a3_297x420mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b4_257x364mm',
                                                     u'jis_b5_182x257mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_ledger_11x17in',
                                                     u'na_legal_8.5x14in',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'na_super-b_13x19in',
                                                     u'roc_16k_7.75x10.75in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'roc_8k_10.75x15.5in',
                                                     u'custom_min_0.5x0.5in',
                                                     u'custom_max_35277.8x35277.8mm'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
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
                                 'orientation-requested-default': 3,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'Brother HL-2140 series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'iceman-desktop',
                                 'printer-make-and-model': u'Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)',
                                 'printer-more-info': u'http://localhost:631/printers/HL-2140-series',
                                 'printer-name': u'HL-2140-series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1272112395,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8564756,
                                 'printer-up-time': 1272112513,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HL-2140-series'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': (['hpijs'], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Brother;CMD:PJL,HBP;MDL:HL-2140 series;CLS:PRINTER;',
                      'device-info': u'Brother HL-2140 series',
                      'device-location': u'',
                      'device-make-and-model': u'Brother HL-2140 series'}}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'PreserveJobHistory': 'No',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 35459,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '24/Apr/2010:08:35:37 +0000',
 'test_page_job_id': [21],
 'test_page_job_status': [(True,
                           21,
                           'HL-2140-series',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'fitplot': True,
                            'job-hold-until': u'no-hold',
                            'job-id': 21,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/21',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'iceman',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1272112541,
                            'job-printer-uri': u'ipp://iceman-desktop:631/printers/HL-2140-series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/21',
                            'job-uuid': u'urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9',
                            'orientation-requested': 3,
                            'printer-uri': u'ipp://localhost/printers/HL-2140-series',
                            'time-at-completed': None,
                            'time-at-creation': 1272112537,
                            'time-at-processing': 1272112537})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [24/Apr/2010:08:35:32 -0400] Get-Jobs ipp://localhost/printers/',
               'D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [24/Apr/2010:08:35:32 -0400] Get-Jobs ipp://localhost/printers/',
               'D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:32 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:32 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1',
               'D [24/Apr/2010:08:35:32 -0400] Create-Printer-Subscription /',
               'D [24/Apr/2010:08:35:32 -0400] cupsdCreateSubscription(con=0x7f94f342af70(11), uri="/")',
               'D [24/Apr/2010:08:35:32 -0400] pullmethod="ippget"',
               'D [24/Apr/2010:08:35:32 -0400] notify-lease-duration=86400',
               'D [24/Apr/2010:08:35:32 -0400] notify-time-interval=0',
               'D [24/Apr/2010:08:35:32 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Apr/2010:08:35:32 -0400] Added subscription 21 for server',
               'D [24/Apr/2010:08:35:32 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:32 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [24/Apr/2010:08:35:32 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:34 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:34 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:34 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:34 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:34 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:34 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:34 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:34 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 13 POST /printers/HL-2140-series HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 13 1.1 Print-Job 1',
               'D [24/Apr/2010:08:35:37 -0400] Print-Job ipp://localhost/printers/HL-2140-series',
               'D [24/Apr/2010:08:35:37 -0400] [Job ???] Auto-typing file...',
               'I [24/Apr/2010:08:35:37 -0400] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)',
               'D [24/Apr/2010:08:35:37 -0400] add_job: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:37 -0400] Adding default job-sheets values "none,none"...',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Adding start banner page "none".',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Adding end banner page "none".',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] File of type application/vnd.cups-banner queued by "iceman".',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] hold_until=0',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Queued on "HL-2140-series" by "iceman".',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(----J-)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] job-sheets=none,none',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[0]="HL-2140-series"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[1]="21"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[2]="iceman"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[3]="Test Page"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[4]="1"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[5]="job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9 fitplot orientation-requested=3 job-originating-host-name=localhost"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] argv[6]="/var/spool/cups/d00021-001"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[10]="SERVER_ADMIN=root@iceman-desktop"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[13]="TZ=America/New_York"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[14]="USER=root"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[17]="IPP_PORT=631"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[18]="CHARSET=utf-8"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[19]="LANG=en_US.UTF-8"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[20]="PPD=/etc/cups/ppd/HL-2140-series.ppd"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[21]="RIP_MAX_CACHE=514506k"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[23]="DEVICE_URI=usb://Brother/HL-2140%20series"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[24]="PRINTER_INFO=Brother HL-2140 series"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[25]="PRINTER_LOCATION=iceman-desktop"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[26]="PRINTER=HL-2140-series"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[27]="CUPS_FILETYPE=document"',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] envp[28]="FINAL_CONTENT_TYPE=printer/HL-2140-series"',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/bannertops (PID 1838)',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/pstopdf (PID 1839)',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/pdftopdf (PID 1840)',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1841)',
               'I [24/Apr/2010:08:35:37 -0400] [Job 21] Started backend /usr/lib/cups/backend/usb (PID 1842)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HL-2140-series) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] pstopdf 5 args: 21 iceman Test Page 1 job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9 fitplot orientation-requested=3 job-originating-host-name=localhost',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD: /etc/cups/ppd/HL-2140-series.ppd',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] STATE: +connecting-to-device',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Getting input from file',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] foomatic-rip version 4.0.4.217 running...',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Parsing PPD file ...',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Resolution',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PageSize',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PrintoutMode',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option InputSlot',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option ImageableArea',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option PaperDimension',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Duplex',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Quality',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Added option Font',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Parameter Summary',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] -----------------',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Spooler: cups',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer: HL-2140-series',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Shell: /bin/bash',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD file: /etc/cups/ppd/HL-2140-series.ppd',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] ATTR file:',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer model: Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Job title: Test Page',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] File(s) to be printed:',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] <STDIN>',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               "D [24/Apr/2010:08:35:37 -0400] [Job 21] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Printing system options:',
               "D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9'",
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option job-uuid=urn:uuid:fa2a927c-271d-3f6d-76e1-747d7a8a66f9.',
               "D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'fitplot'",
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown boolean option "fitplot".',
               "D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'orientation-requested=3'",
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option orientation-requested=3.',
               "D [24/Apr/2010:08:35:37 -0400] [Job 21] Pondering option 'job-originating-host-name=localhost'",
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Unknown option job-originating-host-name=localhost.',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Options from the PPD file:',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] ================================================',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] File: <STDIN>',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] ================================================',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] load_banner(filename="/var/spool/cups/d00021-001")',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Printer using device file "/dev/usblp1"...',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] STATE: -connecting-to-device',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x7febf9a7c6a0)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Page = 612x792; 18,14 to 594,778',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [24/Apr/2010:08:35:37 -0400] PID 1838 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Resolution: 600',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Page size: Letter',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Width: 612, height: 792, absolute margins: 18, 14.40, 594, 777.60',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Relative margins: 18, 14.40, 18, 14.40',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] PostScript to be injected:',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 16',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Jobs ipp://localhost/printers/',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 17',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Job-Attributes ipp://localhost/jobs/21',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Printer-Attributes ipp://iceman-desktop:631/printers/HL-2140-series',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://iceman-desktop:631/printers/HL-2140-series) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 17',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:37 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:37 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:37 -0400] cupsdCloseClient: 18',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Printers',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Classes',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:37 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [24/Apr/2010:08:35:37 -0400] CUPS-Get-Default',
               'D [24/Apr/2010:08:35:37 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Apr/2010:08:35:37 -0400] cupsdSetBusyState: Printing jobs and dirty files',
               'D [24/Apr/2010:08:35:37 -0400] PID 1839 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Filetype: PDF',
               'D [24/Apr/2010:08:35:37 -0400] [Job 21] Storing temporary files in /var/spool/cups/tmp',
               'D [24/Apr/2010:08:35:37 -0400] PID 1840 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] File contains 1 pages',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-qaqiH2',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "kid3" (generation 1)',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "kid4" (generation 2)',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Starting process "renderer" (generation 2)',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] JCL: \x1b%-12345X@PJL',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] <job data>',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21]',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] sh: hpijs: not found',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] GPL Ghostscript 8.71: Can\'t start ijs server "hpijs"',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] renderer exited with status 1',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Read 50 bytes of print data...',
               'D [24/Apr/2010:08:35:38 -0400] PID 1841 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] STATE: -media-empty-warning',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] STATE: -offline-report',
               'I [24/Apr/2010:08:35:38 -0400] [Job 21] Printer is now online.',
               'D [24/Apr/2010:08:35:38 -0400] [Job 21] Wrote 50 bytes of print data...',
               'D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:38 -0400] PID 1842 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)',
               **'E [24/Apr/2010:08:35:38 -0400] [Job 21] Job stopped due to filter errors; please consult the error_log file for details.',**
               'D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(----J-)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 14',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Jobs ipp://localhost/printers/',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Printers',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 17',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Classes',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Default',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Notifications /',
               'D [24/Apr/2010:08:35:38 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Printers',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Classes 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Classes',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Default 1',
               'D [24/Apr/2010:08:35:38 -0400] CUPS-Get-Default',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 13 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 13',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Printer-Attributes ipp://iceman-desktop:631/printers/HL-2140-series',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://iceman-desktop:631/printers/HL-2140-series) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1',
               'D [24/Apr/2010:08:35:38 -0400] Get-Job-Attributes ipp://localhost/jobs/21',
               'D [24/Apr/2010:08:35:38 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost',
               'D [24/Apr/2010:08:35:38 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:38 -0400] cupsdReadClient: 14 WAITING Closing on EOF',
               'D [24/Apr/2010:08:35:38 -0400] cupsdCloseClient: 14',
               'D [24/Apr/2010:08:35:39 -0400] [Job 21] Unloading...',
               'D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [24/Apr/2010:08:35:41 -0400] Get-Job-Attributes ipp://localhost/jobs/21',
               'D [24/Apr/2010:08:35:41 -0400] [Job 21] Loading attributes...',
               'D [24/Apr/2010:08:35:41 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/21) from localhost',
               'D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.',
               'D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [24/Apr/2010:08:35:41 -0400] Cancel-Subscription /',
               'D [24/Apr/2010:08:35:41 -0400] cupsdIsAuthorized: requesting-user-name="iceman"',
               'D [24/Apr/2010:08:35:41 -0400] cupsdMarkDirty(-----S)',
               'D [24/Apr/2010:08:35:41 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Dirty files',
               'D [24/Apr/2010:08:35:41 -0400] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [24/Apr/2010:08:35:41 -0400] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1',
               'D [24/Apr/2010:08:35:41 -0400] cupsdSetBusyState: Active clients and dirty files',
               'D [24/Apr/2010:08:35:41 -0400] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Printer state reasons):
{'printer-state-message': u'Printer is now online.',
 'printer-state-reasons': [u'none']}
Page 12 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}



I'm not very familiar with this stuff, but it seems to be an authentication error or a filter error (not sure what that means). I tried deleting the printer then reinstalling but that did not work either. I also looked at the queue window, but there do not seem to be any pending jobs that could be tying up the printer either. 

I have also tried reinstalling cups but again that did not work either. Is there someting I missed? Thanks in advance.

UPDATE: By downloading a new ppd for this printer, installing hpijs package, and reinstalling the printer using the new ppd allows me to print again. However, I'm unable to mark the thread as solved, even through the advanced post editor. Is there something I missed about that?

---

### Post by P4man on 2010-04-24
Glad you found it. Even gladder I didnt start reading those logs before scrolling to the bottom lol.

Thread Tools -> Mark this thread as solved.

Also, next time put these long logs between code tags, so we dont have to wear out our scroll wheels just to get to the next post or reply button :)

---

### Post by Marioace on 2010-05-24
what ppd did you use?
and what is that hpijs package??

please i have the same printer and had to go back to windows cause it doesnt work well under ubuntu 9.10, now i want to return to ubuntu 10.04 but i don't want to lose my printer.

---

### Post by johnny_vc on 2010-05-31
I have the same weird issue, Brother HL2170W works perfectly in ubuntu 9.10, but very slow in 10.4 ,  I print the same file and it takes 30 seconds (9.10) against more than 8 minutes in (10.4), tried downloading  ppd file from brother, no luck at the moment.

---

### Post by johnny_vc on 2010-06-02
I found a workaround by using :

Device URL:      socket://PrinterIP:9100
Make and Model:   Generic PCL 5e Printer Foomatic/gutenprint-ijs-simplified.5.0

But also found that the problem is not only with this printer, I am experiencing same issues with a HP F380 color inkjet.

---

### Post by t.rei on 2010-06-15
get the same for the photosmart c3180.

This is getting anoying, probably expensive... I will now have to go to town to get a letter printed that needs to get send TODAY. 

THIS is the kind of regression no one needs, really.

---

### Post by Dr_Willis on 2010-07-03
Brother-HL-2170W Slow 

My Brother-HL-2170W was taking an half hour+ to print some web sites.
With the changes mentioned above, its now quite speedy.  I knew somthing was odd when my 15+ yr old laser printer was faster then the new one.


Going to have to bookmark this. and Hope it gets fixed in the future. I have not noticed any lost functionality for my printer by changeing to the generic PCL5e drivers.


Device URL: socket://PrinterIP:9100
Make and Model: Generic PCL 5e Printer Foomatic/gutenprint-ijs-simplified.5.0

---

