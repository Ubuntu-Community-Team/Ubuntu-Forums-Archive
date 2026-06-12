---
title: "Restarts instead of shutdown (poweroff)"
date: 2009-09-13
forum: General Help
---

### Post by Lekensteyn on 2009-09-13
Hello people,

I've recently installed Kubuntu on my system.
I've encountered some problems, and some are still not fixed.
The most annoying so far is the shutdown problem.

I've tried things like adding acpi-things to the starup command, editing menu.lst/modules, but none of them worked.

After I choose Shutdown from the KMenu, it looks like it's shutting down.
However, after the GUI goes away, I get the message
```
halt: Unable to iterate IDE devices: no such file or directory
[182.820656] System halted.

```Soon after getting this message, it restarts.
I've no other choice than shutting down from Windows XP.

I've installed Kubuntu (9.01 Jaunty) from a LiveCD, on a external HDD.
I can't boot from the USB device from default, so I manually boot by pressing F8 to load GRUB from my external HDD.
1GB RAM, 2.93GHz Pentium 4 processor, ATI graphics card
If you need additional information, just say it :)

---

### Post by Lekensteyn on 2009-09-15
Anyone?

---

### Post by sunchiqua on 2009-09-15
What's the result of the following command ?

```
sudo shutdown -h now
```

---

### Post by wojox on 2009-09-15
Try:

```
kdesu kate /etc/modules
```

Add:

```
apm power_off=1
```

---

### Post by Lekensteyn on 2009-09-15
> **sunchiqua said:**
> What's the result of the following command ?

```
sudo shutdown -h now
```

I've tried "sudo shutdown -p 0", is that the same thing?

Edit: I tried this, my PC shuts down, and restarts.

> **wojox said:**
> Try:

```
kdesu kate /etc/modules
```Add:

```
apm power_off=1
```
Already tried that.

Thanks for your replies!

---

### Post by Lekensteyn on 2009-09-15
Edited last post, it's still not working.

---

### Post by Lekensteyn on 2009-09-16
Hmm, now I'm not getting a message at all.
I press "Shutdown", and soon after the desktop disappears, my screen turns off (stand-by).
And it reboots...

Btw, I'm running a dutch version, from [http://ubuntu-nl.org](http://ubuntu-nl.org)

---

### Post by Lekensteyn on 2009-09-22
Bump, I'm still having this problem :s

---

### Post by Lekensteyn on 2009-09-24
Another bump, I still can't shutdown!
It's restarting instead :(

---

### Post by Lekensteyn on 2009-09-30
O my god!!
Updating my Award Medallion Bios from 20q to 20u solved this problem!

---

### Post by wandalalakers on 2010-02-21
I installed Kubuntu 8.04 on a Gateway M305CRV and it wouldn't shutdown, only restart.  Of course I already wiped xp off of this laptop.  In order to update the bios, I had to reinstall windows because the bios update software only runs on windows.  I reinstalled windows and updated the bios.  I then reinstalled Kubuntu 8.04.  I am able to shutdown now after using the newest bios.  Kubuntu 8.0 flies on this laptop whereas xp was running like a snail.

---

### Post by Blue_Mercury on 2010-09-25
I have the exact same problem with my Dell Inspiron 1100 which appeared as soon as I upgraded to Ubuntu 10.04.
When I select shut down, the computer powers down and I can even hear the fan switch off.  Then about 1 second later it powers back up.
When I select restart it does not power down, it just goes straight back into the BIOS.

I tried to upgrade my BIOS in order to fix the problem but unfortunately this is an older computer and my BIOS is already the newest version.  So that did nothing.

I dual boot with XP and that seems to be the only way to get my computer to shut down without manually cutting the power.

---

### Post by stanz on 2010-10-14
Still happening huh?
I'm coming in late here...just updated a couple of days ago--never shut down proper since!

---

### Post by TBerk on 2010-11-07
Why is this thread marked [SOLVED] ?


TBerk

---

