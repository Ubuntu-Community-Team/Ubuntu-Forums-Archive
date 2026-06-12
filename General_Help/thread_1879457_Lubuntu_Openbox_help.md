---
title: "Lubuntu Openbox help"
date: 2011-11-11
forum: General Help
---

### Post by jabema on 2011-11-11
I am fairly new to Linux and have been running Lubuntu 11.10 in an Openbox setting in order to learn more about Linux and how it works under the hood.  Its been an interesting journey so far, but I am learning.  I have two questions however that I have not been able to find solutions for:  (I am the administrator and only user of the computer)

1-I am having permission issues with usb drives, both a 320gb external and usb thumb drives.  I cannot access them from file manager (pcman).  I made myself a sudo Pcman item in the menu and using 'gksudo pcmanfm' as the execute I get the password dialog box before Pcman opens and this solves the issue sort of.  Is there any way to bypass this?

I have tried to alter 'User Settings' in the 'Users and Groups' app, with no luck.  I can not access the advanced settings tab in the menu, I am assuming because this is a Gnome app and I am in an Openbox session?? 

2-Directly related to the first question.  I would like to switch over to Dolphin for my file manager in hopes to solve the usb drive permission issue and I use dolphin as a GUI for ssh.  My problem with this is I: ~$ sudo apt-get install dolphin, and  when I run Dolphin from the terminal: ~$ dolphin, I get a blank dolphin.  It launches with no files and several errors in the termnial:

```
jabema@DellLubuntu:~$ dolphin
trying to create local folder /home/jabema/.kde/cache-DellLubuntu: Permission denied
QFile::remove: Empty or null file name
dolphin(26644)/KSharedDataCache KSharedDataCache::Private::mapSharedMemory: Failed to establish shared memory mapping, will fallback to private memory -- memory usage will increase 
trying to create local folder /home/jabema/.kde/share: Permission denied
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
dolphin(26644): "Unable to save bookmarks in /home/jabema/.kde/share/apps/kfileplaces/bookmarks.xml. File reported the following error-code: 13." 
dolphin(26644) KDirWatchPrivate::KDirWatchPrivate: INotify available:  true
trying to create local folder /home/jabema/.kde/tmp-DellLubuntu: Permission denied
trying to create local folder /home/jabema/.kde/socket-DellLubuntu: Permission denied
trying to create local folder /home/jabema/.kde/tmp-DellLubuntu: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/jabema/.kde/socket-DellLubuntu/kdeinit4__0'
trying to create local folder /home/jabema/.kde/cache-DellLubuntu: Permission denied
trying to create local folder /home/jabema/.kde/share: Permission denied
dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

trying to create local folder /home/jabema/.kde/share: Permission denied
trying to create local folder /home/jabema/.kde/share: Permission denied
trying to create local folder /home/jabema/.kde/share: Permission denied
dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

trying to create local folder /home/jabema/.kde/tmp-DellLubuntu: Permission denied
trying to create local folder /home/jabema/.kde/socket-DellLubuntu: Permission denied
trying to create local folder /home/jabema/.kde/tmp-DellLubuntu: Permission denied
QFile::remove: Empty or null file name
kdeinit4: Aborting. bind() failed: Permission denied
Could not bind to socket '/home/jabema/.kde/socket-DellLubuntu/kdeinit4__0'
dolphin(26644)/kdecore (K*TimeZone*): KSystemTimeZones: ktimezoned initialize() D-Bus call failed:  "The name org.kde.kded was not provided by any .service files" 

dolphin(26644)/kdecore (K*TimeZone*): No time zone information obtained from ktimezoned 
dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

dolphin(26644) KFileItemPrivate::init: "/media/PENDRIVE/Night Running" does not exist anymore
dolphin(26644): No ksycoca4 database available! 

dolphin(26644): No ksycoca4 database available! 

QFile::remove: Empty or null file name
QFile::remove: Empty or null file name
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QFile::remove: Empty or null file name
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QFile::remove: Empty or null file name
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(26644)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
```But.... if I ~$ sudo dolphin.  It launches just fine.  It doesn't even prompt me for a password and gives me full access to thumb drives and external drives.

