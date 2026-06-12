---
title: "Printer sharing - running in ever decreasing circles!"
date: 2010-03-28
forum: General Help
---

### Post by DaveInPhx on 2010-03-28
... and in serious danger of disappearing up my own exhaust pipe!

Scenario : Local network machines on a class C non-routable network (192.168.0.x/16). Print server is running Karmic and has a USB printer direct connected.
Other machines on the network are another Karmic box, a W2K machine and a Vista machine.

Steps taken:

[LIST=1]
[*]Installed the printer on the print server by installing python-qt4 and then running sudo hp-setup. The printer works just fine on the local machine!
[*]Followed some of the tutorials here and set up sharing using the [http://printserver:631/printers](http://printserver:631/printers) route.  That worked to a point, localhost and each of the other machines could get to the webpage showing the printer info, but none could connect to the printer.  This includes the other Ubuntu box which couldn't even see the shared printer!
[*]Installed samba on the print server and configured it following yet another tutorial. result is that W2K managed to connect to the printer and can print a test page, but any other print job sent to it results in only a blank sheet of paper!
[/LIST]
Using the port 631 route, I can connect to the server, check the printer status etc, but cannot connect to actually print anything.  With the samba install, I can connect to the shared files on the server, and even to the printer.  A W2K printer test page prints perfectly, but a simple text file in notepad results in a blank page being ejected.  

The printer makes the appropriate noises (deskjet) but doesn't actually print anything.  I tried swapping fonts between truetype and system fonts to see if that made a difference, but get the same results.

I am now into the 8th hour trying to get this working - any help would be greatly appreciated!!

---

### Post by s_ø on 2010-03-28
You got the printer working on your server, right?
What do you see on [http://localhost:631/printers](http://localhost:631/printers) ?

---

### Post by DaveInPhx on 2010-03-28
I can access the full admin page from any of my machines, and even make changes to the setup for the printer. 

From localhost on the server itself, it displays Cups 1.4.1 and gives the menu options (on the home tab). Going to localhost:631/printers shows the printer as a shortcut under the "queue name" column, with a status of "idle - ready to print"

I get exactly the same view connecting to the same page from this (ubuntu 9.10) machine, across the network

---

### Post by s_ø on 2010-03-28
Click on the link to the printer.Does it say 'Shared' next to idle?
Otherwise select 'Modify printer' and tick shared

---

### Post by DaveInPhx on 2010-03-28
It says "[deskjet_3500]("http://192.168.0.104:631/printers/deskjet_3500") (Idle, Accepting Jobs,  Shared, Server Default)" (sorry, had to take some time off to sleep!)

---

### Post by DaveInPhx on 2010-03-28
OK, I've been chasing my tail around again on this one, here's what I've tried so far:

Edited the cups config file, setting loglevel to info
Edited the smb.conf
managed to connect from the other linux box to print a text page
rebooted the host box, now I can't print again
checked the log and found the following: ```
I [17:31:32] Listening to 0.0.0.0:631 (IPv4)
I [17:31:32] Listening to :::631 (IPv6)
I [17:31:32] Listening to /var/run/cups/cups.sock (Domain)
I [17:31:32] Remote access is enabled.
I [17:31:32] Loaded configuration file "/etc/cups/cupsd.conf"
I [17:31:32] Using default TempDir of /var/spool/cups/tmp...
I [17:31:32] Configured for up to 100 clients.
I [17:31:32] Allowing up to 100 client connections per host.
I [17:31:32] Using policy "default" as the default!
I [17:31:32] Full reload is required.
I [17:31:32] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 38 types, 73 filters...
I [17:31:32] Generating printcap /var/run/cups/printcap...
I [17:31:32] Loading job cache file "/var/cache/cups/job.cache"...
I [17:31:32] Full reload complete.
I [17:31:32] Cleaning out old temporary files in "/var/spool/cups/tmp"...
E [17:31:32] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [17:31:32] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
I [17:31:32] Listening to 0.0.0.0:631 on fd 6...
I [17:31:32] Listening to :::631 on fd 7...
I [17:31:32] Listening to /var/run/cups/cups.sock on fd 8...
I [17:31:32] Resuming new connection processing...
I [17:31:32] Unknown LPDConfigFile scheme!
I [17:31:32] Unknown SMBConfigFile scheme!
I [17:31:33] Started "/usr/lib/cups/daemon/cups-deviced" (pid=2534)
I [17:36:01] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2900)
E [17:36:48] Missing printer-uri, job-uri, or ppd-name attribute!
E [17:36:48] Returning IPP client-error-bad-request for windows-ext (no URI) from 192.168.0.103
I [17:41:40] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2938)
I [17:41:46] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2940)
I [17:42:02] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=2941)
I [17:42:11] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=2942)
I [17:42:16] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=2943)
I [17:42:22] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2944)
I [17:42:23] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2945)
I [17:42:27] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2946)
I [17:42:35] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2949)
I [17:42:35] Started "/usr/lib/cups/daemon/cups-deviced" (pid=2950)
W [17:42:35] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
I [17:43:17] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2967)
I [17:43:28] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2968)
I [17:43:28] Started "/usr/lib/cups/daemon/cups-driverd" (pid=2969)
I [17:43:28] [cups-driverd] Read "/var/cache/cups/ppds.dat", 1326 PPDs...
I [17:43:28] [cups-driverd] No new or changed PPDs...
I [17:44:10] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2975)
I [17:44:10] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2976)
I [17:44:10] Setting deskjet_3500 device-uri to "hp:/usb/deskjet_3500?serial=TH44M1325776" (was "hp:/usb/deskjet_3500?serial=TH44M1325776".)
I [17:44:10] Setting deskjet_3500 printer-is-accepting-jobs to 1 (was 1.)
I [17:44:10] Setting deskjet_3500 printer-is-shared to 1 (was 1.)
I [17:44:10] Setting deskjet_3500 printer-state to 3 (was 3.)
I [17:44:11] Printer "deskjet_3500" modified by "bill".
I [17:44:16] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2978)
I [17:44:16] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2979)
I [17:44:42] Saving printers.conf...
I [17:44:42] Generating printcap /var/run/cups/printcap...
I [17:46:33] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=2980)
I [17:49:29] Saving job cache file "/var/cache/cups/job.cache"...
I [17:49:29] Saving subscriptions.conf...
I [17:51:59] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=3070)
E [17:52:33] Missing printer-uri, job-uri, or ppd-name attribute!
E [17:52:33] Returning IPP client-error-bad-request for windows-ext (no URI) from 192.168.0.103
```(note: lines were edited to remove the date and timezone offset to make it more readable)

---

### Post by DaveInPhx on 2010-03-29
I finally got the sharing to work, after a fashion. 

It took some digging around to find a very basic smb.conf which would work for print sharing only and with no security involved.  The remaining problem is that samba doesn't play nicely - once the computer is booted up I have to **sudo /etc/init.d/samba restart** to get it working properly.  I tried adjusting the startup position, but it didn't help.

Hey, at least I can print now, which is the main thing!

---

### Post by trevornetley on 2010-04-04
Very similar scenario here (except that I have two Windows xps one of which is a virtual machine within Virtual Box on Karmic). I have full networking set up and it is (relatively) easy to get the virtual xp to see and use the printers on the real one. I still am not quite sure what sequence of steps finally resulted in getting a list of Ubuntu attached printers up on both xps, but the final step was using the 'run' box on Windows and putting in "\\[local ip address of the Ubuntu]". **What I wanted to add was that having got such a list on any machine, it is handy to drag and drop a text file icon onto the printer icon of choice and follow instructions. This seems a simple way of getting a connection to a printer of choice and installing a driver (you may have to locate the driver if the locally installed one is not suitable for copying).**

Might be helpful.

---

