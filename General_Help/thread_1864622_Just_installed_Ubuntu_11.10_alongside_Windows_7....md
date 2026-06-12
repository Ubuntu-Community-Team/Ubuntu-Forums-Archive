---
title: "Just installed Ubuntu 11.10 alongside Windows 7... Windows 7 won't start"
date: 2011-10-19
forum: General Help
---

### Post by ViralRiver on 2011-10-19
Hi, just a quick intro: I'm needing Linux on my computer to run programming software such as MatLab and Fortran faster than on Windows. So yesterday I went along to the Linux Society and they helped me install it. We tried a Wubi install but got an error just before reaching 100%. 

So we tried to install it alongside Windows 7. Apparently I already had 4 partitions which were too many, so we deleted my recovery drive for Windows 7. This somehow freed up that extra partition and I started a clean install of Ubuntu 11.10. It asked if I wanted to transfer documents etc from Windows 7 to Ubuntu, I clicked yes.. and the installer froze when retrieving files. Froze in the sense that the caps lock button wouldn't work, cursor wouldn't move etc. So the head of the society member did some amazing thing by pressing alt + prt scr + like 6 letters to restart the computer, unmount and mount something or other and that seemed to work.

So went back onto the installation screen, decided not to transfer files from Windows and it installed perfectly (we overwrote the previous partition). On the GRUB menu I now have Ubuntu, Ubuntu recovery, Memory Test, another sort of memory test, WIndows 7 (sda 1), Windows 7 (sda 2). Now, no one had any idea why there were two Windows showing in the GRUB menu so we tried both out, the first one booted fine, the second wouldn't (I presume it was the remains of the recovery drive).

Either way it was all working perfectly yesterday. So I decided to turn it on today, and Ubuntu loads fine as it did, but Windows 7 now stalls on the "Starting Windows" screen. The windows logo doesn't appear either.

Is there anything I can do to resolve this problem, as I have no idea how to use Linux, and am much more comfortable with Windows!

Sorry for the tl;dr, but I would appreciate all the help I can receive :) .

---

### Post by satanselbow on 2011-10-19
Did you manage to boot into both Windows and Linux successfully yesterday?

If you are getting as far as "starting windows" the bootloader has passed off to the windows kernel so the problem lies on the windows installation itself

Can you hit F8 when you start windows to get into safe mode?

EDIT: You have 2 entries for windows as the windows setup create 1 small (100MB) partition as a bootstrap for the main larger partition during the installation process. It is not advisable to remove this small partition as all manor of horrible stuff can go wrong. To ensure windows only creates 1 partition for itself you need to pre-create the partition using another partition tool and point the installer to that rather than let windows deo the partitioning for you ;) Handy to know if you want to reinstall windows later and free up another of you 4 primary partitions :D

---

### Post by ViralRiver on 2011-10-19
I've just realised it boots fine if I don't have my memory stick connected oO . Is there a specific reason for that? I'm able to insert the memory stick fine after it has loaded.

---

### Post by Mark Phelps on 2011-10-19
If, BEFORE you had rushed into installing Ubuntu, you had used the Win7 Backup feature to create and burn a Win7 Repair CD, you could be using that now to repair the Win7 boot loader.

But since you didn't do that, to repair it now, you will need to do the following:
1) Go to the link below, find the appropriate Win7 version, PURCHASE the disk image, download it, and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

This is a Win7 Repair CD
2) Boot from that CD and run Startup Repair at least three times.

That should restore your ability to get into Win7.

---

### Post by ChaibiAlaa on 2011-10-19
Seems like a problem I had with 11.04 Natty, anyway, it got it repared using the SuperDisk Grub repairer from Ubuntu, you just burn the iso file and boot on the CD / USB, it will repair the boot and the MBR and let you boot on W7.

---

### Post by kurt18947 on 2011-10-19
> **ViralRiver said:**
> I've just realised it boots fine if I don't have my memory stick connected oO . Is there a specific reason for that? I'm able to insert the memory stick fine after it has loaded.

You too, huh?:D My desktop will do the same thing. I have my BIOS boot order set

[LIST=1]
[*]USB-HDD
[*]CD/DVD
[*]Hard Drive
[/LIST]
Even though the USB device doesn't have an operating system on it, the box won't boot unless any USB devices are turned off or unplugged.

---

### Post by ViralRiver on 2011-10-20
I actually took a look at my boot order and reset it to what it was originally. For installation I had it boot from CD before notebook HDD, but it's back to normal now. USB isn't at the top (or there at all I don't think).

---

### Post by satanselbow on 2011-10-20
> **kurt18947 said:**
> Even though the USB device doesn't have an operating system on it, the box won't boot unless any USB devices are turned off or unplugged.

There are a few manufacturers that have taken USB to be the failsafe in the event of bios upgrade boo boos - Acer in particular being one - which may explain why the USB is being read regardless of it's specific place in the boot order ;)

---

### Post by ViralRiver on 2011-10-30
I have the HP beats computer. Is there any way of stopping boot from USB drives? I frequently forget to take out the stick which results in me having to do hold down the power button for 5 seconds or so - which I'm sure isn't a good alternative.

---

