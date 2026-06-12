---
title: "Base System Install &amp; Disk Space on Ubuntu"
date: 2009-12-18
forum: General Help
---

### Post by roonie on 2009-12-18
I recently installed Ubuntu 9.10 on my Laptop with WinXP Pro on dual boot. The installation process went fine but at the end of the whole thing I had 2 issues. 

Issue No.1: After the installation, the available disk space on my main Linux partition was just 2GB, after installing updates and all, it come down to 843.3 MB which sucks because I have to be very careful of what I install on it. I installed it on a 20GB partition and I don't think Ubuntu takes up that much space.

When I bring up the Properties tab for the Filesystem I get this

[QUOTE
]Name: /
Type: folder(inode/directory)

Contents: 369,511 items, totalling 20.2 GB
          (some contents unreadable)

Location:

Volume: unknown

Free space: 843.3 MB[/QUOTE

I also did a **sudo  fdisk -l**. below is the output

> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       14592    96727365    f  W95 Ext'd (LBA)
/dev/sda5            2551        3885    10723356   83  Linux
/dev/sda6            3886        4007      979933+  82  Linux swap / Solaris
/dev/sda7            4008        5100     8779491   83  Linux
/dev/sda8            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda9            7651       10200    20482843+   7  HPFS/NTFS
/dev/sda10          10201       12750    20482843+   7  HPFS/NTFS
/dev/sda11          12751       14592    14795833+   7  HPFS/NTFS


Is anyone else experiencing a similar issue?

Issue No.2: When I use WinXP Pro, It keeps asking me to install some Base System device. I have No clue what drivers I should be looking for or why it is even asking me to install that. Initially I thought that it may have something to do with the HDD and the space issues on Ubuntu but I ruled that out because all my other partitions were unaffected. I've disabled them from the Device Manager so I don't get the install prompt anymore but I still would really like to know what it was?

Anyone have any idea WHAT windows wants?

---

### Post by plucky on 2009-12-18
Open a terminal and post output of ```
df -h
```

Do you have a separate /home partition?

My / partition is 4G used and I think after install it was 2.4G without the any extra software installed.

---

### Post by nightspore on 2009-12-18
The filesystems properties isn't a good indicator of how much space your Ubuntu install is using, as it also contains all of the files in your /home and /media partitions.

Go to System - Administration - System Monitor, & click on the file systems tab. That lists all of the partitions, how much drive space they're using & how much is still available.

---

### Post by warfacegod on 2009-12-18
Some or most of your missing drive space may be do to ubuntu reserving disk space. I think it's default is 5% of the partition.

Terminal commannd tune2fs will help you change that I believe. Search the forums for it and or other ways to reduce reserved space.

---

### Post by roonie on 2009-12-20
@Plucky

Here's the output from df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              11G  9.1G  801M  93% /
udev                  750M  288K  750M   1% /dev
none                  750M  1.4M  749M   1% /dev/shm
none                  750M  196K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
none                  750M     0  750M   0% /lib/init/rw
none                   11G  9.1G  801M  93% /var/lib/ureadahead/debugfs
/dev/sda1              20G   18G  2.3G  89% /media/sda1
/dev/sda8              20G   13G  6.9G  65% /media/sda8
/dev/sda9              20G  2.1G   18G  11% /media/sda9
/dev/sda7             8.3G  2.1G  5.8G  27% /media/Augie
/dev/sda11             15G  1.9G   13G  14% /media/Installers
/dev/sda10             20G  7.2G   13G  37% /media/App

I don't have a separate /home, its all on the same partition.

@nightspore

I checked the System Monitor setting, my main file system is on sda5.  It show's that its 92% used up.

@warfacegod

I used tune2fs to change the reserved space to 2% already but that did not make a difference.

---

### Post by plucky on 2009-12-20
```
/dev/sda5 11G 9.1G 801M 93% /
/dev/sda7 8.3G 2.1G 5.8G 27% /media/Augie
```

Your / partition is 11G and your other linux partition is 8.3G + swap makes up the 20G for your install.

Have you copied a lot of file into your /home directory?

Check out this [thread](http://ubuntuforums.org/showthread.php?t=898573) on how to check for disk full problems.

Good luck

---

### Post by SecretCode on 2009-12-20
Also check the output of du
> du -hx --max-depth 1 /

And then if, for example, /home is taking up most of the space, go to the next level with 
> du -hx --max-depth 1 /home

---

### Post by roonie on 2009-12-21
This is the output from the sudo du -hx --max-depth 1 / command:

72K	/tmp
16K	/lost+found
200K	/srv
15M	/etc
201M	/lib
0	/proc
du: cannot access `/home/omar/.gvfs': Permission denied
5.4G	/home
4.0K	/selinux
2.6G	/usr
172K	/media
0	/dev
4.0K	/mnt
5.4M	/bin
46M	/opt
30M	/boot
0	/sys
7.8M	/sbin
746M	/var
136K	/root
12K	/.cache
9.0G	/

The highest capacities /home is taking up 5.4 Gb, / is 9.0Gb and /usr 2.6Gb 

I think it copied alot of my files from my Windows installation during Install as I remember it asking me if I wanted to. I see all my documents from windows in the ubuntu documents folders too.

Is there any way of checking how many files have been copied and remove them?

---

### Post by SecretCode on 2009-12-21
2.6G for /usr is OK. But your 5.4G in /home is the culprit (compared to a plain Ubuntu install, that is). (The 9G for / is just the total.)

Post the output of 
```
sudo du -hx --max-depth 1 /home
```

---

### Post by roonie on 2009-12-21
Here the output 

1.1G	/home/omar
1.1G	/home

I found Disk Usage Analyser under Application > Accessories and it gave me a detailed view of all the space used on the drive with space used in each folder. I saw that there was about +4GB in the Trash folder which I emptied and now my Filesystem shows 5.1GB Free Space.

I think that is what I wanted to find out. It was pretty dumb of me not to look through that earlier :/

---

### Post by SecretCode on 2009-12-21
That's better!

If you still want to find out what's using the remaining 1.1G you can just repeat the du command, each time examining a specific subfolder (the largest one, or one of the largest) - like _sudo du -hx --max-depth 1 /home/**omar**_ ... although the disk usage analyzer is effectively the same, and easier!

---

### Post by roonie on 2009-12-25
Thanks everyone for your responses!! I`ll mark this post as SOLVED now.

---

