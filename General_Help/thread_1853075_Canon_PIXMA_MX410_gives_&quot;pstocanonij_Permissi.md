---
title: "Canon PIXMA MX410 gives &quot;pstocanonij: Permission Denied&quot; error in log"
date: 2011-10-01
forum: General Help
---

### Post by purpleyuan on 2011-10-01
I recently bought a Canon PIXMA MX410 All-in-one printer. I was able to download the driver via the Canon site; however, after I installed it, it gave errors.

The Printer State is stated as: "Idle - No %%BoundingBox: comment in header"

After attempting to diagnose the issue via the printer troubleshooter, this was in the error log:

```
E [01/Oct/2011:13:35:48 -0500] [Job 16] No %%BoundingBox: comment in header!
E [01/Oct/2011:13:35:48 -0500] [Job 16] Job stopped due to filter errors; please consult the error_log file for details.
D [01/Oct/2011:13:35:48 -0500] [Job 16] The following messages were recorded from 13:35:48 to 13:35:48
D [01/Oct/2011:13:35:48 -0500] [Job 16] Job restarted by user.
D [01/Oct/2011:13:35:48 -0500] [Job 16] job-sheets=none,none
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[0]="Canon-MX410-series"
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[1]="16"
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[2]="yuan"
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[3]="Test Page"
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[4]="1"
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[5]="PageSize=Letter job-uuid=urn:uuid:482da55d-154e-3cdf-55af-4f8d3a49cf93 job-originating-host-name=localhost time-at-creation=1317494089 time-at-processing=1317494148 AP_D_InputSlot="
D [01/Oct/2011:13:35:48 -0500] [Job 16] argv[6]="/var/spool/cups/d00016-001"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[8]="HOME=/var/spool/cups/tmp"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[10]="SERVER_ADMIN=root@Doyle-AC"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[11]="SOFTWARE=CUPS/1.4.6"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[13]="USER=root"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[16]="CHARSET=utf-8"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[17]="LANG=en_US.UTF-8"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[18]="PPD=/etc/cups/ppd/Canon-MX410-series.ppd"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[19]="RIP_MAX_CACHE=auto"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[20]="CONTENT_TYPE=application/postscript"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[21]="DEVICE_URI=usb://Canon/MX410%20series"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[22]="PRINTER_INFO=Canon MX410 series"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[23]="PRINTER_LOCATION=Doyle-AC"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[24]="PRINTER=Canon-MX410-series"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[25]="CUPS_FILETYPE=document"
D [01/Oct/2011:13:35:48 -0500] [Job 16] envp[26]="FINAL_CONTENT_TYPE=printer/Canon-MX410-series"
D [01/Oct/2011:13:35:48 -0500] [Job 16] Started filter /usr/lib/cups/filter/pstops (PID 6229)
D [01/Oct/2011:13:35:48 -0500] [Job 16] Started filter /usr/lib/cups/filter/pstocanonij (PID 6230)
D [01/Oct/2011:13:35:48 -0500] [Job 16] Started backend /usr/lib/cups/backend/usb (PID 6231)
D [01/Oct/2011:13:35:48 -0500] [Job 16] Restarted by "yuan".
D [01/Oct/2011:13:35:48 -0500] [Job 16] /usr/lib/cups/filter/pstocanonij: Permission denied
D [01/Oct/2011:13:35:48 -0500] [Job 16] Page = 612x792; 18,14 to 594,784
D [01/Oct/2011:13:35:48 -0500] [Job 16] slow_collate=0, slow_duplex=0, slow_order=0
D [01/Oct/2011:13:35:48 -0500] [Job 16] Before copy_comments - %!PS-Adobe-3.0
D [01/Oct/2011:13:35:48 -0500] [Job 16] %!PS-Adobe-3.0
D [01/Oct/2011:13:35:48 -0500] [Job 16] %%Title: PPR Test Page
D [01/Oct/2011:13:35:48 -0500] [Job 16] %%Pages: 1
D [01/Oct/2011:13:35:48 -0500] [Job 16] %%DocumentNeededResources: font Helvetica
D [01/Oct/2011:13:35:48 -0500] [Job 16] %%EndComments
D [01/Oct/2011:13:35:48 -0500] [Job 16] Set job-printer-state-message to "No %%BoundingBox: comment in header!", current level=ERROR
D [01/Oct/2011:13:35:48 -0500] [Job 16] STATE: +connecting-to-device
D [01/Oct/2011:13:35:48 -0500] [Job 16] Before copy_prolog - %%BeginProlog
D [01/Oct/2011:13:35:48 -0500] [Job 16] Before copy_setup - %%BeginSetup
D [01/Oct/2011:13:35:48 -0500] [Job 16] Before page loop - %%Page: 1 1
D [01/Oct/2011:13:35:48 -0500] [Job 16] Copying page 1...
D [01/Oct/2011:13:35:48 -0500] [Job 16] pagew = 576.0, pagel = 769.3
D [01/Oct/2011:13:35:48 -0500] [Job 16] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [01/Oct/2011:13:35:48 -0500] [Job 16] PageLeft = 18.1, PageRight = 594.1
D [01/Oct/2011:13:35:48 -0500] [Job 16] PageTop = 783.5, PageBottom = 14.2
D [01/Oct/2011:13:35:48 -0500] [Job 16] PageWidth = 612.0, PageLength = 792.0
D [01/Oct/2011:13:35:48 -0500] [Job 16] Printer using device file "/dev/usblp0"...
D [01/Oct/2011:13:35:48 -0500] [Job 16] STATE: -connecting-to-device
D [01/Oct/2011:13:35:48 -0500] [Job 16] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x7f504a6dfe10)
D [01/Oct/2011:13:35:48 -0500] [Job 16] End of messages
D [01/Oct/2011:13:35:48 -0500] [Job 16] printer-state=3(idle)
D [01/Oct/2011:13:35:48 -0500] [Job 16] printer-state-message="No %%BoundingBox: comment in header!"
D [01/Oct/2011:13:35:48 -0500] [Job 16] printer-state-reasons=none
W [01/Oct/2011:13:35:56 -0500] Duplicate listen address "/var/run/cups/cups.sock" ignored!
```As far as I can see, the issue is usually solve by changing the permissions of my pstocanonij file. However, whenever I do, it gives off a different error (cups-unstable, or something like that). All my files are accessable by root. 

Does anyone have any idea how to make this work? I'd really like not having to return this printer. Thanks!

---

