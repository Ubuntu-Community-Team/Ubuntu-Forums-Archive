---
title: "autodetection of network printers makes all printers disappear"
date: 2010-01-28
forum: General Help
---

### Post by bottleman on 2010-01-28
Hi, I've been using Kubuntu 9.10 for several months now.  For most of that time, I configured and used with no problem several network printers.. a HP LaserJet 3015 at home connected to a Windows machine, and a Xerox Phaser 8560 at my coworking space connected directly to a router.

However, several weeks ago I was at the coworking space, requested a print from my web browser, and in the printer selection dialog, observed the list of printers expanding... some sort of autodetection of network printers was occuring, and multiple instances of the same printer were being offered, with slightly different names.  Printing to these devices did not work. 

Now, after a reboot, there are NO network printers available no matter what network I'm connected to.  When I use the Kubuntu printer configuration tool and try to set up a new printer, it asks me to "Select a connection" to which the only option it gives me is "Other".  When I put in an address for the printer it just cycles endlessly, never finding anything.

Help! I need to print!

---

### Post by venik212 on 2010-02-16
My printers disappear as well from Kubuntu 9.10 64 bits.
XP all of a sudden appears very stable...

---

### Post by bottleman on 2010-02-16
Ping! Still need help if anyone's out there.

I'm pretty sure at this point the problem has to do with cups not being able to run.  I don't see any process with a name like "cups" when i open system monitor.  and when I try to restart cups manually with a statement like this..

```
sudo service cups restart

```I get back..

```
 cupsd: Child exited with status 1!

```.. However I'm not really sure how to diagnose backwards from that point.

---

### Post by bottleman on 2010-02-16
Seem to have fixed it.  In the upgrade process the config file etc/cups/cupsd.conf seems to have disappeared.  When I supplied one it cupsd was able to run.  More details at [http://kubuntuforums.net/forums/index.php?topic=3110088.0](http://kubuntuforums.net/forums/index.php?topic=3110088.0) .

---

