---
title: "Printer No longer working after upgrade to 11.10 (Lexmark S405)"
date: 2011-10-17
forum: General Help
---

### Post by iclestu on 2011-10-17
I think I may have chosen incorrectly when upgrading.

I remember the upgrade dialogue asking me if I wanted to keep a customized cups file or use the default. I opted to keep the existing one but now I cannot print.

See screenshot for error message from KDE's printer tool.

Also tried uninstalling and then reinstalling lexmark's driver from here: [http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_INTERPRET_S405&page=product&frompage=null#1](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_INTERPRET_S405&page=product&frompage=null#1) 

This goes through the motions, installs drivers, finds printer on wlan etc. and appears to terminate correctly but then the printer just doesnt show when I try to print from any KDE app. It just has option for print to file. 

Anyone got any ideas?

---

### Post by iclestu on 2011-10-17
anyone got any ideas?

---

### Post by cnobile on 2011-10-18
I'm getting the same issues and it seems to be printer independent. My printer is an HP Stylus 415. It worked fine on Natty, but on 11.04 I can set it up on the network but nothing will print to it.

This is in the cups log: /var/log/cups/error_log

D [18/Oct/2011:22:59:28 -0400] [Job 30] Getting supported attributes...
D [18/Oct/2011:22:59:28 -0400] [Job 30] Get-Printer-Attributes: server-error-internal-error (Unknown)
D [18/Oct/2011:22:59:28 -0400] [Job 30] Get-Printer-Attributes returned server-error-internal-error.
E [18/Oct/2011:22:59:28 -0400] [Job 30] Unable to get printer status.

This is also in the system log: /var/log/syslog

