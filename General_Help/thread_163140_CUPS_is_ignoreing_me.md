---
title: "CUPS is ignoreing me"
date: 2006-04-20
forum: General Help
---

### Post by _axiom_ on 2006-04-20
I am running Kubuntu Breezy and have an EpsonStylus Photo R300 printer.  It *was* working fine.  Untill I used KJobViewer to delete a printout that was in progress.  It has not worked since then.  I deleted all the jobs I saw there, but when ever I send new jobs, they are always queued, and never print.

First I checked my loopback.


```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2127724 (2.0 MiB)  TX bytes:2127724 (2.0 MiB)
```


Then I tried restarting the CUPS server
```

axiom@axiom:/etc/init.d$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

```

I went to the system setting and tried to fiddle with the printers, but it woudn't work, it said it was "Unable to find a runnin CUPS server"

I tried to make sure it was running.
```

axiom@axiom:/etc/init.d$ ps ax | grep cups
10966 ?        Ss     0:00 /usr/sbin/cupsd -F
10986 pts/2    R+     0:00 grep cups

```

I telneted into it to be sure.
```

axiom@axiom:/etc/init.d$ telnet 127.0.0.1 631
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
```

I checked that it was plugged in.
```

axiom@axiom:/etc/init.d$  lsusb
Bus 004 Device 005: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 004 Device 003: ID 04b8:0803 Seiko Epson Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000


```


I thought maybe there is a ghost printer, so I tried stopping in and telnetting
```

axiom@axiom:/etc/init.d$     sudo /etc/init.d/cupsys stop
 * Stopping Common Unix Printing System: cupsd                           [ ok ]
axiom@axiom:/etc/init.d$ telnet 127.0.0.1 631
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```

I started it again, but I don't know what do do next.
```

axiom@axiom:/etc/init.d$ sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                           [ ok ]
axiom@axiom:/etc/init.d$  

```

I tried accessing CUPS from 127.0.0.1:631, but of course it wants you to log in as root, and we can't do that on ubuntu.  

How can I fix this?

---

### Post by NoNo_231 on 2006-04-20
I cannot help you on your problem, but about accessing cups via 127.0.0.1:631 did you try to use your username and password? I did so and didn't deny access to me. I installed a new printer, and did administration jobs. I hope this could help.

---

### Post by _axiom_ on 2006-04-20
Yeah, I tried that, and it tells me that I am "Unauthorized".

---

### Post by Prospero2006 on 2006-04-20
On my Slackware box, cups keeps a log in /var/log/cups

Check that for output.

Pros

---

### Post by _axiom_ on 2006-04-20
I can see where I tried to log into CUPS (on localhost and it failed).

I also see where jobs have been deleted, and that new jobs are always "queued", but I don't see what is causing it not to ever print.

