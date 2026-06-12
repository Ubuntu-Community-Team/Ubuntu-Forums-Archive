---
title: "Second hdd vanishes after ubuntu installation"
date: 2012-03-17
forum: General Help
---

### Post by ojako on 2012-03-17
Hello all,
   Recently my Windows 7 install spluttered and died in spectacular form. As I usually do in these cases, I cursed, spat, cried a little, and then ran to my old friend Linux to get me going again.
My setup had been a 500gb main drive with Win7 installed on it and a second data drive of about 300gb that I used to store music and old files that I didn't want to lose in case of system failure.
When using a live disk to setup Ubuntu I was able to view both my drives and copy/move data between them with no issues. I grabbed my essentials from my main drive and placed them on my data drive before I installed Ubuntu. All went well and Ubuntu is running smoothly, however I can't see my data drive anymore. Either from inside of my Ubuntu installation or a live disk. Any ideas why this might be? I'm desperately in need of my files from it.

**My PC specs:**

[LIST]
[*]CPU: i7 920
[*]RAM: 8gb DDR3
[*]OS: Ubuntu 11.10 64-bit
[*]GPU: ATi HD Radeon 5x
[*]Mobo: Gigabyte GA-x58 USB3
[/LIST]
As far as I'm aware I'm all up to date with the latest firmware for the mobo. The second drive doesn't appear in gParted either. Shout if you need more system details.

**Thanks in advance for your help =]**

---

### Post by plucky on 2012-03-17
> **ojako said:**
> Hello all,
   Recently my Windows 7 install spluttered and died in spectacular form. As I usually do in these cases, I cursed, spat, cried a little, and then ran to my old friend Linux to get me going again.
My setup had been a 500gb main drive with Win7 installed on it and a second data drive of about 300gb that I used to store music and old files that I didn't want to lose in case of system failure.
When using a live disk to setup Ubuntu I was able to view both my drives and copy/move data between them with no issues. I grabbed my essentials from my main drive and placed them on my data drive before I installed Ubuntu. All went well and Ubuntu is running smoothly, however I can't see my data drive anymore. Either from inside of my Ubuntu installation or a live disk. Any ideas why this might be? I'm desperately in need of my files from it.

**My PC specs:**

[LIST]
[*]CPU: i7 920
[*]RAM: 8gb DDR3
[*]OS: Ubuntu 11.10 64-bit
[*]GPU: ATi HD Radeon 5x
[*]Mobo: Gigabyte GA-x58 USB3
[/LIST]
As far as I'm aware I'm all up to date with the latest firmware for the mobo. The second drive doesn't appear in gParted either. Shout if you need more system details.

**Thanks in advance for your help =]**


Open a terminal and post output of ```
sudo fdisk -l
```

l=lowercase l not a 1 (one)

---

### Post by sidzen on 2012-03-17
If desperate, use [puppy linux]("http://puppylinux.org/main/Download%20Latest%20Release.htm#lucidpuppy") to retrieve your files -- just burn to CD at no more than 8X, boot to it by tweaking the BIOS to boot from cdrom drive and mount the hard drive.

---

### Post by ojako on 2012-03-17
Thanks for the speedy responses!
I'm downloading Puppy now, I'm OK with booting it on a USB stick as opposed to a CD, yea?

**This is my readout:**
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000615c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   957900799   478949376   83  Linux
/dev/sda2       957902846   976771071     9434113    5  Extended
/dev/sda5       957902848   976771071     9434112   82  Linux swap / Solaris

---

