---
title: "CUPS/Splix problem with Samsung ML-1740 printer"
date: 2012-05-14
forum: General Help
---

### Post by djgrant on 2012-05-14
This was not happening before I upgraded to 12.04 so I am pretty confident it is an issue with 12.04 only. When I print to my Samsung ML-1740, somewhere along the way, the job gets lost. The printer will fire up and start warming up but then the job never prints. Sometimes it will though, it's a bit random, possibly a race condition going on.

Here is the cups debug output after I start the job:

D [13/May/2012:23:28:30 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [13/May/2012:23:28:30 -0700] cupsdAuthorize: No authentication data provided.
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [13/May/2012:23:28:30 -0700] Get-Printer-Attributes ipp://localhost:631/printers/Samsung_ML-1740
D [13/May/2012:23:28:30 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost:631/printers/Samsung_ML-1740) from localhost
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 POST /printers/Samsung_ML-1740 HTTP/1.1
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [13/May/2012:23:28:30 -0700] cupsdAuthorize: No authentication data provided.
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 1.1 Create-Job 1
D [13/May/2012:23:28:30 -0700] Create-Job ipp://localhost:631/printers/Samsung_ML-1740
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(----J-)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients"
D [13/May/2012:23:28:30 -0700] add_job: requesting-user-name="david"
I [13/May/2012:23:28:30 -0700] [Job 64] Adding start banner page "none".
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [13/May/2012:23:28:30 -0700] [Job 64] Queued on "Samsung_ML-1740" by "david".
D [13/May/2012:23:28:30 -0700] Returning IPP successful-ok for Create-Job (ipp://localhost:631/printers/Samsung_ML-1740) from localhost
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 POST /printers/Samsung_ML-1740 HTTP/1.1
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/May/2012:23:28:30 -0700] cupsdAuthorize: No authentication data provided.
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 1.1 Send-Document 1
D [13/May/2012:23:28:30 -0700] Send-Document ipp://localhost:631/printers/Samsung_ML-1740
D [13/May/2012:23:28:30 -0700] cupsdIsAuthorized: requesting-user-name="david"
D [13/May/2012:23:28:30 -0700] [Job 64] Auto-typing file...
D [13/May/2012:23:28:30 -0700] [Job 64] Request file type is text/plain.
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(----J-)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [13/May/2012:23:28:30 -0700] [Job 64] File of type text/plain queued by "david".
I [13/May/2012:23:28:30 -0700] [Job 64] Adding end banner page "none".
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(----J-)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(----J-)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] [Job 64] job-sheets=none,none
D [13/May/2012:23:28:30 -0700] [Job 64] argv[0]="Samsung_ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] argv[1]="64"
D [13/May/2012:23:28:30 -0700] [Job 64] argv[2]="david"
D [13/May/2012:23:28:30 -0700] [Job 64] argv[3]="dgrant79_vs_rbrs11_2012_04_01.pgn"
D [13/May/2012:23:28:30 -0700] [Job 64] argv[4]="1"
D [13/May/2012:23:28:30 -0700] [Job 64] argv[5]="finishings=3 number-up=1 job-uuid=urn:uuid:01598f6b-fca8-3a84-7afc-3e3d3dbb0b4a job-originating-host-name=localhost time-at-creation=1336976910 time-at-processing=1336976910 AP_D_InputSlot="
D [13/May/2012:23:28:30 -0700] [Job 64] argv[6]="/var/spool/cups/d00064-001"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[8]="HOME=/var/spool/cups/tmp"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[10]="SERVER_ADMIN=root@centurion"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[11]="SOFTWARE=CUPS/1.5.2"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[13]="USER=root"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[16]="IPP_PORT=631"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[17]="CHARSET=utf-8"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[18]="LANG=en_CA.UTF-8"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[19]="PPD=/etc/cups/ppd/Samsung_ML-1740.ppd"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[20]="RIP_MAX_CACHE=128m"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[21]="CONTENT_TYPE=text/plain"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[22]="DEVICE_URI=usb://Samsung/ML-1740?serial=2W61BKDXC13321A0"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[23]="PRINTER_INFO=Samsung ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[24]="PRINTER_LOCATION=centurion"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[25]="PRINTER=Samsung_ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[26]="PRINTER_STATE_REASONS=none"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[27]="CUPS_FILETYPE=document"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[28]="FINAL_CONTENT_TYPE=printer/Samsung_ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[29]="AUTH_I****"
I [13/May/2012:23:28:30 -0700] [Job 64] Started filter /usr/lib/cups/filter/texttopdf (PID 2651)
I [13/May/2012:23:28:30 -0700] [Job 64] Started filter /usr/lib/cups/filter/pdftopdf (PID 2652)
I [13/May/2012:23:28:30 -0700] [Job 64] Started filter /usr/lib/cups/filter/gstoraster (PID 2653)
I [13/May/2012:23:28:30 -0700] [Job 64] Started filter /usr/lib/cups/filter/rastertoqpdl (PID 2654)
I [13/May/2012:23:28:30 -0700] [Job 64] Started backend /usr/lib/cups/backend/usb (PID 2655)
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [13/May/2012:23:28:30 -0700] Returning IPP successful-ok for Send-Document (ipp://localhost:631/printers/Samsung_ML-1740) from localhost
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [13/May/2012:23:28:30 -0700] cupsdCloseClient: 17
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Job 64] print_device
D [13/May/2012:23:28:30 -0700] [Job 64] Page = 612x792; 11,15 to 601,777
D [13/May/2012:23:28:30 -0700] [Job 64] libusb_get_device_list=11
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX SpliX filter V. 2.0.0 by Aurélien Croc (AP²C)
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX More information at: [http://splix.ap2c.org](http://splix.ap2c.org)
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Compiled with: Threads=enabled (#=2, Cache=30), JBIG=enabled, BlackOptim=enabled
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Monochrome printer Samsung ML-1740 with QPDL v. 1
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Cache controller thread loaded and is waiting for a job
D [13/May/2012:23:28:30 -0700] [Job 64] STATE: +connecting-to-device
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] STATE: -connecting-to-device
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] PID 2651 (/usr/lib/cups/filter/texttopdf) exited with no errors.
I [13/May/2012:23:28:30 -0700] [Job 64] Sending data to printer.
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] PPD uses qualifier 'Gray.OFF.600dpi'
D [13/May/2012:23:28:30 -0700] PID 2652 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [13/May/2012:23:28:30 -0700] [Job 64] Calling FindDeviceById(Samsung_ML-1740)
D [13/May/2012:23:28:30 -0700] [Job 64] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Samsung_ML-1740' does not exists
D [13/May/2012:23:28:30 -0700] [Job 64] Failed to get profile filename!
I [13/May/2012:23:28:30 -0700] [Job 64] no profiles specified in PPD
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -r600x600 -dMediaPosition=1 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsCompression=17 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c -f -_
D [13/May/2012:23:28:30 -0700] [Job 64] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[8]="HOME=/var/spool/cups/tmp"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[10]="SERVER_ADMIN=root@centurion"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[11]="SOFTWARE=CUPS/1.5.2"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[12]="USER=root"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[15]="IPP_PORT=631"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[16]="CHARSET=utf-8"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[17]="LANG=en_CA.UTF-8"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[18]="PPD=/etc/cups/ppd/Samsung_ML-1740.ppd"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[19]="RIP_MAX_CACHE=128m"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[20]="CONTENT_TYPE=text/plain"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[21]="DEVICE_URI=usb://Samsung/ML-1740?serial=2W61BKDXC13321A0"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[22]="PRINTER_INFO=Samsung ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[23]="PRINTER_LOCATION=centurion"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[24]="PRINTER=Samsung_ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[25]="PRINTER_STATE_REASONS=none"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[26]="CUPS_FILETYPE=document"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[27]="FINAL_CONTENT_TYPE=printer/Samsung_ML-1740"
D [13/May/2012:23:28:30 -0700] [Job 64] envp[28]="AUTH_INFO_REQUIRED=none"
I [13/May/2012:23:28:30 -0700] [Job 64] Start rendering...
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "Start rendering...", current level=INFO
I [13/May/2012:23:28:30 -0700] [Job 64] Processing page 1...
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Next requested page : 1 (# pages into memory=0/30)
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Document width=4928 height=6350
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Page width=5104 (638) height=6350
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Margin width in bytes=11 height=125
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Clipping X=0 Y=0
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Line size=616, Plane size=4210800, bytes to copy=616
I [13/May/2012:23:28:30 -0700] [Job 64] Processing page 2...
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "Processing page 2...", current level=INFO
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Page 1 (4921×6350 on 5104×6600) has been successfully loaded into memory
I [13/May/2012:23:28:30 -0700] [Job 64] Rendering completed
D [13/May/2012:23:28:30 -0700] [Job 64] Set job-printer-state-message to "Rendering completed", current level=INFO
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX No more pages
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Compression thread: work done. See ya
D [13/May/2012:23:28:30 -0700] PID 2653 (/usr/lib/cups/filter/gstoraster) exited with no errors.
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Page 1 has been compressed and is ready for rendering
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Compression thread: work done. See ya
D [13/May/2012:23:28:30 -0700] [Job 64] PAGE: 1 1
D [13/May/2012:23:28:30 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:30 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Next requested page : 2 (# pages into memory=0/30)
D [13/May/2012:23:28:30 -0700] [Job 64] SpliX Cache controller unloaded. See ya
D [13/May/2012:23:28:30 -0700] [Job 64] Read 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] PID 2654 (/usr/lib/cups/filter/rastertoqpdl) exited with no errors.
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Notifier] state=3
D [13/May/2012:23:28:30 -0700] [Job 64] Wrote 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Read 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Wrote 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Read 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Wrote 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Read 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Wrote 8192 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Read 7044 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Wrote 7044 bytes of print data...
D [13/May/2012:23:28:30 -0700] [Job 64] Sent 39812 bytes...
D [13/May/2012:23:28:30 -0700] [Job 64] Waiting for read thread to exit...

Then about 7 seconds later...

D [13/May/2012:23:28:37 -0700] [Job 64] Read thread still active, aborting the pending read...
D [13/May/2012:23:28:37 -0700] Report: clients=1
D [13/May/2012:23:28:37 -0700] Report: jobs=32
D [13/May/2012:23:28:37 -0700] Report: jobs-active=1
D [13/May/2012:23:28:37 -0700] Report: printers=3
D [13/May/2012:23:28:37 -0700] Report: printers-implicit=0
D [13/May/2012:23:28:37 -0700] Report: stringpool-string-count=16959
D [13/May/2012:23:28:37 -0700] Report: stringpool-alloc-bytes=13800
D [13/May/2012:23:28:37 -0700] Report: stringpool-total-bytes=317688
D [13/May/2012:23:28:38 -0700] PID 2655 (/usr/lib/cups/backend/usb) exited with no errors.
D [13/May/2012:23:28:38 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:38 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
I [13/May/2012:23:28:38 -0700] [Job 64] Job completed.
D [13/May/2012:23:28:38 -0700] cupsdMarkDirty(----J-)
D [13/May/2012:23:28:38 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:38 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:38 -0700] cupsdMarkDirty(-----S)
D [13/May/2012:23:28:38 -0700] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [13/May/2012:23:28:38 -0700] [Notifier] state=3
D [13/May/2012:23:28:38 -0700] [Notifier] state=3
D [13/May/2012:23:28:38 -0700] [Notifier] state=3
D [13/May/2012:23:28:38 -0700] [Notifier] state=3
D [13/May/2012:23:28:39 -0700] [Job 64] Unloading...
D [13/May/2012:23:28:39 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [13/May/2012:23:28:39 -0700] cupsdNetIFUpdate: "eth0" = 192.168.1.2:631
D [13/May/2012:23:28:39 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [13/May/2012:23:28:39 -0700] cupsdNetIFUpdate: "eth0" = [v1.fe80::64b:80ff:fe80:8003+eth0]:631

I have looked at the change in the splix package between 11.10 and 12.04 and it didn't change much. The PPD for my printer didn't have any significant change. There were recomplied with the most recent version of pddc from cups though.

From cups 1.50 to 1.52 there were a lot of bug fixes. Perhaps one of the fixes caused this problem.

Anyone else seeing this problem? Any help would be appreciated.

I'm also not sure what has changed in cups.

---

### Post by jtarin on 2012-05-21
I also had this experience with my Samsung SCX-4200 on 12.04
[Here's the fix.]("http://ubuntuforums.org/showthread.php?t=341621")

---

### Post by mjcross on 2013-02-01
Thanks for the hint - but that thread has over 100 pages (!)

Could you be a bit more specific please ??:)

---

