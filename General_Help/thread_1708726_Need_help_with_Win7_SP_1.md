---
title: "Need help with Win7 SP 1"
date: 2011-03-17
forum: General Help
---

### Post by t36 on 2011-03-17
Hi,

I'm trying to keep things up to date on my pc so I'd like to install Win7 SP1. However I get the following message:

Windows 7 and Windows Server 2008 R2 Service Pack 1 (SP1) installation error: 0x800F0A12 

and according to the help this can be due to  "Partition created using a program from another software manufacturer"

This seems very plausible as I dual booted Ubuntu AFTER installing Win7.

And further according to the help I have to:

"The Windows system partition needs to be the only active partition in order to install SP1. "

My question is if I do that and then reset the active partition, will this give problems with the Grub boot loader?

Thanks in advance,

t36

---

### Post by WlaadDyaab on 2011-03-17
> **t36 said:**
> Hi,

I'm trying to keep things up to date on my pc so I'd like to install Win7 SP1. However I get the following message:

Windows 7 and Windows Server 2008 R2 Service Pack 1 (SP1) installation error: 0x800F0A12 

and according to the help this can be due to  "Partition created using a program from another software manufacturer"

This seems very plausible as I dual booted Ubuntu AFTER installing Win7.

And further according to the help I have to:

"The Windows system partition needs to be the only active partition in order to install SP1. "

My question is if I do that and then reset the active partition, will this give problems with the Grub boot loader?

Thanks in advance,

t36

I heard that Microsoft has to be installed first in order to work side by side with Linux, but if you already have a Linux distro installed, I heard it's almost impossible to be stable until Linux is off the hard drive (Microsoft was designed not to allow Linux to work fine unless it's installed first...etc)

I think you'll have to uninstall Linux somehow first, then install Windows 7 SP1

---

### Post by Grenage on 2011-03-17
> **WlaadDyaab said:**
> I heard that Microsoft has to be installed first in order to work side by side with Linux, but if you already have a Linux distro installed, I heard it's almost impossible to be stable until Linux is off the hard drive (Microsoft was designed not to allow Linux to work fine unless it's installed first...etc)

I think you'll have to uninstall Linux somehow first, then install Windows 7 SP1

This is all untrue.

OP: [http://www.windows7newsinfo.com/smf/index.php?topic=15359.0](http://www.windows7newsinfo.com/smf/index.php?topic=15359.0)

I find it odd, because I've installed SP1 on a few machines that dual boot, and Linux was installed first.  You're probably going to find more help on a Windows forum, but you might get lucky here.

---

### Post by mastablasta on 2011-03-17
win7 SP1 - now i am guessing you are trying to install SP1 from some CD instead of doing updates in windows.
 
It's probably searching the main boot record. It could overwrite it and you can then restore grub using the liveCD.
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
@WlaadDyaab - i think you heard wrong. the only problem here is that Windows only recognises windows.

---

### Post by t36 on 2011-03-17
Let me clarify. Windows was installed first and then Ubuntu was installed as a dual boot.
I am trying to update via the automatic update. But without taking any special action I get the error mentioned in my opening post.
The solution seems to me marking the Windows partition as the active partition (I suppose this means that this is the partition that will be used to boot), and I looking for information on how this will affect my dual boot.
I.e. will marking the Windows System partition as active from what is now and changing it back after installing the SP1 mess up GRUB?

Thanks!

---

### Post by Grenage on 2011-03-17
I'm not sure that Grub knows what an active partition is, that's really more of a Windows thing.  That said, it is possible; changes to the partition could cause the UUID to change, which could screw things up.

As long as you have a Live CD (ubuntu install disc), we'll be able to sort it out.  A grub-update would probably be enough, but a grub-install would definitely work.

---

### Post by TBABill on 2011-03-17
Common problem. Answers from Microsoft:
 
[http://answers.microsoft.com/en-us/windows/forum/windows_other-windows_update/windows-7-sp1-0x800f0a12-error-code/a584d276-a773-4917-b947-134d5330b825](http://answers.microsoft.com/en-us/windows/forum/windows_other-windows_update/windows-7-sp1-0x800f0a12-error-code/a584d276-a773-4917-b947-134d5330b825)
 
More answers from ZDNet:
 
[http://www.zdnet.com/blog/bott/quick-fix-for-windows-7-sp1-installation-errors/3040](http://www.zdnet.com/blog/bott/quick-fix-for-windows-7-sp1-installation-errors/3040)

---

### Post by WlaadDyaab on 2011-03-17
> **Grenage said:**
> This is all untrue.

OP: [http://www.windows7newsinfo.com/smf/index.php?topic=15359.0](http://www.windows7newsinfo.com/smf/index.php?topic=15359.0)

I find it odd, because I've installed SP1 on a few machines that dual boot, and Linux was installed first.  You're probably going to find more help on a Windows forum, but you might get lucky here.

I'm always learning

Thanks for correcting me. Will definitely do more research to get my facts right

I don't want this post to be with no advise:- [t36]("http://ubuntuforums.org/member.php?u=329192") try YouTube for research and tutorials, since I normally don't get along with reading I normally learn almost everything related to software from there

---

### Post by t36 on 2011-03-18
I tried the tips in the link, but unless I did not understand them I still have trouble installing the SP1. I do have two internal HDD, so maybe that's an additional complication?

---

### Post by thewolfman on 2011-03-18
T36,

which of the drives has the MBR on it, is it on the main (first) drive, or on the 2nd??.

---

### Post by wilee-nilee on 2011-03-18
Post from the terminal.
fdisk -lu

---

### Post by t36 on 2011-03-18
This is the output of fdisk -lu:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3a9f839

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   124659711    62226432    7  HPFS/NTFS
/dev/sda3       124659712  1953421311   914380800    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa059d385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   345188654   172594296   83  Linux
/dev/sdb2      1917679050  1953520064    17920507+   5  Extended
/dev/sdb3       345188655  1917679049   786245197+  83  Linux
/dev/sdb5      1917679113  1953520064    17920476   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by t36 on 2011-03-18
Is it normal that Boot partition and the system partition are different?

---

