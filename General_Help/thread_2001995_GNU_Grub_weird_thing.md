---
title: "GNU Grub weird thing"
date: 2012-06-11
forum: General Help
---

### Post by RimSide on 2012-06-11
Okay, I don't know where to post this, or really how to explain. I went to install Ubuntu 10.04 (old I know, but I plan to update). The installation is over, and I reboot my computer, select Ubuntu to boot, and then a thing pops up. A black screen with text that says "GNU Grub", and some other stuff, then something like a command line interpreter, and the Ubuntu GUI doesn't load.

Does anyone know what I'm talking about? And if so, can anyone help me?

---

### Post by oldfred on 2012-06-11
Welcome to the forums.

It seems grub may not be installed correctly. Run this from liveCD and post link to Boot Info report it creates. Then we can see your configuration in detail.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by RimSide on 2012-06-11
well I can do this, but I can't post the data yet. The computer I am having troubles with my parents wont let me hook it up to the internet :(


What do you mean by the boot info? Where do I go to see this?

---

### Post by joe4ska on 2012-06-11
If oldfred's suggestion doesn't work I'd reinstall and let Ubuntu choose how to partition everything.

Are you dual booting two distributions or something unique?

---

### Post by RimSide on 2012-06-11
> **joe4ska said:**
> If that doesn't work I'd reinstall and let Ubuntu choose how to partition everything.

Are you dual booting two distributions or something unique?

I am trying to do a dual booting of windows and ubuntu but it got screwed up somehow. Do you know what oldfred means?

---

### Post by gn0m3boy on 2012-06-12
Looks like your kind of stuck since your parents want let you hook it up to the internet....sounds like my Dad  :p

Anyways, oldfred is talking about a program called [[COLOR="Blue"]Boot Repair[/COLOR]]("https://help.ubuntu.com/community/Boot-Repair")

Since your parents want let you hook up to the internet your other option is to get the Ubuntu Derivative called [[COLOR="Blue"]Ubuntu Secure Remix[/COLOR]]("https://help.ubuntu.com/community/UbuntuSecureRemix") which comes with Boot Repair already installed on it...

Download the ISO from here: [[COLOR="Blue"]http://sourceforge.net/projects/ubuntu-secured/files/[/COLOR]]("http://sourceforge.net/projects/ubuntu-secured/files/")

Burn it to CD just like you did Ubuntu and crank it up in the computer your having GRUB issues with....

REMEMBER:  read all the documentation on the Boot-Repair page before you use it...Use it at your own risk.  

Let us know if this works or if you resolve the issue yourself,  what you did....thanks in advance  ;)

---

### Post by Kira_Belka on 2012-06-12
> **RimSide said:**
> I am trying to do a dual booting of windows and ubuntu but it got screwed up somehow. Do you know what oldfred means?
hi, it's not new prob.
I think most ubuntu users(exclude console adepts :) ) faced with this thing.
So I got two ways how to solve it easy.
1. using GRUB (grub-pc, grub-2)
so you have to install it on boot partition(disk) (/dev/sda for example)
if your grub is broken.. it's not a prob too.
you can do it without any special program.
you need just two things.
First is Ubuntu install/boot CD.
Second one is a bit patience and 5-7 minutes of your priseless time :lolflag:
1. Boot from CD..
2. wait
3. Click on "Try Ubuntu"
4. wait
5. Open Ubuntu "application" menu .. choose - accessories - then choose "terminal" ( i'm typing from phone now so I can mistake in menu names)
6. open "Places" menu ..  you 'll see list places (Documents, Home and etc) and partitions. Choose your linux partition (btw you 'll see your win partition in list too).
Partition 'll mount.
And you 'll see its icon on desktop(with any name).
7. type in terminal mount
you 'll see list of mounted partitons.
8.  Find your partition. for example /dev/disks/by-uid/bla-bla-bla /media/bla-bla-bla
9. type in terminal:
 sudo mount --bind /dev /way-to-your-where-your-partition-mounted/dev   
for example:
sudo mount --bind /dev /media/bla-bla-bla/dev
same for proc and sys
example:
sudo mount --bind /sys /media/bla-bla-bla/sys
sudo mount --bind /proc /media/bla-bla-bla/proc
10. type in terminal:
sudo chroot /way-to-your-where-your-partition-mounted
for example: sudo chroot /media/bla-bla-bla
11. you 'll see ubuntu root invitations.
12. type fdisk -l 
you 'll see list of partitions.
for example:
/dev/sda1
/dev/sda2 (so /dev/sdxY where x - letter from a to z 
and Y - number from 1 to 1000000 :)
if you have old PC .. you can see /dev/hdxY also).
13. type install-grub ( or grub-install ) on your disk
for ex: install-grub /dev/sda  (or grub-install /dev/sda)
14. update-grub (or grub-update) 
15. reboot :)

2. using EasyBCD ( in windows)
configuration of EasyBCD depends on your win7 configuration too.

---

