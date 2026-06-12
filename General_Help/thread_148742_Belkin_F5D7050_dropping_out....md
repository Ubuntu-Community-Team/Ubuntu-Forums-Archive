---
title: "Belkin F5D7050 dropping out..."
date: 2006-03-22
forum: General Help
---

### Post by thebug on 2006-03-22
Hiya,

I'm using Ubuntu 5.10 on an old Toshiba Satellite Pro laptop.  I also have a new Belkin 54g Wireless USB stick (F5D7050) which took literally hours to get configured... recompiling NDISWrapper, etc...

Now it's working, it's great.  That is, until I go past a certain threshold, and then communication just stops.

Unfortunately, I don't know what that threshold is.  It's not time-related, as I've left the laptop on for a couple of days and gone back to it, and it's working fine.  It could be data-related, as it usually drops out during intensive downloads - i.e. Updates.

Has anyone had any experience on this, or could offer advise or suggestions on how to diagnose/fix the problem?

Cheers,
Dave

---

### Post by bailout on 2006-03-22
I don't want to upset you after you have put in all that work with ndiswrapper but there are native linux drivers available for that chip. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=106846&highlight=ralink](http://www.ubuntuforums.org/showthread.php?t=106846&highlight=ralink)

I have the same belkin adapter and ran it under ndiswrapper and then the native drivers after following the thread above. I can't remember having problems like you describe but I didn't used to be online for that long anyway. Now using dapper which has the drivers built in.

---

### Post by thebug on 2006-03-23
[QUOTE=bailout]I don't want to upset you after you have put in all that work with ndiswrapper but there are native linux drivers available for that chip. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=106846&highlight=ralink](http://www.ubuntuforums.org/showthread.php?t=106846&highlight=ralink)

I have the same belkin adapter and ran it under ndiswrapper and then the native drivers after following the thread above. I can't remember having problems like you describe but I didn't used to be online for that long anyway. Now using dapper which has the drivers built in.[/QUOTE]

Thanks for your reply.  Unfortunately, the version of the F5D7050 (internally 705**a**) I have uses a different chipset to the one that you appear to have.  I can't remember the exact chipset number... it was something like R?73.  The Wireless article in the Ubuntu Wiki said that I needed to use ndiswrapper.

---

### Post by trent dillman on 2006-03-23
I know this sounds silly...but try moving your router. I had problems using a Belkin router, and solved it by moving the stupid thing further away from the monitor. I could connect and run for a while, then the connection would drop.

---

### Post by dmizer on 2006-03-23
this is probably related to your router rather than your os.  have you completely rebooted your network since you got the usb stick up and running?

if you haven't yet rebooted your network try rebooting in this order ...
power off pc's connected to the network, power off router, power off modem.  then power on modem and wait for it to sync, power on router and wait for it to sync, then power on your pc and see if you continue to get interupted.

---

### Post by thebug on 2006-03-25
[QUOTE=trent dillman]I know this sounds silly...but try moving your router. I had problems using a Belkin router, and solved it by moving the stupid thing further away from the monitor. I could connect and run for a while, then the connection would drop.[/QUOTE]

I've never had problems with this router in the past.  I had this same laptop running Windows 2000 with a different USB stick, and it worked an absolute treat.

It's for this reason that I don't believe that it's the router itself.  I appreciate your suggestion though. :)

---

### Post by thebug on 2006-03-25
[QUOTE=dmizer]this is probably related to your router rather than your os.  have you completely rebooted your network since you got the usb stick up and running?

if you haven't yet rebooted your network try rebooting in this order ...
power off pc's connected to the network, power off router, power off modem.  then power on modem and wait for it to sync, power on router and wait for it to sync, then power on your pc and see if you continue to get interupted.[/QUOTE]

I did what you suggested, although I didn't reboot the modem as my wireless router is just another device on my LAN, and the LAN works fine.

Like I mentioned in my previous reply, I don't believe that it has anything to do with the wireless router.  I would suggest that it's more likely to be the OS or the driver/ndiswrapper combination.

The point is, it *does* work... it just decides to give up after a while.

Thanks for your reply though, I appreciate it. :)

---