Oct 19 19:50:40 odyssey kernel: [38119.579286] type=1400 audit(1319068240.145:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=4528 comm="apparmor_parser"
Oct 19 19:50:40 odyssey kernel: [38119.580556] type=1400 audit(1319068240.149:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=4528 comm="apparmor_parser"
Oct 19 19:50:40 odyssey udev-configure-printer: add /module/lp
Oct 19 19:50:40 odyssey udev-configure-printer: Failed to get parent

---

### Post by vanhecke on 2011-10-19
Same here with a HP Laserjet 1710n over a network. Worked perfectly on natty. Other people (windows PCs) have no problems with this printer.

The notifyOSD gives following message:
"the optical photoconductor needs to be replaced"

According to google, this means the toner. But the error stays after replacing the (not empty toner) for a fresh one.

In the printer properties, there is another error:
"print file was not accepted"


I hate to press the community, but being not able to print is quite a severe problem...

error_log:

D [19/Oct/2011:10:14:30 +0200] [Job 412] The following messages were recorded from 10:14:20 to 10:14:30
D [19/Oct/2011:10:14:30 +0200] [Job 412] Adding start banner page "none".
D [19/Oct/2011:10:14:30 +0200] [Job 412] Adding end banner page "none".
D [19/Oct/2011:10:14:30 +0200] [Job 412] File of type application/postscript queued by "vanhecke".
D [19/Oct/2011:10:14:30 +0200] [Job 412] hold_until=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] Queued on "Dell-Laser-Printer-1710n" by "vanhecke".
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-sheets=none,none
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[0]="Dell-Laser-Printer-1710n"
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[1]="412"
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[2]="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[3]="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[4]="1"
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[5]="PageSize=A4 job-uuid=urn:uuid:f5f3dbb4-ae50-3ce0-6abe-430b3e139293 job-originating-host-name=localhost time-at-creation=1319012060 time-at-processing=1319012060 AP_D_InputSlot="
D [19/Oct/2011:10:14:30 +0200] [Job 412] argv[6]="/var/spool/cups/d00412-001"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[8]="HOME=/var/spool/cups/tmp"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[10]="SERVER_ADMIN=root@anaexmo04"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[11]="SOFTWARE=CUPS/1.5.0"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[13]="USER=root"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[16]="IPP_PORT=631"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[17]="CHARSET=utf-8"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[18]="LANG=en_US.UTF-8"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[19]="PPD=/etc/cups/ppd/Dell-Laser-Printer-1710n.ppd"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[20]="RIP_MAX_CACHE=128m"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[21]="CONTENT_TYPE=application/postscript"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[22]="DEVICE_URI=dnssd://Dell%20Laser%20Printer%201710n._ipp._tcp.local/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[23]="PRINTER_INFO=Dell Laser Printer 1710n"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[24]="PRINTER_LOCATION=Office BW Printer"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[25]="PRINTER=Dell-Laser-Printer-1710n"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[26]="PRINTER_STATE_REASONS=none"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[27]="CUPS_FILETYPE=document"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
D [19/Oct/2011:10:14:30 +0200] [Job 412] envp[29]="AUTH_I****"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Started filter /usr/lib/cups/filter/pstops (PID 18894)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Started backend /usr/lib/cups/backend/dnssd (PID 18895)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Resolving "Dell Laser Printer 1710n._ipp._tcp.local"...
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: +connecting-to-device
D [19/Oct/2011:10:14:30 +0200] [Job 412] Resolving "Dell Laser Printer 1710n", regtype="_ipp._tcp", domain="local."...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Page = 595x842; 10,13 to 586,829
D [19/Oct/2011:10:14:30 +0200] [Job 412] slow_collate=0, slow_duplex=0, slow_order=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] Before copy_comments - %!PS-Adobe-3.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] %!PS-Adobe-3.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] %%Title: PPR Test Page
D [19/Oct/2011:10:14:30 +0200] [Job 412] %%Pages: 1
D [19/Oct/2011:10:14:30 +0200] [Job 412] %%BoundingBox: 0 0 595 842
D [19/Oct/2011:10:14:30 +0200] [Job 412] %%DocumentNeededResources: font Helvetica
D [19/Oct/2011:10:14:30 +0200] [Job 412] %%EndComments
D [19/Oct/2011:10:14:30 +0200] [Job 412] Before copy_prolog - %%BeginProlog
D [19/Oct/2011:10:14:30 +0200] [Job 412] Before copy_setup - %%BeginSetup
D [19/Oct/2011:10:14:30 +0200] [Job 412] Before page loop - %%Page: 1 1
D [19/Oct/2011:10:14:30 +0200] [Job 412] Copying page 1...
D [19/Oct/2011:10:14:30 +0200] [Job 412] PAGE: 1 1
D [19/Oct/2011:10:14:30 +0200] [Job 412] pagew = 576.0, pagel = 816.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [19/Oct/2011:10:14:30 +0200] [Job 412] PageLeft = 10.0, PageRight = 586.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] PageTop = 829.0, PageBottom = 13.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] PageWidth = 595.0, PageLength = 842.0
D [19/Oct/2011:10:14:30 +0200] [Job 412] Resolved as "ipp://130.92.22.210:631"...
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -connecting-to-device,offline-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] Executing backend "/usr/lib/cups/backend/ipp"...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Sending stdin for job...
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=0(), s="+connecting-to-device")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op='+', new_reasons=1, state_reasons=1
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: +connecting-to-device
D [19/Oct/2011:10:14:30 +0200] [Job 412] Looking up "130.92.22.210"...
D [19/Oct/2011:10:14:30 +0200] [Job 412] hrDeviceDesc="Dell Laser Printer 1710n 72C1CNM BR.Q.P203 -- Part Number --"
D [19/Oct/2011:10:14:30 +0200] [Job 412] prtMarkerColorantValue.1.1 = "black"
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-colors=#000000,none
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-names="Black Toner","Photo Drum"
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-types=toner,opc
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-levels=60,0
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_supply_state=20, change_state=ffff
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -developer-low-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -developer-empty-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -marker-supply-low-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -marker-supply-empty-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -opc-near-eol-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: +opc-life-over-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -toner-low-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -toner-empty-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_state=0, change_state=ffff
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -media-low-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -media-empty-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -door-open-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -media-jam-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -input-tray-missing-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -output-tray-missing-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -marker-supply-missing-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -output-area-almost-full-report
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -output-area-full-warning
D [19/Oct/2011:10:14:30 +0200] [Job 412] backendWaitLoop(snmp_fd=6, addr=0x7f1e08527e58, side_cb=0x7f1e07d8a270)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Connecting to 130.92.22.210:631
D [19/Oct/2011:10:14:30 +0200] [Job 412] Connecting to printer.
D [19/Oct/2011:10:14:30 +0200] [Job 412] Set job-printer-state-message to "Connecting to printer.", current level=INFO
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=0(), s="-cups-certificate-error")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op='-', new_reasons=1, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=0(), s="-connecting-to-device")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op='-', new_reasons=1, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -connecting-to-device
D [19/Oct/2011:10:14:30 +0200] [Job 412] Connected to printer.
D [19/Oct/2011:10:14:30 +0200] [Job 412] Set job-printer-state-message to "Connected to printer.", current level=INFO
D [19/Oct/2011:10:14:30 +0200] [Job 412] Connected to 130.92.22.210:631...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Getting supported attributes...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: server-error-version-not-supported (bad-request)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes returned server-error-version-not-supported.
D [19/Oct/2011:10:14:30 +0200] [Job 412] Printer does not support IPP/2.0, trying IPP/1.1.
D [19/Oct/2011:10:14:30 +0200] [Job 412] Set job-printer-state-message to "Printer does not support IPP/2.0, trying IPP/1.1.", current level=INFO
D [19/Oct/2011:10:14:30 +0200] [Job 412] Getting supported attributes...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Printer responded with HTTP version 1.0.
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=0(), s="+cups-ipp-conformance-failure-report,cups-ipp-wrong-http-version")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op='+', new_reasons=2, state_reasons=1
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: +cups-ipp-conformance-failure-report,cups-ipp-wrong-http-version
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] copies-supported=1-999
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format-supported (4 values)
D [19/Oct/2011:10:14:30 +0200] [Job 412] [0] = "application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] [1] = "application/postscript"
D [19/Oct/2011:10:14:30 +0200] [Job 412] [2] = "application/vnd.hp-PCL"
D [19/Oct/2011:10:14:30 +0200] [Job 412] [3] = "text/plain"
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=3
D [19/Oct/2011:10:14:30 +0200] [Job 412] STATE: -none
D [19/Oct/2011:10:14:30 +0200] [Job 412] Copying print data.
D [19/Oct/2011:10:14:30 +0200] [Job 412] Set job-printer-state-message to "Copying print data.", current level=INFO
D [19/Oct/2011:10:14:30 +0200] [Job 412] backendRunLoop(print_fd=-1, device_fd=8, snmp_fd=6, addr=0x7f1e08527e58, use_bc=0, side_cb=0x7f1e07d8a270)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] prtMarkerSuppliesLevel.1.1 = 6000
D [19/Oct/2011:10:14:30 +0200] [Job 412] prtMarkerSuppliesLevel.1.2 = -3
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-levels=100,0
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_supply_state=20, change_state=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_state=0, change_state=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 8192 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 4096 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 3407 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 1 pages...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 3407 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Read 93 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Wrote 93 bytes of print data...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Validate-Job: successful-ok (OK)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Print-Job IPP/1.1
D [19/Oct/2011:10:14:30 +0200] [Job 412] printer-uri="ipp://130.92.22.210:631/"
D [19/Oct/2011:10:14:30 +0200] [Job 412] requesting-user-name="vanhecke"
D [19/Oct/2011:10:14:30 +0200] [Job 412] job-name="Test Page"
D [19/Oct/2011:10:14:30 +0200] [Job 412] document-format="application/octet-stream"
D [19/Oct/2011:10:14:30 +0200] [Job 412] Sending file using HTTP/1.0 Content-Length...
D [19/Oct/2011:10:14:30 +0200] [Job 412] Print-Job: server-error-internal-error (Unknown)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Set job-printer-state-message to "Print file was not accepted.", current level=ERROR
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] update_reasons(attr=1(none), s="(null)")
D [19/Oct/2011:10:14:30 +0200] [Job 412] op=' ', new_reasons=0, state_reasons=2
D [19/Oct/2011:10:14:30 +0200] [Job 412] Get-Printer-Attributes: successful-ok-ignored-or-substituted-attributes (successful-ok-ignored-or-substituted-attributes)
D [19/Oct/2011:10:14:30 +0200] [Job 412] prtMarkerSuppliesLevel.1.1 = 6000
D [19/Oct/2011:10:14:30 +0200] [Job 412] prtMarkerSuppliesLevel.1.2 = -3
D [19/Oct/2011:10:14:30 +0200] [Job 412] ATTR: marker-levels=100,0
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_supply_state=20, change_state=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] new_state=0, change_state=0
D [19/Oct/2011:10:14:30 +0200] [Job 412] Backend returned status 4 (stop printer)
D [19/Oct/2011:10:14:30 +0200] [Job 412] Printer stopped due to backend errors; please consult the error_log file for details.
D [19/Oct/2011:10:14:30 +0200] [Job 412] End of messages