### Post by gn0m3boy on 2012-06-12
Now that's REALLY nice 8)

---

### Post by RimSide on 2012-06-12
> **Kira_Belka said:**
> hi, it's not new prob.
I think most ubuntu users(exclude console adepts :) ) faced with this thing.
So I got two ways how to solve it easy.
1. using GRUB (grub-pc, grub-2)
so you have to install it on boot partition(disk) (/dev/sda for example)
if your grub is broken.. it's not a prob too.
you can do it without any special program.
you need just two things.
First is Ubuntu install/boot CD.
Second one is a bit patience and 5-7 minutes of your priseless time :lolflag:
1. Boot from CD..
2. wait
3. Click on "Try Ubuntu"
4. wait
5. Open Ubuntu "application" menu .. choose - accessories - then choose "terminal" ( i'm typing from phone now so I can mistake in menu names)
6. open "Places" menu ..  you 'll see list places (Documents, Home and etc) and partitions. Choose your linux partition (btw you 'll see your win partition in list too).
Partition 'll mount.
And you 'll see its icon on desktop(with any name).
7. type in terminal mount
you 'll see list of mounted partitons.
8.  Find your partition. for example /dev/disks/by-uid/bla-bla-bla /media/bla-bla-bla
9. type in terminal:
 sudo mount --bind /dev /way-to-your-where-your-partition-mounted/dev   
for example:
sudo mount --bind /dev /media/bla-bla-bla/dev
same for proc and sys
example:
sudo mount --bind /sys /media/bla-bla-bla/sys
sudo mount --bind /proc /media/bla-bla-bla/proc
10. type in terminal:
sudo chroot /way-to-your-where-your-partition-mounted
for example: sudo chroot /media/bla-bla-bla
11. you 'll see ubuntu root invitations.
12. type fdisk -l 
you 'll see list of partitions.
for example:
/dev/sda1
/dev/sda2 (so /dev/sdxY where x - letter from a to z 
and Y - number from 1 to 1000000 :)
if you have old PC .. you can see /dev/hdxY also).
13. type install-grub ( or grub-install ) on your disk
for ex: install-grub /dev/sda  (or grub-install /dev/sda)
14. update-grub (or grub-update) 
15. reboot :)

2. using EasyBCD ( in windows)
configuration of EasyBCD depends on your win7 configuration too.

In 6, what do you mean by Partition 'll mount?
and linux partition and all? just the folders in the drive that you can see the contents of?
Other than that, the partition things are the only stuff I'm confused about. I know what a partition is, but in this case do you just mean the folders that would be the root folder of the os?

Ok nvm. when you add the bla bla bla I get confused too. Is there a clear statement of this I can see? with maybe picture references?


And everyone assumes I have windows 7... On the computer I'm talking about it's windows xp. Does that effect any of what you said?

---

### Post by Kira_Belka on 2012-06-12
> In 6, what do you mean by Partition 'll mount?
mmm.. I told about visual side of this process so you 'll see new icon(with name of drive/partition) on your desktop.
> and linux partition and all? just the folders in the drive that you can see the contents of? 
All partitions.
> Other than that, the partition things are the only stuff I'm confused about. I know what a partition is, but in this case do you just mean the folders that would be the root folder of the os? I told about your root partition( you can pass some steps if you know its name or IDs.)
> Ok nvm. when you add the bla bla bla I get confused too. Is there a clear statement of this I can see? with maybe picture references? I didn't want to confuse you.. 
result of "fdisk -l" command on my PC:
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8bb18bb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       40405       60802   163838976    7  HPFS/NTFS
/dev/sda2               1       38245   307200000   83  Linux
/dev/sda3           38245       40405    17346560    5  Extended
/dev/sda5           38245       40405    17345536   82  Linux swap / Solaris
results for  "ls /dev/disk/by-uuid" on my PC
> 6650A8C850A8A073		      f8337772-31e5-46e6-9d0d-c0c1928dc291
d8a7c43a-5604-4177-b6ed-97fd92aa25df
so bla-bla-bla in this case is > f8337772-31e5-46e6-9d0d-c0c1928dc291 or > 6650A8C850A8A073.

> And everyone assumes I have windows 7... On the computer I'm talking about it's windows xp. Does that effect any of what you said? it changes only one thing.. EasyBCD works only with win7 bootloader. so then only GRUB or any third-part bootloader(something like Acronis OS selector) is available. anyways installation and repairing of grub doesn't depend from your second OS( Xp or win7 or mb win98 :) )

---

### Post by RimSide on 2012-06-12
I guess it just loads the grub bootloader. I don't think there is anything wrong with it. Unless it normally doesn't load the grub bootloader and grub doesn't automatically start ubuntu.

If the first stated is the case, what do I need to do to manually boot ubuntu?

---

### Post by oldfred on 2012-06-12
What Kira_Belka  is trying to walk you thru is the chroot procedure to reinstall grub2 from a liveCD. More examples  in these links. 


Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot with screen shots
[http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html](http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html)
[]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html")

---

