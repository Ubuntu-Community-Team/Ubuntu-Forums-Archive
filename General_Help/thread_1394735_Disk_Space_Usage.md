---
title: "Disk Space Usage"
date: 2010-01-31
forum: General Help
---

### Post by hutsky on 2010-01-31
[SIZE=2]I need help in handling space allocation on my hard disk with Ubuntu 9.10 installed.  I set aside a 40 GB partition for Ubuntu installation.  After installation of Ubuntu and several applications I received a warning that the system was about to run out of disk space.  Checking the space allocation I found the following:[/SIZE]
 

 [SIZE=2]_Filesystem_[/SIZE][SIZE=2]	[/SIZE][SIZE=2]_Type_[/SIZE][SIZE=2]	[/SIZE][SIZE=2]_Size_[/SIZE][SIZE=2]	[/SIZE][SIZE=2]_Used_[/SIZE][SIZE=2]	[/SIZE][SIZE=2]_Avail_[/SIZE][SIZE=2] [/SIZE][SIZE=2]_Use%_[/SIZE][SIZE=2]	[/SIZE][SIZE=2]_Mounted On _[/SIZE] 
 [SIZE=2]/dev/loop0 	ext3  	17G	15G 	471M	 97%  	/[/SIZE]
 [SIZE=2]/dev/sda1	fuseblk	40G	18G 	22G  	 45%  	/host[/SIZE]
 

    [SIZE=2]I am not familiar with how Ubuntu/Linux allocates and uses the disk space.  It seems the 40GB partition is there but not fully available to Ubuntu.  Have I set the partition up incorrectly or improperly installed the system?  How do I solve the problem?  Thanks for any suggestions.[/SIZE]

---

### Post by rahulabc on 2010-01-31
Go to System>Administration>System Monitor>File Systems

There u can get info. graphically about the disk space used by ubuntu and total space available.

---

### Post by hutsky on 2010-01-31
> **rahulabc said:**
> Go to System>Administration>System Monitor>File Systems

There u can get info. graphically about the disk space used by ubuntu and total space available.


I had already tried that.  That is where I obtained the information in my post.  The thing I do not understand is that 40 GB of space is allocated to the partition yet the system (Ubuntu) states that I am running out of space for the system when only 15 GB are used and advising me that I have only about 400 MB of storage remaining.

---

### Post by SecretCode on 2010-01-31
It looks like you are running "wubi", where the file system is contained within windows, because of that loop0 device (and the /host mount).

But the entire /host partition is 40GB and the /dev/loop0 is only 17GB so something is not clear.

Can you post the output of 
```
sudo fdisk -l
```
(Post it between [ code ][/ code ] tags to keep the formatting.)

In any case, 15GB is a lot to have used with just a few applications - have you also loaded your own photos/movies etc? Can you also post the output of the following 3 commands:
```
du -hx --max-depth 1 /
du -hx --max-depth 1 /host
du -hx --max-depth 2 /home

```

---

### Post by hutsky on 2010-02-01
> **SecretCode said:**
> It looks like you are running "wubi", where the file system is contained within windows, because of that loop0 device (and the /host mount).

But the entire /host partition is 40GB and the /dev/loop0 is only 17GB so something is not clear.

Can you post the output of 
```
sudo fdisk -l
```(Post it between [ code ][/ code ] tags to keep the formatting.)

In any case, 15GB is a lot to have used with just a few applications - have you also loaded your own photos/movies etc? Can you also post the output of the following 3 commands:
```
du -hx --max-depth 1 /
du -hx --max-depth 1 /host
du -hx --max-depth 2 /home

```


**I have attempted to provide the requested information.  Thanks for your assistance.  It is no doubt apparent that I am new to Ubuntu.**

