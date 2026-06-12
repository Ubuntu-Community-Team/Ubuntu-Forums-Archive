---
title: "Canon IR 5075 printing broken, ouch!"
date: 2010-10-14
forum: General Help
---

### Post by gjohn2 on 2010-10-14
After upgrading to 10.10, I can no longer print to the 
canon ir5075 in my dept. i was using the pslinux 1.80 drivers
that i got from canon new zealand in a deb. 

I get an error message about a missing filter: pstopscpca

This means that I can't print to my Dept. Copier. :( boo.

Anyone know what is going on?

best,
greg

---

### Post by gjohn2 on 2010-10-14
I think the bottom line is relevant. :(



D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [14/Oct/2010:11:55:33 -0400] Get-Jobs ipp://localhost/printers/
D [14/Oct/2010:11:55:33 -0400] [Job 58] Loading attributes...
D [14/Oct/2010:11:55:33 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [14/Oct/2010:11:55:33 -0400] Get-Jobs ipp://localhost/printers/
D [14/Oct/2010:11:55:33 -0400] [Job 56] Loading attributes...
D [14/Oct/2010:11:55:33 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:33 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:33 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1
D [14/Oct/2010:11:55:33 -0400] Create-Printer-Subscription /
D [14/Oct/2010:11:55:33 -0400] cupsdCreateSubscription(con=0x206d02f0(11), uri="/")
D [14/Oct/2010:11:55:33 -0400] pullmethod="ippget"
D [14/Oct/2010:11:55:33 -0400] notify-lease-duration=86400
D [14/Oct/2010:11:55:33 -0400] notify-time-interval=0
D [14/Oct/2010:11:55:33 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [14/Oct/2010:11:55:33 -0400] Added subscription 47 for server
D [14/Oct/2010:11:55:33 -0400] cupsdMarkDirty(-----S)
D [14/Oct/2010:11:55:33 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [14/Oct/2010:11:55:33 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:35 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:55:35 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:35 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:35 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [14/Oct/2010:11:55:35 -0400] Get-Notifications /
D [14/Oct/2010:11:55:35 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:55:35 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2010:11:55:35 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 12 POST /printers/Canon-iR5075 HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 12 1.1 Print-Job 1
D [14/Oct/2010:11:55:39 -0400] Print-Job ipp://localhost/printers/Canon-iR5075
D [14/Oct/2010:11:55:39 -0400] [Job ???] Auto-typing file...
I [14/Oct/2010:11:55:39 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(----J-)
D [14/Oct/2010:11:55:39 -0400] add_job: requesting-user-name="haka"
D [14/Oct/2010:11:55:39 -0400] Adding default job-sheets values "none,none"...
I [14/Oct/2010:11:55:39 -0400] [Job 60] Adding start banner page "none".
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(-----S)
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(----J-)
I [14/Oct/2010:11:55:39 -0400] [Job 60] Adding end banner page "none".
I [14/Oct/2010:11:55:39 -0400] [Job 60] File of type application/vnd.cups-banner queued by "haka".
D [14/Oct/2010:11:55:39 -0400] [Job 60] hold_until=0
I [14/Oct/2010:11:55:39 -0400] [Job 60] Queued on "Canon-iR5075" by "haka".
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(----J-)
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(-----S)
D [14/Oct/2010:11:55:39 -0400] [Job 60] job-sheets=none,none
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[0]="Canon-iR5075"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[1]="60"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[2]="haka"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[3]="Test Page"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[4]="1"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[5]="job-uuid=urn:uuid:4f64e5b3-4dd9-3c4b-481a-4b2be416cbdd job-originating-host-name=localhost"
D [14/Oct/2010:11:55:39 -0400] [Job 60] argv[6]="/var/spool/cups/d00060-001"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[10]="SERVER_ADMIN=root@louhi"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[11]="SOFTWARE=CUPS/1.4.4"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[13]="USER=root"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[16]="IPP_PORT=631"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[17]="CHARSET=utf-8"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[18]="LANG=en_US.UTF-8"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[19]="PPD=/etc/cups/ppd/Canon-iR5075.ppd"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[20]="RIP_MAX_CACHE=auto"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[22]="DEVICE_URI=socket://35.8.73.42:9100"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[23]="PRINTER_INFO=Canon iR5075"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[24]="PRINTER_LOCATION="
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[25]="PRINTER=Canon-iR5075"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[26]="CUPS_FILETYPE=document"
D [14/Oct/2010:11:55:39 -0400] [Job 60] envp[27]="FINAL_CONTENT_TYPE=printer/Canon-iR5075"
I [14/Oct/2010:11:55:39 -0400] [Job 60] Started filter /usr/lib/cups/filter/bannertops (PID 3563)
I [14/Oct/2010:11:55:39 -0400] [Job 60] Started filter /usr/lib/cups/filter/pstops (PID 3564)
E [14/Oct/2010:11:55:39 -0400] Unable to execute /usr/lib/cups/filter/pstopscpca: No such file or directory
E [14/Oct/2010:11:55:39 -0400] [Job 60] Unable to start filter "pstopscpca" - Success.
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(-----S)
E [14/Oct/2010:11:55:39 -0400] [Job 60] Stopping job because the scheduler could not execute a filter.
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(----J-)
D [14/Oct/2010:11:55:39 -0400] cupsdMarkDirty(-----S)
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon-iR5075) from localhost
D [14/Oct/2010:11:55:39 -0400] PID 3563 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.
D [14/Oct/2010:11:55:39 -0400] PID 3564 (/usr/lib/cups/filter/pstops) was terminated normally with signal 15.
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 1.1 Get-Jobs 1
D [14/Oct/2010:11:55:39 -0400] Get-Jobs ipp://localhost/printers/
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 WAITING Closing on EOF
D [14/Oct/2010:11:55:39 -0400] cupsdCloseClient: 14
D [14/Oct/2010:11:55:39 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 1.1 Get-Notifications 1
D [14/Oct/2010:11:55:39 -0400] Get-Notifications /
D [14/Oct/2010:11:55:39 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 14 1.1 Get-Job-Attributes 1
D [14/Oct/2010:11:55:39 -0400] Get-Job-Attributes ipp://localhost/jobs/60
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/60) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [14/Oct/2010:11:55:39 -0400] Get-Printer-Attributes ipp://louhi:0/printers/Canon-iR5075
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://louhi:0/printers/Canon-iR5075) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [14/Oct/2010:11:55:39 -0400] Get-Job-Attributes ipp://localhost/jobs/60
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/60) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [14/Oct/2010:11:55:39 -0400] Get-Notifications /
D [14/Oct/2010:11:55:39 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 12 WAITING Closing on EOF
D [14/Oct/2010:11:55:39 -0400] cupsdCloseClient: 12
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [14/Oct/2010:11:55:39 -0400] cupsdCloseClient: 16
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [14/Oct/2010:11:55:39 -0400] Get-Printer-Attributes ipp://louhi:0/printers/Canon-iR5075
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://louhi:0/printers/Canon-iR5075) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:39 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:39 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [14/Oct/2010:11:55:39 -0400] Get-Job-Attributes ipp://localhost/jobs/60
D [14/Oct/2010:11:55:39 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/60) from localhost
D [14/Oct/2010:11:55:39 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:40 -0400] [Job 60] Unloading...
D [14/Oct/2010:11:55:47 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [14/Oct/2010:11:55:47 -0400] cupsdReadClient: 12 POST /jobs/ HTTP/1.1
D [14/Oct/2010:11:55:47 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:47 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:47 -0400] cupsdReadClient: 12 1.1 Cancel-Job 1
D [14/Oct/2010:11:55:47 -0400] Cancel-Job ipp://localhost/jobs/60
D [14/Oct/2010:11:55:47 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:55:47 -0400] [Job 60] Loading attributes...
D [14/Oct/2010:11:55:47 -0400] cupsdMarkDirty(-----S)
I [14/Oct/2010:11:55:47 -0400] [Job 60] Job purged by "haka"
D [14/Oct/2010:11:55:47 -0400] [Job 60] Unloading...
I [14/Oct/2010:11:55:47 -0400] [Job 60] Purged by "haka".
D [14/Oct/2010:11:55:47 -0400] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/60) from localhost
D [14/Oct/2010:11:55:47 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:47 -0400] cupsdReadClient: 12 WAITING Closing on EOF
D [14/Oct/2010:11:55:47 -0400] cupsdCloseClient: 12
D [14/Oct/2010:11:55:48 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [14/Oct/2010:11:55:48 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [14/Oct/2010:11:55:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:55:48 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:55:48 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [14/Oct/2010:11:55:48 -0400] Get-Notifications /
D [14/Oct/2010:11:55:48 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:55:48 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [14/Oct/2010:11:55:48 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:55:48 -0400] cupsdReadClient: 12 WAITING Closing on EOF
D [14/Oct/2010:11:55:48 -0400] cupsdCloseClient: 12
I [14/Oct/2010:11:56:01 -0400] Saving printers.conf...
I [14/Oct/2010:11:56:01 -0400] Generating printcap /var/run/cups/printcap...
I [14/Oct/2010:11:56:01 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [14/Oct/2010:11:56:01 -0400] Saving subscriptions.conf...
D [14/Oct/2010:11:56:01 -0400] cupsdSetBusyState: Not busy
D [14/Oct/2010:11:56:04 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:56:04 -0400] cupsdSetBusyState: Active clients
D [14/Oct/2010:11:56:04 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:56:04 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1
D [14/Oct/2010:11:56:04 -0400] Get-Job-Attributes ipp://localhost/jobs/60
D [14/Oct/2010:11:56:04 -0400] Get-Job-Attributes client-error-not-found: Job #60 does not exist!
D [14/Oct/2010:11:56:04 -0400] Returning IPP client-error-not-found for Get-Job-Attributes (ipp://localhost/jobs/60) from localhost
D [14/Oct/2010:11:56:04 -0400] cupsdSetBusyState: Not busy
D [14/Oct/2010:11:56:05 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Active clients
D [14/Oct/2010:11:56:05 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:56:05 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1
D [14/Oct/2010:11:56:05 -0400] Cancel-Subscription /
D [14/Oct/2010:11:56:05 -0400] cupsdIsAuthorized: requesting-user-name="haka"
D [14/Oct/2010:11:56:05 -0400] cupsdMarkDirty(-----S)
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:56:05 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:56:05 -0400] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:56:05 -0400] cupsdAuthorize: No authentication data provided.
D [14/Oct/2010:11:56:05 -0400] cupsdIsAuthorized: username=""
D [14/Oct/2010:11:56:05 -0400] cupsdSendHeader: 11 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [14/Oct/2010:11:56:05 -0400] cupsdCloseClient: 11
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:56:05 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [14/Oct/2010:11:56:05 -0400] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [14/Oct/2010:11:56:05 -0400] cupsdAuthorize: Authorized as haka using PeerCred
D [14/Oct/2010:11:56:05 -0400] cupsdIsAuthorized: username="haka"
I [14/Oct/2010:11:56:05 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Dirty files
D [14/Oct/2010:11:56:05 -0400] cupsdCloseClient: 14
D [14/Oct/2010:11:56:05 -0400] cupsdCloseClient: 17
D [14/Oct/2010:11:56:05 -0400] cupsdCloseClient: 11
I [14/Oct/2010:11:56:05 -0400] Saving subscriptions.conf...
D [14/Oct/2010:11:56:05 -0400] cupsdSetBusyState: Not busy
E [14/Oct/2010:11:56:05 -0400] Filter "/usr/lib/cups/filter/pstopscpca" for printer "Canon-iR5075" not available: No such file or directory

---

