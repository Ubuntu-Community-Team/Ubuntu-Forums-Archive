---
title: "Ubuntu 9.04 becomes slow if left on overnight"
date: 2009-07-17
forum: General Help
---

### Post by Noob Programmer on 2009-07-17
Does any one else have this problem? When I leave my laptop on over night and come back in the morning Ubuntu runs slow all round. Graphics and general usage. The only way I found to get it working again is a full reboot. Is there a known memory leak? It  doesn't kill me to reboot in the morning but I thought this was worth mentioning.

---

### Post by NightwishFan on 2009-07-17
Are you aware what programs are using CPU/RAM? Gnome System Monitor is good to learn this.

Perhaps you installed using a bad cd. Place the disc you used to install in the drive and run this command (in terminal)

```
cd /media/cdrom0 && md5sum -c md5sum.txt
```
You will see a list of files. If there is no ERROR report at the end, your disk is fine.

My installation has never been shut down, and I have no slowdowns. Linux should be able to keep performance constant.

---

### Post by cmost on 2009-07-17
Do you have an Nvidia graphics card and if so, are you using the bleeding edge drivers?  Some recent nvidia drivers have been reported to have a gaping memory hole that causes significant slow down of the system over time.

---

### Post by vesselp on 2009-08-03
Hey
I run jaunty on dell latitude d420 gig ram duo core 1.2 gig
as long as i use the system it is fine, as soon as i leave it idle for longer than hour, the system grinds to a halt as if running in sludge.  then i have to reboot to get it to work normally.
dont have nvidia graphix.
downloaded jaunty on the day of release.  since then, the system has slowly become slower, though i am certain this is understandable due to the use it sees.

checked my install image and it is error free.
8.10  did not have the same problem.

just for info

Thanks Vessel

---

### Post by cloudscream on 2009-08-29
I also have this problem. Starts fast and nice upon fresh boot. After about 1 and a half hours or so, the LED for disk usage starts to blink frantically. I have turned swappiness from 0 to 40 to 60 to 100, but all yielded the same results. Turn off compiz to no avail. Reduced the number of background process, nada. Even changed my browser from Firefox to Epiphany but still slowdowns caused by an unknown process were happening.
Of course it is common sense to look at the System Monitor to see what programs are causing memory/CPU usage, but I see no abnormal CPU/ RAM usage stat in the System Monitor during the slowdowns...

I have an acer 2.1GHz Intel core 2 duo processor
1G RAM
Intel GM965
Ubuntu Jaunty 32-bit
Linux 2.6.28-15

---

### Post by stinger30au on 2009-08-29
> **Noob Programmer said:**
> Does any one else have this problem? When I leave my laptop on over night and come back in the morning Ubuntu runs slow all round. Graphics and general usage. The only way I found to get it working again is a full reboot. Is there a known memory leak? It  doesn't kill me to reboot in the morning but I thought this was worth mentioning.

my pc runs 24x7x365 with 9.04 on it

i dont have these issues

just lucky i guess

---

### Post by XCan on 2009-08-29
That does indeed sound like your comp is forced to swap alot. Could you do a ```
 free 
``` next time it slows down so we can see if it's swapping or not?

---

### Post by PostChache on 2009-08-29
I have a problem similar to this but I don't notice the slowdown until I try to re/open an application then the application won't open until a few seconds later. This use to not happen and it just started. I'm using Ubuntu 9.04 64Bit have any solutions?

---