```

hutsky@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002eee0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5093    40909491    7  HPFS/NTFS
/dev/sda2            5710       18764   104864287+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c662bec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       31198   250591224    7  HPFS/NTFS
/dev/sdb2           31199       35046    30909060    b  W95 FAT32
/dev/sdb3           35047       58741   190330087+   5  Extended
/dev/sdb5           35047       58741   190330056    7  HPFS/NTFS
----------------------------------------------------------------------------


hutsky@ubuntu:~$ du -hx --max-depth 1 /
6.7M    /bin
146M    /opt
du: cannot read directory `/root': Permission denied
4.0K    /root
du: cannot read directory `/etc/ssl/private': Permission denied
du: cannot read directory `/etc/ppp/peers': Permission denied
du: cannot read directory `/etc/cups/ssl': Permission denied
du: cannot read directory `/etc/chatscripts': Permission denied
17M    /etc
du: cannot read directory `/lost+found': Permission denied
16K    /lost+found
4.0K    /selinux
du: cannot read directory `/tmp/pulse-PKdhtXMmr18n': Permission denied
96K    /tmp
16K    /media
208M    /lib
4.0K    /mnt
du: cannot read directory `/var/lib/gdm': Permission denied
du: cannot read directory `/var/lib/PolicyKit': Permission denied
du: cannot read directory `/var/lib/ggzd/gamedata': Permission denied
du: cannot read directory `/var/lib/polkit-1': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/spool/cron/crontabs': Permission denied
du: cannot read directory `/var/spool/cron/atjobs': Permission denied
du: cannot read directory `/var/spool/cron/atspool': Permission denied
du: cannot read directory `/var/spool/cups': Permission denied
du: cannot read directory `/var/cache/ldconfig': Permission denied
du: cannot read directory `/var/cache/system-tools-backends/backup': Permission denied
3.2G    /var
4.0K    /boot
12K    /.cache
0    /dev
4.9G    /home
0    /proc
0    /sys
4.0K    /srv
6.4G    /usr
4.0K    /host
8.1M    /sbin
15G    /

----------------------------------------------------------------------

hutsky@ubuntu:~$ du -hx --max-depth 1 /host
512    /host/$RECYCLE.BIN
20K    /host/System Volume Information
18G    /host/ubuntu
18G    /host

-----------------------------------------------------------------------

hutsky@ubuntu:~$ du -hx --max-depth 2 /home
16K    /home/hutsky/.qt
32K    /home/hutsky/.nautilus
964K    /home/hutsky/.adobe
12K    /home/hutsky/.renpy
4.0K    /home/hutsky/.gnome2_private
28K    /home/hutsky/.gl-117
4.0K    /home/hutsky/.ssh
100K    /home/hutsky/.gconfd
200K    /home/hutsky/.pulse
4.0K    /home/hutsky/Ubuntu One
35M    /home/hutsky/.mozilla
124K    /home/hutsky/GNUstep
24K    /home/hutsky/.xine
4.0K    /home/hutsky/.icons
24K    /home/hutsky/My GCompris
12K    /home/hutsky/.tomatoes
52K    /home/hutsky/Documents
4.0K    /home/hutsky/.Trash
28K    /home/hutsky/.gnupg
28K    /home/hutsky/.AbiSuite
308K    /home/hutsky/.evolution
4.0K    /home/hutsky/Videos
1.4M    /home/hutsky/.kde
4.0K    /home/hutsky/.fonts
44K    /home/hutsky/.gramps
448K    /home/hutsky/.macromedia
4.0K    /home/hutsky/Templates
308K    /home/hutsky/.tuxmath
36K    /home/hutsky/.schoolsplay.rc
4.0K    /home/hutsky/Public
2.8M    /home/hutsky/.openoffice.org
684K    /home/hutsky/.config
132K    /home/hutsky/.scribus
464K    /home/hutsky/.gimp-2.6
8.0K    /home/hutsky/.wxbanker
12K    /home/hutsky/.PiXJuegos
16K    /home/hutsky/.gegl-0.0
8.0K    /home/hutsky/.emilia
34M    /home/hutsky/Music
4.0K    /home/hutsky/.sdlnewstuff
160K    /home/hutsky/.tomboy
304K    /home/hutsky/.pcsx
28K    /home/hutsky/.wapi
20K    /home/hutsky/.fgfs
1.2M    /home/hutsky/.cache
12K    /home/hutsky/.fltk
224K    /home/hutsky/.java
16K    /home/hutsky/.sane
4.0K    /home/hutsky/.xinput.d
12K    /home/hutsky/.mission-control
1.8M    /home/hutsky/.gconf
20K    /home/hutsky/.tuxpaint
28K    /home/hutsky/.dosemu
5.1M    /home/hutsky/.thumbnails
4.0K    /home/hutsky/.themes
28K    /home/hutsky/pysycache
0    /home/hutsky/.gvfs
12K    /home/hutsky/.dbus
600K    /home/hutsky/.gnome2
252K    /home/hutsky/.assistant
48K    /home/hutsky/.pokerth
8.0K    /home/hutsky/.ggz
2.3G    /home/hutsky/Desktop
256K    /home/hutsky/.fontconfig
173M    /home/hutsky/.local
8.0K    /home/hutsky/.frozen-bubble
556K    /home/hutsky/.gstreamer-0.10
8.0K    /home/hutsky/.update-notifier
12K    /home/hutsky/.update-manager-core
2.4G    /home/hutsky/Pictures
8.0K    /home/hutsky/.tuxtype
32K    /home/hutsky/.gnucash
4.9G    /home/hutsky
4.9G    /home

```