So with that logic, I add the Dolphin item to my menu list and make 'sudo dolphin' the execute.  I then select Dolphin from my menu list and.... (pause for dramatic suspense), absolutely nothing.  Dolphin doesn't launch at all.  

I plan on using Gwenview as well, as I deal with a ton of image files and find it to be one of the best image managers I have ever used.  But I am assuming I am going to have similar issues using it.  

If anyone has any tips or advice on these issues, I would greatly appreciate it.

---

### Post by Rodney9 on 2011-11-11
To my mind there is nothing wrong with PCManFM, I think it maybe the usb, it's permissions have to be changed, this link has a similar problem with a fix - 

[http://ubuntuforums.org/showthread.php?t=1055333&highlight=usb+permission](http://ubuntuforums.org/showthread.php?t=1055333&highlight=usb+permission)

Dolphin is no doubt giving problems as it is a KDE app and Gwenview may also as it too is a KDE app.


For How-To's, Information and Screen-Casts on Lubuntu, and if you need further help, go to the **[Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")** - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Rodney

---

### Post by jabema on 2011-11-11
Okay, I ran through the thread with no luck and I already searched through the One stop thread.  

Heres everything I tried from the thread along with fdisk info

```

jabema@DellLubuntu:~$ sudo fdisk -l
[sudo] password for jabema: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd9a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1953791      975872   82  Linux swap / Solaris
/dev/sda2         1955838    78163967    38104065    5  Extended
/dev/sda5         1955840    78163967    38104064   83  Linux

Disk /dev/sdb: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008dcd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3223366752  3470046675   123339962   f4  SpeedStor
/dev/sdc2   ?   378192737   710426324   166116794   10  OPUS
/dev/sdc3   ?   225603442   225603451           5   74  Unknown

Partition table entries are not in disk order
jabema@DellLubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              36G  3.8G   31G  12% /
udev                  304M  4.0K  304M   1% /dev
tmpfs                 125M  900K  124M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  311M  140K  311M   1% /run/shm
/dev/sdb1             299G   29G  270G  10% /media/External320
/dev/sdc              3.8G  108M  3.7G   3% /media/PENDRIVE
jabema@DellLubuntu:~$ sudo adduser jabema plugdev
The user `jabema' is already a member of `plugdev'.
jabema@DellLubuntu:~$ sudo ls -la /media
total 24
drwxrwxr-x  4 root root 4096 2011-11-11 16:41 .
drwxr-xr-x 23 root root 4096 2011-11-10 09:04 ..
drwx------  1 root root 8192 2011-11-06 22:12 External320
drwx------  8 root root 8192 1969-12-31 19:00 PENDRIVE
jabema@DellLubuntu:~$ sudo chmod 755 /media
jabema@DellLubuntu:~$ sudo ls -la /media
total 24
drwxr-xr-x  4 root root 4096 2011-11-11 16:41 .
drwxr-xr-x 23 root root 4096 2011-11-10 09:04 ..
drwx------  1 root root 8192 2011-11-06 22:12 External320
drwx------  8 root root 8192 1969-12-31 19:00 PENDRIVE
jabema@DellLubuntu:~$
``` 

External320 is my external drive and PENDRIVE is a thumb drive.  I need to keep them ntfs formatted as I share with windows machines.

---

### Post by haresear on 2011-11-11
Do your USB drives auto-mount if you plug them in after the desktop is up and running? If not, there should be a setting to have removable media auto-mount. You might try going to a Lubuntu session or LXDE session when looking for desktop settings -- I experienced some difficulty sometimes trying to find settings in an Openbox session. If you can get it to work the way you want in a Lubuntu or LXDE session you may gather some clues about how to get Openbox to work also.

---

### Post by jabema on 2011-11-11
Yes, everything auto mounts just fine when I plug them in.  If I leave them plugged in and turn off my system I have to remount them on start up.  But when my machine is on everything I plug into it auto mounts.

I had the same machine with the same set up running Kubuntu and had no problems, so I am guessing its an OpenBox specific issue.

---

