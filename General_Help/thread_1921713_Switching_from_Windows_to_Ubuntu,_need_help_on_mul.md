---
title: "Switching from Windows to Ubuntu, need help on multiple harddrives"
date: 2012-02-07
forum: General Help
---

### Post by syntaqx on 2012-02-07
Hey guys,
I've been putting off switching to Ubuntu for far too long now.. but I've run into a problem that I'm not sure if there's an elegant solution for.

Currently, I have a Windows 7 install with a 128 GB SSD and a 500 GB SATA drive. My configuration more or less looks like this as far as files are placed:

SATA = C:\Users\Me\*
SSD  = Operating system, programs, drivers, and almost everything else

What would be the best way of accomplishing the same thing with Ubuntu?

I've considered mounting my /home/me to the secondary drive, which would more or less give me the same result, but as a web developer, a lot of my files are going to be within /var/www as well. Plus, I don't understand the internals of Linux file storage to ensure that I won't run out of space on my 128GB SSD.

Anyways, let me know what a good solution will be :)

---

### Post by dragonfly41 on 2012-02-07
Here are some rough ideas to get you started .. just one scenario ..

I would:- 

backup contents of SATA (your data ?)

use ubuntu Live CD and launch GParted

take a screenshot of SSD and SSTA partitions for future reference (post here)

also run in terminal **sudo fdisk -l **(post here)

downsize the (single?) partition (NTFS?) in SATA device from 500 GB to 250 GB

create **extended partition** in unallocated space (250 GB) released by downsizing 

create four **logical partitions **inside extended partition .. typically as follows ..

partition    file system    mount point             label                      size
1                ntfs                                                 shared_data         100 GB
2                ext4                /                              ubuntu_root            20 GB          
3                ext4                /home                     ubuntu_home       100 GB            
4                unallocated                                                                    30 GB

install ubuntu in the two ext4 partitions (set root and home)

setup dual boot Grub between windows and ubuntu

---

### Post by oldfred on 2012-02-07
Are you planning on dual booting or just installing Ubuntu to the SSD?

If you are planning on keeping Windows, I might just start with Ubuntu  on the rotating drive. Yes, it will not be as fast as on the SSD, but  you keep each drive with a bootable system and keep them independent for  operating system and only share data on different drives that would not  prevent booting. dragonfly41's post gives a good idea for partitioning if using the rotating drive for your install.

Not sure how large your var/www will be, but my install with lots of programs is about 7GB in a 25GB /(root) partition. I prefer to leave /home inside my root on the SSD, but move all data to data partitions on my rotating drives. I also have moved all hidden files & folders with data except .wine which I understand is more difficult to redirect. My 7GB includes about 1Gb of .wine just for the Windows version of Picasa.

Many suggest gpt partitions for SSD, but you cannot use gpt with Windows unless you boot with UEFI. I boot with BIOS and just have an old XP install on a old MBR drive.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by syntaqx on 2012-02-07
I actually don't want to have a dual boot, I want to use Ubuntu exclusively. For any of my windows needs (games or photoshop) I think a VirtualBox will be sufficient.

Would you recommend the same approach for that?

---

### Post by Cheesemill on 2012-02-07
> **syntaqx said:**
> I actually don't want to have a dual boot, I want to use Ubuntu exclusively. For any of my windows needs (games or photoshop) I think a VirtualBox will be sufficient.
In that case I would use the entire SSD for / and have /home and swap on the HD.

---

### Post by syntaqx on 2012-02-07
So what would I need to do to get /home and swap on the rotating drive from the install screen? Sorry, kinda retarded when it comes to custom installations.

---

### Post by oldfred on 2012-02-08
I prefer to partition in advance with gparted from Ubuntu liveCD or a gparted liveCD. Then you have total control of partitions and locations. I also prefer to in effect split /home into user settings which have to be in /home and user data which really can be anywhere. Then /home is tiny and stays on SSD in / to help in loading user settings faster. Only data which is accessed less often is on rotating drive.

You have a large SSD. I normally make / (root) only 25GB. 

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

If you are thinking of installing systems other than Debian based, data partitions may have UID or GID issues. 
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

---

