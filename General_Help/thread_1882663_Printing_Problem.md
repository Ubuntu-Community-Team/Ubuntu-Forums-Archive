---
title: "Printing Problem"
date: 2011-11-17
forum: General Help
---

### Post by HydroMX on 2011-11-17
I have a Lexmark X4650 Printer ans I installed the drivers from their site.  Every time I try to print I get the same error.  "There was a problem processing the document."
Here is my debug information, if anyone can help.

```
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 1.1 Get-Jobs 1
D [17/Nov/2011:16:42:50 -0500] Get-Jobs ipp://localhost/printers/
D [17/Nov/2011:16:42:50 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 1.1 Get-Jobs 1
D [17/Nov/2011:16:42:50 -0500] Get-Jobs ipp://localhost/printers/
D [17/Nov/2011:16:42:50 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:50 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:50 -0500] cupsdReadClient: 14 1.1 Create-Printer-Subscription 1
D [17/Nov/2011:16:42:50 -0500] Create-Printer-Subscription /
D [17/Nov/2011:16:42:50 -0500] cupsdCreateSubscription(con=0x7fc66bffea20(14), uri="/")
D [17/Nov/2011:16:42:50 -0500] pullmethod="ippget"
D [17/Nov/2011:16:42:50 -0500] notify-lease-duration=86400
D [17/Nov/2011:16:42:50 -0500] notify-time-interval=0
D [17/Nov/2011:16:42:50 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [17/Nov/2011:16:42:50 -0500] Added subscription #149 for server.
D [17/Nov/2011:16:42:50 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:50 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [17/Nov/2011:16:42:50 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:52 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:52 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:52 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:52 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [17/Nov/2011:16:42:52 -0500] Get-Notifications /
D [17/Nov/2011:16:42:52 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:42:52 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:42:52 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 16 POST /printers/Lexmark-X4650 HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 16 1.1 Print-Job 1
D [17/Nov/2011:16:42:57 -0500] Print-Job ipp://localhost/printers/Lexmark-X4650
D [17/Nov/2011:16:42:57 -0500] [Job ???] Auto-typing file...
I [17/Nov/2011:16:42:57 -0500] [Job ???] Request file type is application/vnd.cups-banner.
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(----J-)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] add_job: requesting-user-name="chris"
D [17/Nov/2011:16:42:57 -0500] Adding default job-sheets values "none,none"...
I [17/Nov/2011:16:42:57 -0500] [Job 8] Adding start banner page "none".
D [17/Nov/2011:16:42:57 -0500] Notifier dbus started - PID = 10542
D [17/Nov/2011:16:42:57 -0500] Notifier dbus started - PID = 10543
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(----J-)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
I [17/Nov/2011:16:42:57 -0500] [Job 8] Adding end banner page "none".
I [17/Nov/2011:16:42:57 -0500] [Job 8] File of type application/vnd.cups-banner queued by "chris".
D [17/Nov/2011:16:42:57 -0500] [Job 8] hold_until=0
I [17/Nov/2011:16:42:57 -0500] [Job 8] Queued on "Lexmark-X4650" by "chris".
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(----J-)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] [Job 8] job-sheets=none,none
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[0]="Lexmark-X4650"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[1]="8"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[2]="chris"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[3]="Test Page"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[4]="1"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[5]="job-uuid=urn:uuid:c9e334e1-ad6c-3c8a-529e-d45ea5c0f4e0 media=na_letter_8.5x11in number-up=16 print-color-mode=color print-quality=4 printer-resolution=300x300dpi job-originating-host-name=localhost time-at-creation=1321566177 time-at-processing=1321566177 AP_D_InputSlot= PageSize=Letter"
D [17/Nov/2011:16:42:57 -0500] [Job 8] argv[6]="/var/spool/cups/d00008-001"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[8]="HOME=/var/spool/cups/tmp"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[10]="SERVER_ADMIN=root@chris-laptop"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[11]="SOFTWARE=CUPS/1.5.0"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[13]="USER=root"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[16]="IPP_PORT=631"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[17]="CHARSET=utf-8"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[18]="LANG=en_US.UTF-8"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[19]="PPD=/etc/cups/ppd/Lexmark-X4650.ppd"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[20]="RIP_MAX_CACHE=128m"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[22]="DEVICE_URI=socket://192.168.1.119:9100"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[23]="PRINTER_INFO=Lexmark-X4650"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[24]="PRINTER_LOCATION="
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[25]="PRINTER=Lexmark-X4650"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[26]="PRINTER_STATE_REASONS=none"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[27]="CUPS_FILETYPE=document"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[28]="FINAL_CONTENT_TYPE=printer/Lexmark-X4650"
D [17/Nov/2011:16:42:57 -0500] [Job 8] envp[29]="AUTH_I****"
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started filter /usr/lib/cups/filter/bannertops (PID 10544)
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started filter /usr/lib/cups/filter/pstopdf (PID 10545)
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started filter /usr/lib/cups/filter/pdftopdf (PID 10546)
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started filter /usr/lib/cups/filter/gstoraster (PID 10547)
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started filter /usr/lexinkjet/08zero/bin/printdriver (PID 10550)
I [17/Nov/2011:16:42:57 -0500] [Job 8] Started backend /usr/lib/cups/backend/socket (PID 10551)
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Lexmark-X4650) from localhost
D [17/Nov/2011:16:42:57 -0500] PID 10550 (/usr/lexinkjet/08zero/bin/printdriver) stopped with status 127 (File too large)
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Notifier] Connected to D-BUS
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Job 8] pstopdf 5 args: 8 chris Test Page 1 job-uuid=urn:uuid:c9e334e1-ad6c-3c8a-529e-d45ea5c0f4e0 media=na_letter_8.5x11in number-up=16 print-color-mode=color print-quality=4 printer-resolution=300x300dpi job-originating-host-name=localhost time-at-creation=1321566177 time-at-processing=1321566177 AP_D_InputSlot= PageSize=Letter
D [17/Nov/2011:16:42:57 -0500] [Job 8] PPD: /etc/cups/ppd/Lexmark-X4650.ppd
D [17/Nov/2011:16:42:57 -0500] [Job 8] Lexmark-X4650: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [17/Nov/2011:16:42:57 -0500] [Notifier] Connected to D-BUS
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Job 8] STATE: +connecting-to-device
D [17/Nov/2011:16:42:57 -0500] [Job 8] Looking up "192.168.1.119"...
D [17/Nov/2011:16:42:57 -0500] [Job 8] load_banner(filename="/var/spool/cups/d00008-001")
D [17/Nov/2011:16:42:57 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Printing jobs and dirty files"
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:57 -0500] [Job 8] 1 #CUPS-BANNER
D [17/Nov/2011:16:42:57 -0500] [Job 8] 2 Show printer-name printer-info printer-location printer-make-and-model printer-driver-name printer-driver-version paper-size imageable-area
D [17/Nov/2011:16:42:57 -0500] [Job 8] 3 Header Printer Test Page
D [17/Nov/2011:16:42:57 -0500] [Job 8] 4 Footer Printer Test Page
D [17/Nov/2011:16:42:57 -0500] [Job 8] 5 Notice CUPS 1.5.0.
D [17/Nov/2011:16:42:57 -0500] [Job 8] 6 Image images/cups.png
D [17/Nov/2011:16:42:57 -0500] [Job 8] 7 Image images/color-wheel.png
D [17/Nov/2011:16:42:57 -0500] [Job 8] Page = 612x792; 18,36 to 594,787
D [17/Nov/2011:16:42:57 -0500] [Job 8] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [17/Nov/2011:16:42:57 -0500] [Job 8] PNG image: 192x128x8, color_type=2 (RGB)
D [17/Nov/2011:16:42:57 -0500] PID 10544 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [17/Nov/2011:16:42:57 -0500] [Job 8] Resolution:
D [17/Nov/2011:16:42:57 -0500] [Job 8] Page size: Letter
D [17/Nov/2011:16:42:57 -0500] [Job 8] Width: 612.00, height: 792.00, absolute margins: 18.00, 36.00, 594.00, 787.20
D [17/Nov/2011:16:42:57 -0500] [Job 8] Relative margins: 18.00, 36.00, 18.00, 4.80
D [17/Nov/2011:16:42:57 -0500] [Job 8] PPD options: -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00
D [17/Nov/2011:16:42:57 -0500] [Job 8] PostScript to be injected:
D [17/Nov/2011:16:42:57 -0500] [Job 8] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -dNOINTERPOLATE -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 -sOutputFile=-  -c .setpdfwrite -f -
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 22 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 22 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 22 1.1 Get-Notifications 1
D [17/Nov/2011:16:42:57 -0500] Get-Notifications /
D [17/Nov/2011:16:42:57 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 22 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Printer-Attributes
D [17/Nov/2011:16:42:57 -0500] Get-Printer-Attributes client-error-not-found: The printer or class does not exist.
D [17/Nov/2011:16:42:57 -0500] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 24 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 24 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 24 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 24 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 24
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Printer-Attributes ipp://chris-laptop/printers/Lexmark-X4650
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://chris-laptop/printers/Lexmark-X4650) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:57 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 22 WAITING Closing on EOF
D [17/Nov/2011:16:42:57 -0500] cupsdCloseClient: 22
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:57 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:57 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [17/Nov/2011:16:42:57 -0500] Get-Notifications /
D [17/Nov/2011:16:42:57 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:42:57 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:42:57 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:58 -0500] PID 10545 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [17/Nov/2011:16:42:58 -0500] PID 10546 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [17/Nov/2011:16:42:58 -0500] [Job 8] PPD uses qualifier 'Color.Automatic.'
D [17/Nov/2011:16:42:58 -0500] [Job 8] Calling FindDeviceById(Lexmark-X4650)
D [17/Nov/2011:16:42:58 -0500] [Job 8] Failed to send: org.freedesktop.DBus.Error.AccessDenied:Rejected send message, 1 matched rules; type="method_call", sender=":1.169" (uid=7 pid=10547 comm="Lexmark-X4650 8 chris Test Page 1 job-uuid=urn:uui") interface="org.freedesktop.ColorManager" member="FindDeviceById" error name="(unset)" requested_reply="0" destination="org.freedesktop.ColorManager" (uid=102 pid=1330 comm="/usr/lib/x86_64-linux-gnu/colord/colord ")
D [17/Nov/2011:16:42:58 -0500] [Job 8] Failed to get profile filename!
I [17/Nov/2011:16:42:58 -0500] [Job 8] no profiles specified in PPD
D [17/Nov/2011:16:42:58 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] [Job 8] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sOutputType=5 -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsCompression=1 -dcupsRowStep=1 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c -f -_
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[8]="HOME=/var/spool/cups/tmp"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[10]="SERVER_ADMIN=root@chris-laptop"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[11]="SOFTWARE=CUPS/1.5.0"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[12]="USER=root"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[15]="IPP_PORT=631"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[16]="CHARSET=utf-8"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[17]="LANG=en_US.UTF-8"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[18]="PPD=/etc/cups/ppd/Lexmark-X4650.ppd"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[19]="RIP_MAX_CACHE=128m"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[20]="CONTENT_TYPE=application/vnd.cups-banner"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[21]="DEVICE_URI=socket://192.168.1.119:9100"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[22]="PRINTER_INFO=Lexmark-X4650"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[23]="PRINTER_LOCATION="
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[24]="PRINTER=Lexmark-X4650"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[25]="PRINTER_STATE_REASONS=none"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[26]="CUPS_FILETYPE=document"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[27]="FINAL_CONTENT_TYPE=printer/Lexmark-X4650"
D [17/Nov/2011:16:42:58 -0500] [Job 8] envp[28]="AUTH_INFO_REQUIRED=none"
D [17/Nov/2011:16:42:58 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:58 -0500] [Notifier] state=3
I [17/Nov/2011:16:42:58 -0500] [Job 8] Start rendering...
I [17/Nov/2011:16:42:58 -0500] [Job 8] Processing page 1...
D [17/Nov/2011:16:42:58 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:58 -0500] [Notifier] state=3
D [17/Nov/2011:16:42:58 -0500] cupsdAcceptClient: 22 from localhost (Domain)
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 22 POST / HTTP/1.1
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 22 1.1 Get-Notifications 1
D [17/Nov/2011:16:42:58 -0500] Get-Notifications /
D [17/Nov/2011:16:42:58 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:42:58 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:58 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:58 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:58 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:42:58 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:42:58 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 23 WAITING Closing on EOF
D [17/Nov/2011:16:42:58 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 22 WAITING Closing on EOF
D [17/Nov/2011:16:42:58 -0500] cupsdCloseClient: 22
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:42:58 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:42:58 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [17/Nov/2011:16:42:58 -0500] Get-Notifications /
D [17/Nov/2011:16:42:58 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:42:58 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:42:58 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:42:59 -0500] PID 10547 (/usr/lib/cups/filter/gstoraster) stopped with status 13.
D [17/Nov/2011:16:43:01 -0500] [Job 8] prtGeneralCurrentLocalization type is 7fff, expected 2!
D [17/Nov/2011:16:43:01 -0500] [Job 8] backendWaitLoop(snmp_fd=5, addr=0x7f8a4b5609b8, side_cb=0x7f8a4a321dd0)
D [17/Nov/2011:16:43:01 -0500] PID 10551 (/usr/lib/cups/backend/socket) exited with no errors.
D [17/Nov/2011:16:43:01 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Dirty files"
E [17/Nov/2011:16:43:01 -0500] [Job 8] Job stopped due to filter errors; please consult the error_log file for details.
D [17/Nov/2011:16:43:01 -0500] cupsdMarkDirty(----J-)
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [17/Nov/2011:16:43:01 -0500] [Job 8] The following messages were recorded from 16:42:59 to 16:42:59
D [17/Nov/2011:16:43:01 -0500] [Job 8] hrDeviceDesc="Unknown"
D [17/Nov/2011:16:43:01 -0500] [Job 8] End of messages
D [17/Nov/2011:16:43:01 -0500] [Job 8] printer-state=3(idle)
D [17/Nov/2011:16:43:01 -0500] [Job 8] printer-state-message="Processing page 1..."
D [17/Nov/2011:16:43:01 -0500] [Job 8] printer-state-reasons=none
D [17/Nov/2011:16:43:01 -0500] [Notifier] state=3
D [17/Nov/2011:16:43:01 -0500] [Notifier] state=3
D [17/Nov/2011:16:43:01 -0500] [Notifier] state=3
D [17/Nov/2011:16:43:01 -0500] cupsdAcceptClient: 19 from localhost (Domain)
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 19 POST / HTTP/1.1
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Printing jobs and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 19 1.1 Get-Notifications 1
D [17/Nov/2011:16:43:01 -0500] Get-Notifications /
D [17/Nov/2011:16:43:01 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:43:01 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAcceptClient: 22 from localhost (Domain)
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 22 POST / HTTP/1.1
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 22 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:43:01 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:43:01 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAcceptClient: 23 from localhost (Domain)
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [17/Nov/2011:16:43:01 -0500] Get-Printer-Attributes ipp://chris-laptop/printers/Lexmark-X4650
D [17/Nov/2011:16:43:01 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://chris-laptop/printers/Lexmark-X4650) from localhost
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 23 POST / HTTP/1.1
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:43:01 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:43:01 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:01 -0500] cupsdReadClient: 22 WAITING Closing on EOF
D [17/Nov/2011:16:43:01 -0500] cupsdCloseClient: 22
D [17/Nov/2011:16:43:01 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:02 -0500] cupsdReadClient: 19 WAITING Closing on EOF
D [17/Nov/2011:16:43:02 -0500] cupsdCloseClient: 19
D [17/Nov/2011:16:43:02 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:02 -0500] [Job 8] Unloading...
D [17/Nov/2011:16:43:02 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:43:02 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:02 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:02 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [17/Nov/2011:16:43:02 -0500] Get-Notifications /
D [17/Nov/2011:16:43:02 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:43:02 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [17/Nov/2011:16:43:02 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 1.1 Get-Job-Attributes 1
D [17/Nov/2011:16:43:07 -0500] Get-Job-Attributes ipp://localhost/jobs/8
D [17/Nov/2011:16:43:07 -0500] [Job 8] Loading attributes...
D [17/Nov/2011:16:43:07 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/8) from localhost
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 1.1 Cancel-Subscription 1
D [17/Nov/2011:16:43:07 -0500] Cancel-Subscription /
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: requesting-user-name="chris"
D [17/Nov/2011:16:43:07 -0500] cupsdMarkDirty(-----S)
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: No authentication data provided.
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: username=""
D [17/Nov/2011:16:43:07 -0500] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [17/Nov/2011:16:43:07 -0500] cupsdCloseClient: 14
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: Authorized as chris using PeerCred
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: username="chris"
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: Authorized as chris using PeerCred
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: username="chris"
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: Authorized as chris using PeerCred
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: username="chris"
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [17/Nov/2011:16:43:07 -0500] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:07 -0500] cupsdAuthorize: Authorized as chris using PeerCred
D [17/Nov/2011:16:43:07 -0500] cupsdIsAuthorized: username="chris"
I [17/Nov/2011:16:43:07 -0500] Installing config file "/etc/cups/cupsd.conf"...
D [17/Nov/2011:16:43:08 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [17/Nov/2011:16:43:08 -0500] cupsdCloseClient: 16
D [17/Nov/2011:16:43:08 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:08 -0500] cupsdCloseClient: 23
D [17/Nov/2011:16:43:08 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [17/Nov/2011:16:43:08 -0500] cupsdCloseClient: 14
D [17/Nov/2011:16:43:08 -0500] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [17/Nov/2011:16:43:08 -0500] Generating printcap /var/run/cups/printcap...
I [17/Nov/2011:16:43:08 -0500] Saving job.cache...
I [17/Nov/2011:16:43:08 -0500] Saving subscriptions.conf...
D [17/Nov/2011:16:43:08 -0500] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [17/Nov/2011:16:43:08 -0500] Unknown directive JobPrivateAccess on line 88.
E [17/Nov/2011:16:43:08 -0500] Unknown directive JobPrivateValues on line 89.
E [17/Nov/2011:16:43:08 -0500] Unknown directive SubscriptionPrivateAccess on line 90.
E [17/Nov/2011:16:43:08 -0500] Unknown directive SubscriptionPrivateValues on line 91.
W [17/Nov/2011:16:43:08 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/3600_4600_Series_Gray__' has already been added
W [17/Nov/2011:16:43:08 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/3600_4600_Series_RGB__' has already been added
W [17/Nov/2011:16:43:08 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_X4650_Gray__' has already been added
W [17/Nov/2011:16:43:08 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_X4650_RGB__' has already been added
```

---

### Post by mrsanna1 on 2012-05-13
Hello, I have the same printer and the same problem.
Have you solved?

---

