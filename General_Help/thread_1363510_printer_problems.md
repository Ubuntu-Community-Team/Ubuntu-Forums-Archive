---
title: "printer problems"
date: 2009-12-24
forum: General Help
---

### Post by 2roombas on 2009-12-24
Up until last night I have been printing with no problem at all, then today see this error, which makes no sense?!  I've used these cartridges for months and it's been working fine.

1.  I re-installed my OS.. same error  
2.  I also unplugged the printer, both cable and electric outlet, hoping that would *reset* whatever is wrong, nope, same error.

All I have done since last night was download the new Chrome for Linux (beta) and also the Opera browser. I played a little with those, then I decided I just  preferred my "fits like an ol' shoe" FireFox instead.   That has been the only changes I've made.  

What the heck could be wrong?  I obviously cannot re-install the printer software since it's all Windows.  I did do the diagnostic wizard, but in conclusion I only get "could not figure it out" then this below, as if Im supposed to understand it. (scoff!):(  Can anyone here please help me with this?

```
D [24/Dec/2009:09:59:13 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:13 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:13 -0800] Get-Jobs ipp://localhost/printers/
D [24/Dec/2009:09:59:13 -0800] [Job 7] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] [Job 8] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:13 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:13 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:13 -0800] Get-Jobs ipp://localhost/printers/
D [24/Dec/2009:09:59:13 -0800] [Job 2] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] [Job 3] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] [Job 4] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] [Job 5] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] [Job 6] Loading attributes...
D [24/Dec/2009:09:59:13 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:19 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:19 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:19 -0800] Create-Printer-Subscription /
D [24/Dec/2009:09:59:19 -0800] cupsdCreateSubscription(con=0xb8bfea50(8), uri="/")
D [24/Dec/2009:09:59:19 -0800] pullmethod="ippget"
D [24/Dec/2009:09:59:19 -0800] notify-lease-duration=86400
D [24/Dec/2009:09:59:19 -0800] notify-time-interval=0
D [24/Dec/2009:09:59:19 -0800] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Dec/2009:09:59:19 -0800] Added subscription 11 for server
I [24/Dec/2009:09:59:19 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:19 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:20 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:20 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:20 -0800] Get-Notifications /
D [24/Dec/2009:09:59:20 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:20 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:24 -0800] cupsdAcceptClient: 9 from localhost (Domain)
D [24/Dec/2009:09:59:24 -0800] cupsdReadClient: 9 POST /printers/Photosmart-C4400-series HTTP/1.1
D [24/Dec/2009:09:59:24 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:24 -0800] Print-Job ipp://localhost/printers/Photosmart-C4400-series
D [24/Dec/2009:09:59:24 -0800] [Job ???] Auto-typing file...
I [24/Dec/2009:09:59:24 -0800] [Job ???] Request file type is application/postscript.
D [24/Dec/2009:09:59:24 -0800] add_job: requesting-user-name="me"
D [24/Dec/2009:09:59:24 -0800] Adding default job-sheets values "none,none"...
I [24/Dec/2009:09:59:24 -0800] [Job 9] Adding start banner page "none".
I [24/Dec/2009:09:59:24 -0800] Saving subscriptions.conf...
I [24/Dec/2009:09:59:24 -0800] [Job 9] Adding end banner page "none".
I [24/Dec/2009:09:59:24 -0800] [Job 9] File of type application/postscript queued by "me".
D [24/Dec/2009:09:59:24 -0800] [Job 9] hold_until=0
I [24/Dec/2009:09:59:24 -0800] [Job 9] Queued on "Photosmart-C4400-series" by "me".
I [24/Dec/2009:09:59:24 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:24 -0800] [Job 9] job-sheets=none,none
D [24/Dec/2009:09:59:24 -0800] [Job 9] banner_page = 0
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[0]="Photosmart-C4400-series"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[1]="9"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[2]="me"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[3]="Test Page"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[4]="1"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[5]="job-uuid=urn:uuid:5fc767f2-f3ee-3b92-5340-7376fd239730"
D [24/Dec/2009:09:59:24 -0800] [Job 9] argv[6]="/var/spool/cups/d00009-001"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[9]="SERVER_ADMIN=root@me-desktop"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[10]="SOFTWARE=CUPS/1.3.9"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[12]="TZ=America/Los_Angeles"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[13]="USER=root"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[16]="IPP_PORT=631"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[17]="CHARSET=utf-8"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[18]="LANG=en_US.UTF8"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[19]="PPD=/etc/cups/ppd/Photosmart-C4400-series.ppd"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[20]="RIP_MAX_CACHE=8m"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[21]="CONTENT_TYPE=application/postscript"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[22]="DEVICE_URI=hp:/usb/Photosmart_C4400_series?serial=CN8AMHY2QQ05BN"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[23]="PRINTER=Photosmart-C4400-series"
D [24/Dec/2009:09:59:24 -0800] [Job 9] envp[24]="FINAL_CONTENT_TYPE=printer/Photosmart-C4400-series"
I [24/Dec/2009:09:59:24 -0800] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 7154)
I [24/Dec/2009:09:59:24 -0800] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 7157)
I [24/Dec/2009:09:59:24 -0800] [Job 9] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7160)
I [24/Dec/2009:09:59:24 -0800] [Job 9] Started backend /usr/lib/cups/backend/hp (PID 7161)
I [24/Dec/2009:09:59:24 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:24 -0800] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:24 -0800] [Job 9] pstopdf 6 args: 9 me Test Page 1 job-uuid=urn:uuid:5fc767f2-f3ee-3b92-5340-7376fd239730 /var/spool/cups/d00009-001
D [24/Dec/2009:09:59:24 -0800] [Job 9] PPD: /etc/cups/ppd/Photosmart-C4400-series.ppd
I [24/Dec/2009:09:59:24 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:24 -0800] [Job 9] Resolution: 1200
D [24/Dec/2009:09:59:24 -0800] [Job 9] Getting input from file
D [24/Dec/2009:09:59:24 -0800] [Job 9] foomatic-rip version 4.0.0.195 running...
D [24/Dec/2009:09:59:24 -0800] [Job 9] Parsing PPD file ...
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option Resolution
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option PageSize
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option Model
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option PrintoutMode
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option InputSlot
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option Duplex
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option DryTime
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option Quality
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option ImageableArea
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option PaperDimension
D [24/Dec/2009:09:59:24 -0800] [Job 9] Added option Font
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] Parameter Summary
D [24/Dec/2009:09:59:24 -0800] [Job 9] -----------------
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] Spooler: cups
D [24/Dec/2009:09:59:24 -0800] [Job 9] Printer: Photosmart-C4400-series
D [24/Dec/2009:09:59:24 -0800] [Job 9] Shell: /bin/bash
D [24/Dec/2009:09:59:24 -0800] [Job 9] PPD file: /etc/cups/ppd/Photosmart-C4400-series.ppd
D [24/Dec/2009:09:59:24 -0800] [Job 9] ATTR file:
D [24/Dec/2009:09:59:24 -0800] [Job 9] Printer model: HP Photosmart c4400 Series hpijs, 3.9.2
D [24/Dec/2009:09:59:24 -0800] [Job 9] Job title: Test Page
D [24/Dec/2009:09:59:24 -0800] [Job 9] File(s) to be printed:
D [24/Dec/2009:09:59:24 -0800] [Job 9] <STDIN>
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [24/Dec/2009:09:59:24 -0800] [Job 9] Printing system options:
D [24/Dec/2009:09:59:24 -0800] [Job 9] Pondering option 'job-uuid=urn:uuid:5fc767f2-f3ee-3b92-5340-7376fd239730'
D [24/Dec/2009:09:59:24 -0800] [Job 9] Unknown option job-uuid=urn:uuid:5fc767f2-f3ee-3b92-5340-7376fd239730.
D [24/Dec/2009:09:59:24 -0800] [Job 9] Options from the PPD file:
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] ================================================
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] File: <STDIN>
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] ================================================
D [24/Dec/2009:09:59:24 -0800] [Job 9]
D [24/Dec/2009:09:59:24 -0800] [Job 9] Page size: Letter
D [24/Dec/2009:09:59:24 -0800] [Job 9] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 783.00
D [24/Dec/2009:09:59:24 -0800] [Job 9] Relative margins: 18.00, 36.00, 18.00, 9.00
D [24/Dec/2009:09:59:24 -0800] [Job 9] PPD options: -r1200 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00
D [24/Dec/2009:09:59:24 -0800] [Job 9] PostScript to be injected:
D [24/Dec/2009:09:59:24 -0800] [Job 9] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r1200 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 - -
D [24/Dec/2009:09:59:24 -0800] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Dec/2009:09:59:24 -0800] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Dec/2009:09:59:24 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:24 -0800] Get-Notifications /
D [24/Dec/2009:09:59:24 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:24 -0800] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:24 -0800] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Dec/2009:09:59:24 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:24 -0800] Get-Job-Attributes ipp://localhost/jobs/9
D [24/Dec/2009:09:59:24 -0800] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:24 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:24 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:24 -0800] Get-Notifications /
D [24/Dec/2009:09:59:24 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:24 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:24 -0800] [Job 9] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [24/Dec/2009:09:59:24 -0800] cupsdCloseClient: 11
D [24/Dec/2009:09:59:24 -0800] [Job 9] Filetype: PDF
D [24/Dec/2009:09:59:24 -0800] [Job 9] Storing temporary files in /var/spool/cups/tmp
D [24/Dec/2009:09:59:24 -0800] PID 7154 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [24/Dec/2009:09:59:25 -0800] PID 7157 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Dec/2009:09:59:25 -0800] [Job 9] File contains 1 pages
D [24/Dec/2009:09:59:25 -0800] [Job 9] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-aQYCjs
D [24/Dec/2009:09:59:25 -0800] [Job 9] Starting process "kid3" (generation 1)
D [24/Dec/2009:09:59:25 -0800] [Job 9] Starting process "kid4" (generation 2)
D [24/Dec/2009:09:59:25 -0800] [Job 9] JCL: %-12345X@PJL
D [24/Dec/2009:09:59:25 -0800] [Job 9] <job data>
D [24/Dec/2009:09:59:25 -0800] [Job 9]
D [24/Dec/2009:09:59:25 -0800] [Job 9] Starting process "renderer" (generation 2)
D [24/Dec/2009:09:59:25 -0800] [Job 9] Segmentation fault
D [24/Dec/2009:09:59:25 -0800] [Job 9] GPL Ghostscript 8.64: Can't start ijs server "hpijs"
D [24/Dec/2009:09:59:25 -0800] [Job 9] renderer exited with status 1
D [24/Dec/2009:09:59:25 -0800] [Job 9] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
E [24/Dec/2009:09:59:25 -0800] PID 7160 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [24/Dec/2009:09:59:25 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:25 -0800] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Dec/2009:09:59:25 -0800] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Dec/2009:09:59:25 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:25 -0800] Get-Notifications /
D [24/Dec/2009:09:59:25 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:25 -0800] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:25 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:25 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:25 -0800] Get-Notifications /
D [24/Dec/2009:09:59:25 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:25 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:25 -0800] cupsdCloseClient: 11
D [24/Dec/2009:09:59:48 -0800] cupsdReadClient: 8 POST /jobs/ HTTP/1.1
D [24/Dec/2009:09:59:48 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:48 -0800] Cancel-Job ipp://localhost/jobs/8
D [24/Dec/2009:09:59:48 -0800] cupsdIsAuthorized: requesting-user-name="me"
I [24/Dec/2009:09:59:48 -0800] Saving subscriptions.conf...
I [24/Dec/2009:09:59:48 -0800] [Job 8] Canceled by "me".
D [24/Dec/2009:09:59:48 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:48 -0800] cupsdReadClient: 8 POST /jobs/ HTTP/1.1
D [24/Dec/2009:09:59:48 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:48 -0800] Cancel-Job ipp://localhost/jobs/9
D [24/Dec/2009:09:59:48 -0800] cupsdIsAuthorized: requesting-user-name="me"
I [24/Dec/2009:09:59:48 -0800] Saving subscriptions.conf...
I [24/Dec/2009:09:59:48 -0800] Saving subscriptions.conf...
I [24/Dec/2009:09:59:48 -0800] [Job 9] Canceled by "me".
D [24/Dec/2009:09:59:48 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:48 -0800] PID 7161 (/usr/lib/cups/backend/hp) exited with no errors.
D [24/Dec/2009:09:59:48 -0800] cupsdReadClient: 8 POST /jobs/ HTTP/1.1
D [24/Dec/2009:09:59:48 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:48 -0800] Cancel-Job ipp://localhost/jobs/7
D [24/Dec/2009:09:59:48 -0800] cupsdIsAuthorized: requesting-user-name="me"
I [24/Dec/2009:09:59:48 -0800] Saving subscriptions.conf...
I [24/Dec/2009:09:59:48 -0800] [Job 7] Canceled by "me".
D [24/Dec/2009:09:59:48 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:48 -0800] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Dec/2009:09:59:48 -0800] cupsdReadClient: 11 POST / HTTP/1.1
D [24/Dec/2009:09:59:48 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:48 -0800] Get-Notifications /
D [24/Dec/2009:09:59:48 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:48 -0800] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:48 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:48 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:48 -0800] Get-Notifications /
D [24/Dec/2009:09:59:48 -0800] cupsdIsAuthorized: requesting-user-name="me"
D [24/Dec/2009:09:59:48 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:49 -0800] cupsdCloseClient: 11
D [24/Dec/2009:09:59:49 -0800] [Job 9] Unloading...
D [24/Dec/2009:09:59:55 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:55 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:55 -0800] Get-Job-Attributes ipp://localhost/jobs/9
D [24/Dec/2009:09:59:55 -0800] [Job 9] Loading attributes...
D [24/Dec/2009:09:59:55 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:55 -0800] Report: clients=2
D [24/Dec/2009:09:59:55 -0800] Report: jobs=8
D [24/Dec/2009:09:59:55 -0800] Report: jobs-active=0
D [24/Dec/2009:09:59:55 -0800] Report: printers=1
D [24/Dec/2009:09:59:55 -0800] Report: printers-implicit=0
D [24/Dec/2009:09:59:55 -0800] Report: stringpool-string-count=3916
D [24/Dec/2009:09:59:55 -0800] Report: stringpool-alloc-bytes=10152
D [24/Dec/2009:09:59:55 -0800] Report: stringpool-total-bytes=88648
D [24/Dec/2009:09:59:55 -0800] cupsdReadClient: 8 POST / HTTP/1.1
D [24/Dec/2009:09:59:55 -0800] cupsdAuthorize: No authentication data provided.
D [24/Dec/2009:09:59:55 -0800] Cancel-Subscription /
D [24/Dec/2009:09:59:55 -0800] cupsdIsAuthorized: requesting-user-name="me"
I [24/Dec/2009:09:59:55 -0800] Saving subscriptions.conf...
D [24/Dec/2009:09:59:55 -0800] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [24/Dec/2009:09:59:55 -0800] cupsdAcceptClient: 11 from localhost (Domain)
D [24/Dec/2009:09:59:55 -0800] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1
D [24/Dec/2009:09:59:55 -0800] cupsdAuthorize: No authentication data provided.
```

