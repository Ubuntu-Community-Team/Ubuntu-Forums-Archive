---
title: "not printing to XP network printer"
date: 2010-09-06
forum: General Help
---

### Post by KeithBCDN on 2010-09-06
The printer is connected to a networked XP machine that is accessible from Ubuntu.
I have set up the printer as instructed in this help file...
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
SAMBA sees the printer on the network , verifies the printer and the driver loads.
Everything goes along just fine until "print test page" No go.
The printer shows up in the "Printing -local host" window.
Under "printer properties" the "Make and Model"are showing the correct device in the correct location.
The "Printer State" shows "idle - /usr/lib/cups/filter/foomatic-rip failed"
Is there something I might have missed in the set-up?

---

### Post by QLee on 2010-09-06
[QUOTE=KeithBCDN]...
Is there something I might have missed in the set-up?[/QUOTE]

Maybe, but you didn't even tell us what kind of printer it is and there have been various problems with various printer drivers in the past (and probably today too). A forum search with the printer model might bring up something useful or helpful.

I suppose you could also set the loglevel to debug in cupsd.conf and then send a simple text file or something to the printer and examine the log to see if anything helpful is printed.

---

### Post by KeithBCDN on 2010-09-06
Sorry, forgot the printer model.
HP Lasejet 1018.
I did follow the "diagnose" option that was offered when the printer didn't respond and it came back with this error...
"cups/filter/foomatic-rip failed"
Followed the debugging option and there is a HUGE diagnostic file.
> set the loglevel to debug in cupsd.conf What are the specific commands for this action?
I tried this" /etc/cups/cupsd.conf:" and come up with " Permission denied"

Please appreciate that I come to Linux from a Windows environment and I'm not well versed in command line actions.
Mostly point and click ...

I shall search further for printer specific problems but mostly I have found older info relating to the driver which is now included in the 10.04 build.

---

### Post by QLee on 2010-09-06
[QUOTE=KeithBCDN]...
Followed the debugging option and there is a HUGE diagnostic file.
...[/QUOTE]

You won't need to point out your first cupness to me again, I remember from the other thread, so I came here to amend this.

The cupsd.conf I mentioned is in /etc/cups/ 

The error log file I meant is in var/log/cups/ and it should be all about printers, I'm not sure what log you are looking at. I would expect, given that you are inspecting the log immediately after trying to print, that the last entries would be of most interest because log entries are appended to the file.

However, given what you have told me, something like this might be too difficult for an inexperienced user to try and I can't stay around today to make sure you don't make a mistake editing something and make your system worse.

Hopefully, you'll find a thread with an easy to follow step-by-step when you search for your specific printer.

Edit: And, forgive me for not welcoming you to the forums, often people get that on their first post and I was remiss in not noticing that you are new here.

---

### Post by QLee on 2010-09-06
[QUOTE=KeithBCDN]...
 What are the specific commands for this action?
I tried this" /etc/cups/cupsd.conf:" and come up with " Permission denied"
...[/QUOTE]
Yup! You have to edit that file with root (superuser) permissions. In Ubuntu that is done by temporarily elevating your user permissions.


Have a look at 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
it can help you to understand how to edit files that belong to root.

Now I really have to go.

---

### Post by KeithBCDN on 2010-09-06
Thanks QLee.
I'll work away at this for a while and post the results.
"first cupness":lolflag:

---

### Post by KeithBCDN on 2010-09-06
Found this error file using graphical interface to get to /var/log/cups
 This was the latest attempt to print a text document.

