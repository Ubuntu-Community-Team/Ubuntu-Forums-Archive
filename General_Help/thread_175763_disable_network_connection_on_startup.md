---
title: "disable network connection on startup"
date: 2006-05-13
forum: General Help
---

### Post by paradox814 on 2006-05-13
When I turn on my laptop it always searches for a ethernet network, 99% of the time I never have a ethernet connection, (I use wireless almost exclusively) . How can I get ubunto to stop waisting the 120 seconds or so searching for this non-existant network connection during start up.

Thanks!

---

### Post by Gannin on 2006-05-13
How comfortable with the command line are you?  If you're somewhat comfortable, then you can use apt-get or Synaptic to install sysv-config-rc.  Then, from the command line, type "sudo sysv-config-rc".

Once you've done that, move the cursor over to the column labeled "S" and scroll down the list and find all the various network entries.  Remove the x's from the boxes of the network entries, and then exit the program.  When you restart your computer, it shouldn't look for the network anymore.

---

### Post by bluevoodoo1 on 2006-05-13
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

here's a guide for it.


you can also press ctrl+c during bootup to skip the "network connection" if you don't feel like messing around with sysv-rc-conf

---

### Post by nanotube on 2006-05-13
i would second bluevoodoo's suggestion - just press control-c while it is "configuring network interfaces", and it will move on. that way you are at no risk of screwing up your system, playing around with startup scripts and whatnot.

---

