---
title: "Hard Drive Partitions All Messed Up!"
date: 2012-06-18
forum: General Help
---

### Post by JackOConnor on 2012-06-18
Firstly, I wasn't that sure where to post this so if there's somewhere better please tell me and also it's not entirely concerning linux. 
       
      OK, I have a 500gb hard drive and a while back I installed ubuntu 11.10 on it alongside windows 7. At the time I thought that all I would be using from then on would be ubuntu so I made the size of the linux partition so large that all windows had left was 55gb. However, recently I began gaming again and ubuntu does not satisfy my needs in that field. I thought it would be easily changed but I was wrong. Using GParted in ubuntu I'm not allowed to touch the windows partition at all but I made the linux side smaller to free up space. Then I went into windows to find that the c drive's maximum size is 55gb even though it had been 500gb before. I have found that the reason for this problem is because the free space is called "free space" when it has to be called "unallocated" in order for it to be absorbed into the c drive.
 
         Is there a way for me to make it into "unallocated" space and if not, I've heard that uninstalling and reinstalling linux after I've changed the partition will work, is it safe to do this if my computer boots linux first and I access windows through it. 
 
         Please help, I'd much rather not go to the trouble of uninstalling linux if there's a quicker way.

---

### Post by sudodus on 2012-06-18
There are several ways to solve your problem. But first of all: editing partitions is risky, so you should have a recent backup of as much as possible:

1. An image of the whole drive (for example using a boot CD or USB drive with Clonezilla).
or at least
2. A recovery disk for Windows plus backup of all your private files (documents, pictures, personal video clips etc).

Please post the output of the following command (within CODE tags, that you get by marking the text and pressing the # sign at the top of the editing window)!```

sudo fdisk -lu
```
It makes it easier to understand and help.

---

### Post by JackOConnor on 2012-06-18
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe062c19d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   117394347    58593750    7  HPFS/NTFS/exFAT
/dev/sda3       117395454   976771071   429687809    5  Extended
/dev/sda5       117395456   117899263      251904   83  Linux
/dev/sda6       117901312   121804799     1951744   82  Linux swap / Solaris
/dev/sda7       141338624   346138623   102400000   83  Linux
/dev/sda8       346140672   352434175     3146752   83  Linux
/dev/sda9       960167936   976771071     8301568   82  Linux swap / Solaris
/dev/sda10      352436224   943548415   295556096   83  Linux
/dev/sda11      943550464   960157695     8303616   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 32.5 GB, 32463912960 bytes
256 heads, 45 sectors/track, 5504 cylinders, total 63406080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    63406079    31703024    c  W95 FAT32 (LBA)
```

There you go, hope this helps.

---

### Post by sudodus on 2012-06-18
You have 4 linux partitions and 3 swap areas.

Do you have different linux versions on those partitions? And are you using them, or is there any junk occupying disk space?

It should be enough with one swap area (partition). So you should be able to wipe the other two. If you want to hibernate, you need at least a swap size equal to the RAM (in GiBi-bytes). Otherwise it can be smaller.

The reason why Windows can't expand into the free space is that the Windows partitions are outside the extended partition and the free space is inside it.

An easy solution would be to rely on the backup and wipe the whole extended partition.

Then boot into Windows and increase the size of the partition next to the free space.

Then boot into an Ubuntu live session and create an extended partition and inside it linux partitions and a swap partition.

And finally install Ubuntu again using the option 'Something Else' at the partitioning screen.

---

### Post by JackOConnor on 2012-06-18
Yes, I know it's a mess. There's only one linux distro there believe or not! It's a long story. 

Just so we are clear, you want me to back up linux, wipe linux off the hard drive, expand windows into where I want it and then reinstall linux by setting up the partitions first in a live cd session? 

Also if what I have said above is correct, can you tell me what the correct linux partitions are for ubuntu 11.10?

Another question, can I not just set up the linux partitions in the something else option?

Thanks for your help so far.

---

### Post by sudodus on 2012-06-18
> **JackOConnor said:**
> Yes, I know it's a mess. There's only one linux distro there believe or not! It's a long story. 

Just so we are clear, you want me to back up linux, wipe linux off the hard drive, expand windows into where I want it and then reinstall linux by setting up the partitions first in a live cd session? 

Also if what I have said above is correct, can you tell me what the correct linux partitions are for ubuntu 11.10?

Another question, can I not just set up the linux partitions in the something else option?

Thanks for your help so far.
Well, it will probably be easier and safer than to do a lot of resizing and moving of logical partitions and the extended partition.

But backup what you think is relevant. Unless you have a lot of configuring, it might be enough to backup your private files from the linux partitions.

And don't forget to back up Windows, because it might also be damaged during the partition editing!

I would suggest that you use an ext4 file system for the root partition. Swap is swap, unless you select encrypted home directories. Then encrypted swap will be created automatically from the original swap partition (at least with 12.04 LTS).

Another question is if you want one partition or separate
root and home partitions

/
/home

and possibly a separate data partition (NTFS if it should be accessible from Windows, otherwise ext3 or ext4), or a partition for testing other linux distros.

It should be enough with 32 GB for the root partition unless you plan to save a lot of data there. Data can be saved in either /home or a separate data partition.

*Edit: If you plan to backup+wipe+install, test 12.04 as a live session booted from CD/USB, and if it works well, use that instead of 11.10, because it is an LTS version with 5 years of support.*

---

### Post by JackOConnor on 2012-06-18
Thanks, I'll give that a try!

---

### Post by JackOConnor on 2012-06-18
Actually, just to let you know, I'm going to wait until Thursday to do this as I'm in the middle of exams and I don't want to rush it.

---

### Post by Mark Phelps on 2012-06-18
> Then I went into windows to find that the c drive's maximum size is 55gb even though it had been 500gb before. I have found that the reason for this problem is because the free space is called "free space" when it has to be called "unallocated" in order for it to be absorbed into the c drive.

That's because "free space" is unused space INSIDE a partition, where "unallocated space" is unused space OUTSIDE a partition.

Since partitions can't overlap, to move free space from partition 2 to partition 1, you have to do the following:
1) Shrink partition 2 to eliminate the free space.  The free space will now turn into unallocated space.
2) Expand partition 1 to incorporate the unallocated space.

