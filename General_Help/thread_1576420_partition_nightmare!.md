---
title: "partition nightmare!"
date: 2010-09-17
forum: General Help
---

### Post by Th3P4rk2 on 2010-09-17
Hiya all, thanks for looking in and I hope you can help me!

Right...I have just brought a new laptop, its a HP dv3-4050

It has a 500gb hdd and came setup as follows,

[Boot settings 100mb][Windows][HP tools][Hp backup]

I am currently creating a backup of the windows 7 partition so I can restore this to the new partition when its ready so no need for drive shrinking etc because I can format completely and start from scratch.

I want to multiboot windows 7 64bit, Ubuntu 64bit and Backtrack linux and have an area accessible by windows and linux I would think looking something like this.

[EXT4 Ubuntu 120gb][NTFS Windows 120gb][EXT 4 Backtrack 30gb][Fat 16/32? Shared area][Swap]

but this odviously isnt possible given a maximum of 4 primary partitions here are my questions.


1) does the bootloader have to have its own primary partition? 2) Should I keep the windows bootloader thats already there or install grub or similar?
3) Am I able to have or do I even need a Swap partition for linux?
4) What is the best way to do this? 

Thanks in advance,

Ant

---

### Post by ratcheer on 2010-09-17
You could do it all in three partitions: a primary for Win 7, a swap for both Linuxes, and an extended partition with sub-partitions for the Linuxes, themselves. I have never done it that way, but I am pretty sure it will work.

Tim

---

### Post by aytech on 2010-09-17
> **Th3P4rk2 said:**
> 
1) does the bootloader have to have its own primary partition? 2) Should I keep the windows bootloader thats already there or install grub or similar?

 
Bootloader in Win doesnt need a separate partition, its there because of whatever backup software you have installed there, dunno what HP uses, in Lenovo machines its One Key Recovery.

---

### Post by Th3P4rk2 on 2010-09-17
SO I format the drive,

create 3 partitions,

[NTFS 120gb windows][Extended partition 2x logical forlinux][swap]

so I dont need a dedictaed boot partition?

also would the extended partiton be accessible by windows?

Thanks

---

### Post by ratcheer on 2010-09-17
Well, yes, but you can create many subpartitions in the extended partition for your Linux systems. For example, each Linux could have a root and a home of its own.

I have no idea whether Win7 can access the Linux partitions.

Tim

---

### Post by aytech on 2010-09-17
> **ratcheer said:**
>  
I have no idea whether Win7 can access the Linux partitions.
Tim
 
Windows doesnt support ext partitions natively, but there're various tools to do it, like LTools. not sure if it supports ext4 though

---

### Post by WorMzy on 2010-09-17
> **Th3P4rk2 said:**
> SO I format the drive,

create 3 partitions,

[NTFS 120gb windows][Extended partition 2x logical forlinux][swap]

so I dont need a dedictaed boot partition?

also would the extended partiton be accessible by windows?

Thanks

It's best to put the extended partition last in the partition table, so that you don't get confused later on by the numbering (the first partition inside the extended partition will be sda5, so with that set up you'd have sda1, sda2, sda5, sda6, sda3, in that order. While this makes no difference to the usability of the system, it can cause some confusion for the average user).

You don't need a dedicated boot partition. Part of grub will be installed to MBR of the disk (which will probably be in the Windows partition), and the rest will be installed to the /boot directory in your Linux partition (assuming you choose not to install a bootloader during the second Linux installation - which is correct, you should be able to update grub from the first Linux installation to make it see the second).

You can create NTFS and FAT partitions inside the extended partition, and these will be seen by Windows. EXT partitions, not so much. There's tools for Windows that allow you to read EXT2 (and the similar EXT3) but nothing for EXT4 as of yet (to my knowledge).

I'd recommend using NTFS for your shared partition if you decide to have one. You can defrag it from inside Windows if need be.

Lastly, you don't "need" a swap partition, but if you're going to use a lot of RAM intensive programs, like high resolution image editing software and/or video editing software, then a swap partition would be a good idea. Also, if you plan on using hibernate/sleep (whichever one unloads RAM to disk to be recalled later) then you'll need as much swap as you have RAM.

---

### Post by srs5694 on 2010-09-17
> **Th3P4rk2 said:**
> Hiya all, thanks for looking in and I hope you can help me!

Right...I have just brought a new laptop, its a HP dv3-4050

It has a 500gb hdd and came setup as follows,

[Boot settings 100mb][Windows][HP tools][Hp backup]
...
I would think looking something like this.

[EXT4 Ubuntu 120gb][NTFS Windows 120gb][EXT 4 Backtrack 30gb][Fat 16/32? Shared area][Swap]

but this odviously isnt possible given a maximum of 4 primary partitions here are my questions.


1) does the bootloader have to have its own primary partition?

