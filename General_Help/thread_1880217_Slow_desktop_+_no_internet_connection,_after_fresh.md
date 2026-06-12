---
title: "Slow desktop + no internet connection, after fresh install on internal hard disk"
date: 2011-11-13
forum: General Help
---

### Post by kaiwi on 2011-11-13
**I. Background**

Way back in 2007, I installed Ubuntu on an external hard drive /dev/sdb (SATA 250 Gigabytes) from where it was loaded using GRUB Legacy. My internal hard drive /dev/sda (also 250 Gigabytes) has Windows Vista installed on it. GRUB let me choose between Ubuntu and Windows. 

Everything was working nicely, except that GRUB always produced Error 21 when my external drive was disconnected. In other words, the external drive was needed not only for loading Ubuntu, but also for loading Windows Vista (although Windows Vista is installed on my internal disk). I suspect that a first stage of GRUB was installed on my internal drive and that a second stage was installed on my external drive, so GRUB needed both drives to function. This seems be a known bug (see e.g. [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996"))

Anyway, I finally (after more than four years...) decided that it was unacceptable to rely on two drives for running GRUB, and used "Boot Repair" (a very nice tool!) to restore my internal drive's Master Boot Record (MBR) so that BIOS would load Windows Vista instead of GRUB. This was successful, and I was again able to boot into Windows Vista directly from my internal drive. 

**II. Fresh installation**

Next, I freshly installed Ubuntu 10.04 LTS on my internal drive /dev/sda using a new Ubuntu Live CD. The live CD created a partition of 19 Gigabytes on that internal drive and installed Ubuntu there. 

Only to rule out any possible confusion: My external drive, which still contains my original Ubuntu 10.04 installation, was not connected to my computer during the installation process and disconnected ever since.

**III. Current problems**

So far, so good. Windows Vista still works fine. Ubuntu 10.04 LTS on the internal disk also works in principal, BUT...

1. the Ubuntu desktop environment (the default one, Gnome, I think - I am writing this from Windows, so cannot check without rebooting) is VERY SLOW. For instance, maximizing, closing or moving a window on the desktop (e.g. a terminal window or a Firefox window) is not "instantaneous" as required, but with a delay of perhaps a second or even several seconds!

2. Ubuntu does not connect to the internet. My PC is connected to the internet via an external DSL modem.

I did not have these problems when running the same version (Ubuntu 10.04 LTS Lucid Lynx) from my external hard drive.

Could it be that the 19 Gigabytes partition on my internal drive is too small? I deliberately chose a small partition, as I am not intending to put any user data in that partition.

The following information may be helpful:

1. Output from "sudo fdisk", concering the internal disk:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d77b8ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28089   225616195    7  HPFS/NTFS
/dev/sda2           28089       30402    18580481    5  Extended
/dev/sda5           28089       30300    17759232   83  Linux
/dev/sda6           30300       30402      820224   82  Linux swap / Solaris

```

/dev/sda1 is the Windows Vista partition.

2. Output from "sudo ifconfig", concerning the internet connection:

```
eth0      Link encap:Ethernet  HWaddr 00:19:db:77:a0:34  
          inet6 addr: fe80::219:dbff:fe77:a034/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1638 (1.6 KB)  TX bytes:2094 (2.0 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8208 (8.2 KB)  TX bytes:8208 (8.2 KB)


```

One more observation: The same problems (slow desktop, no internet connection) occurred when booting Ubuntu from the Live CD (before installing Ubuntu on hard disk). I attributed it to slow data read from the CD, but this is not necessarily the case.

Thanks in advance for any help! I will respond to any suggestions, although this may not be at once, as I need to quit Ubuntu and boot Windows to have internet (to make things worse, my 8-month old daugther is fascinated by the blue light of my computer's restart button...)

---

### Post by kaiwi on 2011-11-13
The speed problem with Gnome was due to "Visual Effects". These effects (which ruined my Sunday) can be deactivated by clicking System -> Preferences -> Appearance, then unchecking them. Now my Gnome desktop is working normally. 

Ubuntu developpers: The Visual Effects of Gnome ought to be deactivated by default.

---

