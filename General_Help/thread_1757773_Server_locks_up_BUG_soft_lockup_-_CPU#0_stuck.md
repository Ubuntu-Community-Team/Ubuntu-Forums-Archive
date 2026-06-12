---
title: "Server locks up: BUG: soft lockup - CPU#0 stuck"
date: 2011-05-13
forum: General Help
---

### Post by mogie on 2011-05-13
Hey ho!

I've had my server running for some time now, but in some rare occasions I get lock-ups with this error:

```
... BUG: soft lockup - CPU#0 stuck for 61s! [mysqld:1330] ... (repeating)..
```

[IMG]http://bildr.no/view/882576[/IMG]

I've found some threads about some similar problems, but there's no clear solution since it seams everyone have different orgins (espesially boot-up trouble which I dont have)

[http://ubuntuforums.org/showthread.php?t=935396]("http://ubuntuforums.org/showthread.php?t=935396")

The lock-ups usually (only!) come when there's a lot of traffic to my rTorrent-server (some 5-10MB/s). My server can run for months/weeks as long there's not too much torrent-traffic. I'm running a lot of traffic from/to the server locally (Samba, FTP etc.) which never triggers these problems. 


I then ask myself if the bug has anything to relate to mysql-daemon which it marks at the end of the BUG-line? I'm running both Apache webserver and Pure-FTPD which both have connection to mysqld. My rTorrent server uses wTorrent with SQLite and Lighttpd so I cant really relate it here either.

Or could it be hardware failure (highly unlikely the way I see it..) or the problem that the system doesn't utilizes all the 4 cores in the @6600? I got the impression the kernel isn't developed enough yet (for 9.10) to use them all right and sees the CPU as a dual-core..

It seems that there's no traces of any log of these error's in any /var/log file, cause I just searched through all of them..

Oh, yeah! I almost forgot to thank you all in advance for anything you can contribute with for diagnosing :-)


Some computer specs:
Core 2 Duo 6600 4xcore
Intel P35 motherboard
2GB RAM
Ubuntu 9.10:  2.6.31-23-server x86_64 GNU/Linux

---

### Post by bchurchill on 2011-05-13
I have had some experience with problems of this sort before -- especially when I used arch linux.  I generally found that they came up more often after the system was up for a while, and that the situation is entirely dependent on the stuff that runs in your kernel and how it interacts with your hardware.

Version to version extremely small changes in the kernel can have unknown effects on specific platforms.  Typically I've found that the kernels that are shipped with Ubuntu are very stable and I rarely (if ever) have problems with them (Arch, however, was a different story).  You might want to try upgrading your distribution, just the kernel, or possibly any proprietary drivers you have.  I've often noticed that nVidia proprietary drivers need to be upgraded with the kernel, so if you use those you should try upgrading that.

As you mentioned it's typically difficult to pinpoint the exact source of the problems.  You could let it be, or maybe try upgrading something-or-other.

EDIT: rereading your post, it could be beneficial to upgrade any firmware/drivers that your network equipment uses.  I have a feeling (although I TOTALLY could be wrong) that this isn't an application-level problem and that it is a kernel/module-level issue.  If the kernel is working right a soft lockup should never happen...

---

### Post by mogie on 2011-05-13
Wow! Man! Thank you for such quick response!

Yeah, I had the same though about maybe try to update the kernel. Is there a one-line command for doing so with aptitude? Haven't updated kernel before (unless the whole system is bein updated with all applications... which I rather avoid first hand..) - dist-upgrade this would be then..

Again, thanks in advance!

---

### Post by bchurchill on 2011-05-13
Yes, you "should" be able to install it as a package.  First find your kernel version '$uname -r'.  Then seach the repositories for linux-image-xxxxxxx.  You should be able to just apt-get install it.  I think the easiest way is to search using apt-get with

#apt-get update
#apt-cache search linux-image