A further complication is that, if the free space is inside a partition INSIDE an Extended partition, you have to shrink the INSIDE partition first, then, shrink the Extended partition -- before it can become unallocated space.

---

### Post by JackOConnor on 2012-06-19
Thanks, this the type of method I was looking for, but since my hard drive is such a mess, I'm just going to do it the other way to clean it up. Thanks for your input though.

---

### Post by Deepak J on 2012-06-19
yep the best thing to do is to clean it first. Better get rid of those unwanted swap partitions. Well it's using quite a lot of space. It'll turn into a problem only when you start having much data on your drive.

---

### Post by JackOConnor on 2012-06-27
Ok, sorry everyone, my internet was gone for the past week, maintenance or something like that was the excuse.

So anyway I have some questions.

[LIST=1]
[*]How do I back up windows and my current version  of ubuntu?
[*]How much memory will I need to back up windows if my c drive is 55gb and just about full?
[*]How do I actually wipe the whole side with ubuntu and the junk space?
[/LIST]
I know these questions are probably basic but please help!

---

### Post by U202E on 2012-06-27
if nothing will help:

[LIST]
[*]Wine with winetricks can help you to easyly install games on ubuntu, **really** need for speed world **will work on Wine**.
[*]you could use ext2fsd, which is a filesystem driver for windows, so that you can access your ubuntu partition from windows 7 (even if you use ext3 or ext4).
[*]or integrate windows 7 into ubuntu:
[LIST]
[*]put seamless rdp onto your windows 7 c drive
[*]install virtualbox OSE on ubuntu (or VMware)
[*]create 2 virtual harddisks pointing to win7 and sys-reserved partition
[*]access win7 running in virtualbox with rdesktop
[/LIST]
[/LIST]
info about the second thingy:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/) <<seamless rdp
[help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization") <<how you **could** use seamless rdp.
[https://www.virtualbox.org/](https://www.virtualbox.org/) <<sudo apt-get install virtualbox-ose **/ **the software center will work to
```
Login into linux and locate your windows partition:  terminal ”sudo fdisk -l” Device Boot      Start         End      Blocks   Id  System /dev/sda1               1        1306    10490413+  27  Unknown **/dev/sda2   *        1307       20110   151041024    7  HPFS/NTFS** /dev/sda3           20111       24328    33881085   83  Linux /dev/sda4           24329       38913   117154012+   5  Extended /dev/sda5           24329       24450      979933+  82  Linux swap / Solaris /dev/sda6           24451       38913   116174016   83  Linux In  my case, windows partition is ‘dev/sda2&#8242; (the one with NTFS filesystem format)

```
and make a vmdk file to that partion (windows 7 will not work without some sort of system reserved partition) (100 MB or so, it can be 400MB)
sudo vboxmanage internalcommands createrawvmdk -filename ~/.VirtualBox/vista_physical_partition-sda.vmdk -rawdisk [B]/dev/sda2
[FONT=Arial]if it doesn't work:
[/FONT][/B]sudo vboxmanage **-convertSettings** internalcommands createrawvmdk -filename ~/.VirtualBox/vista_physical_partition-sda.vmdk -rawdisk /dev/sda2
[B][FONT=Arial]make sure you replace sda2 with your partition. (and you could change the name of the vista_partition-sda.vmdk)

now make yourself owner of those vmdk's[/FONT][/B] with the terminal
sudo chown <your_user_name> ~/.VirtualBox/vista_physical_partition-sda.vmdk

then create a virtual machine that uses the win7.vmdk file
before you run it goto setting>storage>add another drive>system_reserved.vmdk

and you can click that link above to figure out how seamless rdp works.

---

### Post by JackOConnor on 2012-06-27
I already know about wine but to avoid the hassle of it I'm going to run my games on windows, for now at least.

Look, all I want to know is the answers to my three most recent questions.
> 
[LIST=1]
[*]How do I back up windows and my current version  of ubuntu?
[*]How much memory will I need to back up windows if my c drive is 55gb and just about full?
[*]How do I actually wipe the whole side with ubuntu and the junk space?
[/LIST]
I do appreciate your help though. If you could please answer those questions it would be great. I want windows and ubuntu separate.

---

### Post by sudodus on 2012-06-27
> **JackOConnor said:**
> Ok, sorry everyone, my internet was gone for the past week, maintenance or something like that was the excuse.

So anyway I have some questions.

[*]How do I back up windows and my current version  of ubuntu?

I suggest that you download the iso file of ***Clonezilla*** and make a boot CD or USB drive and use Clonezilla to backup your drive or selected partitions (make image files). This way you can get a complete backup so that you can restore your drive or partitions to exactly what there were a the backup moment.
> 
[*]How much memory will I need to back up windows if my c drive is 55gb and just about full?

Depending on how well it can be compressed maybe 30 to 40 GB.
> 
[*]How do I actually wipe the whole side with ubuntu and the junk space?

Boot from an Ubuntu live CD or USB drive and run ***gparted*** to view and edit your partition table. ***Backup first*** because this is risky!!!
> 
I know these questions are probably basic but please help!

---

### Post by JackOConnor on 2012-06-27
Thanks very much. So basically, to back up windows I'm going to need a memory stick or another hard drive? Hopefully I can squeeze it on to my 32gb!!![-o<

---

### Post by sudodus on 2012-06-27
> **JackOConnor said:**
> Thanks very much. So basically, to back up windows I'm going to need a memory stick or another hard drive? Hopefully I can squeeze it on to my 32gb!!![-o<
I would not rely on a memory stick for backup. I strongly recommend that you get a an external hard disk drive.

---

### Post by JackOConnor on 2012-06-27
On second thought, your probably right. Ok, I'll report back in a few days when I've managed to procure one.

---

### Post by JackOConnor on 2012-07-04
I finally managed to get another hard drive to back up on and I downloaded clonezilla but I'm terrified of using it.

I have it on a live cd and I'm just afraid of doing something wrong and messing up everything. All I want to backup is windows 7. I don't want to back up ubuntu, I don't have it very long and there's nothing on it that I can't get again very easily.

So my main hard drive is 500gb. 100mb of that is the windows boot and 55gb is the c drive. That's what I want to clone. The drive that I'm going to use to backup is a 250gb internal drive.

Could someone please give me a guide on how to do this and then how to verify the backup?

---

### Post by oldfred on 2012-07-04
I have not done a full backup of my old XP as it now is used so little. But many have suggested these options. Often better to use Windows tools for Windows and Linux tools for Linux.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by sudodus on 2012-07-04
> **JackOConnor said:**
> I finally managed to get another hard drive to back up on and I downloaded clonezilla but I'm terrified of using it.

I have it on a live cd and I'm just afraid of doing something wrong and messing up everything. All I want to backup is windows 7. I don't want to back up ubuntu, I don't have it very long and there's nothing on it that I can't get again very easily.

So my main hard drive is 500gb. 100mb of that is the windows boot and 55gb is the c drive. That's what I want to clone. The drive that I'm going to use to backup is a 250gb internal drive.

Could someone please give me a guide on how to do this and then how to verify the backup?

Following Clonezilla's text-based wizard and choose ***beginner*** mode. I run that mode myself ;-)

Select to make an image file on your external drive and continue answer to the questions. If necessary, I can help you understand what to answer in a particular case.

According to post #3 your sda1 and sda2 partitions contain Windows, and the rest of the drive is an extended partition with several linux partitions and swap partitions.
```
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   117394347    58593750    7  HPFS/NTFS/exFAT
```

If you haven't changed the partitions for Windows, you can backup only these two partitions (and the MBR if you like, but the MBR will probably be overwritten anyway.)

/dev/sda1
/dev/sda2

It is actually simpler to backup the whole drive, but when you want to restore Windows without overwriting Ubuntu, it is better to have a backup with only the Windows partitions.

---

### Post by JackOConnor on 2012-07-04
I used driveimage XML to back up my drive. Then, I wiped all of the Linux stuff, extended the c drive and reinstalled Ubuntu(12.04). All that I then had to do was go into windows to make it aware of Ubuntu using easy BCD to make a boot menu. A problem arose. It wouldn't boot. I had this problem previously. You see, when I originally installed Ubuntu, I choose the install alongside windows option instead of "something else". Then when I turned on the computer, Ubuntu would boot first and I would access windows through it. Previously, I tried to change this and the same thing happened as is happening now. It says :> Loading operating system...
..................error: no such partition.
grub rescue>
I tried typing help but it didn't recognise the command. So basically windows won't boot now so I can't use easy BCD to set up the boot menu.

Can anyone help me? I have no idea what the problem is, bar the fact that it's not damage from changing the  partitions unless I did it during my first install of Ubuntu. I want to boot windows first.

---

### Post by JackOConnor on 2012-07-04
Update:

I used boot repair and now at least I can boot both windows and Ubuntu. Apart from the boot problem the whole operation went smoothly. 

I still have a problem though. When the system boots, the first thing that boots is Ubuntu with it's boot menu. From there I can access windows but there are two options to boot windows from now.

Also, I want windows to boot first so the first thing that I can see is the easy BCD screen and I can access Ubuntu from there. But I'm going to mark this thread as solved and start another one because my original problem is solved. You can find the new thread here [http://ubuntuforums.org/showthread.php?p=12076107#post12076107](http://ubuntuforums.org/showthread.php?p=12076107#post12076107)
I solved it by:

[LIST=1]
[*]Backing up windows 7  with ***DiskImage XML ***onto a separate hard drive.
[*]Booting Ubuntu 12.04 from a live cd.
[*]Using ***GParted*** I Deleted all of the Ubuntu partitions and expanded the windows c drive.
[*]Then I reinstalled Ubuntu using the "something else" option.
[*]Fixed boot using boot repair.
[/LIST]
I'd like to thank everyone for all their help. It is greatly appreciated. Hopefully someone can help me solve my new problem!

---

