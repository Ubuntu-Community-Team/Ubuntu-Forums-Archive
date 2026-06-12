---
title: "Printer Stopped working after CUPS update a few days ago"
date: 2010-03-06
forum: General Help
---

### Post by lildigiman on 2010-03-06
My printer no longer prints anything with exception to the TestPrint page.
Any other job I give it, it says is "completed" in the queue, though nothing has printed. Installed cups again, after a complete removal. No change. 

Please help! Any help is greatly appreciated!

Heres what troubleshooting gave me: 

```

D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Mar/2010:07:26:01 -0500] Get-Jobs ipp://localhost/printers/
D [06/Mar/2010:07:26:01 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1
D [06/Mar/2010:07:26:01 -0500] Get-Jobs ipp://localhost/printers/
D [06/Mar/2010:07:26:01 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:01 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:01 -0500] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [06/Mar/2010:07:26:01 -0500] Create-Printer-Subscription /
D [06/Mar/2010:07:26:01 -0500] cupsdCreateSubscription(con=0x21acf120(12), uri="/")
D [06/Mar/2010:07:26:01 -0500] pullmethod="ippget"
D [06/Mar/2010:07:26:01 -0500] notify-lease-duration=86400
D [06/Mar/2010:07:26:01 -0500] notify-time-interval=0
D [06/Mar/2010:07:26:01 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [06/Mar/2010:07:26:01 -0500] Added subscription 60 for server
D [06/Mar/2010:07:26:01 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:01 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [06/Mar/2010:07:26:01 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:02 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:02 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:02 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:02 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Mar/2010:07:26:02 -0500] Get-Notifications /
D [06/Mar/2010:07:26:02 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:02 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Mar/2010:07:26:02 -0500] cupsdSetBusyState: Dirty files
I [06/Mar/2010:07:26:29 -0500] Generating printcap /var/run/cups/printcap...
I [06/Mar/2010:07:26:29 -0500] Saving subscriptions.conf...
D [06/Mar/2010:07:26:29 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:30 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:30 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:30 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:30 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:30 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:30 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:30 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:30 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:30 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 14 GET /printers/EPSON-Stylus-COLOR-980.ppd HTTP/1.1
D [06/Mar/2010:07:26:30 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:30 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:30 -0500] cupsdAcceptClient: 16 from localhost (Domain)
D [06/Mar/2010:07:26:30 -0500] cupsdAcceptClient: 17 from localhost (Domain)
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 16 WAITING Closing on EOF
D [06/Mar/2010:07:26:30 -0500] cupsdCloseClient: 16
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 17 POST / HTTP/1.1
D [06/Mar/2010:07:26:30 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:30 -0500] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:30 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:30 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:31 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:32 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:32 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:32 -0500] cupsdReadClient: 17 WAITING Closing on EOF
D [06/Mar/2010:07:26:32 -0500] cupsdCloseClient: 17
D [06/Mar/2010:07:26:32 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:32 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:32 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:32 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:32 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:32 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:32 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:32 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:32 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:32 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:32 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:33 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:33 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:33 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:33 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:33 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:33 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:33 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:33 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:33 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:33 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:33 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:33 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:33 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:33 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:33 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:34 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:34 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:34 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:34 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:34 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:34 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:34 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:34 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:34 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:34 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:34 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:34 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:34 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:34 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:35 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:35 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:35 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:35 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:35 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:35 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:35 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:35 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:35 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:35 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:35 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:35 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:35 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Not busy
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:35 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:35 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 14 POST /printers/EPSON-Stylus-COLOR-980 HTTP/1.1
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Active clients
D [06/Mar/2010:07:26:35 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:35 -0500] cupsdReadClient: 14 1.1 Print-Job 1
D [06/Mar/2010:07:26:35 -0500] Print-Job ipp://localhost:631/printers/EPSON-Stylus-COLOR-980
D [06/Mar/2010:07:26:35 -0500] [Job ???] Auto-typing file...
I [06/Mar/2010:07:26:35 -0500] [Job ???] Request file type is application/pdf.
D [06/Mar/2010:07:26:35 -0500] cupsdMarkDirty(----J-)
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:35 -0500] add_job: requesting-user-name="curtis"
I [06/Mar/2010:07:26:35 -0500] [Job 1] Adding start banner page "none".
D [06/Mar/2010:07:26:35 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:35 -0500] cupsdMarkDirty(----J-)
I [06/Mar/2010:07:26:35 -0500] [Job 1] Adding end banner page "none".
I [06/Mar/2010:07:26:35 -0500] [Job 1] File of type application/pdf queued by "curtis".
D [06/Mar/2010:07:26:35 -0500] [Job 1] hold_until=0
I [06/Mar/2010:07:26:35 -0500] [Job 1] Queued on "EPSON-Stylus-COLOR-980" by "curtis".
D [06/Mar/2010:07:26:35 -0500] cupsdMarkDirty(----J-)
D [06/Mar/2010:07:26:35 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:35 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:35 -0500] [Job 1] job-sheets=none,none
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[0]="EPSON-Stylus-COLOR-980"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[1]="1"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[2]="curtis"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[3]="newegg.pdf"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[4]="1"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[5]="StpFineCyanBalance=None StpHGray1Value=None ColorModel=RGB number-up=1 StpHGray3Scale=None StpFineHGray3Value=None StpDropSize2=None StpFineBlackGamma=None StpFineHGray5Scale=None MediaType=Plain StpFineBlackTrans=None StpHGray3Trans=None StpDropSize1=None StpFineContrast=None StpDropSize3=None StpSaturation=None StpGamma=None StpFineHGray5Trans=None StpHGray4Value=None StpContrast=None StpGray1Value=None StpFineGray2Value=None StpInkSet=None StpFineMagentaBalance=None StpBrightness=None StpFineMagentaDensity=None StpFineMagentaGamma=None StpHGray1Scale=None StpiShrinkOutput=Shrink StpFineBlackDensity=None StpFineHGray1Value=None StpFineHGray3Scale=None StpInkLimit=None StpHGray1Trans=None StpInkType=None StpFineDropSize1=None StpFineDropSize2=None StpFineDropSize3=None StpColorPrecision=Normal StpHGray2Value=None StpCyanGamma=None StpFineHGray4Value=None StpHGray4Scale=None StpMagentaGamma=None StpHGray4Trans=None Resolution=361x360dpi StpFineDensity=None StpQuality=Standard StpFineHGray3Trans=None StpFineGCRLower=None StpDensity=None StpFineHGray1Scale=None StpImageType=TextGraphics StpHGray5Value=None StpFineGCRUpper=None StpGray2Value=None StpBlackTrans=None StpBlackGamma=None StpFineCyanGamma=None StpFineYellowDensity=None StpFineGray3Value=None StpYellowDensity=None StpFineHGray1Trans=None StpHGray2Scale=None StpCyanDensity=None StpColorCorrection=None StpDitherAlgorithm=None StpFineHGray4Scale=None StpHGray2Trans=None StpFineHGray2Value=None StpYellowGamma=None PageSize=Letter StpMagentaDensity=None StpGCRLower=None StpBlackDensity=None StpFeedSequence=None StpFineSaturation=None StpCyanBalance=None StpFineHGray4Trans=None StpFineBrightness=None StpHGray3Value=None StpFineYellowBalance=None StpFineGray1Value=None StpFineHGray5Value=None StpHGray5Scale=None StpGCRUpper=None StpHGray5Trans=None StpYellowBalance=None StpPrintingDirection=None StpWeave=None StpFineInkLimit=None StpFineCyanDensity=None StpFineHGray2Scale=None StpBandEnhancement=None StpFineHGray2Trans=None StpFineYellowGamma=None StpMagentaBalance=None noStpLinearContrast StpFineGamma=None StpGray3Value=None job-uuid=urn:uuid:996f285f-ea44-3a31-54da-deff299e8962 job-originating-host-name=localhost"
D [06/Mar/2010:07:26:35 -0500] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[10]="SERVER_ADMIN=root@CMDU02"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.1"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[13]="TZ=America/New_York"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[14]="USER=root"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[17]="IPP_PORT=631"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[18]="CHARSET=utf-8"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[19]="LANG=en_US.UTF-8"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[20]="PPD=/etc/cups/ppd/EPSON-Stylus-COLOR-980.ppd"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[21]="RIP_MAX_CACHE=256449k"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[22]="CONTENT_TYPE=application/pdf"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[23]="DEVICE_URI=usb://EPSON/Stylus%20COLOR%20980"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[24]="PRINTER_INFO=EPSON Stylus COLOR 980"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[25]="PRINTER_LOCATION=CMDU02"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[26]="PRINTER=EPSON-Stylus-COLOR-980"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[27]="CUPS_FILETYPE=document"
D [06/Mar/2010:07:26:35 -0500] [Job 1] envp[28]="FINAL_CONTENT_TYPE=printer/EPSON-Stylus-COLOR-980"
I [06/Mar/2010:07:26:35 -0500] [Job 1] Started filter /usr/lib/cups/filter/pdftopdf (PID 8304)
I [06/Mar/2010:07:26:35 -0500] [Job 1] Started filter /usr/lib/cups/filter/pdftoraster (PID 8305)
I [06/Mar/2010:07:26:36 -0500] [Job 1] Started filter /usr/lib/cups/filter/rastertogutenprint.5.2 (PID 8306)
I [06/Mar/2010:07:26:36 -0500] [Job 1] Started backend /usr/lib/cups/backend/usb (PID 8307)
D [06/Mar/2010:07:26:36 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/EPSON-Stylus-COLOR-980) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] [Job 1] STATE: +connecting-to-device
D [06/Mar/2010:07:26:36 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:36 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:36 -0500] PID 8304 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [06/Mar/2010:07:26:36 -0500] [Job 1] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -sMediaType=Plain -r720x360 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=1 -dcupsRowFeed=4 -scupsPageSizeName=Letter -c -f -_
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[10]="SERVER_ADMIN=root@CMDU02"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.1"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[12]="TZ=America/New_York"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[13]="USER=root"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[16]="IPP_PORT=631"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[17]="CHARSET=utf-8"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[18]="LANG=en_US.UTF-8"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[19]="PPD=/etc/cups/ppd/EPSON-Stylus-COLOR-980.ppd"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[20]="RIP_MAX_CACHE=256449k"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[21]="CONTENT_TYPE=application/pdf"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20COLOR%20980"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[23]="PRINTER_INFO=EPSON Stylus COLOR 980"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[24]="PRINTER_LOCATION=CMDU02"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[25]="PRINTER=EPSON-Stylus-COLOR-980"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[26]="CUPS_FILETYPE=document"
D [06/Mar/2010:07:26:36 -0500] [Job 1] envp[27]="FINAL_CONTENT_TYPE=printer/EPSON-Stylus-COLOR-980"
D [06/Mar/2010:07:26:36 -0500] [Job 1] Printer using device file "/dev/usblp0"...
D [06/Mar/2010:07:26:36 -0500] [Job 1] STATE: -connecting-to-device
D [06/Mar/2010:07:26:36 -0500] [Job 1] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=1, side_cb=0xe40b30)
D [06/Mar/2010:07:26:36 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:36 -0500] PID 8305 (/usr/lib/cups/filter/pdftoraster) exited with no errors.
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint 5.2.4 Starting
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint command line: EPSON-Stylus-COLOR-980 '1' 'curtis' 'newegg.pdf' '1' <args>
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint using PPD file /etc/cups/ppd/EPSON-Stylus-COLOR-980.ppd
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option count is 102 (2204 bytes)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 0 ColorModel = RGB
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 1 job-originating-host-name = localhost
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 2 job-uuid = urn:uuid:996f285f-ea44-3a31-54da-deff299e8962
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 3 MediaType = Plain
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 4 number-up = 1
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 5 PageSize = Letter
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 6 Resolution = 361x360dpi
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 7 StpBandEnhancement = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 8 StpBlackDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 9 StpBlackGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 10 StpBlackTrans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 11 StpBrightness = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 12 StpColorCorrection = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 13 StpColorPrecision = Normal
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 14 StpContrast = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 15 StpCyanBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 16 StpCyanDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 17 StpCyanGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 18 StpDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 19 StpDitherAlgorithm = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 20 StpDropSize1 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 21 StpDropSize2 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 22 StpDropSize3 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 23 StpFeedSequence = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 24 StpFineBlackDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 25 StpFineBlackGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 26 StpFineBlackTrans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 27 StpFineBrightness = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 28 StpFineContrast = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 29 StpFineCyanBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 30 StpFineCyanDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 31 StpFineCyanGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 32 StpFineDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 33 StpFineDropSize1 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 34 StpFineDropSize2 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 35 StpFineDropSize3 = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 36 StpFineGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 37 StpFineGCRLower = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 38 StpFineGCRUpper = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 39 StpFineGray1Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 40 StpFineGray2Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 41 StpFineGray3Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 42 StpFineHGray1Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 43 StpFineHGray1Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 44 StpFineHGray1Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 45 StpFineHGray2Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 46 StpFineHGray2Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 47 StpFineHGray2Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 48 StpFineHGray3Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 49 StpFineHGray3Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 50 StpFineHGray3Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 51 StpFineHGray4Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 52 StpFineHGray4Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 53 StpFineHGray4Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 54 StpFineHGray5Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 55 StpFineHGray5Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 56 StpFineHGray5Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 57 StpFineInkLimit = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 58 StpFineMagentaBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 59 StpFineMagentaDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 60 StpFineMagentaGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 61 StpFineSaturation = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 62 StpFineYellowBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 63 StpFineYellowDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 64 StpFineYellowGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 65 StpGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 66 StpGCRLower = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 67 StpGCRUpper = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 68 StpGray1Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 69 StpGray2Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 70 StpGray3Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 71 StpHGray1Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 72 StpHGray1Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 73 StpHGray1Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 74 StpHGray2Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 75 StpHGray2Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 76 StpHGray2Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 77 StpHGray3Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 78 StpHGray3Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 79 StpHGray3Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 80 StpHGray4Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 81 StpHGray4Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 82 StpHGray4Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 83 StpHGray5Scale = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 84 StpHGray5Trans = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 85 StpHGray5Value = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 86 StpImageType = TextGraphics
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 87 StpInkLimit = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 88 StpInkSet = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 89 StpInkType = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 90 StpiShrinkOutput = Shrink
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 91 StpLinearContrast = false
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 92 StpMagentaBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 93 StpMagentaDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 94 StpMagentaGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 95 StpPrintingDirection = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 96 StpQuality = Standard
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 97 StpSaturation = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 98 StpWeave = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 99 StpYellowBalance = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 100 StpYellowDensity = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: CUPS option 101 StpYellowGamma = None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: Driver Epson Stylus Color 980
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: Using fd 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: Set options:
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string Quality to Standard
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string Quality to Standard
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PageSize to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting MediaType to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting InputSlot to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting Duplex to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CDInnerRadius to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CDOuterDiameter to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CDInnerDiameter to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CDXAdjustment to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CDYAdjustment to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting Resolution to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string InkType to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string InkType to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting UseGloss to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string InkSet to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string InkSet to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string PrintingDirection to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string PrintingDirection to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting FullBleed to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string Weave to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string Weave to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting OutputOrder to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting AlignmentPasses to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting AlignmentChoices to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting InkChange to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting AlternateAlignmentPasses to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting AlternateAlignmentChoices to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting SupportsPacketMode to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting InterchangeableInk to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting InkChannels to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting RawChannelNames to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting ChannelNames to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PrintingMode to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting RawChannels to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CyanHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting MagentaHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting YellowHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting BlueHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting OrangeHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting RedHueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_hres to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_vres to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_hres to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_vres to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_black_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_fast_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_black_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_fast_nozzles to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_nozzle_start to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_black_nozzle_start to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_fast_nozzle_start to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_nozzle_separation to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_black_nozzle_separation to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_fast_nozzle_separation to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_separation_rows to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_paper_width to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_paper_height to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_paper_width to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_paper_height to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_imageable_width to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_imageable_height to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_extra_feed to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_pseudo_separation_rows to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_base_separation to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_resolution_scale to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_initial_vertical_offset to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_black_initial_vertical_offset to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_max_black_resolution to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_zero_margin_offset to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_extra_720dpi_separation to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_micro_left_margin to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_min_horizontal_position_alignment to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_base_horizontal_position_alignment to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_bidirectional_upper_limit to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_physical_channels to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_left_margin to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_right_margin to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_top_margin to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_bottom_margin to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_ink_type to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_bits to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_base_res to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_alignment_passes to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_alignment_choices to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_alternate_alignment_passes to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_alternate_alignment_choices to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_cd_x_offset to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_cd_y_offset to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_cd_page_width to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_cd_page_height to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_paper_extra_bottom to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_preinit_sequence to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_preinit_remote_sequence to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_postinit_remote_sequence to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting escp2_vertical_borderless_sequence to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 1, depth = 1
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 3, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 1, cupsBitsPerColor = 1
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 1, dither_grays = 2
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 0, dither_colors = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] Updating PageSize to [612 792]...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting initial media size, [612 792] = 6120x3960 pixels...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting MediaType to "Plain"...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting cupsBitsPerColor to 8...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting cupsColorOrder to 0...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting cupsColorSpace to 1...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting cupsRowFeed to 4...
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting cupsPageSizeName to "Letter"...
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 3, depth = 24
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 1, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 0, dither_grays = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 255, dither_colors = 256
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting initial media size, [612 792] = 6120x3960 pixels...
I [06/Mar/2010:07:26:36 -0500] [Job 1] Processing page 1...
D [06/Mar/2010:07:26:36 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:36 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 3, depth = 24
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 1, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 0, dither_grays = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 255, dither_colors = 256
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting BandEnhancement to 'None'
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PaperThickness to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting VacuumIntensity to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting FeedSequence to 'None'
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PrintMethod to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PlatenGap to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting FeedAdjustment to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string ColorCorrection to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string ColorCorrection to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting ChannelBitDepth to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting InputImageType to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting STPIOutputType to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting STPIRawChannels to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting SimpleGamma to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set bool LinearContrast to false (0)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting LUTDumpFile to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CyanCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting MagentaCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting YellowCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting BlackCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting RedCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting GreenCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting BlueCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting WhiteCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting HueMap to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting SatMap to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting LumMap to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting GCRCurve to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh0 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh1 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh2 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh3 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh4 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh5 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh6 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh7 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh8 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh9 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh10 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh11 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh12 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh13 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh14 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh15 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh16 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh17 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh18 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh19 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh20 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh21 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh22 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh23 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh24 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh25 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh26 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh27 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh28 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh29 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh30 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting CurveCh31 to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string DitherAlgorithm to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string DitherAlgorithm to None
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set string ImageType to TextGraphics
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Set special string ImageType to TextGraphics
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting JobMode to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint:   Not setting PageNumber to (null)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Gutenprint: End options
D [06/Mar/2010:07:26:36 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting LeadingEdge to 0...
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 3, depth = 24
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 1, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 0, dither_grays = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 255, dither_colors = 256
D [06/Mar/2010:07:26:36 -0500] [Job 1] Updating PageSize to [612 792]...
D [06/Mar/2010:07:26:36 -0500] [Job 1] size = Letter
D [06/Mar/2010:07:26:36 -0500] [Job 1] margins[] = [ 0.125000 0.125000 0.125000 0.000000 ]
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 Get-Notifications 1
D [06/Mar/2010:07:26:36 -0500] Get-Notifications /
D [06/Mar/2010:07:26:36 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 WAITING Closing on EOF
D [06/Mar/2010:07:26:36 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:36 -0500] cupsdAcceptClient: 14 from localhost (Domain)
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Mar/2010:07:26:36 -0500] Get-Notifications /
D [06/Mar/2010:07:26:36 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Classes
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Default 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Default
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Classes
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Default 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Default
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Classes
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Default 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Default
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Classes
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [06/Mar/2010:07:26:36 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:36 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Default 1
D [06/Mar/2010:07:26:36 -0500] CUPS-Get-Default
D [06/Mar/2010:07:26:36 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [06/Mar/2010:07:26:36 -0500] cupsdSetBusyState: Printing jobs and dirty files
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting LeadingEdge to 0...
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 3, depth = 24
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 1, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 0, dither_grays = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 255, dither_colors = 256
D [06/Mar/2010:07:26:36 -0500] [Job 1] Setting LeadingEdge to 0...
D [06/Mar/2010:07:26:36 -0500] [Job 1] num_components = 3, depth = 24
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsColorSpace = 1, cupsColorOrder = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] cupsBitsPerPixel = 24, cupsBitsPerColor = 8
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_gray = 0, dither_grays = 0
D [06/Mar/2010:07:26:36 -0500] [Job 1] max_color = 255, dither_colors = 256
D [06/Mar/2010:07:26:36 -0500] [Job 1] Updating PageSize to [612 792]...
D [06/Mar/2010:07:26:36 -0500] [Job 1] size = Letter
D [06/Mar/2010:07:26:36 -0500] [Job 1] margins[] = [ 0.125000 0.125000 0.125000 0.000000 ]
D [06/Mar/2010:07:26:37 -0500] [Job 1] Error: /unknownerror in --run--
D [06/Mar/2010:07:26:37 -0500] [Job 1] Operand stack:
D [06/Mar/2010:07:26:37 -0500] [Job 1] (/tmp/gs_CTchoD)   --nostringval--   --dict:7/16(L)--   0.0   -0.0
D [06/Mar/2010:07:26:37 -0500] [Job 1] Execution stack:
D [06/Mar/2010:07:26:37 -0500] [Job 1] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1862   1   3   %oparray_pop   1861   1   3   %oparray_pop   1845   1   3   %oparray_pop   --nostringval--   --nostringval--   --nostringval--   2   1   2   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   %array_continue   --nostringval--   false   1   %stopped_push   --nostringval--   %loop_continue   --nostringval--   --nostringval--
D [06/Mar/2010:07:26:37 -0500] [Job 1] Dictionary stack:
D [06/Mar/2010:07:26:37 -0500] [Job 1] --dict:1161/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:106/127(ro)(G)--   --dict:285/300(ro)(G)--   --dict:22/25(L)--   --dict:4/6(L)--   --dict:21/40(L)--   --dict:1/1(ro)(G)--   --dict:5/5(L)--
D [06/Mar/2010:07:26:37 -0500] [Job 1] Current allocation mode is local
D [06/Mar/2010:07:26:37 -0500] [Job 1] Last OS error: 2
D [06/Mar/2010:07:26:37 -0500] [Job 1] GPL Ghostscript 8.70: Unrecoverable error, exit code 1
D [06/Mar/2010:07:26:37 -0500] [Job 1] Gutenprint: About to start printing loop.
D [06/Mar/2010:07:26:37 -0500] [Job 1] Gutenprint: Printed total 0 bytes
D [06/Mar/2010:07:26:37 -0500] [Job 1] Gutenprint: Used 0.120 seconds user, 0.000 seconds system, 1.620 seconds elapsed
D [06/Mar/2010:07:26:37 -0500] PID 8306 (/usr/lib/cups/filter/rastertogutenprint.5.2) exited with no errors.
D [06/Mar/2010:07:26:37 -0500] PID 8307 (/usr/lib/cups/backend/usb) exited with no errors.
D [06/Mar/2010:07:26:37 -0500] cupsdMarkDirty(-----S)
I [06/Mar/2010:07:26:37 -0500] [Job 1] Job completed.
D [06/Mar/2010:07:26:37 -0500] cupsdMarkDirty(----J-)
D [06/Mar/2010:07:26:37 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:37 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 15 POST / HTTP/1.1
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 15 1.1 Get-Notifications 1
D [06/Mar/2010:07:26:37 -0500] Get-Notifications /
D [06/Mar/2010:07:26:37 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:37 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 15 WAITING Closing on EOF
D [06/Mar/2010:07:26:37 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1
D [06/Mar/2010:07:26:37 -0500] Get-Notifications /
D [06/Mar/2010:07:26:37 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:37 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1
D [06/Mar/2010:07:26:37 -0500] CUPS-Get-Printers
D [06/Mar/2010:07:26:37 -0500] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1
D [06/Mar/2010:07:26:37 -0500] CUPS-Get-Classes
D [06/Mar/2010:07:26:37 -0500] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 POST / HTTP/1.1
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:37 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:37 -0500] cupsdReadClient: 14 1.1 CUPS-Get-Default 1
D [06/Mar/2010:07:26:37 -0500] CUPS-Get-Default
D [06/Mar/2010:07:26:37 -0500] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [06/Mar/2010:07:26:37 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:38 -0500] [Job 1] Unloading...
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [06/Mar/2010:07:26:41 -0500] Get-Job-Attributes ipp://localhost/jobs/1
D [06/Mar/2010:07:26:41 -0500] [Job 1] Loading attributes...
D [06/Mar/2010:07:26:41 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/1) from localhost
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 12 POST / HTTP/1.1
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [06/Mar/2010:07:26:41 -0500] Cancel-Subscription /
D [06/Mar/2010:07:26:41 -0500] cupsdIsAuthorized: requesting-user-name="curtis"
D [06/Mar/2010:07:26:41 -0500] cupsdMarkDirty(-----S)
D [06/Mar/2010:07:26:41 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAuthorize: No authentication data provided.
D [06/Mar/2010:07:26:41 -0500] cupsdIsAuthorized: username=""
D [06/Mar/2010:07:26:41 -0500] cupsdSendHeader: 15 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [06/Mar/2010:07:26:41 -0500] cupsdCloseClient: 15
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAcceptClient: 15 from localhost (Domain)
D [06/Mar/2010:07:26:41 -0500] cupsdReadClient: 15 PUT /admin/conf/cupsd.conf HTTP/1.1
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Active clients and dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdAuthorize: Authorized as curtis using PeerCred
D [06/Mar/2010:07:26:41 -0500] cupsdIsAuthorized: username="curtis"
I [06/Mar/2010:07:26:41 -0500] Installing config file "/etc/cups/cupsd.conf"...
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Dirty files
D [06/Mar/2010:07:26:41 -0500] cupsdCloseClient: 12
D [06/Mar/2010:07:26:41 -0500] cupsdCloseClient: 14
D [06/Mar/2010:07:26:41 -0500] cupsdCloseClient: 15
I [06/Mar/2010:07:26:41 -0500] Saving job cache file "/var/cache/cups/job.cache"...
I [06/Mar/2010:07:26:41 -0500] Saving subscriptions.conf...
D [06/Mar/2010:07:26:41 -0500] cupsdSetBusyState: Not busy
I [06/Mar/2010:07:26:41 -0500] cupsdDefaultRIPCacheSize: 256449k
E [06/Mar/2010:07:27:15 -0500] cupsdReadClient: 16 IPP Read Error!

```

---

### Post by checkit on 2010-03-06
I'm having the same problem on Intrepid.  I found this bug report that looks like it might be related:

*Regression: PDF and Postscript files stopped printing after security update 1.4.1-5ubuntu2.4*
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/532009](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/532009)

---

### Post by lildigiman on 2010-03-06
> **checkit said:**
> I'm having the same problem on Intrepid.  I found this bug report that looks like it might be related:

*Regression: PDF and Postscript files stopped printing after security update 1.4.1-5ubuntu2.4*
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/532009](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/532009)

Hey thanks for the response, Maybe this is related.

---

