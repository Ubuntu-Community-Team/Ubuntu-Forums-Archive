---
title: "Cannot Reinstall Windows"
date: 2010-08-30
forum: General Help
---

### Post by Deztruct on 2010-08-30
Ubunto Community:

I've always had my Windows Vista installed alongside Ubunto.  Recently however, I reinstalled Ubunto and completely wiped out Vista and any other OS on my laptop.  So right now it's just Ubunto.

Now, I've decided I would like a windows OS on my laptop but cannot seem to get it working.   Ever since I deleted my Windows Vista partition, I haven't had any luck restoring it.  I keep trying and failing at installing Windows XP.  I keep getting this error message on a blue screen and then installation exits.  It says I need to check for virus, etc.  That is clearly not the problem.

I installed Linux Mint alongside Ubunto to delete Ubunto to make and format a drive to reinstall windows.  That also didn't work.  So I have absolutely no idea what to do now. There's just something wrong where my laptop won't accept Windows.  

I figured Vista or better might work, but i don't have the money for that yet!  Any Ideas?

Best,
Deztruct

---

### Post by QIII on 2010-08-30
You want to completely destroy Ubuntu and any data you have?

---

### Post by Miljet on 2010-08-30
First of all I would suggest running Windows in a virtual machine. But that is not what you asked. Probably the reason that your Windows installation disk will not install is that it does not recognize the disk drive. You need to use gparted to create space for Windows. Either format the space as NTFS or just leave it unallocated and Windows should then find it.

---

### Post by Deztruct on 2010-08-31
What I did was delete Linux mint to format that empty driver space and formatted it, but it still didn't work.  The empty formatted drive wasn't enough to install windows.  I DO NOT want to completely destroy Ubunto.  But if I have to, then I have no choice.  But how can you destroy everything including your OS on any PC?

---

### Post by coffeecat on 2010-08-31
> **Deztruct said:**
> The empty formatted drive wasn't enough to install windows.

What do you mean by that? If you have a primary partition on your drive formatted NTFS and it's of an adequate size, then the Windows XP installer will detect that and be quite happy with it. If it's a logical partition or a filesystem other than NTFS, then the XP installer will get confused.

To give us the right information, boot into Ubuntu,  open a terminal and post the output of:

```
sudo fdisk -l
```> **Deztruct said:**
> So right now it's just Ubunto.

No. It's Ubunt[SIZE=5]u[/SIZE]. :wink:

**Edit:** oh, by the way, when you do get Windows installed it will overwrite Ubuntu's grub stage 1 on the MBR and you'll only be able to boot into Windows. Easily fixed with an Ubuntu live CD, but we'll need the output of fdisk as above to help you with that.

---

### Post by inso_741 on 2010-08-31
> **Deztruct said:**
> Ubunto Community:

I've always had my Windows Vista installed alongside Ubunto.  Recently however, I reinstalled Ubunto and completely wiped out Vista and any other OS on my laptop.  So right now it's just Ubunto.

Now, I've decided I would like a windows OS on my laptop but cannot seem to get it working.   Ever since I deleted my Windows Vista partition, I haven't had any luck restoring it.  I keep trying and failing at installing Windows XP.  I keep getting this error message on a blue screen and then installation exits.  It says I need to check for virus, etc.  That is clearly not the problem.

I installed Linux Mint alongside Ubunto to delete Ubunto to make and format a drive to reinstall windows.  That also didn't work.  So I have absolutely no idea what to do now. There's just something wrong where my laptop won't accept Windows.  

I figured Vista or better might work, but i don't have the money for that yet!  Any Ideas?

Best,
Deztruct

since you had windows vista why dont you try installing it again?? anyways...
to setup a dual boot system you need to have a clear understanding of your system partitions...with that you can install any OS anytime...and as many times w/o messing up the other OS...:P

---

### Post by coffeecat on 2010-08-31
> **inso_741 said:**
> to setup a dual boot system you need to have a clear understanding of your system partitions

Good point.

@Deztruct, here's a useful link for you in case you have questions about partitions and filesystems:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by sikander3786 on 2010-08-31
> **Deztruct said:**
> But how can you destroy everything including your OS on any PC?

By formatting the whole HDD (of course if there is no important data on it).

One doesn't need to be a geek for dual booting. You can install windows before or after installing Ubuntu. What is required is a little patience and clear mind frame i.e, what you want. If you want just Windows, go with it without any hesitations. Wipe whole of your HDD and install Windows to it. You are free in choosing any OS, and that should be the one that meets your needs.

Just decide what you want. If dual boot, then post back the output of the command [COLOR="Red"]coffeecat[/COLOR] asked.

```

sudo fdisk -l

```

---

### Post by Deztruct on 2010-08-31
OK, I am very bad at explaining my problems.

First of all I cannot reinstall Vista because my laptop didn't come with a CD, and I deleted the recovery images off of my laptop.

I did make a large partition, named it windows, and formated it NTFS format.  I will post a screen shot of my disk utility screen once I can figure out where I can find the pictures I actually took!  Once I figure that out, you guys should have a better idea of what my problem is.

---

### Post by Deztruct on 2010-08-31
I typed that into a terminal and got:

[PHP]
anthony@anthony-laptop:~$ sudo fdisk -l
[sudo] password for anthony: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b8ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32784   263337448+   7  HPFS/NTFS
/dev/sda2           32785       38914    49232897    5  Extended
/dev/sda5           37785       38914     9069568   82  Linux swap / Solaris
/dev/sda6           32785       37574    38469632   83  Linux
/dev/sda7           37574       37785     1691648   82  Linux swap / Solaris

Partition table entries are not in disk order



[/PHP]

---

### Post by wilee-nilee on 2010-08-31
Post a screenshot of gparted on Ubuntu.

---

### Post by Rasa1111 on 2010-08-31
> No. It's Ubunt[SIZE="6"]u[/SIZE]. 

lol, thank you!
 jeeez. talk about intentional. lol

---

### Post by rockager on 2010-08-31
installing windows after ubuntu will erase grub so if you want to instrall windows without touching ubuntu you will have to install grub again.
installing ubuntu (or any linux distro) after installing windows is much easier.
windows xp can only be installed on a ntfs or fat32 partition and it does not recognise ext4 filesystem. however you can install a driver for reading/writing on ext2/3 partitions on win xp
 
i suggest you delete ubuntu, repartition your hard disk and install windows to it and then install ubuntu alonside windows on an ext2/3 partition. there is a partition utility software named gparted on the ubuntu live cd (system>>administration>>gparted) which you can use for partitioning your system.
 
the following links might help:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by inso_741 on 2010-09-01
[this]("http://www.computer-how-to-guide.com/windows-software/windows-xp-bsod-intel-motherboard/") might be the reason why you cant install xp

---

