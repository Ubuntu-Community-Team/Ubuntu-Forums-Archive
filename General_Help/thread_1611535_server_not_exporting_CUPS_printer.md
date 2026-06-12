---
title: "server not exporting CUPS printer"
date: 2010-11-02
forum: General Help
---

### Post by swaprava on 2010-11-02
Hi all,

I was sharing my HP Laserjet USB printer over the local network using the CUPS page. The installation was fine and I configured it to publish the printer over the network. While I can print from the machine locally, I can't print remotely. The error it shows is "server not exporting printer". I checked the settings in the server PC and it is indeed sharing, however the standard troubleshooting recognize this isn't the case. I enabled debugging to see what is going on and printed a test page from the remote machine. It didn't print as usual. The following is the output of the debug:

```
D [02/Nov/2010:10:30:26 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:26 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:26 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:26 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:26 +0530] cupsdReadClient: 12 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:26 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:26 +0530] [Job 87] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 88] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 89] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:26 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:26 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:26 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:26 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:26 +0530] cupsdReadClient: 12 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:26 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:26 +0530] [Job 1] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 2] Loading attributes...
E [02/Nov/2010:10:30:26 +0530] [Job 2] Unable to queue job for destination "HP_HP_Officejet_Pro_8500_A909a"!
D [02/Nov/2010:10:30:26 +0530] [Job 3] Loading attributes...
E [02/Nov/2010:10:30:26 +0530] [Job 3] Unable to queue job for destination "HP_HP_Officejet_Pro_8500_A909a"!
D [02/Nov/2010:10:30:26 +0530] [Job 4] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 5] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 6] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 7] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 8] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 9] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 10] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 11] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 12] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 13] Loading attributes...
E [02/Nov/2010:10:30:26 +0530] [Job 13] Unable to queue job for destination "hp_hp_LaserJet_2430"!
D [02/Nov/2010:10:30:26 +0530] [Job 14] Loading attributes...
E [02/Nov/2010:10:30:26 +0530] [Job 14] Unable to queue job for destination "HP-LaserJet-2430"!
D [02/Nov/2010:10:30:26 +0530] [Job 15] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 16] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 17] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 18] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 19] Loading attributes...
E [02/Nov/2010:10:30:26 +0530] [Job 19] Unable to queue job for destination "HP-LaserJet-2430"!
D [02/Nov/2010:10:30:26 +0530] [Job 20] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 21] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 22] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 23] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 24] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 25] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 26] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 27] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 28] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 29] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 30] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 31] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 32] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 33] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 34] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 35] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 36] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 37] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 38] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 39] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 40] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 41] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 42] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 43] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 44] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 45] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 46] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 47] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 48] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 49] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 50] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 51] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 52] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 53] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 54] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 55] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 56] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 57] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 58] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 59] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 60] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 61] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 62] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 63] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 64] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 65] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 66] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 67] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 68] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 69] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 70] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 71] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 72] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 73] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 74] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 75] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 76] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 77] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 78] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 79] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 80] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 81] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 82] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 83] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 84] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 85] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] [Job 86] Loading attributes...
D [02/Nov/2010:10:30:26 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:26 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [02/Nov/2010:10:30:27 +0530] Create-Printer-Subscription /
D [02/Nov/2010:10:30:27 +0530] cupsdCreateSubscription(con=0x220355a8(12), uri="/")
D [02/Nov/2010:10:30:27 +0530] pullmethod="ippget"
D [02/Nov/2010:10:30:27 +0530] notify-lease-duration=86400
D [02/Nov/2010:10:30:27 +0530] notify-time-interval=0
D [02/Nov/2010:10:30:27 +0530] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [02/Nov/2010:10:30:27 +0530] Added subscription 44 for server
D [02/Nov/2010:10:30:27 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:27 +0530] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdAcceptClient: 15 from 10.192.16.20:631 (IPv4)
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:27 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:27 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:27 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:27 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:27 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:27 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:27 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:28 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:28 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:28 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:28 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:28 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:28 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:28 +0530] Get-Notifications /
D [02/Nov/2010:10:30:28 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:28 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:28 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:30 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:30 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:30 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:30 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:30 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:30 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:30 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:30 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:30 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:30 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:30 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:30 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:30 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:30 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:31 +0530] cupsdAcceptClient: 16 from localhost (Domain)
D [02/Nov/2010:10:30:31 +0530] cupsdReadClient: 16 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:31 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:31 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:31 +0530] cupsdReadClient: 16 1.1 Print-Job 1
D [02/Nov/2010:10:30:31 +0530] Print-Job ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:31 +0530] [Job ???] Auto-typing file...
I [02/Nov/2010:10:30:31 +0530] [Job ???] Request file type is application/vnd.cups-banner.
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(----J-)
D [02/Nov/2010:10:30:31 +0530] add_job: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:31 +0530] Adding default job-sheets values "none,none"...
I [02/Nov/2010:10:30:31 +0530] [Job 91] Adding start banner page "none".
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(----J-)
I [02/Nov/2010:10:30:31 +0530] [Job 91] Adding end banner page "none".
I [02/Nov/2010:10:30:31 +0530] [Job 91] File of type application/vnd.cups-banner queued by "swaprava".
D [02/Nov/2010:10:30:31 +0530] [Job 91] hold_until=0
I [02/Nov/2010:10:30:31 +0530] [Job 91] Queued on "LaserjetP2015d" by "swaprava".
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(----J-)
D [02/Nov/2010:10:30:31 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:31 +0530] [Job 91] job-sheets=none,none
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[0]="LaserjetP2015d"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[1]="91"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[2]="swaprava"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[3]="Test Page"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[4]="1"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[5]="job-uuid=urn:uuid:24ce224a-8e4e-3351-570b-fc1197e83e57 job-originating-host-name=localhost"
D [02/Nov/2010:10:30:31 +0530] [Job 91] argv[6]="/var/spool/cups/d00091-001"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[8]="HOME=/var/spool/cups/tmp"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[10]="SERVER_ADMIN=root@kolmogorov"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[11]="SOFTWARE=CUPS/1.4.3"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[13]="TZ=Asia/Kolkata"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[14]="USER=root"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[17]="IPP_PORT=631"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[18]="CHARSET=utf-8"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[19]="LANG=en_IN.UTF-8"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[20]="PPD=/etc/cups/ppd/LaserjetP2015d.ppd"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[21]="RIP_MAX_CACHE=901209k"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[23]="DEVICE_URI=http://10.192.16.20:631/printers/HP_LaserJet_P2015_Series"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[24]="PRINTER_INFO=HP Laserjet"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[25]="PRINTER_LOCATION=Swaprava's Desk"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[26]="PRINTER=LaserjetP2015d"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[27]="CUPS_FILETYPE=document"
D [02/Nov/2010:10:30:31 +0530] [Job 91] envp[28]="FINAL_CONTENT_TYPE=printer/LaserjetP2015d"
I [02/Nov/2010:10:30:31 +0530] [Job 91] Started filter /usr/lib/cups/filter/bannertops (PID 20762)
I [02/Nov/2010:10:30:31 +0530] [Job 91] Started filter /usr/lib/cups/filter/pstopdf (PID 20763)
I [02/Nov/2010:10:30:31 +0530] [Job 91] Started filter /usr/lib/cups/filter/pdftopdf (PID 20764)
I [02/Nov/2010:10:30:31 +0530] [Job 91] Started filter /usr/lib/cups/filter/foomatic-rip (PID 20765)
I [02/Nov/2010:10:30:31 +0530] [Job 91] Started backend /usr/lib/cups/backend/http (PID 20766)
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:31 +0530] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:31 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:31 +0530] [Job 91] Getting input from file
D [02/Nov/2010:10:30:31 +0530] [Job 91] foomatic-rip version 4.0.4.217 running...
D [02/Nov/2010:10:30:31 +0530] [Job 91] pstopdf 5 args: 91 swaprava Test Page 1 job-uuid=urn:uuid:24ce224a-8e4e-3351-570b-fc1197e83e57 job-originating-host-name=localhost
D [02/Nov/2010:10:30:31 +0530] [Job 91] PPD: /etc/cups/ppd/LaserjetP2015d.ppd
D [02/Nov/2010:10:30:31 +0530] [Job 91] Parsing PPD file ...
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option Resolution
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option PageSize
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option Model
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option PrintoutMode
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option InputSlot
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option Duplex
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option Quality
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option ImageableArea
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option PaperDimension
D [02/Nov/2010:10:30:31 +0530] [Job 91] Added option Font
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] Parameter Summary
D [02/Nov/2010:10:30:31 +0530] [Job 91] -----------------
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] Spooler: cups
D [02/Nov/2010:10:30:31 +0530] [Job 91] Printer: LaserjetP2015d
D [02/Nov/2010:10:30:31 +0530] [Job 91] Shell: /bin/bash
D [02/Nov/2010:10:30:31 +0530] [Job 91] PPD file: /etc/cups/ppd/LaserjetP2015d.ppd
D [02/Nov/2010:10:30:31 +0530] [Job 91] ATTR file:
D [02/Nov/2010:10:30:31 +0530] [Job 91] Printer model: HP LaserJet p2015d Series hpijs, 3.10.2
D [02/Nov/2010:10:30:31 +0530] [Job 91] Job title: Test Page
D [02/Nov/2010:10:30:31 +0530] [Job 91] File(s) to be printed:
D [02/Nov/2010:10:30:31 +0530] [Job 91] <STDIN>
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [02/Nov/2010:10:30:31 +0530] [Job 91] Printing system options:
D [02/Nov/2010:10:30:31 +0530] [Job 91] Pondering option 'job-uuid=urn:uuid:24ce224a-8e4e-3351-570b-fc1197e83e57'
D [02/Nov/2010:10:30:31 +0530] [Job 91] Unknown option job-uuid=urn:uuid:24ce224a-8e4e-3351-570b-fc1197e83e57.
D [02/Nov/2010:10:30:31 +0530] [Job 91] Pondering option 'job-originating-host-name=localhost'
D [02/Nov/2010:10:30:31 +0530] [Job 91] Unknown option job-originating-host-name=localhost.
D [02/Nov/2010:10:30:31 +0530] [Job 91] Options from the PPD file:
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] ================================================
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] File: <STDIN>
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] ================================================
D [02/Nov/2010:10:30:31 +0530] [Job 91]
D [02/Nov/2010:10:30:31 +0530] [Job 91] STATE: +connecting-to-device
D [02/Nov/2010:10:30:31 +0530] [Job 91] Looking up "10.192.16.20"...
I [02/Nov/2010:10:30:31 +0530] [Job 91] Copying print data...
D [02/Nov/2010:10:30:31 +0530] [Job 91] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x22cab844, use_bc=0, side_cb=0xee1620)
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:31 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:31 +0530] [Job 91] load_banner(filename="/var/spool/cups/d00091-001")
D [02/Nov/2010:10:30:31 +0530] [Job 91] Page = 595x842; 18,14 to 577,828
D [02/Nov/2010:10:30:31 +0530] [Job 91] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [02/Nov/2010:10:30:31 +0530] [Job 91] PNG image: 192x128x8, color_type=2 (RGB)
D [02/Nov/2010:10:30:31 +0530] PID 20762 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [02/Nov/2010:10:30:32 +0530] [Job 91] Resolution: 600
D [02/Nov/2010:10:30:32 +0530] [Job 91] Page size: A4
D [02/Nov/2010:10:30:32 +0530] [Job 91] Width: 595, height: 842, absolute margins: 18, 14.39999961853, 577, 827.60000038147
D [02/Nov/2010:10:30:32 +0530] [Job 91] Relative margins: 18, 14.39999961853, 18, 14.39999961853
D [02/Nov/2010:10:30:32 +0530] [Job 91] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [02/Nov/2010:10:30:32 +0530] [Job 91] PostScript to be injected:
D [02/Nov/2010:10:30:32 +0530] [Job 91] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 18 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 18 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 18 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:32 +0530] Get-Notifications /
D [02/Nov/2010:10:30:32 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 19 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:32 +0530] Get-Notifications /
D [02/Nov/2010:10:30:32 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:32 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:32 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 21 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdAcceptClient: 22 from localhost (Domain)
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:32 +0530] Get-Notifications /
D [02/Nov/2010:10:30:32 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 20 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Job-Attributes ipp://localhost/jobs/91
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/91) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:32 +0530] Get-Notifications /
D [02/Nov/2010:10:30:32 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:32 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:32 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:32 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:32 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:32 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:32 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:33 +0530] PID 20763 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [02/Nov/2010:10:30:33 +0530] [Job 91] Filetype: PDF
D [02/Nov/2010:10:30:33 +0530] [Job 91] Storing temporary files in /var/spool/cups/tmp
D [02/Nov/2010:10:30:33 +0530] PID 20764 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [02/Nov/2010:10:30:33 +0530] [Job 91] File contains 2 pages
D [02/Nov/2010:10:30:33 +0530] [Job 91] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="HP LaserJet" -dDuplex=true -dTumble=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:PenSet=0,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-Sfg5ke
D [02/Nov/2010:10:30:33 +0530] [Job 91] Starting process "kid3" (generation 1)
D [02/Nov/2010:10:30:33 +0530] [Job 91] Starting process "kid4" (generation 2)
D [02/Nov/2010:10:30:33 +0530] [Job 91] Starting process "renderer" (generation 2)
D [02/Nov/2010:10:30:33 +0530] [Job 91] JCL: %-12345X@PJL
D [02/Nov/2010:10:30:33 +0530] [Job 91] <job data>
D [02/Nov/2010:10:30:33 +0530] [Job 91]
D [02/Nov/2010:10:30:33 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:33 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:33 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:33 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:33 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:33 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:33 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:33 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:33 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:33 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:33 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:33 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:33 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:33 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:33 +0530] [Job 91] sh: hpijs: not found
D [02/Nov/2010:10:30:33 +0530] [Job 91] GPL Ghostscript 8.71: Can't start ijs server "hpijs"
D [02/Nov/2010:10:30:33 +0530] [Job 91] renderer exited with status 1
D [02/Nov/2010:10:30:33 +0530] [Job 91] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [02/Nov/2010:10:30:33 +0530] PID 20765 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [02/Nov/2010:10:30:33 +0530] [Job 91] Read 50 bytes of print data...
D [02/Nov/2010:10:30:33 +0530] [Job 91] Wrote 50 bytes of print data...
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] [Job 91] prtGeneralCurrentLocalization type is 0, expected 2!
D [02/Nov/2010:10:30:37 +0530] [Job 91] 1 files to send in job...
D [02/Nov/2010:10:30:37 +0530] [Job 91] STATE: +connecting-to-device
D [02/Nov/2010:10:30:37 +0530] [Job 91] Connecting to 10.192.16.20:631
I [02/Nov/2010:10:30:37 +0530] [Job 91] Connecting to printer...
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] [Job 91] STATE: -connecting-to-device
I [02/Nov/2010:10:30:37 +0530] [Job 91] Connected to printer...
D [02/Nov/2010:10:30:37 +0530] [Job 91] Connected to 10.192.16.20:631 (IPv4)...
D [02/Nov/2010:10:30:37 +0530] [Job 91] Getting supported attributes...
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] [Job 91] document-format-supported (32 values)
D [02/Nov/2010:10:30:37 +0530] [Job 91] [0] = "application/octet-stream"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [1] = "application/openofficeps"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [2] = "application/pdf"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [3] = "application/postscript"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [4] = "application/vnd.cups-banner"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [5] = "application/vnd.cups-pdf"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [6] = "application/vnd.cups-postscript"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [7] = "application/vnd.cups-raster"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [8] = "application/vnd.cups-raw"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [9] = "application/vnd.hp-hpgl"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [10] = "application/x-cshell"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [11] = "application/x-csource"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [12] = "application/x-perl"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [13] = "application/x-shell"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [14] = "image/gif"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [15] = "image/jpeg"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [16] = "image/png"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [17] = "image/tiff"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [18] = "image/x-bitmap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [19] = "image/x-photocd"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [20] = "image/x-portable-anymap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [21] = "image/x-portable-bitmap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [22] = "image/x-portable-graymap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [23] = "image/x-portable-pixmap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [24] = "image/x-sgi-rgb"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [25] = "image/x-sun-raster"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [26] = "image/x-xbitmap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [27] = "image/x-xpixmap"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [28] = "image/x-xwindowdump"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [29] = "text/css"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [30] = "text/html"
D [02/Nov/2010:10:30:37 +0530] [Job 91] [31] = "text/plain"
I [02/Nov/2010:10:30:37 +0530] [Job 91] ready to print
D [02/Nov/2010:10:30:37 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:37 +0530] [Job 91] printer-uri = "http://10.192.16.20:631/printers/HP_LaserJet_P2015_Series"
D [02/Nov/2010:10:30:37 +0530] [Job 91] requesting-user-name = "swaprava"
D [02/Nov/2010:10:30:37 +0530] [Job 91] job-name = "Test Page"
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
N [02/Nov/2010:10:30:37 +0530] [Job 91] Print file accepted - job ID 320.
I [02/Nov/2010:10:30:37 +0530] [Job 91] Waiting for job to complete...
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
I [02/Nov/2010:10:30:37 +0530] [Job 91]
D [02/Nov/2010:10:30:37 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:37 +0530] cupsdAcceptClient: 23 from localhost (Domain)
D [02/Nov/2010:10:30:37 +0530] cupsdAcceptClient: 24 from localhost (Domain)
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 23 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdAcceptClient: 25 from localhost (Domain)
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 25 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 23 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:37 +0530] Get-Notifications /
D [02/Nov/2010:10:30:37 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:37 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 25 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:37 +0530] Get-Notifications /
D [02/Nov/2010:10:30:37 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 24
D [02/Nov/2010:10:30:37 +0530] cupsdAcceptClient: 24 from localhost (Domain)
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:37 +0530] Get-Notifications /
D [02/Nov/2010:10:30:37 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 18 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 18
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:37 +0530] Get-Notifications /
D [02/Nov/2010:10:30:37 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 24 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 24
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 23 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 23
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:37 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 25 WAITING Closing on EOF
D [02/Nov/2010:10:30:37 +0530] cupsdCloseClient: 25
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:37 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:37 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:37 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:37 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:37 +0530] cupsdSetBusyState: Printing jobs and dirty files
I [02/Nov/2010:10:30:38 +0530] [Job 91] Processing page 2...
D [02/Nov/2010:10:30:38 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:38 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:38 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:38 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:38 +0530] cupsdAcceptClient: 18 from localhost (Domain)
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 18 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:38 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 18 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:38 +0530] Get-Notifications /
D [02/Nov/2010:10:30:38 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:38 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 20 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:38 +0530] Get-Notifications /
D [02/Nov/2010:10:30:38 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:38 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:38 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:38 +0530] Get-Notifications /
D [02/Nov/2010:10:30:38 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:38 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:38 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:38 +0530] Get-Notifications /
D [02/Nov/2010:10:30:38 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:38 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 18 WAITING Closing on EOF
D [02/Nov/2010:10:30:38 +0530] cupsdCloseClient: 18
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:38 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:38 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:38 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:38 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:38 +0530] cupsdCloseClient: 19
I [02/Nov/2010:10:30:40 +0530] [Job 91] Processing page 2...
D [02/Nov/2010:10:30:40 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:40 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:40 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:40 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:40 +0530] cupsdAcceptClient: 18 from localhost (Domain)
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 18 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:40 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 18 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:40 +0530] Get-Notifications /
D [02/Nov/2010:10:30:40 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:40 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 20 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:40 +0530] Get-Notifications /
D [02/Nov/2010:10:30:40 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:40 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:40 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:40 +0530] Get-Notifications /
D [02/Nov/2010:10:30:40 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:40 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:40 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:40 +0530] Get-Notifications /
D [02/Nov/2010:10:30:40 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 18 WAITING Closing on EOF
D [02/Nov/2010:10:30:40 +0530] cupsdCloseClient: 18
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:40 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:40 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:40 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:40 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:40 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:40 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:42 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:42 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:42 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:42 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:42 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:42 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:42 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:42 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:42 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:42 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:42 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:42 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:42 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:42 +0530] cupsdSetBusyState: Printing jobs and dirty files
I [02/Nov/2010:10:30:43 +0530] [Job 91] Processing page 2...
D [02/Nov/2010:10:30:43 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:43 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:43 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:43 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:43 +0530] cupsdAcceptClient: 18 from localhost (Domain)
D [02/Nov/2010:10:30:43 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 18 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 18 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:43 +0530] Get-Notifications /
D [02/Nov/2010:10:30:43 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:43 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 20 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:43 +0530] Get-Notifications /
D [02/Nov/2010:10:30:43 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:43 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:43 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:43 +0530] Get-Notifications /
D [02/Nov/2010:10:30:43 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:43 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:43 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:43 +0530] Get-Notifications /
D [02/Nov/2010:10:30:43 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 18 WAITING Closing on EOF
D [02/Nov/2010:10:30:43 +0530] cupsdCloseClient: 18
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:43 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:43 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:43 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:43 +0530] cupsdSetBusyState: Printing jobs and dirty files
D [02/Nov/2010:10:30:43 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:43 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:47 +0530] [Job 91] PAGE: total 2
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
I [02/Nov/2010:10:30:47 +0530] [Job 91] ready to print
D [02/Nov/2010:10:30:47 +0530] [Job 91] STATE: none
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(P-----)
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:47 +0530] [Job 91] ATTR: auth-info-required=none
D [02/Nov/2010:10:30:47 +0530] load_ppd: Loading /var/cache/cups/LaserjetP2015d.ipp...
D [02/Nov/2010:10:30:47 +0530] cupsdRegisterPrinter(p=0x220214f8(LaserjetP2015d))
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(P-----)
I [02/Nov/2010:10:30:47 +0530] [Job 91] Ready to print.
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:47 +0530] PID 20766 (/usr/lib/cups/backend/http) exited with no errors.
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
E [02/Nov/2010:10:30:47 +0530] [Job 91] Job stopped due to filter errors; please consult the error_log file for details.
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(----J-)
D [02/Nov/2010:10:30:47 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:30:47 +0530] [Job 91] The following messages were recorded from 10:30:35 to 10:30:35
D [02/Nov/2010:10:30:47 +0530] [Job 91] hrDeviceDesc="Unknown"
D [02/Nov/2010:10:30:47 +0530] [Job 91] End of messages
D [02/Nov/2010:10:30:47 +0530] [Job 91] printer-state=3(idle)
D [02/Nov/2010:10:30:47 +0530] [Job 91] printer-state-message="Ready to print."
D [02/Nov/2010:10:30:47 +0530] [Job 91] printer-state-reasons=none
D [02/Nov/2010:10:30:47 +0530] cupsdAcceptClient: 17 from localhost (Domain)
D [02/Nov/2010:10:30:47 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdAcceptClient: 20 from localhost (Domain)
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 20 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:47 +0530] Get-Notifications /
D [02/Nov/2010:10:30:47 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 1.1 Get-Jobs 1
D [02/Nov/2010:10:30:47 +0530] Get-Jobs ipp://localhost/printers/
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 20 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:47 +0530] Get-Notifications /
D [02/Nov/2010:10:30:47 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:47 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:47 +0530] cupsdAcceptClient: 19 from localhost (Domain)
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:47 +0530] Get-Notifications /
D [02/Nov/2010:10:30:47 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 12 1.1 Get-Notifications 1
D [02/Nov/2010:10:30:47 +0530] Get-Notifications /
D [02/Nov/2010:10:30:47 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://localhost/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 WAITING Closing on EOF
D [02/Nov/2010:10:30:47 +0530] cupsdCloseClient: 17
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 20 WAITING Closing on EOF
D [02/Nov/2010:10:30:47 +0530] cupsdCloseClient: 20
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAcceptClient: 17 from localhost (Domain)
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 16 WAITING Closing on EOF
D [02/Nov/2010:10:30:47 +0530] cupsdCloseClient: 16
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Printer-Attributes ipp://kolmogorov:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://kolmogorov:631/printers/LaserjetP2015d) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:47 +0530] Get-Job-Attributes ipp://localhost/jobs/91
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/91) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 22 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Printers
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Classes 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Classes
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 POST / HTTP/1.1
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 21 1.1 CUPS-Get-Default 1
D [02/Nov/2010:10:30:47 +0530] CUPS-Get-Default
D [02/Nov/2010:10:30:47 +0530] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [02/Nov/2010:10:30:47 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:47 +0530] cupsdReadClient: 19 WAITING Closing on EOF
D [02/Nov/2010:10:30:47 +0530] cupsdCloseClient: 19
D [02/Nov/2010:10:30:48 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:48 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:48 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:48 +0530] [Job 91] Unloading...
D [02/Nov/2010:10:30:48 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:48 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:48 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:48 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:30:48 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:48 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:30:48 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:48 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:48 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:48 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:48 +0530] cupsdSetBusyState: Dirty files
I [02/Nov/2010:10:30:53 +0530] Saving printers.conf...
I [02/Nov/2010:10:30:53 +0530] Generating printcap /var/run/cups/printcap...
I [02/Nov/2010:10:30:53 +0530] Saving job cache file "/var/cache/cups/job.cache"...
I [02/Nov/2010:10:30:53 +0530] Saving subscriptions.conf...
D [02/Nov/2010:10:30:53 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:30:55 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:55 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:30:55 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:55 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:30:55 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:55 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:55 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:30:55 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:30:55 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:30:55 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:30:55 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:30:55 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:30:55 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:30:55 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:31:03 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:31:03 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:31:03 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:31:03 +0530] [Job 90] Unloading...
D [02/Nov/2010:10:31:03 +0530] cupsdReadClient: 15 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:31:03 +0530] Get-Job-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:31:03 +0530] [Job 90] Loading attributes...
D [02/Nov/2010:10:31:03 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:31:03 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:31:03 +0530] cupsdReadClient: 15 POST /printers/LaserjetP2015d HTTP/1.1
D [02/Nov/2010:10:31:03 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:31:03 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:31:03 +0530] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [02/Nov/2010:10:31:03 +0530] Get-Printer-Attributes ipp://10.192.16.30:631/printers/LaserjetP2015d
D [02/Nov/2010:10:31:03 +0530] Returning IPP successful-ok for Get-Printer-Attributes (ipp://10.192.16.30:631/printers/LaserjetP2015d) from 10.192.16.20
D [02/Nov/2010:10:31:03 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:31:05 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:31:05 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:31:05 +0530] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [02/Nov/2010:10:31:05 +0530] Get-Job-Attributes ipp://localhost/jobs/91
D [02/Nov/2010:10:31:05 +0530] [Job 91] Loading attributes...
D [02/Nov/2010:10:31:05 +0530] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/91) from localhost
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Not busy
D [02/Nov/2010:10:31:05 +0530] cupsdReadClient: 12 POST / HTTP/1.1
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Active clients
D [02/Nov/2010:10:31:05 +0530] cupsdAuthorize: No authentication data provided.
D [02/Nov/2010:10:31:05 +0530] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [02/Nov/2010:10:31:05 +0530] Cancel-Subscription /
D [02/Nov/2010:10:31:05 +0530] cupsdIsAuthorized: requesting-user-name="swaprava"
D [02/Nov/2010:10:31:05 +0530] cupsdMarkDirty(-----S)
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:31:05 +0530] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Dirty files
D [02/Nov/2010:10:31:05 +0530] cupsdAcceptClient: 16 from localhost (Domain)
D [02/Nov/2010:10:31:05 +0530] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1
D [02/Nov/2010:10:31:05 +0530] cupsdSetBusyState: Active clients and dirty files
D [02/Nov/2010:10:31:05 +0530] cupsdAuthorize: No authentication data provided.
```Please help. This printer was earlier shared properly, and was working fine. I installed a new printer other than the printer in question for which I had to install the drivers externally, I guess that might have screwed it up. However I don't know how to undo this external driver installation. I'm also attaching the content of my server PC's /etc/cups/cupsd.conf file.