---

### Post by cariboo on 2009-12-24
I'm a bit confused, is the printer connected to a system running Ubuntu or Windows. If it is running Ubuntu, why do you need windows drivers. More info please.

---

### Post by 2roombas on 2009-12-24
I never said I needed Windows drivers.  All I meant by mentioning "that" OS was that the literature (etc) that came with the printer is all in Windows,  

It's an hp Photosmart C4480 (an all-in-one) and I use ubuntu 9.04.  When I bought this (less then a year ago) all I had to do was plug it in and my system quickly recognised it and I've been printing with it ever since. No problem with it until now.

I've web searched and found this is rather common and so far the solution is to just buy a new cartridge.  Totally ridiculous as I print very seldom and I know this cartridge is still over half full.:confused:

---

### Post by Barriehie on 2009-12-24
Looking through the CODE you posted it appears to be an error with software and not the printer.  I'ld start with reinstalling the hpijs package from the repos.
```

...muted...
D [24/Dec/2009:09:59:25 -0800] [Job 9] Starting process "renderer" (generation 2)
D [24/Dec/2009:09:59:25 -0800] [Job 9] Segmentation fault
D [24/Dec/2009:09:59:25 -0800] [Job 9] GPL Ghostscript 8.64: **Can't start ijs server "hpijs"**
D [24/Dec/2009:09:59:25 -0800] [Job 9] renderer exited with status 1
D [24/Dec/2009:09:59:25 -0800] [Job 9] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
E [24/Dec/2009:09:59:25 -0800] PID 7160 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
...muted...

```