---

### Post by SecretCode on 2010-02-01
You provided all the requested information just right, thanks!

Firstly, the 15G usage is quite a lot - but since there is 6.4G in /usr (and 3.2G in /var), it just says that you have installed some pretty large applications. The 4.9G in /home is your actual documents - and obviously some installations have a lot more than that.

So it's unlikely that you can quickly clear out some space.

What's wrong - and not what you planned - is that your partition /dev/sda1 (the first partition on the first physical disk) is 40GB in size, but it's formatted as NTFS (the *fdisk* output shows this). Your Ubuntu installation is actually in the folder C:\ubuntu on this drive - and it shows up as /host/ubuntu 18G in the *du ... /host* listing. This is how "wubi" works.

What you probably meant to do was use the entire /dev/sda1 partition for Ubuntu, with a Linux format (ext3 or ext4 instead of ntfs). This would in any case be more reliable and better performing than using wubi.

You have two basic options ... 
* you could reinstall Ubuntu from scratch, onto this partition /dev/sda1 - and reinstall all your applications. This might be simplest if you haven't done a lot of configuring
* or you could use a tool like clonezilla to image the existing installation ... although thinking about it ... I don't know how you can make an imaging tool run against a wubi installation.

There is no way that I know of to resize an installation done with wubi. 

Third option is to back up all your existing data - the /home directory - reinstall as above, then copy back the /home directory which would restore all your settings and documents.

How do you want to go ahead?

---

### Post by hutsky on 2010-02-03
Thanks for your reply.  Your explanation is clear and makes sense to me.  It was not my intent to install within Windows but it seems that is what I did.

I do not have anything on the drive that really matters if it is lost.  I have only recently begun looking at Linux via Ubuntu and see its potential.  I can see myself using it more as I become familiar wit it.  I think the best solution is to make a fresh start by re-installing.  Is Ubuntu 9.10 the correct choice?

Before installing I think I will expand the 40 GB partition to 80 GB and keep the remaining 80 GB for file storage that can be used by both Ubuntu and Windows.  Does this make sense?  I store a moderate amount of pictures and some music but nothing significant.  Most of my storage amounts to personal records and information files.

I have Windows Vista on another 500 GB drive and am able to dual boot to either system and would like to keep that capability.  I have also been able to connect all into my personal wireless network which has three computers and a couple of printers.  I also like that capability  I am rather familiar with Microsoft's products but am very new with Linus and networking.

I am most appreciative of the assistance you provide and welcome any suggestions you can offer.

OHIO, USA

---

