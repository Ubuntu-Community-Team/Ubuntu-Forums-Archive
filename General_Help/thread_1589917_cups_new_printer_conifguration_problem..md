---
title: "cups new printer conifguration problem."
date: 2010-10-07
forum: General Help
---

### Post by aboud on 2010-10-07
Hello there ! 


I have hp printer connected to Ubuntu 10.4 Server, shared with other windows and operating perfectly. I've added one more hp printer and it's working well under linux, but windows including the one on the same machine on a vmware refuses to connect to it. This same windows is using the other printer without problems. 


Windows sort of find the printer and ask for driver, after copying the drivers files, the error message appear : " Windows can't connect to the printer. operation could not be complete " 
on this windows the credential for this server is saved and I am using shared folder without need to enter the password. firewall is not showing any events . 
 
just to make sure, is the printer name is the same sharename, if not where is the sharename is specified ? 


CUPS error while trying to connect the printer
```

D [07/Oct/2010:12:01:02 +0300] cupsdAcceptClient: 14 from localhost:631 (IPv4)
D [07/Oct/2010:12:01:02 +0300] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1
D [07/Oct/2010:12:01:02 +0300] cupsdSetBusyState: Active clients
D [07/Oct/2010:12:01:02 +0300] cupsdAuthorize: No authentication data provided.
D [07/Oct/2010:12:01:02 +0300] cupsdSetBusyState: Not busy
D [07/Oct/2010:12:01:16 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:16 +0300] [Job 3] Unloading...
	... many Unloadings ..
 
D [07/Oct/2010:12:01:16 +0300] [Job 111] Unloading...
D [07/Oct/2010:12:01:16 +0300] cupsdAcceptClient: 16 from localhost (Domain)
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:16 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:16 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 16 WAITING Closing on EOF
D [07/Oct/2010:12:01:16 +0300] cupsdCloseClient: 16
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 POST / HTTP/1.1
D [07/Oct/2010:12:01:16 +0300] cupsdSetBusyState: Active clients
D [07/Oct/2010:12:01:16 +0300] cupsdAuthorize: No authentication data provided.
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 1.1 Get-Jobs 1
D [07/Oct/2010:12:01:16 +0300] Get-Jobs ipp://localhost/printers/HP-LaserJet-P1005
D [07/Oct/2010:12:01:16 +0300] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/HP-LaserJet-P1005) from localhost
D [07/Oct/2010:12:01:16 +0300] cupsdSetBusyState: Not busy
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 POST / HTTP/1.1
D [07/Oct/2010:12:01:16 +0300] cupsdSetBusyState: Active clients
D [07/Oct/2010:12:01:16 +0300] cupsdAuthorize: No authentication data provided.
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [07/Oct/2010:12:01:16 +0300] Get-Printer-Attributes ipp://localhost/printers/HP-LaserJet-P1005
D [07/Oct/2010:12:01:16 +0300] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP-LaserJet-P1005) from localhost
D [07/Oct/2010:12:01:16 +0300] cupsdSetBusyState: Not busy
D [07/Oct/2010:12:01:16 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:16 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 16 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 16 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 16
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdAcceptClient: 16 from localhost (Domain)
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:18 +0300] cupsdReadClient: 16 WAITING Closing on EOF
D [07/Oct/2010:12:01:18 +0300] cupsdCloseClient: 16
D [07/Oct/2010:12:01:19 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:19 +0300] cupsdReadClient: 15 POST / HTTP/1.1
D [07/Oct/2010:12:01:19 +0300] cupsdSetBusyState: Active clients
D [07/Oct/2010:12:01:19 +0300] cupsdAuthorize: No authentication data provided.
D [07/Oct/2010:12:01:19 +0300] cupsdReadClient: 15 1.1 Get-Notifications 1
D [07/Oct/2010:12:01:19 +0300] Get-Notifications /
D [07/Oct/2010:12:01:19 +0300] cupsdIsAuthorized: requesting-user-name="aboud"
D [07/Oct/2010:12:01:19 +0300] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [07/Oct/2010:12:01:19 +0300] cupsdSetBusyState: Not busy
D [07/Oct/2010:12:01:19 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:19 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:20 +0300] cupsdAcceptClient: 15 from localhost (Domain)
D [07/Oct/2010:12:01:20 +0300] cupsdReadClient: 15 WAITING Closing on EOF
D [07/Oct/2010:12:01:20 +0300] cupsdCloseClient: 15
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "lo" = localhost:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "eth0" = 192.168.1.100:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "vmnet1" = 192.168.241.1:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "vmnet8" = 192.168.238.1:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "lo" = localhost:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "eth0" = fe80::92e6:baff:feb9:6c93%eth0:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "vmnet1" = fe80::250:56ff:fec0:1%vmnet1:631
D [07/Oct/2010:12:01:35 +0300] cupsdNetIFUpdate: "vmnet8" = fe80::250:56ff:fec0:8%vmnet8:631
D [07/Oct/2010:12:01:35 +0300] Report: clients=2
D [07/Oct/2010:12:01:35 +0300] Report: jobs=105
D [07/Oct/2010:12:01:35 +0300] Report: jobs-active=0
D [07/Oct/2010:12:01:35 +0300] Report: printers=2
D [07/Oct/2010:12:01:35 +0300] Report: printers-implicit=0
D [07/Oct/2010:12:01:35 +0300] Report: stringpool-string-count=616
D [07/Oct/2010:12:01:35 +0300] Report: stringpool-alloc-bytes=6872
D [07/Oct/2010:12:01:35 +0300] Report: stringpool-total-bytes=11128
D [07/Oct/2010:12:01:43 +0300] cupsdReadClient: 14 WAITING Closing on EOF
D [07/Oct/2010:12:01:43 +0300] cupsdCloseClient: 14
D [07/Oct/2010:12:01:48 +0300] cupsdAcceptClient: 14 from localhost:631 (IPv4)
D [07/Oct/2010:12:01:48 +0300] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1
D [07/Oct/2010:12:01:48 +0300] cupsdSetBusyState: Active clients
D [07/Oct/2010:12:01:48 +0300] cupsdAuthorize: No authentication data provided.


```

---

### Post by aboud on 2010-10-08
Bump for solution !

---

### Post by aboud on 2010-10-10
wired problem, ah!

---