Barrie

---

### Post by 2roombas on 2009-12-24
I reinstalled that, rebooted, turned on the printer and still get that erro message.:(

---

### Post by Barriehie on 2009-12-24
Since the error indicated a segmentation fault how about doing a memory check?

Barrie

---

### Post by 2roombas on 2009-12-24
How do I do that?

---

### Post by 2roombas on 2009-12-24
Here'as the output"

             total       used       free     shared    buffers     cached
Mem:          1001        480        521          0         16        242
-/+ buffers/cache:        221        779
Swap:         1223          0       1223

---

### Post by Barriehie on 2009-12-24
> **2roombas said:**
> How do I do that?

At the bottom, usually, of the GRUB boot menu is a memtest option.

Barrie

---

### Post by 2roombas on 2009-12-24
I did a free -m in terminal. Is that not the same? I googled and found that.

---

### Post by Barriehie on 2009-12-24
> **2roombas said:**
> I did a free -m in terminal. Is that not the same? I googled and found that.

No, it's not.  The memtest in the GRUB menu runs test doing x number of reads, writes, and verifies.  Might try going to [http://localhost:631/](http://localhost:631/) , which is the CUPS, common unix printing system, and see if you can find anything there.  

Barrie

---

### Post by Barriehie on 2009-12-24
I'm googling this and found you should run, in the terminal, ```
hp-check -t
``` and post the output here please.

Barrie

---

### Post by 2roombas on 2009-12-24
Thank you.. trying that...

HP Linux Imaging and Printing System (ver. 3.9.2)
Dependency/Version Check Utility ver. 14.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux me-desktop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libdbus-1-dev

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes openssl

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libjpeg62-dev

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsnmp-dev

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libtool

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libusb-dev

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4-dbus

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python2.5-dev

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-reportlab

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
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
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=3.9.2.49
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes




Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hp:/usb/Photosmart_C4400_series?serial=CN8AMHY2QQ05BN

[installation]
date_time = 12/24/09 16:17:45
version = 3.9.2.49



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart-C4400-series
-----------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Photosmart_C4400_series?serial=CN8AMHY2QQ05BN
PPD: /etc/cups/ppd/Photosmart-C4400-series.ppd
PPD Description: HP Photosmart c4400 Series hpijs, 3.9.2
Printer status: printer Photosmart-C4400-series disabled since Thu 24 Dec 2009 03:00:04 Unplugged or turned off

HP Linux Imaging and Printing System (ver. 3.9.2)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
error: Unable to communicate with device (code=12): hp:/usb/Photosmart_C4400_series?serial=CN8AMHY2QQ05BN
error: Device not found


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
-----------
| SUMMARY |
-----------

error: 16 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd
sudo aptitude install --assume-yes libdbus-1-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes openssl
sudo aptitude install --assume-yes libjpeg62-dev
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes libusb-dev
sudo aptitude install --assume-yes python-qt4
sudo aptitude install --assume-yes python-qt4-dbus
sudo aptitude install --assume-yes python2.5-dev
sudo aptitude install --assume-yes python-reportlab
sudo aptitude install --assume-yes libsane-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

---

### Post by Barriehie on 2009-12-24
> **2roombas said:**
> Can the memtest be done in terminal?  Or do I have to open grub in a re-bootup?"

I'm pretty sure you have to reboot.  I've been googling and you're not the only one with this issue!

Barrie

---

### Post by 2roombas on 2009-12-24
> **Barriehie said:**
> I'm pretty sure you have to reboot.  I've been googling and you're not the only one with this issue!

Barrie

What I just sent wasn't right?  I thought I was told I could do it through terminal?!

Yes, I too have been googling snd see it's common. (sigh)

---

### Post by Barriehie on 2009-12-24
> **2roombas said:**
> What I just sent wasn't right?  I thought I was told I could do it through terminal?!

Yes, I too have been googling snd see it's common. (sigh)

The posting of hp-check is right; I'm getting tired now but I'll keep digging tomorrow!

Barrie

---