I should warn you that usually it takes a little more work.  For example in the past I've had GRUB entries not update properly (although my guess is that they've got the upgrade process figured out better with GRUB2 these days... I still use legacy).  Again, you may need to upgrade drivers too.

---

### Post by bchurchill on 2011-05-13
By the way, I'm pretty sure kernels have supported several cores (well more than 4) for a while now, so that by itself probably wasn't the problem.

---

### Post by tgalati4 on 2011-05-13
Modern kernels support either 16 or 64 cores before you have to reconfigure.  I'm guessing there's a motherboard problem, probably the southbridge chip.  It controls the I/O and ethernet traffic.  If your torrents cause it to heat up, then it could cause errors on the bus and cause the CPU to shutdown.  The Intel P35 boards are not known for their reliability.

Note:  Jaunty kernel has support for 2 to 512 processor cores--64 is set by default--I presume for a server blade chassis with 8-cores-per-blade and 8-blades-per-chassis.

---

### Post by mogie on 2011-05-14
Thanks for the advice tgalati4!

I tried out some aptitude upgrading, but it will have to be an do-dist-upgrade, because the kernel is the latest of Ubuntu 9.10 which is now installed. I've also updated all packages on my server now - luckily without any trouble yet.

As for trouble maybe related to the South bridge - is there anything else I should try to solve this? I could do a dist-upgrade, but I will have to make some backups first tonight (its mid-day here right now..). Could alternatively a BIOS-upgrade possibly to the magic, or how well-known is the problems with P35-chipsets? If there are any related threads to this I would like to read about it :)

OH.. one more question: Is it possible to dist-upgrade directly to the 10.04 LTS from a non-LTS (9.10) safely? On the other hand should I go for the 11.04 because it possibly has a more supportive kernel than the 10.04 LTS - or is it the other way around?

---

### Post by tgalati4 on 2011-05-21
Clean installs are always preferred over dist-upgrades.  Dist-upgrades are convenient, but expect some breakage.  If you know how to fix such breakage (or are patient enough to research the fixes) then by all means try a dist-upgrade.  You can go from LTS-to-LTS, but not otherwise.  You would need to upgrade incrementally to the nearest LTS then jump to the latest LTS.  It might be easier to backup and do a clean install.

Yes, a BIOS upgrade is usually helpful.  I built 2 P35 machines for a client and I had problems with them and had to return one board.  I had stability issues with RAID, RAM, processor lockups.  It took some tweaking in the BIOS to get the machines to behave.

To see all four cores:

sudo apt-get install htop
htop

I would try declocking (slowing down) your CPU's and see if stability improves.  I don't know if the P35 has problems or if it's the motherboard manufacturer's implementation that causes the issues.  Mine were Intel boards with Intel chips so you would assume bullet-proof, right?
Wrong.

If nothing else, clean the machine, reseat everything, run memtest for 30 cycles (over night).  You need to pinpoint why your cores are shutting down.  It's not normal.  The fact that you can't find anything in the logs points to a hardware issue.

---

### Post by mogie on 2011-05-23
I just found 2 cores with htop. So I'll go for an BIOS update right away.

---

### Post by mogie on 2011-05-23
Just changed my P35 board to a Asus P43 P5QL Pro. BIOS is of the latest. I now also gone from ICH9-> ICH10 chipset. 

With lscpu I get this:

```
Architecture:          x86_64
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              6
CPU MHz:               1603.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K
```

Shouldn't it be showing 4 CPU(s)? I still haven't got any more crashes, but I will report one if I get it soon.

htop also shows only 2 CPU-graphs..

UPDATE: After gone through dmidecode -t 4,  cat /proc/cpuinfo and lscpu - I'm convinced that I do have the 6600, NOT the Q6600 which I have on another PC :p

UPDATE2: I'm setting this thread to SOLVED. I'm trying to stress the server right now and I dont get any halts. Thanks tgalati4 and bchurchill :)

---

