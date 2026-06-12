---
title: "Printing Problems with no error msg"
date: 2006-04-11
forum: General Help
---

### Post by jimisdead on 2006-04-11
I seem to have messed up printing on my kubuntu breezy laptop when I tried to share it's printer on the network ](*,) and haven't had much luck in getting it working again.

I have reverted all the config files that I changed (I think) and even done a 'complete uninstall' then reinstall of the following packages:

cups-pd
cupsys 
cupsys-bsd
cupsys-client 
cupsys-driver-gutenprint
hplip
hplip-data

to no avail, in the 'printer jobs' window the jobs just appear then disappear as if everything worked fine but /var/log/cups/error_log doesn't seem to give much information:

I [11/Apr/2006:07:35:06 +0200] Listening to 7f000001:631
I [11/Apr/2006:07:35:06 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [11/Apr/2006:07:35:06 +0200] Configured for up to 100 clients.
I [11/Apr/2006:07:35:06 +0200] Allowing up to 100 client connections per host.
I [11/Apr/2006:07:35:06 +0200] Full reload is required.
E [11/Apr/2006:07:35:06 +0200] LoadAllClasses: Unable to open /etc/cups/classes.
conf - No such file or directory
I [11/Apr/2006:07:35:10 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 4105 PPDs...
I [11/Apr/2006:07:35:13 +0200] LoadPPDs: No new or changed PPDs...
I [11/Apr/2006:07:35:14 +0200] Full reload complete.
I [11/Apr/2006:17:05:13 +0200] Adding start banner page "none" to job 3.
I [11/Apr/2006:17:05:13 +0200] Adding end banner page "none" to job 3.
I [11/Apr/2006:17:05:13 +0200] Job 3 queued on 'printer' by 'veronika'.
I [11/Apr/2006:17:05:13 +0200] Started filter /usr/lib/cups/filter/pstops (PID 1
3858) for job 3.
I [11/Apr/2006:17:05:13 +0200] Started filter /usr/lib/cups/filter/foomatic-rip
(PID 13859) for job 3.
I [11/Apr/2006:17:05:13 +0200] Started backend /usr/lib/cups/backend/usb (PID 13
860) for job 3.

does anyone have any ideas? Any help at all would be greatly appreciated, I've been searching for a solution for 3 days now and am close to jumping out the window at this point.

---

### Post by Sef on 2006-04-12
What's the brand and make of the computer?

---

### Post by jimisdead on 2006-04-12
It's a Compaq Evo N600c laptop, a bit old but works still works great. The printer is a HP Officejet G85 connected through USB. I've removed the printer from the System Settings and added it again with no probs... it just won't print.

---

### Post by jimisdead on 2006-04-12
I just tried it on the serial port and it works, so it's a problem with USB - the scanner also doesn't work (it did before) via USB.

does anyone have any ideas?

---