---

### Post by vanhecke on 2011-10-19
I tried to install other network printers (all HP) and all gave the same problem. Apparently something went wrong during the update of cups to Oneiric.

However, I could solve my problem by purging cups, reinstalling it and reinstalling the printers.

sudo apt-get purge cups
sudo apt-get install cups*

---

### Post by cnobile on 2011-10-19
I wouldn't recommend running purge it will try to remove hundreds of files. Doing a reinstall may be better in some cases, with me it didn't help either.

---

### Post by gtwin on 2011-10-25
I am having the same problem.  I have tried everything in this thread and a lot of things gleaned from google, but, no dice.  

Very unhappy, I use this for school.  It used to work flawlessly even via wireless for my lexmark.  I hope that this issue is addressed.

Is there any way to find out if it is being worked on??

Also, any workaround would be greatly appreciated.

---

### Post by bach on 2011-10-25
Same problem here. After upgrading to Ubuntu 11.10 I no longer can print to my HP Deskjet 810C.

---

### Post by oldtimer7777 on 2011-10-25
> **bach said:**
> Same problem here. After upgrading to Ubuntu 11.10 I no longer can print to my HP Deskjet 810C.

I had that problem with 11.04.. 

Something changed about printer driver configuration. I used the drop-down to select a similar printer driver and got it working again.  I can't find the same Printer configuration layout in 11.10 by going to Applications >> Systems Tools >> System Settings >> Printer.  It doesn't seem to give me the option to select different drivers on installed Printers. 