### Post by SecretCode on 2010-02-03
Yes, a reinstall with Ubuntu 9.10 is a good choice. Your plan to repartition is OK.

First boot into the existing ubuntu installation and copy any individual data files or folders you want to save - to a different drive.

When you reinstall you'll need to boot from the Ubuntu CD and tell it to install to the hard drive. When it prompts you to partition the disk, do not use the entire disk! - Make sure it goes into the 80GB partition you'll have created. (It will also suggest a swap partition which can be carved out of the same space - this is normal but actually not required.)

Your existing windows installation on the other drive should be found and included in the "GRUB" boot loader. 

Networking with other computers and printers all works fine - but this would be a good thing to test out in your current installation before you reinstall.

If you are unsure of details post new threads and you're bound to get help here!

---

### Post by hutsky on 2010-03-05
SecretCode,
 
Your earlier explanation was clear and allowed me to understand where I went wrong with the earlier installation.  I repartitioned the disk and installed Ubuntu as you suggested.  It works fine and with a little bootloader work I am now able to selectively boot between Ubuntu and Windows.  I am still becoming acquainted with the Linus system and find that it has many desirable features.  Thanks again for your assistance.

---

### Post by crlutes on 2010-04-15
This is not really a reply but a similar question.  New to the forum and not sure if this is the appropriate way to do this.  Please advise if I'm in the wrong forum and posting incorrectly.

My question is this.  I installed Ubuntu on a laptop for my daughter and after removing/deleting the windows partitions I ended up with the attached allocation.  I'm not sure if I should be combining the first 3, placing those under sda3, or in fact, exactly what is the "Best" way to organize ubuntu devices.

Any and all help will be greatly appreciated.


Thanks
Carl Lutes

[email]carl.lutes@gmail.com[/email]

---

### Post by srs5694 on 2010-04-15
> **crlutes said:**
> My question is this.  I installed Ubuntu on a laptop for my daughter and after removing/deleting the windows partitions I ended up with the attached allocation.  I'm not sure if I should be combining the first 3, placing those under sda3, or in fact, exactly what is the "Best" way to organize ubuntu devices.

There is no single "best" way to organize a Linux installation. First, some background: Under Linux, most partitions are "mounted" at specific directories. All systems use a root (/) filesystem, and you can optionally split most specific subdirectories off into their own partitions. For instance, you can put /home or /usr or /usr/local on separate partitions. This enables you to separate them for safety (to keep filesystem errors on one partition from damaging data on another), to integrate multiple physical disks, to simplify future software upgrades, and to do other things. Swap space is a special case in that it's not mounted, although it's usually put in its own partition with a size to match or exceed the size of RAM on the computer. (Your screen shot shows only 1.19GB in swap space. If the laptop has more than 1GB of RAM you might want to increase that so that you can use suspend-to-disk features.)

I believe that by default Ubuntu just creates one mongo huge root (/) partition and one swap partition. IMHO, though, it makes sense to split off /home, since this creates better flexibility in future software upgrades -- you can wipe out your current install to install an upgraded version, or even an entirely different distribution, without sacrificing user data. Advanced users often split off other directories, such as /usr, /var, /tmp, and others. New users aren't likely to benefit from this, though, unless they have specific needs that they understand better than most new users do. In the three-partition configuration I've described (/, /home, and swap), the root (/) partition should be 5-20GB, depending on how much software you plan to install; swap should be as big as your RAM or a bit bigger, and /home should be everything else.

Given your current layout, the path of least resistance is to merge /dev/sda1 and /dev/sda2 and use it as /home, keeping /dev/sda5 as root (/). /dev/sda5 is a bit big for this use, but not by much. (You could shrink it to increase your swap space size, if desired.) If you've already installed Ubuntu (and it looks as if you have), you'll need to do a bit of juggling to get this done; or you could merge your first two partitions and then re-install, telling the system to use the new partition (probably /dev/sda1) as /home from the start. Post again with details of what you want to do for more advice.

---

