---
title: "Help - Printers refuse to print some files"
date: 2011-09-14
forum: General Help
---

### Post by Bob Morane on 2011-09-14
Hello, i have a rather strange and very annoying issue here. My printers (an HP laserjet and an all-in one HP photosmart) both refuse to print some files. It seems like the cups is rejecting those files.

It will seemingly randomly reject printing at some point during the file edition (openoffice documents). From there, it will always refuse to print that particular file and the only way to be able to print it is copying the text unformatted, then add the formatting and images back. For some files it will work and the finished file can be printed, while others will stop being printable at some point (not always the same) during the application of the text styles.

I don't get any error code, just a message telling me there was an error, however i gathered what i could from the cups web interface and log. The web interface lists the job as :
```
stopped
"/usr/lib/cups/pstopdf failed"
```
Not sure why this pstopdf was called. I didn't try to export as pdf, just to print the file.
The cups error_log received those lines when i tried to print after tailing it :
```
E [14/Sep/2011:16:45:16 +0200] [Job 877] Job stopped due to filter errors; please consult the error_log file for details.
D [14/Sep/2011:16:45:16 +0200] [Job 877] The following messages were recorded from 16:45:04 to 16:45:15
D [14/Sep/2011:16:45:16 +0200] [Job 877] Adding start banner page "none".
D [14/Sep/2011:16:45:16 +0200] [Job 877] Queued on "HP_LaserJet" by "roseline".
D [14/Sep/2011:16:45:16 +0200] [Job 877] Auto-typing file...
D [14/Sep/2011:16:45:16 +0200] [Job 877] Request file type is application/postscript.
D [14/Sep/2011:16:45:16 +0200] [Job 877] File of type application/postscript queued by "roseline".
D [14/Sep/2011:16:45:16 +0200] [Job 877] Adding end banner page "none".
D [14/Sep/2011:16:45:16 +0200] [Job 877] job-sheets=none,none
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[0]="HP_LaserJet"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[1]="877"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[2]="roseline"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[3]="Sans nom3"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[4]="1"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[5]="InputSlot=Upper PageSize=A4 PrintoutMode=Normal.Gray job-uuid=urn:uuid:4a6ce8db-899d-3215-5113-91611cbb2ef0 job-originating-host-name=localhost"
D [14/Sep/2011:16:45:16 +0200] [Job 877] argv[6]="/var/spool/cups/d00877-001"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[10]="SERVER_ADMIN=root@Pinny"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[11]="SOFTWARE=CUPS/1.4.3"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[13]="TZ=Europe/Brussels"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[14]="USER=root"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[17]="IPP_PORT=631"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[18]="CHARSET=utf-8"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[19]="LANG=fr_BE.UTF-8"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[20]="PPD=/etc/cups/ppd/HP_LaserJet.ppd"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[21]="RIP_MAX_CACHE=515434k"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[22]="CONTENT_TYPE=application/postscript"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[23]="DEVICE_URI=hp:/net/HP_Color_LaserJet_CP2025n?zc=NPI872578"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[24]="PRINTER_INFO=HP_LaserJet"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[25]="PRINTER_LOCATION="
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[26]="PRINTER=HP_LaserJet"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[27]="CUPS_FILETYPE=document"
D [14/Sep/2011:16:45:16 +0200] [Job 877] envp[28]="FINAL_CONTENT_TYPE=printer/HP_LaserJet"
D [14/Sep/2011:16:45:16 +0200] [Job 877] Started filter /usr/lib/cups/filter/pstopdf (PID 4277)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Started filter /usr/lib/cups/filter/pdftopdf (PID 4278)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4279)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Started backend /usr/lib/cups/backend/hp (PID 4280)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Getting input from file 
D [14/Sep/2011:16:45:16 +0200] [Job 877] foomatic-rip version 4.0.4.217 running...
D [14/Sep/2011:16:45:16 +0200] [Job 877] Parsing PPD file ...
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option Resolution
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option PageSize
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option Model
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option PrintoutMode
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option InputSlot
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option Duplex
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option Quality
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option ImageableArea
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option PaperDimension
D [14/Sep/2011:16:45:16 +0200] [Job 877] Added option Font
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Parameter Summary
D [14/Sep/2011:16:45:16 +0200] [Job 877] -----------------
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Spooler: cups
D [14/Sep/2011:16:45:16 +0200] [Job 877] Printer: HP_LaserJet
D [14/Sep/2011:16:45:16 +0200] [Job 877] Shell: /bin/bash
D [14/Sep/2011:16:45:16 +0200] [Job 877] PPD file: /etc/cups/ppd/HP_LaserJet.ppd
D [14/Sep/2011:16:45:16 +0200] [Job 877] ATTR file: 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Printer model: HP Color LaserJet cp2025n hpijs pcl3, 3.10.2
D [14/Sep/2011:16:45:16 +0200] [Job 877] Job title: Sans nom3
D [14/Sep/2011:16:45:16 +0200] [Job 877] File(s) to be printed:
D [14/Sep/2011:16:45:16 +0200] [Job 877] <STDIN>
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [14/Sep/2011:16:45:16 +0200] [Job 877] Printing system options:
D [14/Sep/2011:16:45:16 +0200] [Job 877] Pondering option 'job-uuid=urn:uuid:4a6ce8db-899d-3215-5113-91611cbb2ef0'
D [14/Sep/2011:16:45:16 +0200] [Job 877] Unknown option job-uuid=urn:uuid:4a6ce8db-899d-3215-5113-91611cbb2ef0.
D [14/Sep/2011:16:45:16 +0200] [Job 877] Pondering option 'job-originating-host-name=localhost'
D [14/Sep/2011:16:45:16 +0200] [Job 877] Unknown option job-originating-host-name=localhost.
D [14/Sep/2011:16:45:16 +0200] [Job 877] Options from the PPD file:
D [14/Sep/2011:16:45:16 +0200] [Job 877] Pondering option 'InputSlot=Upper'
D [14/Sep/2011:16:45:16 +0200] [Job 877] Pondering option 'PageSize=A4'
D [14/Sep/2011:16:45:16 +0200] [Job 877] Pondering option 'PrintoutMode=Normal.Gray'
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] ================================================
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] File: <STDIN>
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] ================================================
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] pstopdf 6 args: 877 roseline Sans nom3 1 InputSlot=Upper PageSize=A4 PrintoutMode=Normal.Gray job-uuid=urn:uuid:4a6ce8db-899d-3215-5113-91611cbb2ef0 job-originating-host-name=localhost /var/spool/cups/d00877-001
D [14/Sep/2011:16:45:16 +0200] [Job 877] PPD: /etc/cups/ppd/HP_LaserJet.ppd
D [14/Sep/2011:16:45:16 +0200] [Job 877] Resolution: 600
D [14/Sep/2011:16:45:16 +0200] [Job 877] Page size: A4
D [14/Sep/2011:16:45:16 +0200] [Job 877] Width: 595, height: 842, absolute margins: 18, 14.39999961853, 577, 827.60000038147
D [14/Sep/2011:16:45:16 +0200] [Job 877] Relative margins: 18, 14.39999961853, 18, 14.39999961853
D [14/Sep/2011:16:45:16 +0200] [Job 877] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [14/Sep/2011:16:45:16 +0200] [Job 877] PostScript to be injected: 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
D [14/Sep/2011:16:45:16 +0200] [Job 877] Error: /undefined in --eexec--
D [14/Sep/2011:16:45:16 +0200] [Job 877] Operand stack:
D [14/Sep/2011:16:45:16 +0200] [Job 877] --dict:8/11(L)--   --dict:8/11(L)--   Private   --dict:9/18(L)--   BlueScale
D [14/Sep/2011:16:45:16 +0200] [Job 877] Execution stack:
D [14/Sep/2011:16:45:16 +0200] [Job 877] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1878   1   3   %oparray_pop   1877   1   3   %oparray_pop   1861   1   3   %oparray_pop   1755   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   1746   2   3   %oparray_pop   --nostringval--   --nostringval--
D [14/Sep/2011:16:45:16 +0200] [Job 877] Dictionary stack:
D [14/Sep/2011:16:45:16 +0200] [Job 877] --dict:1165/1684(ro)(G)--   --dict:0/20(G)--   --dict:82/200(L)--   --dict:1165/1684(ro)(G)--   --dict:9/18(L)--
D [14/Sep/2011:16:45:16 +0200] [Job 877] Current allocation mode is local
D [14/Sep/2011:16:45:16 +0200] [Job 877] GPL Ghostscript 8.71: Unrecoverable error, exit code 1
D [14/Sep/2011:16:45:16 +0200] [Job 877] Filetype: PDF
D [14/Sep/2011:16:45:16 +0200] [Job 877] Storing temporary files in /var/spool/cups/tmp
D [14/Sep/2011:16:45:16 +0200] [Job 877] File contains 1 pages
D [14/Sep/2011:16:45:16 +0200] [Job 877] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="hp color LaserJet" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=1 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-bscLTu 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Starting process "kid3" (generation 1)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Starting process "kid4" (generation 2)
D [14/Sep/2011:16:45:16 +0200] [Job 877] Starting process "renderer" (generation 2)
D [14/Sep/2011:16:45:16 +0200] [Job 877] JCL: %-12345X@PJL
D [14/Sep/2011:16:45:16 +0200] [Job 877] <job data> 
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] renderer exited with status 0
D [14/Sep/2011:16:45:16 +0200] [Job 877] STATE: +connecting-to-device
D [14/Sep/2011:16:45:16 +0200] [Job 877] kid4 exited with status 0
D [14/Sep/2011:16:45:16 +0200] [Job 877] kid3 finished
D [14/Sep/2011:16:45:16 +0200] [Job 877] Kid3 exit status: 0
D [14/Sep/2011:16:45:16 +0200] [Job 877] 
D [14/Sep/2011:16:45:16 +0200] [Job 877] Closing foomatic-rip.
D [14/Sep/2011:16:45:16 +0200] [Job 877] STATE: -connecting-to-device
D [14/Sep/2011:16:45:16 +0200] [Job 877] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [14/Sep/2011:16:45:16 +0200] [Job 877] ready to print
D [14/Sep/2011:16:45:16 +0200] [Job 877] End of messages
D [14/Sep/2011:16:45:16 +0200] [Job 877] printer-state=3(idle)
D [14/Sep/2011:16:45:16 +0200] [Job 877] printer-state-message="ready to print"
D [14/Sep/2011:16:45:16 +0200] [Job 877] printer-state-reasons=none

```
To make thing even more annoying, i tried exporting the file to pdf. It worked out but the pdf couldn't be printed, either on this computer or on another one running WinXP.

It's extremely annying as those files are needed for job, so i would be extremely grateful to anyone able to help me.

---