Does your printer show up as installed, but not printing? Or does it not show any printers installed in Printers settings?

---

### Post by gtwin on 2011-10-26
My printer is showing up as installed but is not printing.  It seems to be a breakdown in the usb communication.  When running the Lexmark package to install the driver it sets up the printer.  When running the wireless utility from Lexmark the printer is never even recognized as being plugged into the computer. (Kubuntu still sees it) ???  So strange.

I am about ready to install a new KDE distro that has no ubuntu kernel :(  It is my last resort.  I was hoping the CUPS update the other day was going to fix it.

---

### Post by cnobile on 2011-10-26
I have now tried an old HP DeskJet-880C directly to the USB port. I can configure it fine, but it won't print. This is the same results I get from my network printer an Epson NX415, as I mention above.

So it seems not to be printer drivers or a connection issue. I'm betting there is a problem with the cups server itself. I compared the /etc/cups/cupsd.conf with the one on an older machine which has Kubuntu 10.04 on it and except for a few minor things they were exactly the same.

Edit: I burned 11.10 onto a thumb drive and booted it from my eeePC 900 and guess what? Yup, the printer doesn't work from there either. There is definitely something wrong with cups itself.

Soooo, still no joy here. I'm hesitant to move off this version of Kubuntu, because they finally got sound to work with the HDMI port.

Edit: I have created an official bug report: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/883585](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/883585)

I recommend that everybody follow the bug I put in above. This would be the first place that any fixes will show up.

---

### Post by gtwin on 2011-11-01
ohhhhhhh cups update, hope that solves it, will know later

---

### Post by MrLeek on 2011-11-03
getting the same problem here (got a S405 as well) which worked just fine in 11.04. 

I managed to get the official Lexmark driver to run this time around (after fixing the typo in the script). The system "sees" the printer then throws a tantrum about not having the postscript driver. 

Ironically I can scan in documents just fine - which I couldn't do before - but can't print!

---

### Post by cnobile on 2011-11-11
There is a work around on the bug I put in. Go to: [https://bugs.launchpad.net/ubuntu/+s...ps/+bug/883585](https://bugs.launchpad.net/ubuntu/+s...ps/+bug/883585)

You will be using an smb server. You may have to configure samba first if your printer is plugged into the same machine that you are using. This is a no brainer in a network printer however.

---

### Post by DrIainAnderson on 2011-11-23
I experienced the same problems working under Gnome 3 but not Xfce (ie Xubuntu). This seems to imply that the problem lies in Unity/Gnome rather than with Cups.

---

### Post by cnobile on 2011-11-23
It doesn't work in KDE either. If you follow the post, to a bug I reported, that I put up earlier here, you will see that it is definitely something to do with cups. The developer that is working on cups is already on the issue.

There have been recent updates to cups which I haven't been able to try yet because I'm away from home which is where my printer is.

---

### Post by sharky6000 on 2011-12-12
> **DrIainAnderson said:**
> I experienced the same problems working under Gnome 3 but not Xfce (ie Xubuntu). This seems to imply that the problem lies in Unity/Gnome rather than with Cups.

I've got a Lexmark Interpret S405, I am using Xfce and it hasn't worked since the upgrade. I've tried reinstall cups, reinstalling the driver, removed and re-added the printer, etc. etc. 

The error message / printer status after trying to print a test page is **/usr/lib/cups/filter/gstoraster failed** . Can someone confirm that they see the same message? When I enable CUPS verbose logging it seems that gstoraster is terminating with exit code 13. 

(BTW, gstoraster is in the ghostscript-cups package)

There have been a number of updates to cups and ghostscript-cups since the upgrade and I always make sure the packages are all up-to-date before I try it again.

@cnobile: that link no longer works.. can you describe your workaround or point us to a new source?

---

### Post by cnobile on 2011-12-13
Everybody, there is a fix in the works for this issue. You can also put on the proposed package on your system now, which will fix it. It should get upgraded when the actual package comes out.

Go to the bug I put in at: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/883585](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/883585)

---

### Post by Etienne Bertens on 2012-01-25
I use a HP Laserjet 6P.
When I ask for a test page I get a lot of blanc pages.
Only the first page shows text. 
It says % ! PS-Adobe-3.0 %% Title: PPR Test Page %% DocumentNeededResources: font Helvetica.

The rest ( I estimate about 20 pages) are blanc pages.

---

