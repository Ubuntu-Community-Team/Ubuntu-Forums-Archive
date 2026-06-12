---
title: "Canon PIXMA iP 1600 Refuses to work under Natty"
date: 2011-07-16
forum: General Help
---

### Post by LoneSt4r on 2011-07-16
Hello!

I got this printer to work on all the previous releases, but not 11.04.  I followed the same process as before, using Canon's iP 2200 drivers and using them to configure the iP 1600.  I get that far, but when I try and print the test page, the job counter increases, I briefly see the job in the queue, but the printer never reacts.

This is the only error shown in /var/logs/cups/error_log :

```
E [16/Jul/2011:23:33:03 -0400] [Job 20] aucun %%BoundingBox*: commentaire dans l’en-tête.
```

When changing the log level from Warning to Debug, I get this :

```
I [16/Jul/2011:23:32:55 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [16/Jul/2011:23:32:56 -0400] Listening to [v1.::1]:631 (IPv6)
I [16/Jul/2011:23:32:56 -0400] Listening to 127.0.0.1:631 (IPv4)
I [16/Jul/2011:23:32:56 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [16/Jul/2011:23:32:56 -0400] Remote access is disabled.
D [16/Jul/2011:23:32:56 -0400] Added auto ServerAlias boulac
I [16/Jul/2011:23:32:56 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [16/Jul/2011:23:32:56 -0400] Using default TempDir of /var/spool/cups/tmp...
I [16/Jul/2011:23:32:56 -0400] Configured for up to 100 clients.
I [16/Jul/2011:23:32:56 -0400] Allowing up to 100 client connections per host.
I [16/Jul/2011:23:32:56 -0400] Using policy "default" as the default!
I [16/Jul/2011:23:32:56 -0400] Full reload is required.
I [16/Jul/2011:23:32:56 -0400] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 38 types, 77 filters...
D [16/Jul/2011:23:32:56 -0400] Loading printer Canon-iP1600...
D [16/Jul/2011:23:32:56 -0400] load_ppd: Loading /var/cache/cups/Canon-iP1600.ipp4...
D [16/Jul/2011:23:32:56 -0400] cupsdRegisterPrinter(p=0x222f73e0(Canon-iP1600))
D [16/Jul/2011:23:32:56 -0400] cupsdLoadRemoteCache: Not loading remote cache.
I [16/Jul/2011:23:32:56 -0400] Loading job cache file "/var/cache/cups/job.cache"...
D [16/Jul/2011:23:32:56 -0400] [Job 10] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 11] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 12] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 13] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 14] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 15] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 16] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 17] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 18] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] [Job 19] Loading from cache...
D [16/Jul/2011:23:32:56 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
D [16/Jul/2011:23:32:56 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
D [16/Jul/2011:23:32:56 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
D [16/Jul/2011:23:32:56 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
D [16/Jul/2011:23:32:56 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
I [16/Jul/2011:23:32:56 -0400] Full reload complete.
D [16/Jul/2011:23:32:56 -0400] cupsd_clean_files(path="/var/spool/cups/tmp", pattern="(null)")
I [16/Jul/2011:23:32:56 -0400] Cleaning out old files in "/var/spool/cups/tmp"...
D [16/Jul/2011:23:32:56 -0400] cupsd_clean_files(path="/var/cache/cups", pattern="*.ipp")
I [16/Jul/2011:23:32:56 -0400] Cleaning out old files in "/var/cache/cups"...
I [16/Jul/2011:23:32:56 -0400] Listening to [v1.::1]:631 on fd 6...
I [16/Jul/2011:23:32:56 -0400] Listening to 127.0.0.1:631 on fd 7...
I [16/Jul/2011:23:32:56 -0400] Listening to /var/run/cups/cups.sock on fd 8...
I [16/Jul/2011:23:32:56 -0400] Resuming new connection processing...
D [16/Jul/2011:23:32:56 -0400] Discarding unused server-started event...
D [16/Jul/2011:23:32:57 -0400] Report: clients=0
D [16/Jul/2011:23:32:57 -0400] Report: jobs=10
D [16/Jul/2011:23:32:57 -0400] Report: jobs-active=0
D [16/Jul/2011:23:32:57 -0400] Report: printers=1
D [16/Jul/2011:23:32:57 -0400] Report: printers-implicit=0
D [16/Jul/2011:23:32:57 -0400] Report: stringpool-string-count=3403
D [16/Jul/2011:23:32:57 -0400] Report: stringpool-alloc-bytes=7984
D [16/Jul/2011:23:32:57 -0400] Report: stringpool-total-bytes=63128
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 11 POST /printers/Canon-iP1600 HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 11 1.1 Print-Job 1
D [16/Jul/2011:23:33:03 -0400] Print-Job ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:03 -0400] [Job ???] Auto-typing file...
I [16/Jul/2011:23:33:03 -0400] [Job ???] Request file type is application/postscript.
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(----J-)
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:03 -0400] add_job: requesting-user-name="momo"
D [16/Jul/2011:23:33:03 -0400] Adding default job-sheets values "none,none"...
I [16/Jul/2011:23:33:03 -0400] [Job 20] Adding start banner page "none".
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(----J-)
I [16/Jul/2011:23:33:03 -0400] [Job 20] Adding end banner page "none".
I [16/Jul/2011:23:33:03 -0400] [Job 20] File of type application/postscript queued by "momo".
D [16/Jul/2011:23:33:03 -0400] [Job 20] hold_until=0
I [16/Jul/2011:23:33:03 -0400] [Job 20] Queued on "Canon-iP1600" by "momo".
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(----J-)
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] [Job 20] job-sheets=none,none
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[0]="Canon-iP1600"
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[1]="20"
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[2]="momo"
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[3]="Test Page"
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[4]="1"
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[5]="PageSize=Letter job-uuid=urn:uuid:ceec023b-9e69-37ab-71e9-6f09f3923049 job-originating-host-name=localhost time-at-creation=1310873583 time-at-processing=1310873583 AP_D_InputSlot="
D [16/Jul/2011:23:33:03 -0400] [Job 20] argv[6]="/var/spool/cups/d00020-001"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[8]="HOME=/var/spool/cups/tmp"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[10]="SERVER_ADMIN=root@boulac"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[11]="SOFTWARE=CUPS/1.4.6"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[13]="USER=root"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[16]="IPP_PORT=631"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[17]="CHARSET=utf-8"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[18]="LANG=fr_CA.UTF-8"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[19]="PPD=/etc/cups/ppd/Canon-iP1600.ppd"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[20]="RIP_MAX_CACHE=auto"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[21]="CONTENT_TYPE=application/postscript"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[22]="DEVICE_URI=usb://Canon/iP1600"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[23]="PRINTER_INFO=Canon iP1600"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[24]="PRINTER_LOCATION=boulac"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[25]="PRINTER=Canon-iP1600"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[26]="CUPS_FILETYPE=document"
D [16/Jul/2011:23:33:03 -0400] [Job 20] envp[27]="FINAL_CONTENT_TYPE=printer/Canon-iP1600"
I [16/Jul/2011:23:33:03 -0400] [Job 20] Started filter /usr/lib/cups/filter/pstops (PID 9788)
I [16/Jul/2011:23:33:03 -0400] [Job 20] Started filter /usr/lib/cups/filter/pstocanonij (PID 9789)
I [16/Jul/2011:23:33:03 -0400] [Job 20] Started backend /usr/lib/cups/backend/usb (PID 9790)
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] [Job 20] Page = 612x792; 18,14 to 594,784
D [16/Jul/2011:23:33:03 -0400] [Job 20] slow_collate=0, slow_duplex=0, slow_order=0
D [16/Jul/2011:23:33:03 -0400] [Job 20] Before copy_comments - %!PS-Adobe-3.0
D [16/Jul/2011:23:33:03 -0400] [Job 20] %!PS-Adobe-3.0
D [16/Jul/2011:23:33:03 -0400] [Job 20] %%Title: PPR Test Page
D [16/Jul/2011:23:33:03 -0400] [Job 20] %%Pages: 1
D [16/Jul/2011:23:33:03 -0400] [Job 20] %%DocumentNeededResources: font Helvetica
D [16/Jul/2011:23:33:03 -0400] [Job 20] %%EndComments
E [16/Jul/2011:23:33:03 -0400] [Job 20] aucun %%BoundingBox*: commentaire dans l’en-tête.
D [16/Jul/2011:23:33:03 -0400] [Job 20] Set job-printer-state-message to "aucun %%BoundingBox*: commentaire dans l’en-tête.", current level=ERROR
D [16/Jul/2011:23:33:03 -0400] [Job 20] Before copy_prolog - %%BeginProlog
D [16/Jul/2011:23:33:03 -0400] [Job 20] Before copy_setup - %%BeginSetup
D [16/Jul/2011:23:33:03 -0400] [Job 20] Before page loop - %%Page: 1 1
D [16/Jul/2011:23:33:03 -0400] [Job 20] Copying page 1...
D [16/Jul/2011:23:33:03 -0400] [Job 20] pagew = 576.0, pagel = 769.3
D [16/Jul/2011:23:33:03 -0400] [Job 20] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [16/Jul/2011:23:33:03 -0400] [Job 20] PageLeft = 18.1, PageRight = 594.1
D [16/Jul/2011:23:33:03 -0400] [Job 20] PageTop = 783.5, PageBottom = 14.2
D [16/Jul/2011:23:33:03 -0400] [Job 20] PageWidth = 612.0, PageLength = 792.0
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] [Job 20] STATE: +connecting-to-device
D [16/Jul/2011:23:33:03 -0400] [Job 20] pstocanonij start.
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] [Job 20] Printer using device file "/dev/usblp0"...
D [16/Jul/2011:23:33:03 -0400] [Job 20] STATE: -connecting-to-device
D [16/Jul/2011:23:33:03 -0400] [Job 20] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0xbf0230)
D [16/Jul/2011:23:33:03 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:03 -0400] [Job 20] pstocanonij: /usr/bin/gs -r600 -g5100x6600 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/local/bin/cifip2200 --imageres 600 --papersize letter --media plain --bbox 18,14,594,784 
D [16/Jul/2011:23:33:03 -0400] [Job 20] Wrote 1 pages...
D [16/Jul/2011:23:33:03 -0400] PID 9788 (/usr/lib/cups/filter/pstops) exited with no errors.
D [16/Jul/2011:23:33:03 -0400] [Job 20] /usr/local/bin/cifip2200: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:03 -0400] Get-Notifications /
D [16/Jul/2011:23:33:03 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [16/Jul/2011:23:33:03 -0400] cupsdCloseClient: 16
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [16/Jul/2011:23:33:03 -0400] cupsdCloseClient: 16
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [16/Jul/2011:23:33:03 -0400] cupsdCloseClient: 16
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [16/Jul/2011:23:33:03 -0400] cupsdCloseClient: 16
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [16/Jul/2011:23:33:03 -0400] cupsdCloseClient: 15
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:03 -0400] Get-Notifications /
D [16/Jul/2011:23:33:03 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:03 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:03 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:03 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:03 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:03 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 15
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:04 -0400] Get-Notifications /
D [16/Jul/2011:23:33:04 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 17
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 17
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 17
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [16/Jul/2011:23:33:04 -0400] Get-Job-Attributes ipp://localhost/jobs/20
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/20) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 17
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [16/Jul/2011:23:33:04 -0400] cupsdCloseClient: 15
D [16/Jul/2011:23:33:04 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [16/Jul/2011:23:33:04 -0400] CUPS-Get-Printers
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [16/Jul/2011:23:33:04 -0400] CUPS-Get-Classes
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [16/Jul/2011:23:33:04 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:04 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [16/Jul/2011:23:33:04 -0400] CUPS-Get-Default
D [16/Jul/2011:23:33:04 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [16/Jul/2011:23:33:04 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [16/Jul/2011:23:33:05 -0400] PID 9789 (/usr/lib/cups/filter/pstocanonij) exited with no errors.
D [16/Jul/2011:23:33:05 -0400] PID 9790 (/usr/lib/cups/backend/usb) exited with no errors.
D [16/Jul/2011:23:33:05 -0400] cupsdMarkDirty(-----S)
I [16/Jul/2011:23:33:05 -0400] [Job 20] Job completed.
D [16/Jul/2011:23:33:05 -0400] cupsdMarkDirty(----J-)
D [16/Jul/2011:23:33:05 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:05 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:05 -0400] Get-Notifications /
D [16/Jul/2011:23:33:05 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:05 -0400] Get-Printer-Attributes ipp://boulac/printers/Canon-iP1600
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://boulac/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 WAITING Closing on EOF
D [16/Jul/2011:23:33:05 -0400] cupsdCloseClient: 13
D [16/Jul/2011:23:33:05 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:05 -0400] Get-Notifications /
D [16/Jul/2011:23:33:05 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [16/Jul/2011:23:33:05 -0400] Get-Printer-Attributes ipp://localhost/printers/Canon-iP1600
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon-iP1600) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 WAITING Closing on EOF
D [16/Jul/2011:23:33:05 -0400] cupsdCloseClient: 13
D [16/Jul/2011:23:33:05 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [16/Jul/2011:23:33:05 -0400] Get-Notifications /
D [16/Jul/2011:23:33:05 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 13 WAITING Closing on EOF
D [16/Jul/2011:23:33:05 -0400] cupsdCloseClient: 13
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [16/Jul/2011:23:33:05 -0400] CUPS-Get-Printers
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Classes 1
D [16/Jul/2011:23:33:05 -0400] CUPS-Get-Classes
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:05 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:05 -0400] cupsdReadClient: 15 1.1 CUPS-Get-Default 1
D [16/Jul/2011:23:33:05 -0400] CUPS-Get-Default
D [16/Jul/2011:23:33:05 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [16/Jul/2011:23:33:05 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:06 -0400] Avahi client started
D [16/Jul/2011:23:33:06 -0400] [Job 20] Unloading...
D [16/Jul/2011:23:33:11 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [16/Jul/2011:23:33:11 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [16/Jul/2011:23:33:11 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:11 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:11 -0400] cupsdReadClient: 18 1.1 Cancel-Subscription 1
D [16/Jul/2011:23:33:11 -0400] Cancel-Subscription /
D [16/Jul/2011:23:33:11 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:11 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:11 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [16/Jul/2011:23:33:11 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:11 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [16/Jul/2011:23:33:11 -0400] cupsdCloseClient: 18
D [16/Jul/2011:23:33:12 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [16/Jul/2011:23:33:12 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [16/Jul/2011:23:33:12 -0400] cupsdSetBusyState: Active clients and dirty files
D [16/Jul/2011:23:33:12 -0400] cupsdAuthorize: No authentication data provided.
D [16/Jul/2011:23:33:12 -0400] cupsdReadClient: 18 1.1 Cancel-Subscription 1
D [16/Jul/2011:23:33:12 -0400] Cancel-Subscription /
D [16/Jul/2011:23:33:12 -0400] cupsdIsAuthorized: requesting-user-name="momo"
D [16/Jul/2011:23:33:12 -0400] cupsdMarkDirty(-----S)
D [16/Jul/2011:23:33:12 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [16/Jul/2011:23:33:12 -0400] cupsdSetBusyState: Dirty files
D [16/Jul/2011:23:33:12 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [16/Jul/2011:23:33:12 -0400] cupsdCloseClient: 18
D [16/Jul/2011:23:33:19 -0400] cupsdReadClient: 11 WAITING Closing on EOF
D [16/Jul/2011:23:33:19 -0400] cupsdCloseClient: 11
D [16/Jul/2011:23:33:20 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [16/Jul/2011:23:33:20 -0400] cupsdCloseClient: 15
D [16/Jul/2011:23:33:20 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [16/Jul/2011:23:33:20 -0400] cupsdCloseClient: 16
I [16/Jul/2011:23:33:34 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [16/Jul/2011:23:33:34 -0400] Saving subscriptions.conf...
D [16/Jul/2011:23:33:34 -0400] cupsdSetBusyState: Not busy
```

All of this seems to indicate that the job went through.  Any idea what might be missing?

Thanks!

---

### Post by pmalvr on 2012-01-29
I have the same problem. I could not print anymore since I updated to Ubuntu 11.10 :-(

---

### Post by LoneSt4r on 2012-01-30
Good morning,

I have found a magic command allowing you to find what is wrong with your printer.

```
ldd /usr/local/bin/cifip2200
```

The full article is at [http://forum.ubuntu-fr.org/viewtopic.php?pid=5212941#p5212941]("http://forum.ubuntu-fr.org/viewtopic.php?pid=5212941#p5212941")

Enjoy!

---

