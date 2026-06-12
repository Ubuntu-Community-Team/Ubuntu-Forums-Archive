---
title: "how to change the disk to boot from ?"
date: 2012-09-15
forum: General Help
---

### Post by masuch on 2012-09-15
Hi,

After have been released new grub* ubuntu packages couple of days ago and have been properly installed ... my booting disk sequence has been changed.
---
sda DATA disk
sdb booting disk , grub
sdc DATA disk
sdd booting disk , grub
---
before installation it was ok and booting has been done from sdb which is correct.
after grub* packages have been installed - booting (grub menu) is taken from sdd disk instead of from sdb.

Is there any way how to force it to boot from sdb again ?

(Both disks sdb and sdd are properly booting if I choose one of them to boot from BIOS)

thank you,
kind regards,
M.

---

### Post by oldfred on 2012-09-15
Some like a gui. But you have to go into advanced options to choose boot drive.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

But from any working install your can install the grub2 boot loader to any MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But grub remembers where it originally installed. That may have been your problem.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You can use the BootInfo report in Boot-Repair to see what grub is installed in what MBR and then use BIOS to choose which to default from. I prefer to have the boot loader in the same drive's MBR as the install. That way when (not if) one hard drive fails, my other drives have all the files needed to boot.

---

### Post by dcstar on 2012-09-16
> **masuch said:**
> 
..........
Is there any way how to force it to boot from sdb again ?


```
sudo dpkg-reconfigure grub-pc
```

---

### Post by YannBuntu on 2012-09-17
Hello

> **masuch said:**
> my booting disk sequence has been changed.
---
sda DATA disk
sdb booting disk , grub
sdc DATA disk
sdd booting disk , grub
---
before installation it was ok and booting has been done from sdb which is correct.
after grub* packages have been installed - booting (grub menu) is taken from sdd disk instead of from sdb.

Is there any way how to force it to boot from sdb again ?

This is not a problem in GRUB/Ubuntu.
This is your BIOS that changed the boot order. You can modify it via your BIOS setup menu.

---

### Post by oldfred on 2012-09-17
Ubuntu reports my drives as the motherboard port order plugged into the BIOS. Except I have one empty in the middle and when I plug in a flash drive that can be first, middle or last or sda, sdc or sde reordering all my drives.

But BIOS controls which drive is boot drive and the order they boot in. And grub will always call the boot drive hd0. As near as I can tell grub then follows the same order as Ubuntu for the remaining drives. Or I normally boot from my SSD which is usually sdd and grub sees as hd0. Then sda is hd1.

---

### Post by masuch on 2012-10-13
Hi,

Thank you very much to all of you for help.

First problem was/is that sometimes BIOS does not properly detect some of the drive/s (not all of them) what can leads to reordering of disk drives.

At this moment I am using > grub-install /dev/sdX to change from which disk I want to see menuentry (within last couple of weeks 100 % success. Unfortunately no other suggestions worked for me - tried many times) - [COLOR="Green"]BUT the grub-install has to be done on the same running OS instance where "grub menuentry" supposed to be booted/started/taken from[/COLOR].

---------------------------------
(little corresponding thing - just for 12.10 (last 4 days) - Every time when grub is installed (what happened for last couple of days very often), my booting process went to grub rescue shell, so I have to always type an usual stuff:
> set prefix=(hd0,gptX)/boot/grub
set root=hd0,gptX
insmod normal
normal

and boot into instance, where I want to see, on the next reboot, grub menuentry taken from (after typed grub-install /dev/sdX) )

At this moment it is only one way for me how to achieve what I need :-(  .(That's what I have been experiencing for last couple of weeks. Due to that fact, I am seriously thinking about temporarily prevent to install grub* packages using something like apt-get --config-file --no-upgrade for specific package - if it is possible :-)

regards,

M.

---

### Post by oldfred on 2012-10-13
Are you using UEFI, if not you need a bios_grub partition for grub to install correctly.

Are you checking where grub expects to reinstall? And/or running BootInfo from Boot-Repair to know what is installed where?

---

### Post by masuch on 2012-10-14
> **oldfred said:**
> Are you using UEFI, if not you need a bios_grub partition for grub to install correctly.

> For couple of instances I am using bios_grub booting partitions, some of them are uefi. What I have been talking about previously are flagged by bios_grub flag.


Are you checking where grub expects to reinstall? And/or running BootInfo from Boot-Repair to know what is installed where?
One of my ubuntu instance which I am mainly using is on oczrevo drive SSD. Due to lack of open source driver (because of license nonsenses) for this hard disk (it is offering only as an enterprise driver as the binary file and only for some kernel versions - I did not succeeded to force to install it in different kernel versions than driver has been compiled - so it useless for me to use it) I cannot boot/grub "directly" from this raid0 OS instance. I have to boot/grub up from different OS partition (have to had exactly same initrd versions) and than start my OS instance on my RAID SSD drive. menuentry similar to this:
> set root=(/dev/disk/by-uuid/numberA)
search --no-floppy --fs-uuid --set=root numberA
linux /boot/vmlinuz-3.5.0-17-generic root=UUID=numberB


I cannot use "numberA" and "numberB" as the same disk and partition.

It looks understandable that every time when grub is going to install, after reboot, went to grub rescue shell.
(by the way update-initramfs -u -k all is my favourite command) 

That is how it is working from the moment when I bought ssd disk one year ago. 
BUT, if you have some ideas how to persuade my os instance within 
grub installation to finalize it properly I would like to learn new stuff. 
Every time when grub is going to be installed (different version/changing grub directory/s does not have influence on it) it behaves like that. 
This is only happening for only one OS ubuntu (mainly used) instance located on oczrevo disk as raid0. All other (backup) ubuntu instances do not have this problem and never had.

Usually I am not checking where is grub installed - but it is visible within installation process. 
(When something is going worse than that, I have onlive cloned OS instances (by rsync) from currently running OS instance (exec from crontab each 4 hours) to another partition and to another raid0 filesystem, which are automatically generated into grub.cfg through 40_custom. So, if one OS instance does not work for whatever reason - I can switch immediately to cloned instance , which is max 4 hours old version (including my web server/ftp server and all other dev stuff).

bootinfoscript - I have run it minutes ago and at the first glance , except info about installed grub version, I did not find it more informative than blkid, fdisk, gdisk, fstab, mdadm.conf, grub.cfg, 40_custom - maybe I should dig more deeply.


I understand that all about this is out of topic of this thread but just trying to explain that.

M.

---

### Post by oldfred on 2012-10-14
If it is RAID, then you should use the Alternative installer. It has the RAID driver where the standard desktop install does not. You can add the driver when using liveCD mode.

# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

I do not know RAID but you do have to install to the root of the RAID drive not the MBR.

I think it is similar to this, but there are many types of RAID and it may vary.
For RAID reinstall from liveCD
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

