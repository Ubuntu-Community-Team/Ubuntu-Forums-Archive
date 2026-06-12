---
title: "/ full"
date: 2010-05-25
forum: General Help
---

### Post by Randymanme on 2010-05-25
randymanme@randymanme-desktop:~$ sudo fdisk -l 
 [sudo] password for randymanme:  
  
 Disk /dev/sda: 250.1 GB, 250059350016 bytes 
 240 heads, 63 sectors/track, 32301 cylinders 
 Units = cylinders of 15120 * 512 = 7741440 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xffffffff 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1        6935    52428568+   7  HPFS/NTFS 
 /dev/sda2            6936       24333   131525748    7  HPFS/NTFS 
 /dev/sda3           25355       32302    52516454+   5  Extended 
 /dev/sda5           25355       27912    19334196   83  Linux 
 /dev/sda6           32012       32302     2192841   82  Linux swap / Solaris 
 /dev/sda7           30636       30798     1232248+  82  Linux swap / Solaris 
 /dev/sda8           30799       32011     9169920   83  Linux 
 /dev/sda9           27912       30634    20578304   83  Linux 
  
 Partition table entries are not in disk order 
 randymanme@randymanme-desktop:~$  
 

 My inquiry concerns /dev/sda8 (/) and /dev/sda9 (/home).  Presently, sda8 is 8.75 GiB with 8.05 GiB used and 706.82 MiB unused; while /dev/sda9 is 19.62 Gib with 1.60 GiB used and 18.03 unused.  My OS keeps warning me that I'm running out of disk space but seems to keep putting every thing in /.
 

 What can I do about this?  What can I cut and paste from / to /home?  Computer janitor has been grinding away for 35 minutes and doesn't seem to be making any progress, but doesn't respond to the cancel button, either.
 

 Any help would be appreciated.
 

 By the way, I have 7.37 GiB of unallocated space.  How might I format that and put some  files from /dev/sda8 there?  Thanks.

---

### Post by philinux on 2010-05-25
Check this first. I've never gone over 5 gig in my /.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by rob-ward on 2010-05-25
also if you could paste the output of the following two commands it could help to see if there are any other issues causing it
```
mount
```

```
df -h
```

---

### Post by Randymanme on 2010-05-25
Thanks for your responses.  I'll have to check out the links later.:)

---

### Post by Randymanme on 2010-05-25
randymanme@randymanme-desktop:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda9 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/randymanme/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=randymanme)
randymanme@randymanme-desktop:~$ 
randymanme@randymanme-desktop:~$ 
randymanme@randymanme-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             8.7G  7.7G  527M  94% /
none                 1000M  336K  999M   1% /dev
none                 1007M  352K 1006M   1% /dev/shm
none                 1007M  204K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda9              20G  1.2G   18G   7% /home
randymanme@randymanme-desktop:~$

---

### Post by dino99 on 2010-05-25
a little info how to get partitions:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

if you need/want to resize partitions, boot on partedmagic to do it.

you can clean the system too:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install -f

sudo apt-get install gconf-cleaner
( run it : apps system gconf-cleaner)

more room can be done with bleachbit too

---

### Post by Randymanme on 2010-05-25
randymanme@randymanme-desktop:~$ du -h /var/cache/apt/  
 4.0K	/var/cache/apt/archives/partial  
 241M	/var/cache/apt/archives  
 268M	/var/cache/apt/  
 randymanme@randymanme-desktop:~$ sudo apt-get clean  
 [sudo] password for randymanme:  
 randymanme@randymanme-desktop:~$ sudo apt-get clean  
 randymanme@randymanme-desktop:~$ sudo apt-get autoclean  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 randymanme@randymanme-desktop:~$ sudo apt-get autoremove  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.  
 randymanme@randymanme-desktop:~$  
 

 

 randymanme@randymanme-desktop:~$ sudo du -h /var/log  
 104K	/var/log/gdm  
 4.0K	/var/log/unattended-upgrades  
 4.0K	/var/log/dist-upgrade  
 1.3M	/var/log/installer  
 7.9M	/var/log/bootchart  
 12K	/var/log/fsck  
 12K	/var/log/cups  
 8.0K	/var/log/ConsoleKit  
 408K	/var/log/apt  
 16K	/var/log/clamav  
 4.0K	/var/log/samba/cores/winbindd  
 8.0K	/var/log/samba/cores  
 20K	/var/log/samba  
 4.0K	/var/log/apparmor  
 4.0K	/var/log/news  
 4.0K	/var/log/speech-dispatcher  
 14M	/var/log  
 randymanme@randymanme-desktop:~$  
 

 

 

 

 randymanme@randymanme-desktop:~$ df -Th /dev/sdXX  
 df: `/dev/sdXX': No such file or directory  
 df: no file systems processed  
 randymanme@randymanme-desktop:~$  
 

 

 randymanme@randymanme-desktop:~$ sudo find / -name ''lost+found'' | sudo xargs du -h  
 16K	/lost+found  
 16K	/home/lost+found  
 randymanme@randymanme-desktop:~$  
 

 

 randymanme@randymanme-desktop:~$ sudo apt-get install deborphan gtkorphan  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following extra packages will be installed:  
   dialog  
 The following NEW packages will be installed:  
   deborphan dialog gtkorphan  
 0 upgraded, 3 newly installed, 0 to remove and 24 not upgraded.  
 Need to get 384kB of archives.  
 After this operation, 2,273kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe deborphan 1.7.28ubuntu1 [82.3kB]  
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe dialog 1.1-20080819-1 [271kB]  
 Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe gtkorphan 0.4.4-1 [30.7kB]  
 Fetched 384kB in 1s (278kB/s)    
 Selecting previously deselected package deborphan.  
 (Reading database ... 515991 files and directories currently installed.)  
 Unpacking deborphan (from .../deborphan_1.7.28ubuntu1_i386.deb) ...  
 Selecting previously deselected package dialog.  
 Unpacking dialog (from .../dialog_1.1-20080819-1_i386.deb) ...  
 Selecting previously deselected package gtkorphan.  
 Unpacking gtkorphan (from .../gtkorphan_0.4.4-1_all.deb) ...  
 Processing triggers for man-db ...  
 Processing triggers for menu ...  
 Processing triggers for desktop-file-utils ...  
 Processing triggers for python-gmenu ...  
 Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...  
 Processing triggers for python-support ...  
 Setting up deborphan (1.7.28ubuntu1) ...  
 

 Setting up dialog (1.1-20080819-1) ...  
 Processing triggers for menu ...  
 Setting up gtkorphan (0.4.4-1) ...  
 randymanme@randymanme-desktop:~$  
 

 

 randymanme@randymanme-desktop:~$ sudo deborphan  
 [EMAIL="randymanme@randymanme-desktop"]randymanme@randymanme-desktop[/EMAIL]:~$
 

 (no orphaned packages found)

---