---

### Post by swaprava on 2010-11-02
Well, I solved it, not a very elegant solution though. I reinstalled CUPS. It appears that the later installation of the HP drivers conflict with the current installation of CUPS and hence the printer stopped working.

Moreover, adding printers using CUPS is not bug-free. In fact, even though one adds a new printer and explicitly ticks the share printer checkbox, it doesn't do so. You can check it in the /etc/cups/cupsd.conf file. where the following lines won't be present:

```
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd

```

which is a bug for sure in CUPS. So, one needs to add these lines in the above file in order to share it over the network and to view it from remote PC. The example file is attached in the previous post. I just shared this info for the people who have standalone printers and want to share it over the network. Thanks for reading.

---

### Post by clockworkpc on 2010-12-15
This is for anyone who has had trouble printing from a printer that is connected via USB. In my case it had nothing to do with the make of the printer (Brother HL-2140), but rather with the USB connection.

My printer was connected via USB, but the USB was connected to a faulty USB hub. I connected it to a fully functional USB hub (Model UH-315, [http://www.amazon.com/CP-TECHNOLOGIE.../dp/B00076TK2Q](http://www.amazon.com/CP-TECHNOLOGIE.../dp/B00076TK2Q)), and it worked perfectly.

Moral of the story, if you connect your USB printer via a USB hub, try connecting it to a different one, or directly to your PC.

If you have a USB printer connected via USB and get the message "Server not exporting", try this solution.

I tried reinstalling CUPS and all that, but there was nothing wrong with my files or my printer or my drivers. It was simply and solely due to my crappy 4-port usb hub.

---

