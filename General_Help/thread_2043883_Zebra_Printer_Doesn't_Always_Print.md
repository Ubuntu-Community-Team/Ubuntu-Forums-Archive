---
title: "Zebra Printer Doesn't Always Print"
date: 2012-08-17
forum: General Help
---

### Post by CrusaderAD on 2012-08-17
Weird issue here. I have a Zebra LP-2844 successfully installed and printing test pages with the EP2 PPD driver. I can also print using the lpr command from the terminal like this:

```
lpr -P "Zebra" test.txt
```

But when I use the print dialog box using something like Gedit or Firefox, the print job just hangs in the queue. Any ideas?

---

### Post by CrusaderAD on 2012-08-17
When checking the CUPS web interface, this is all it says about the queued job, which has been sitting there for a while.

---

### Post by CrusaderAD on 2012-08-21
Bump

---

### Post by CrusaderAD on 2012-08-22
Anyone?

---

### Post by CrusaderAD on 2012-08-22
Here's the log output of a fail job:

> W [22/Aug/2012:07:33:02 -0400] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Zebra-LP2844-Gray..' already exists
W [22/Aug/2012:07:33:02 -0400] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Zebra-LP2844' already exists
E [22/Aug/2012:08:18:28 -0400] [Job 33] No pages were found.
E [22/Aug/2012:08:18:36 -0400] [Job 33] Job stopped due to filter errors; please consult the error_log file for details.
D [22/Aug/2012:08:18:36 -0400] [Job 33] The following messages were recorded from 08:18:27 to 08:18:35
D [22/Aug/2012:08:18:36 -0400] [Job 33] Adding start banner page "none".
D [22/Aug/2012:08:18:36 -0400] [Job 33] Adding end banner page "none".
D [22/Aug/2012:08:18:36 -0400] [Job 33] File of type application/pdf queued by "user".
D [22/Aug/2012:08:18:36 -0400] [Job 33] hold_until=0
D [22/Aug/2012:08:18:36 -0400] [Job 33] Queued on "Zebra-LP2844" by "user".
D [22/Aug/2012:08:18:36 -0400] [Job 33] job-sheets=none,none
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[0]="Zebra-LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[1]="33"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[2]="user"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[3]="Ubuntu Start Page"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[4]="1"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[5]="Darkness=-1 zePrintRate=Default PageSize=Custom.Custom.595.28x841.89 MediaType=Saved Resolution=203dpi number-up=1 job-uuid=urn:uuid:3eda07f8-15a2-3f9a-7e8a-8331162f2d2d job-originating-host-name=localhost time-at-creation=1345637907 time-at-processing=1345637907"
D [22/Aug/2012:08:18:36 -0400] [Job 33] argv[6]="/var/spool/cups/d00033-001"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[8]="HOME=/var/spool/cups/tmp"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[10]="SERVER_ADMIN=root@shipping1"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[11]="SOFTWARE=CUPS/1.5.3"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[13]="USER=root"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[16]="IPP_PORT=631"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[17]="CHARSET=utf-8"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[18]="LANG=en_US.UTF-8"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[19]="PPD=/etc/cups/ppd/Zebra-LP2844.ppd"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[20]="RIP_MAX_CACHE=128m"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[21]="CONTENT_TYPE=application/pdf"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[22]="DEVICE_URI=usb://Zebra/LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[23]="PRINTER_INFO=Zebra LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[24]="PRINTER_LOCATION=shipping1"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[25]="PRINTER=Zebra-LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[26]="PRINTER_STATE_REASONS=none"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[27]="CUPS_FILETYPE=document"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[28]="FINAL_CONTENT_TYPE=printer/Zebra-LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[29]="AUTH_I****"
D [22/Aug/2012:08:18:36 -0400] [Job 33] Started filter /usr/lib/cups/filter/pdftopdf (PID 9035)
D [22/Aug/2012:08:18:36 -0400] [Job 33] Started filter /usr/lib/cups/filter/gstoraster (PID 9036)
D [22/Aug/2012:08:18:36 -0400] [Job 33] Started filter /usr/lib/cups/filter/rastertolabel (PID 9037)
D [22/Aug/2012:08:18:36 -0400] [Job 33] Started backend /usr/lib/cups/backend/usb (PID 9038)
D [22/Aug/2012:08:18:36 -0400] [Job 33] Printing on printer with URI: usb://Zebra/LP2844
D [22/Aug/2012:08:18:36 -0400] [Job 33] PPD uses qualifier 'Gray.Saved.203dpi'
D [22/Aug/2012:08:18:36 -0400] [Job 33] libusb_get_device_list=12
D [22/Aug/2012:08:18:36 -0400] [Job 33] Calling FindDeviceById(Zebra-LP2844)
D [22/Aug/2012:08:18:36 -0400] [Job 33] Failed to send: org.freedesktop.ColorManager.Failed:device id 'Zebra-LP2844' does not exists
D [22/Aug/2012:08:18:36 -0400] [Job 33] Failed to get profile filename!
D [22/Aug/2012:08:18:36 -0400] [Job 33] no profiles specified in PPD
D [22/Aug/2012:08:18:36 -0400] [Job 33] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [22/Aug/2012:08:18:36 -0400] [Job 33] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -r203x203 -dDEVICEWIDTHPOINTS=0 -dDEVICEHEIGHTPOINTS=0 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsCompression=-1 -scupsPageSizeName=Custom -I/usr/share/cups/fonts -c -f -_
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[8]="HOME=/var/spool/cups/tmp"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[10]="SERVER_ADMIN=root@shipping1"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[11]="SOFTWARE=CUPS/1.5.3"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[12]="USER=root"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[14]="CUPS_ENCRYPTION=IfRequested"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[15]="IPP_PORT=631"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[16]="CHARSET=utf-8"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[17]="LANG=en_US.UTF-8"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[18]="PPD=/etc/cups/ppd/Zebra-LP2844.ppd"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[19]="RIP_MAX_CACHE=128m"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[20]="CONTENT_TYPE=application/pdf"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[21]="DEVICE_URI=usb://Zebra/LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[22]="PRINTER_INFO=Zebra LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[23]="PRINTER_LOCATION=shipping1"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[24]="PRINTER=Zebra-LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[25]="PRINTER_STATE_REASONS=none"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[26]="CUPS_FILETYPE=document"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[27]="FINAL_CONTENT_TYPE=printer/Zebra-LP2844"
D [22/Aug/2012:08:18:36 -0400] [Job 33] envp[28]="AUTH_INFO_REQUIRED=none"
D [22/Aug/2012:08:18:36 -0400] [Job 33] Start rendering...
D [22/Aug/2012:08:18:36 -0400] [Job 33] Set job-printer-state-message to "Start rendering...", current level=INFO
D [22/Aug/2012:08:18:36 -0400] [Job 33] Processing page 1...
D [22/Aug/2012:08:18:36 -0400] [Job 33] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [22/Aug/2012:08:18:36 -0400] [Job 33] Unrecoverable error: rangecheck in setpagedevice
D [22/Aug/2012:08:18:36 -0400] [Job 33] Operand stack:
D [22/Aug/2012:08:18:36 -0400] [Job 33] true  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  --nostringval--  true  --nostringval--  .LockSafetyParams  true  %MediaSource  0  %MediaDestination  0  LeadingEdge  0  --nostringval--  --nostringval--  --nostringval--  0  --nostringval--  false  --nostringval--
D [22/Aug/2012:08:18:36 -0400] [Job 33] Rendering completed
D [22/Aug/2012:08:18:36 -0400] [Job 33] Set job-printer-state-message to "Rendering completed", current level=INFO
D [22/Aug/2012:08:18:36 -0400] [Job 33] Set job-printer-state-message to "No pages were found.", current level=ERROR
D [22/Aug/2012:08:18:36 -0400] [Job 33] STATE: +connecting-to-device
D [22/Aug/2012:08:18:36 -0400] [Job 33] STATE: -connecting-to-device
D [22/Aug/2012:08:18:36 -0400] [Job 33] Printer found with device ID: MFG:Zebra ;CMD:None;MDL:LP2844 ; Device URI: usb://Zebra/LP2844
D [22/Aug/2012:08:18:36 -0400] [Job 33] Device protocol: 2
D [22/Aug/2012:08:18:36 -0400] [Job 33] Sending data to printer.
D [22/Aug/2012:08:18:36 -0400] [Job 33] Sent 0 bytes...
D [22/Aug/2012:08:18:36 -0400] [Job 33] Waiting for read thread to exit...
D [22/Aug/2012:08:18:36 -0400] [Job 33] Read thread still active, aborting the pending read...
D [22/Aug/2012:08:18:36 -0400] [Job 33] End of messages
D [22/Aug/2012:08:18:36 -0400] [Job 33] printer-state=3(idle)
D [22/Aug/2012:08:18:36 -0400] [Job 33] printer-state-message="Sending data to printer."
D [22/Aug/2012:08:18:36 -0400] [Job 33] printer-state-reasons=none


---

### Post by wolfsden3 on 2012-10-15
I'm having a similar problem, still working on the fix.  If I find it I'll let you know.

My specific problem is:
[INDENT]stopped 
[/INDENT][INDENT]*"No pages were found."*
[/INDENT] IT's a curious error indeed...

---

### Post by CrusaderAD on 2012-10-15
I just print from the command line. That seems to work. The bug seems to be somewhere in the GUI print dialog.

---

### Post by Radiot7777 on 2012-11-30
> **wolfsden3 said:**
> I'm having a similar problem, still working on the fix.  If I find it I'll let you know.

My specific problem is:
[INDENT]stopped 
[/INDENT][INDENT]*"No pages were found."*
[/INDENT] IT's a curious error indeed...



I have 12.04 64bit installed.
Using a Zebra LP2824. glabel gives me the error if I hit print. But if I hit print preview, then print, it'll print. cups reports....

stopped 
"No pages were found."

Chromium can print to the printer fine. Firefox results in same error. Somewhere, somebody seemed to mention a privileges error. but that's unconfirmed for this. Going to take some work to try and solve. Need to learn how to generate and find those error reports. ( I know, probably read above. )

---