I [06/Sep/2010:12:07:05 -0400] Listening to 0.0.0.0:631 (IPv4)
I [06/Sep/2010:12:07:05 -0400] Listening to :::631 (IPv6)
I [06/Sep/2010:12:07:05 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [06/Sep/2010:12:07:05 -0400] Remote access is enabled.
D [06/Sep/2010:12:07:05 -0400] Added auto ServerAlias Penguin
I [06/Sep/2010:12:07:05 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [06/Sep/2010:12:07:05 -0400] Using default TempDir of /var/spool/cups/tmp...
I [06/Sep/2010:12:07:05 -0400] Configured for up to 100 clients.
I [06/Sep/2010:12:07:05 -0400] Allowing up to 100 client connections per host.
I [06/Sep/2010:12:07:05 -0400] Using policy "default" as the default!
D [06/Sep/2010:12:07:05 -0400] load_ppd: Loading /var/cache/cups/HP.ipp...
D [06/Sep/2010:12:07:05 -0400] cupsdRegisterPrinter(p=0x21d082e0(HP))
D [06/Sep/2010:12:07:05 -0400] load_ppd: Loading /var/cache/cups/PDF.ipp...
D [06/Sep/2010:12:07:05 -0400] cupsdRegisterPrinter(p=0x21cbc888(PDF))
D [06/Sep/2010:12:07:05 -0400] cupsdMarkDirty(---p--)
D [06/Sep/2010:12:07:05 -0400] cupsdSetBusyState: Dirty files
I [06/Sep/2010:12:07:05 -0400] Partial reload complete.
I [06/Sep/2010:12:07:05 -0400] Listening to 0.0.0.0:631 on fd 5...
I [06/Sep/2010:12:07:05 -0400] Listening to :::631 on fd 7...
I [06/Sep/2010:12:07:05 -0400] Listening to /var/run/cups/cups.sock on fd 8...
I [06/Sep/2010:12:07:05 -0400] Resuming new connection processing...
D [06/Sep/2010:12:07:05 -0400] cupsdRegisterPrinter(p=0x21d082e0(HP))
D [06/Sep/2010:12:07:05 -0400] cupsdRegisterPrinter(p=0x21cbc888(PDF))
D [06/Sep/2010:12:07:05 -0400] Discarding unused server-restarted event...
D [06/Sep/2010:12:07:06 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [06/Sep/2010:12:07:06 -0400] Report: clients=1
D [06/Sep/2010:12:07:06 -0400] Report: jobs=16
D [06/Sep/2010:12:07:06 -0400] Report: jobs-active=1
D [06/Sep/2010:12:07:06 -0400] Report: printers=2
D [06/Sep/2010:12:07:06 -0400] Report: printers-implicit=0
D [06/Sep/2010:12:07:06 -0400] Report: stringpool-string-count=1414
D [06/Sep/2010:12:07:06 -0400] Report: stringpool-alloc-bytes=10432
D [06/Sep/2010:12:07:06 -0400] Report: stringpool-total-bytes=29312
D [06/Sep/2010:12:07:08 -0400] cupsdReadClient: 12 GET /admin/log/error_log HTTP/1.1
D [06/Sep/2010:12:07:08 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:08 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:08 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:08 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:08 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:08 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:08 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:08 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:08 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:08 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:08 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:08 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:08 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:08 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:08 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:08 -0400] [Job 12] Loading attributes...
D [06/Sep/2010:12:07:09 -0400] [Job 13] Loading attributes...
D [06/Sep/2010:12:07:09 -0400] [Job 14] Loading attributes...
D [06/Sep/2010:12:07:09 -0400] [Job 15] Loading attributes...
D [06/Sep/2010:12:07:09 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:09 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:09 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:09 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:09 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:09 -0400] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [06/Sep/2010:12:07:09 -0400] Create-Printer-Subscription /
D [06/Sep/2010:12:07:09 -0400] cupsdCreateSubscription(con=0x21cc7ce8(12), uri="/")
D [06/Sep/2010:12:07:09 -0400] pullmethod="ippget"
D [06/Sep/2010:12:07:09 -0400] notify-lease-duration=86400
D [06/Sep/2010:12:07:09 -0400] notify-time-interval=0
D [06/Sep/2010:12:07:09 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [06/Sep/2010:12:07:09 -0400] Added subscription 34 for server
D [06/Sep/2010:12:07:09 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:09 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [06/Sep/2010:12:07:09 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:10 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:10 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:10 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:10 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:10 -0400] Get-Notifications /
D [06/Sep/2010:12:07:10 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:10 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:10 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:16 -0400] [Job 16] Unloading...
D [06/Sep/2010:12:07:28 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 15 POST /printers/HP HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 15 1.1 Print-Job 1
D [06/Sep/2010:12:07:28 -0400] Print-Job ipp://localhost/printers/HP
D [06/Sep/2010:12:07:28 -0400] [Job ???] Auto-typing file...
I [06/Sep/2010:12:07:28 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(----J-)
D [06/Sep/2010:12:07:28 -0400] add_job: requesting-user-name="admin"
D [06/Sep/2010:12:07:28 -0400] Adding default job-sheets values "none,none"...
I [06/Sep/2010:12:07:28 -0400] [Job 17] Adding start banner page "none".
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(----J-)
I [06/Sep/2010:12:07:28 -0400] [Job 17] Adding end banner page "none".
I [06/Sep/2010:12:07:28 -0400] [Job 17] File of type application/vnd.cups-banner queued by "admin".
D [06/Sep/2010:12:07:28 -0400] [Job 17] hold_until=0
I [06/Sep/2010:12:07:28 -0400] [Job 17] Queued on "HP" by "admin".
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(----J-)
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:28 -0400] [Job 17] job-sheets=none,none
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[0]="HP"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[1]="17"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[2]="admin"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[3]="Test Page"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[4]="1"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[5]="job-uuid=urn:uuid:bf41c2d8-a235-3ac2-7054-426ed400fc48 job-originating-host-name=localhost"
D [06/Sep/2010:12:07:28 -0400] [Job 17] argv[6]="/var/spool/cups/d00017-001"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[10]="SERVER_ADMIN=root@Penguin"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[11]="SOFTWARE=CUPS/1.4.3"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[13]="TZ=America/Toronto"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[14]="USER=root"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[17]="IPP_PORT=631"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[18]="CHARSET=utf-8"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[19]="LANG=en_CA.UTF-8"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[20]="PPD=/etc/cups/ppd/HP.ppd"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[21]="RIP_MAX_CACHE=119153k"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[23]="DEVICE_URI=smb://JOOLZ/KATITUDE/HPLaserJ"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[24]="PRINTER_INFO=HP LaserJet 1018"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[25]="PRINTER_LOCATION="
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[26]="PRINTER=HP"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[27]="CUPS_FILETYPE=document"
D [06/Sep/2010:12:07:28 -0400] [Job 17] envp[28]="FINAL_CONTENT_TYPE=printer/HP"
I [06/Sep/2010:12:07:28 -0400] [Job 17] Started filter /usr/lib/cups/filter/bannertops (PID 6262)
I [06/Sep/2010:12:07:28 -0400] [Job 17] Started filter /usr/lib/cups/filter/pstopdf (PID 6263)
I [06/Sep/2010:12:07:28 -0400] [Job 17] Started filter /usr/lib/cups/filter/pdftopdf (PID 6264)
I [06/Sep/2010:12:07:28 -0400] [Job 17] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6265)
I [06/Sep/2010:12:07:28 -0400] [Job 17] Started backend /usr/lib/cups/backend/smb (PID 6266)
D [06/Sep/2010:12:07:28 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [06/Sep/2010:12:07:28 -0400] [Job 17] Getting input from file 
D [06/Sep/2010:12:07:28 -0400] [Job 17] foomatic-rip version 4.0.4.217 running...
D [06/Sep/2010:12:07:28 -0400] [Job 17] Parsing PPD file ...
D [06/Sep/2010:12:07:28 -0400] [Job 17] load_banner(filename="/var/spool/cups/d00017-001")
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option Resolution
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option PageSize
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option Model
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option PrintoutMode
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option MediaType
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option InputSlot
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option Quality
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option ImageableArea
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option PaperDimension
D [06/Sep/2010:12:07:28 -0400] [Job 17] Added option Font
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] Parameter Summary
D [06/Sep/2010:12:07:28 -0400] [Job 17] -----------------
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] Spooler: cups
D [06/Sep/2010:12:07:28 -0400] [Job 17] Printer: HP
D [06/Sep/2010:12:07:28 -0400] [Job 17] Shell: /bin/bash
D [06/Sep/2010:12:07:28 -0400] [Job 17] PPD file: /etc/cups/ppd/HP.ppd
D [06/Sep/2010:12:07:28 -0400] [Job 17] ATTR file: 
D [06/Sep/2010:12:07:28 -0400] [Job 17] Printer model: HP LaserJet 1018 hpijs, 3.10.2, requires proprietary plugin
D [06/Sep/2010:12:07:28 -0400] [Job 17] Job title: Test Page
D [06/Sep/2010:12:07:28 -0400] [Job 17] File(s) to be printed:
D [06/Sep/2010:12:07:28 -0400] [Job 17] <STDIN>
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [06/Sep/2010:12:07:28 -0400] [Job 17] Printing system options:
D [06/Sep/2010:12:07:28 -0400] [Job 17] Pondering option 'job-uuid=urn:uuid:bf41c2d8-a235-3ac2-7054-426ed400fc48'
D [06/Sep/2010:12:07:28 -0400] [Job 17] Unknown option job-uuid=urn:uuid:bf41c2d8-a235-3ac2-7054-426ed400fc48.
D [06/Sep/2010:12:07:28 -0400] [Job 17] Pondering option 'job-originating-host-name=localhost'
D [06/Sep/2010:12:07:28 -0400] [Job 17] Unknown option job-originating-host-name=localhost.
D [06/Sep/2010:12:07:28 -0400] [Job 17] Options from the PPD file:
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] ================================================
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] File: <STDIN>
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] ================================================
D [06/Sep/2010:12:07:28 -0400] [Job 17] 
D [06/Sep/2010:12:07:28 -0400] [Job 17] pstopdf 5 args: 17 admin Test Page 1 job-uuid=urn:uuid:bf41c2d8-a235-3ac2-7054-426ed400fc48 job-originating-host-name=localhost
D [06/Sep/2010:12:07:28 -0400] [Job 17] PPD: /etc/cups/ppd/HP.ppd
D [06/Sep/2010:12:07:28 -0400] [Job 17] Page = 612x792; 18,14 to 594,778
D [06/Sep/2010:12:07:28 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:28 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:28 -0400] [Job 16] Loading attributes...
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Sep/2010:12:07:28 -0400] cupsdCloseClient: 17
D [06/Sep/2010:12:07:28 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:28 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:28 -0400] Get-Notifications /
D [06/Sep/2010:12:07:28 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [06/Sep/2010:12:07:28 -0400] cupsdCloseClient: 18
D [06/Sep/2010:12:07:28 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] [Job 17] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [06/Sep/2010:12:07:28 -0400] [Job 17] PNG image: 192x128x8, color_type=2 (RGB)
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:28 -0400] Get-Notifications /
D [06/Sep/2010:12:07:28 -0400] cupsdIsAuthorized: requesting-user-name="keith"
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [06/Sep/2010:12:07:28 -0400] Get-Job-Attributes ipp://localhost/jobs/17
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/17) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [06/Sep/2010:12:07:28 -0400] Get-Job-Attributes ipp://localhost/jobs/17
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/17) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [06/Sep/2010:12:07:28 -0400] Get-Job-Attributes ipp://localhost/jobs/17
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/17) from localhost
D [06/Sep/2010:12:07:28 -0400] PID 6262 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:28 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:28 -0400] Get-Notifications /
D [06/Sep/2010:12:07:28 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:28 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [06/Sep/2010:12:07:28 -0400] cupsdCloseClient: 18
D [06/Sep/2010:12:07:28 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [06/Sep/2010:12:07:28 -0400] [Job 17] Resolution: 600
D [06/Sep/2010:12:07:28 -0400] [Job 17] Page size: Letter
D [06/Sep/2010:12:07:28 -0400] [Job 17] Connected using Kerberos...
D [06/Sep/2010:12:07:28 -0400] [Job 17] Width: 612, height: 792, absolute margins: 18, 14.39999961853, 594, 777.60000038147
D [06/Sep/2010:12:07:28 -0400] [Job 17] Relative margins: 18, 14.39999961853, 18, 14.39999961853
D [06/Sep/2010:12:07:28 -0400] [Job 17] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [06/Sep/2010:12:07:28 -0400] [Job 17] PostScript to be injected: 
D [06/Sep/2010:12:07:28 -0400] [Job 17] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [06/Sep/2010:12:07:28 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Sep/2010:12:07:28 -0400] cupsdCloseClient: 17
D [06/Sep/2010:12:07:30 -0400] PID 6263 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [06/Sep/2010:12:07:30 -0400] [Job 17] Filetype: PDF
D [06/Sep/2010:12:07:30 -0400] [Job 17] Storing temporary files in /var/spool/cups/tmp
D [06/Sep/2010:12:07:30 -0400] PID 6264 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [06/Sep/2010:12:07:30 -0400] [Job 17] File contains 1 pages
D [06/Sep/2010:12:07:30 -0400] [Job 17] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet 1018" -r600 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-phKEdg 
D [06/Sep/2010:12:07:30 -0400] [Job 17] Starting process "kid3" (generation 1)
D [06/Sep/2010:12:07:30 -0400] [Job 17] Starting process "kid4" (generation 2)
D [06/Sep/2010:12:07:30 -0400] [Job 17] Starting process "renderer" (generation 2)
D [06/Sep/2010:12:07:30 -0400] [Job 17] JCL: %-12345X@PJL
D [06/Sep/2010:12:07:30 -0400] [Job 17] <job data> 
D [06/Sep/2010:12:07:30 -0400] [Job 17] 
D [06/Sep/2010:12:07:30 -0400] [Job 17] prnt/hpijs/hpijs.cpp 268: unable to set device=HP LaserJet 1018, err=48
D [06/Sep/2010:12:07:30 -0400] [Job 17] prnt/hpijs/hpijs.cpp 289: unable to set device=HP LaserJet 1018, err=48
D [06/Sep/2010:12:07:30 -0400] [Job 17] prnt/hpijs/hpijs.cpp 694: unable to read client data err=-2
D [06/Sep/2010:12:07:30 -0400] [Job 17] renderer exited with status 1
D [06/Sep/2010:12:07:30 -0400] [Job 17] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [06/Sep/2010:12:07:30 -0400] PID 6265 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [06/Sep/2010:12:07:30 -0400] PID 6266 (/usr/lib/cups/backend/smb) exited with no errors.
D [06/Sep/2010:12:07:30 -0400] cupsdMarkDirty(-----S)
E [06/Sep/2010:12:07:30 -0400] [Job 17] Job stopped due to filter errors; please consult the error_log file for details.
D [06/Sep/2010:12:07:30 -0400] cupsdMarkDirty(----J-)
D [06/Sep/2010:12:07:30 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:30 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Sep/2010:12:07:30 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 16 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:30 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 1.1 Get-Jobs 1
D [06/Sep/2010:12:07:30 -0400] Get-Jobs ipp://localhost/printers/
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Sep/2010:12:07:30 -0400] cupsdCloseClient: 17
D [06/Sep/2010:12:07:30 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [06/Sep/2010:12:07:30 -0400] cupsdCloseClient: 16
D [06/Sep/2010:12:07:30 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:30 -0400] Get-Notifications /
D [06/Sep/2010:12:07:30 -0400] cupsdIsAuthorized: requesting-user-name="keith"
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:30 -0400] Get-Notifications /
D [06/Sep/2010:12:07:30 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Sep/2010:12:07:30 -0400] cupsdCloseClient: 17
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Sep/2010:12:07:30 -0400] cupsdCloseClient: 15
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [06/Sep/2010:12:07:30 -0400] Get-Printer-Attributes ipp://Penguin:631/printers/HP
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Penguin:631/printers/HP) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [06/Sep/2010:12:07:30 -0400] Get-Job-Attributes ipp://localhost/jobs/17
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/17) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:30 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:30 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Sep/2010:12:07:30 -0400] Get-Notifications /
D [06/Sep/2010:12:07:30 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Sep/2010:12:07:30 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:31 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [06/Sep/2010:12:07:31 -0400] cupsdCloseClient: 16
D [06/Sep/2010:12:07:31 -0400] [Job 17] Unloading...
I [06/Sep/2010:12:07:36 -0400] Generating printcap /var/run/cups/printcap...
I [06/Sep/2010:12:07:36 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [06/Sep/2010:12:07:36 -0400] Saving subscriptions.conf...
D [06/Sep/2010:12:07:36 -0400] cupsdSetBusyState: Not busy
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients
D [06/Sep/2010:12:07:38 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [06/Sep/2010:12:07:38 -0400] Get-Job-Attributes ipp://localhost/jobs/17
D [06/Sep/2010:12:07:38 -0400] [Job 17] Loading attributes...
D [06/Sep/2010:12:07:38 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/17) from localhost
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Not busy
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients
D [06/Sep/2010:12:07:38 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [06/Sep/2010:12:07:38 -0400] Cancel-Subscription /
D [06/Sep/2010:12:07:38 -0400] cupsdIsAuthorized: requesting-user-name="admin"
D [06/Sep/2010:12:07:38 -0400] cupsdMarkDirty(-----S)
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:38 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdAuthorize: No authentication data provided.
D [06/Sep/2010:12:07:38 -0400] cupsdIsAuthorized: username=""
D [06/Sep/2010:12:07:38 -0400] cupsdSendHeader: 15 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [06/Sep/2010:12:07:38 -0400] cupsdCloseClient: 15
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Sep/2010:12:07:38 -0400] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdAuthorize: Authorized as admin using PeerCred
D [06/Sep/2010:12:07:38 -0400] cupsdIsAuthorized: username="admin"
I [06/Sep/2010:12:07:38 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Dirty files
D [06/Sep/2010:12:07:38 -0400] cupsdCloseClient: 12
D [06/Sep/2010:12:07:38 -0400] cupsdCloseClient: 17
D [06/Sep/2010:12:07:38 -0400] cupsdCloseClient: 15
D [06/Sep/2010:12:07:38 -0400] cupsdDeregisterPrinter(p=0x21d082e0(HP), removeit=1)
D [06/Sep/2010:12:07:38 -0400] cupsdDeregisterPrinter(p=0x21cbc888(PDF), removeit=1)
I [06/Sep/2010:12:07:38 -0400] Saving subscriptions.conf...
D [06/Sep/2010:12:07:38 -0400] cupsdSetBusyState: Not busy
I [06/Sep/2010:12:07:38 -0400] cupsdDefaultRIPCacheSize: 119153k

---

### Post by QLee on 2010-09-07
I looked at some threads before logging on. Have you seen this one yet?
[http://newyork.ubuntuforums.org/showpost.php?p=9432204&postcount=3](http://newyork.ubuntuforums.org/showpost.php?p=9432204&postcount=3) I'm not sure what to think about that solution, but I wouldn't do it as a first choice.

I hate to even suggest this but several of the threads I looked at had some success after purging CUPS (purge to get rid of the configuration files too) and installing again. I usually prefer to fix rather than re-install but I don't have a better idea and it would ensure that everything was new and even if you made some mistake it would then be gone. Of course, you may have already tried that, and I don't mean that I think you made a mistake. I don't know much about CUPS, have had good luck with printers, that's why I'd probably try what was suggested by several of those threads, it might be a waste of time.

Instructions for above would be something like this. From the command line in a terminal, sudo apt-get purge cups or in Synaptic Package Manager select(highlight) the package cups and push Shift + Delete, mark the changes and then click apply.

Then install again and set up the printer again.
sudo apt-get install cups or in Synaptic Package Manager select(highlight) the package cups and push Ctrl + i, mark the changes and then click apply.

I hope that helps, at least I hope I explained it well enough for you as an inexperienced user to follow. I'm confident I did, you seem to be picking this up quickly.

Note: Next time you want to post a long document, encase it in "tags"```
 your text here 
```, it makes the thread easier to read on the forum. But usually only the last 10 or so lines are necessary from an error log.

---

### Post by KeithBCDN on 2010-09-07
Couple of options to work at.
I'm leaning to the clean and re-install idea. I'll post the results.
Thanks QLee

---

### Post by KeithBCDN on 2010-09-12
I have completed the following..
"sudo apt-get purge cups" 
"sudo apt-get install cups"
Followed the usual "add printer" via SAMBA in the GUI
"print test page" is now "job 1" and it still comes up as
" /usr/lib/cups/filter/foomatic-rip failed"

---

### Post by QLee on 2010-09-13
[QUOTE=KeithBCDN]I have completed the following..
"sudo apt-get purge cups" 
"sudo apt-get install cups"
Followed the usual "add printer" via SAMBA in the GUI
"print test page" is now "job 1" and it still comes up as
" /usr/lib/cups/filter/foomatic-rip failed"[/QUOTE]

Well Keith, I've looked back over the old forum posts and it seems this specific printer has always presented problems in Ubuntu. Not exactly a "win printer" but a ZjStream protocol printer and all the solutions I've found seem to be using a driver other than one available to Ubuntu, however, all these reports seem old and you've probably already seen them in your quest.If it was my printer, at this point, I would try that driver from the HP site. As I mentioned, I don't know much about CUPS, maybe a visit to the openprinting.org page for that specific printer might be helpful. 
[http://www.openprinting.org/printer/HP/HP-LaserJet_1018](http://www.openprinting.org/printer/HP/HP-LaserJet_1018)

Other than that, I'm out of ideas about your printer.

---

### Post by KeithBCDN on 2010-09-13
Thanks QLee. I do appreciate the time you took to help.
I'll figure something out.

---

### Post by QLee on 2010-09-14
> **KeithBCDN said:**
> Thanks QLee. I do appreciate the time you took to help.
I'll figure something out.
I'm sorry I wasn't able to find the answer for your problem.

It occurred to me that, if the driver from the HP site doesn't correct the problem, you might consider asking a mod to move this thread to the Networking and Wireless sub forum. There is going to be a lot of wireless stuff over there but there might also be a CUPS expert monitoring. Or you could just close this thread and open one over in that sub forum.

---

### Post by KeithBCDN on 2010-09-20
Problem solved!
Did a complete re-install of Ubuntu 10.04.
Changed Ubuntu server from WORKGROUP to the name of the new Windows network I had created
Installed printer through SAMBA all works well.

---

