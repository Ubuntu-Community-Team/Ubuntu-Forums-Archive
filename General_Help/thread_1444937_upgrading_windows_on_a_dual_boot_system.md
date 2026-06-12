---
title: "upgrading windows on a dual boot system"
date: 2010-04-01
forum: General Help
---

### Post by 37fleetwood on 2010-04-01
Hi, I don't use Windows that often but thought since I have a copy of Win7 I might upgrade from the XP I'm currently using.
I'm anticipating several issues, first Grub, can I get it going again after the Win7 upgrade without messing with my current Ubuntu install?
the next issue is Win7 will want to make a "boot" partition, does this create any problem with partition names for Ubuntu?
can this be solved by making the windows "primary" partition and using an extended partition inside that? is there anything I'm missing?

---

### Post by Notebooks on 2010-04-02
This should be relatively easy. I can do it, after all ;). Just put in the WIn7 install disk, and when it asks you which partition you want to use, select your current windows partition. BACK UP FIRST! After that, just grab a linux live cd of some kind and run 
```

sudo grub-install hd0

```replace hd0 with correct hdd number.
that should do it.

And no, partition names will be the same with the aforementioned method.

---

### Post by Mark Phelps on 2010-04-02
You should know, before you do this, that Win7 will NOT do an in-place upgrade from any version of XP. Period.

It will basically wipe out your XP installation and replace it with a Win7 installation.  I believe that it may retain your user info and settings, and maybe even your data, but I'm not clear on that.

What it will NOT do is retain your applications (programs).

If you really want to do an in-place upgrade from XP to Win7, suggest you go to the LapLink website and check out their XP-to-Win7 migration product.  It is currently the ONLY product that will support that kind of upgrade.

---

### Post by 37fleetwood on 2010-04-02
thanks for the info, I really never use the Windows install so there's nothing really on it. just thought if it was easy, why not.;)

---

### Post by Michl on 2010-04-06
What about upgrading from Windows 2000 to WIndows XP?  I have two disks, dual boot, ubuntu is primary, windows slave.  I need to upgrade to XP to be able to use Turbo Tax and I don't want a clean install of XP.

---

### Post by 37fleetwood on 2010-04-06
good question, I would think it would be the same going from 2000 to XP. it would seem to be even simpler since 2000 will directly upgrade to XP. my concern was that 7 uses a separate boot partition.
which brings my next question, which partition do I put GRUB on? the 7 boot partition? and then will it automatically find 7 or will I have to edit the list and add 7? I would hate to get half way through and have missed something:confused:

---

### Post by wilee-nilee on 2010-04-06
So if this is a upgrade version of W7 it is quite possible that a fresh install will cause problems with the key. This can be taken care of easily with the activate by phone automated system.

This can be avoided if you install from XP. It will save your XP information on a old windows file which can be accessed for moving applicable stuff. I am not sure where the boot files are then, but the MBR is now set to boot W7, so you will just install grub to the MBR of the HD.

Let us know exactly what version of Ubuntu your using and if it is grub2 and any one will give you a link to installing legacy grub or grub2 after a MS install.

---

### Post by 37fleetwood on 2010-04-07
sorry I just realized that I didn't put what I'm running.
I'm running Ubuntu 9.10 64bit.
currently this is the drive configuration:

SDA1 - ntfs windows XP -- 65.11gb --- boot
SDA2 - extended --------- 400.65gb -- lba
SDA5 - ext4 Ubuntu 9.10 - 389.68gb
SDA6 - Linux swap ------- 10.98gb

---

### Post by oldfred on 2010-04-07
Grub only goes into the MBR. If you install grub to a partition with windows you destroy essential windows files and have to do a windows repair.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

How windows boots and good info on MBR and PBR boot sectors and what is installed where for windows:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by wilee-nilee on 2010-04-07
So here is a link for grub2 it appears you have grub2 although I am assuming here, since I see karmic and ext4. The steps in #11 is what your looking for.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)
This is for reinstalling grub in the MBR, when it is needed like after a MS install.

---

### Post by wilee-nilee on 2010-04-07
So I thought I would add that the last two times I did a fresh install of W7 with lucid already in place I let the windows installer overwrite/format the partition, this left Lucid unallocated both times. So back everything up off your computer if possible. I could not load the Ubuntu partition into grub then the MBR, it was gone. Although the partition was still intact, if I had needed stuff off of it test disk probably would have worked, but I have all my stuff on external hard drives.

I have installed W7 fresh after building the partition with gparted, and had no loss of Ubuntu.

---

### Post by 37fleetwood on 2010-04-08
Ok, let me see if I understand you correctly. if I use G Parted before I start and format the current Windows drive, I should be fine, if I use the Windows 7 install disk to format the partition I may have problems, do I have that right?
if so, when I format the partition, do I make it an extended partition and make a small boot partition and a larger partition for the OS?
or perhaps I should play it safe and just forget the whole idea.:)

---

### Post by Mark Phelps on 2010-04-08
> **37fleetwood said:**
> Ok, let me see if I understand you correctly. if I use G Parted before I start and format the current Windows drive, I should be fine, 
If you're formatting the drive for Linux, yes. If you're formatting the drive for Win7, it's best to use MS Windows utilities to do that format.
> if I use the Windows 7 install disk to format the partition I may have problems, do I have that right?
If you're using Win7 to format the drive for Win7, that's the correct thing to do -- but it can't handle Linux formats.  You need to use GParted to format Linux partitions.
> if so, when I format the partition, do I make it an extended partition and make a small boot partition and a larger partition for the OS?
MS Windows OSs won't install in an Extended partition; they require a Primary partition.  Linux OSs, on the other hand, have no problems with Extended partitions.
> or perhaps I should play it safe and just forget the whole idea.:)
That IS the safest approach.

---

