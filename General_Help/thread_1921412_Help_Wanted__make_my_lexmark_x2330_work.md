---
title: "Help Wanted:  make my lexmark x2330 work"
date: 2012-02-06
forum: General Help
---

### Post by owencousins on 2012-02-06
Hello, trying to get the old x2330 to work on a shared network with the printer hooked up to an xp desktop.

cannot get this thing to work, i have managed to get the laptop to locate the printer on the network, and even to send printing jobs to it, but only by using the incorrect lexmark drivers.  The desktop reports that printing has started, spooled, and completed, but the printer doesnt move or blink.

So i figured I better get the right driver, and make it work locally plugged into the ubuntu laptop.  However the driver doesn't exist on the lexmark website, but i did find the post here:

[http://ubuntuforums.org/showthread.php?t=1243920&highlight=lexmark+x2330]("http://ubuntuforums.org/showthread.php?t=1243920&highlight=lexmark+x2330")

which would likely work for the x2330 if I new the x2330 PID, but when I type in terminal:
dmesg | grep lp

i get:

[    0.000000] On node 0 totalpages: 982014
[    0.008010] Calibrating delay loop (skipped), value calculated using timer frequency.. 2393.92 BogoMIPS (lpj=4787844)
[   11.611404] lp: driver loaded but no devices found
[   19.306057] ath: Country alpha2 being used: 00

which lists no devices found so I can't find the right PID (i am assuming here that it's not going to be 010b like the x2500?)

Can anyone help?

---

### Post by wolfen69 on 2012-02-06
You might want to look [here]("http://linuxshellaccount.blogspot.com/2008/08/finding-running-process-ids-on-linux.html") to find out how to run *pidof*

---

### Post by bluexrider on 2012-02-06
Wow, vintage 1990's printer. I think '98 was the first support for that printer in Windows 98 and ME.

I cannot recall any support for that printer. You can't take a Windows binary driver and use it as a driver on Ubuntu as is.

---

### Post by bluexrider on 2012-02-06
> **wolfen69 said:**
> You might want to look [here]("http://linuxshellaccount.blogspot.com/2008/08/finding-running-process-ids-on-linux.html") to find out how to run *pidof*

I fail to understand what 'pidof' is to, or how it relates to the OP's issue? Maybe you could clarify so I could see what you see.

---

### Post by owencousins on 2012-02-07
yes, it is old...but still functioning.

Anyone else able to shed some light on the situation?

---