First, you may want to check out one or more of many recent threads on this topic, such as [this one.](http://ubuntuforums.org/showthread.php?t=1571332)

As to your specific question, it seems that you're under the mistaken impression that one of your existing four partitions is a boot loader partition. It's not. Your four partitions are probably:


[list=1]
[*]A [Windows Recovery Environment](http://en.wikipedia.org/wiki/Windows_Recovery_Environment) partition, which helps the system recover from errors. I've seen some suggestions that this partition is part of the normal boot process, and so should not be removed, but I've never investigated this issue in depth.
[*]The Windows boot partition.
[*]A partition containing the equivalent of Windows installation DVD(s), since your computer manufacturer is too cheap to include physical DVD(s) totalling $1 or less with your several-hundred-dollar purchase.
[*]A partition containing manufacturer-specific tools.
[/list]


Of these, partition #3 is probably easiest and safest to remove, since there should be a utility that will enable you to create the physical DVDs that your manufacturer *should have* included with your purchase. (Instead of twiddling your thumbs while you act as a human disc changer during this process, consider writing to the computer maker and Microsoft to express your displeasure at how cheap they are.) With this task done, and ideally after you've made *two* copies for safety, you can trash that partition, resize the Windows boot partition, and install Linux in as many logical partitons as you need.

A side note: *Do not* attempt to move the Windows boot partition using Linux tools! In fact, even resizing it with Linux tools can be risky. Windows is very very fussy about its boot partition, and it will stop booting and be very hard to recover if you muck with it in certain ways. Windows includes a partitioning tool that can be used to resize the Windows partition, so use it for this job.

> 2) Should I keep the windows bootloader thats already there or install grub or similar?

The Windows boot loader is incapable of booting Linux by itself; you *must* install GRUB (or LILO or some other Linux-capable boot loader) to boot Linux. The question is *where* you install GRUB. You can either have it take over the Master Boot Record's (MBR's) boot code area or leave the MBR's boot code area occupied by the Microsoft boot loader and install GRUB in a primary partition's boot record. The latter won't be possible unless you remove *two* of the existing partitions, though, and use one of the two freed partitions for a Linux filesystem. The reason is that the Windows boot loader can't redirect the boot process to logical partitions, only to primary partitions.

As noted above, partition #1 is *not* a Windows boot loader, at least not exclusively. You should probably keep it in place.

---

### Post by Mark Phelps on 2010-09-17
Based on the little info you've provided, it's a guess saying whether or not the first partition IS a boot loader partition.

You can find that out by looking for the "boot" directory and the "bootmgr" program.  These are what Win7 uses to boot, and if they are in that partition, then it IS a boot loader partition.

As to why it's there, I thought by now that it would be common knowledge that this is the default partitioning scheme that most (if not all) large-scale OEMs use when they setup Win7 machines.

The rationale, at least when they started doing it (which, BTW, is the SAME default scheme used by the Win7 installer when it encounters an unformatted drive during installation), was to allow users to encrypt their entire Win7 OS partition.  Since the boot loader can't run when it's encrypted, it (and its supporting files) must be installed to an unencrypted partition -- hence, the "boot" partition that OEMs stick onto their systems.

I would agree, however, that you should leave it alone.  If you remove it, you won't be able to boot Win7.

However, you can download the EasyBCD program from the NeoSmart Technology forums, install it, and it will provide you a feature that will allow you to "move" the Win 7 bootloader files into your Win7 OS partition.  Once you do that and confirm that you can reboot Win7 OK, you could then remove the "boot" partition.

---

