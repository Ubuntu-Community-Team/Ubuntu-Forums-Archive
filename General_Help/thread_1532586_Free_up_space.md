---
title: "Free up space?"
date: 2010-07-16
forum: General Help
---

### Post by oleink on 2010-07-16
Hey
I installed a bunch of games.  Some of them were in wine others in cedega.  I removed cedega so all those games are gone.  I don't even know how this happened and I havent installed anything else so we know its not other stuff... but somehow my space on my computer jumped from being like 14-15gb of space taken up to 36gb and I don't know how to remove it... any ideas?

---

### Post by drs305 on 2010-07-16
I wrote a guide on 'lost' disk space, or find out what was filling up disks. It provides both terminal commands and GUI app methods.

Here's the link:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by oleink on 2010-07-16
> **drs305 said:**
> I wrote a guide on 'lost' disk space, or find out what was filling up disks. It provides both terminal commands and GUI app methods.

Here's the link:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Nice thanks. I got 1 gb back... I'll have to try the rest of the stuff later

---

### Post by nmaster on 2010-07-16
depending on how you deleted things, they might be in the trash folder for root.  this is different than your trash folder.

---

### Post by drs305 on 2010-07-16
> **oleink said:**
> Nice thanks. I got 1 gb back... I'll have to try the rest of the stuff later

1GB means there is still a problem. Usually the problem is unemptied trash bins (your's and roots), large log files, a especially large file due to an error, or backups made to the wrong partition. 

The last one is caused by a backup being made without the backup partition being mounted at the time. This causes the files to be written to the system partition instead.

When troubleshooting, make sure to unmount any external or additional internal partitions, as these may mask the problem by hiding files located 'underneath' in a system partition.

If you don't understand any of the commands or results from the link I posted, just ask here.

---

### Post by linux18 on 2010-07-16
Here is a shell script that I use on new installations to lighten the load and perform various actions:

```

#!/bin/sh
echo "this program is designed specifically to free up disk space in ubuntu"
echo 
echo "version 0.01.1    revision 2_lite"
echo 
echo "question 1: will you need to use a printer (y/n)?"
read c 
if [ $c = "n" ] ; then 
  sudo apt-get remove cups hplip foomatic-filters hpijs system-config-printer-common
fi
echo
echo
echo "question 3: will you need to use any help files excluding man pages(y/n)?"
read c
if [ $c = "n" ] ; then
  sudo apt-get remove *buntu-docs
fi
echo 
echo
echo "clean .deb caches (y/n) ?"
read a
if [ $a = "y" ] ; then
  echo "cleaning caches"
  mkdir ~/Documents/Cleaner
  sudo apt-get clean 
  sudo apt-get autoclean 
  sudo apt-get autoremove 
  sudo rm /var/cache/apt/*.bin 
  echo
  echo
fi
echo "clean all '/var/log/' log files (y/n) ?"
echo "errors are normal"
read a
if [ $a = "y" ] ; then
  sudo rm /var/log/* 
  sudo rm /var/log/*/* 
  echo
  echo
fi
echo "run a disk usage diagnostic? " 
read a
if [ $a = "y" ] ; then 
  sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort 
  echo
  echo
  echo
  sudo du -h /var/cache/apt/ 
  echo
  echo
  echo
  sudo du -h /var/log 
  echo
  echo
  echo
  echo "usage of all filesystems"
  sudo df -Th | grep -v "fs" | sort 
  echo
  echo
  echo
  echo "total filesystem disk usage"
  sudo du -hs / | grep -v "read" | grep -v "cannot" 
  echo  
  echo
  echo
  echo
fi

```I wrote this a long time ago before I knew about the read -p option, it works so I haven't re-coded it yet.
All of the commands came from various sources and i just put them together, there is more to the script, but I want to improve it a lot first.

---

### Post by oleink on 2010-07-16
> **drs305 said:**
> 1GB means there is still a problem. Usually the problem is unemptied trash bins (your's and roots), large log files, a especially large file due to an error, or backups made to the wrong partition. 

The last one is caused by a backup being made without the backup partition being mounted at the time. This causes the files to be written to the system partition instead.

When troubleshooting, make sure to unmount any external or additional internal partitions, as these may mask the problem by hiding files located 'underneath' in a system partition.

If you don't understand any of the commands or results from the link I posted, just ask here.

nothing in root trash..

---