```
axiom@axiom:~$ cat /var/log/cups/error_log
I [20/Apr/2006:08:47:17 -0400] Listening to 7f000001:631
I [20/Apr/2006:08:47:17 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:08:47:17 -0400] Configured for up to 100 clients.
I [20/Apr/2006:08:47:17 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:08:47:17 -0400] Full reload is required.
I [20/Apr/2006:08:47:18 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:08:47:18 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:08:47:18 -0400] Full reload complete.
I [20/Apr/2006:08:50:19 -0400] Job 353 was cancelled by 'root'.
I [20/Apr/2006:08:50:20 -0400] Job 354 was cancelled by 'root'.
I [20/Apr/2006:08:50:31 -0400] Adding start banner page "none" to job 355.
I [20/Apr/2006:08:50:31 -0400] Adding end banner page "none" to job 355.
I [20/Apr/2006:08:50:31 -0400] Job 355 queued on 'EPSONStylusPhotoR300' by 'axiom'.
I [20/Apr/2006:08:50:41 -0400] Job 355 was cancelled by 'root'.
I [20/Apr/2006:08:50:58 -0400] Adding start banner page "none" to job 356.
I [20/Apr/2006:08:50:58 -0400] Adding end banner page "none" to job 356.
I [20/Apr/2006:08:50:58 -0400] Job 356 queued on 'EPSONStylusPhotoR300' by 'axiom'.
I [20/Apr/2006:08:51:40 -0400] Job 356 was cancelled by 'root'.
I [20/Apr/2006:08:52:23 -0400] Scheduler shutting down normally.
I [20/Apr/2006:08:54:35 -0400] Listening to 7f000001:631
I [20/Apr/2006:08:54:35 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:08:54:35 -0400] Configured for up to 100 clients.
I [20/Apr/2006:08:54:35 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:08:54:35 -0400] Full reload is required.
I [20/Apr/2006:08:54:37 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:08:54:42 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:08:54:46 -0400] Full reload complete.
I [20/Apr/2006:08:56:57 -0400] Adding start banner page "none" to job 357.
I [20/Apr/2006:08:56:57 -0400] Adding end banner page "none" to job 357.
I [20/Apr/2006:08:56:57 -0400] Job 357 queued on 'EPSONStylusPhotoR300' by 'axiom'.
I [20/Apr/2006:09:08:14 -0400] Installing config file "/etc/cups/cupsd.conf"...
I [20/Apr/2006:09:47:35 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:09:47:35 -0400] Configured for up to 100 clients.
I [20/Apr/2006:09:47:35 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:09:47:35 -0400] Full reload is required.
I [20/Apr/2006:09:47:35 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:09:47:36 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:09:47:36 -0400] Full reload complete.
I [20/Apr/2006:09:47:48 -0400] Adding start banner page "none" to job 358.
I [20/Apr/2006:09:47:48 -0400] Adding end banner page "none" to job 358.
I [20/Apr/2006:09:47:48 -0400] Job 358 queued on 'EPSONStylusPhotoR300' by 'axiom'.
I [20/Apr/2006:09:48:00 -0400] Job 357 was cancelled by 'root'.
I [20/Apr/2006:09:48:02 -0400] Job 358 was cancelled by 'root'.
I [20/Apr/2006:09:48:07 -0400] Scheduler shutting down normally.
I [20/Apr/2006:09:48:07 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:09:48:07 -0400] Configured for up to 100 clients.
I [20/Apr/2006:09:48:07 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:09:48:07 -0400] Full reload is required.
I [20/Apr/2006:09:48:08 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:09:48:08 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:09:48:08 -0400] Full reload complete.
I [20/Apr/2006:09:48:37 -0400] Adding start banner page "none" to job 357.
I [20/Apr/2006:09:48:37 -0400] Adding end banner page "none" to job 357.
I [20/Apr/2006:09:48:37 -0400] Job 357 queued on 'EPSONStylusPhotoR300' by 'axiom'.
I [20/Apr/2006:09:52:24 -0400] Scheduler shutting down normally.
I [20/Apr/2006:09:52:24 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:09:52:24 -0400] Configured for up to 100 clients.
I [20/Apr/2006:09:52:24 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:09:52:24 -0400] Full reload is required.
I [20/Apr/2006:09:52:24 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:09:52:24 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:09:52:25 -0400] Full reload complete.
I [20/Apr/2006:09:56:27 -0400] Job 357 was cancelled by 'root'.
I [20/Apr/2006:09:58:32 -0400] Scheduler shutting down normally.
I [20/Apr/2006:09:59:12 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [20/Apr/2006:09:59:12 -0400] Configured for up to 100 clients.
I [20/Apr/2006:09:59:12 -0400] Allowing up to 100 client connections per host.
I [20/Apr/2006:09:59:12 -0400] Full reload is required.
I [20/Apr/2006:09:59:12 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [20/Apr/2006:09:59:12 -0400] LoadPPDs: No new or changed PPDs...
I [20/Apr/2006:09:59:13 -0400] Full reload complete.
I [20/Apr/2006:09:59:42 -0400] Adding start banner page "none" to job 357.
I [20/Apr/2006:09:59:42 -0400] Adding end banner page "none" to job 357.
I [20/Apr/2006:09:59:42 -0400] Job 357 queued on 'EPSONStylusPhotoR300' by 'axiom'.
E [20/Apr/2006:10:00:37 -0400] IsAuthorized: pam_authenticate() returned 7 (Authentication failure)!
E [20/Apr/2006:10:00:47 -0400] IsAuthorized: pam_authenticate() returned 7 (Authentication failure)!
I [20/Apr/2006:10:00:55 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=11259)
I [20/Apr/2006:10:01:00 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=11261)
I [20/Apr/2006:10:01:00 -0400] Adding start banner page "none" to job 358.
I [20/Apr/2006:10:01:00 -0400] Adding end banner page "none" to job 358.
I [20/Apr/2006:10:01:00 -0400] Job 358 queued on 'EPSONStylusPhotoR300' by ''.
E [20/Apr/2006:13:54:57 -0400] IsAuthorized: pam_authenticate() returned 7 (Authentication failure)!
E [20/Apr/2006:13:55:06 -0400] IsAuthorized: pam_authenticate() returned 7 (Authentication failure)!

```

---

