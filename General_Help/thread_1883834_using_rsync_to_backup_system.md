---
title: "using rsync to backup system"
date: 2011-11-20
forum: General Help
---

### Post by rng on 2011-11-20
I am trying to use rsync to backup my system to external usb hard disk. There are 3 questions:

1. Can I use rsync to backup running system or do I need to boot from livecd and then run rsync to copy hard disk system to external usb disk?

2. Does the format of external usb hard disk need to be ext4 only or can I use fat32 or ntfs also?

3. Is following command sufficient or any other option is needed and do I need a '/' after each folder name? 

```
rsync -av --delete /media/ubuntu_hard_disk /media/ext_usb_disk
```

Thanks for your help.

---

### Post by papibe on 2011-11-20
Hi rng.

I would use rsync to backup personal data and configuration files, but it make less sense to me to use it to backup a booting partition. For that I would recommend taking a look at [Clonezilla]("http://clonezilla.org/").

Backing up to ext4 would preserve ownership and permissions, however ntfs will make it easy to access your data from almost any platform. I would avoid at all costs fat32.

Just some thoughts.
Regards.

---

### Post by raja.genupula on 2011-11-20
Hi man use this link , it have complete rsync info 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

1...you can take backup from running system. no problem.
2...i think any type format will be fine . no restrictions in that.

---

### Post by rng on 2011-11-20
I am keen to use rsync since it can update only changed files and would take less time. I think clonezilla will get the entire system every time.

For running rsync from running system, the command should be (I think): 

```
rsync -av --delete / /media/ext_usb_disk
```

---

### Post by rng on 2011-11-29
Do I need to exclude /media /sys and /proc folders? 

rsync -auv --exclude='/media' --exclude='/proc' --exclude='/sys'   /  /media/backup-partition

---

### Post by Lars Noodén on 2011-11-29
> **rng said:**
> Do I need to exclude /media /sys and /proc folders? 

Also exclude /dev

---

### Post by oldfred on 2011-11-29
You cannot copy to NTFS and preserve ownership and permissions as Windows does not support that. NTFS is ok for data, but not system. Use a Linux filesystem.

Example script in post #20
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

I plan on total reinstall, so I only backup configuration and data.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Paddy Landau on 2011-11-29
May I ask why you want to back up the entire system?

To back up the entire system, as papibe said, use [CloneZilla]("http://www.clonezilla.org/"). It's fast and thorough.

But I wouldn't bother, because if you totally break your system, it's quicker to reinstall especially if your [FONT=Fixedsys]/home[/FONT] is on a separate partition; if it's not, restore your entire [FONT=Fixedsys]/home[/FONT] folder after reinstalling.

For backing up your data, I recommend looking at [FONT=Fixedsys]rdiff-backup[/FONT]. It uses [FONT=Fixedsys]rsync[/FONT] (so it's fast except for the very first time you back up), but it has the ability to keep previous versions, either indefinitely or for a set period; and you can fine-tune what is backed up. I back up my entire [FONT=Fixedsys]/home[/FONT] folder (for me and everyone else who uses the computer, so I use [FONT=Fixedsys]sudo[/FONT]) with [FONT=Fixedsys]rdiff-backup[/FONT] every day and it takes just 5-15 minutes depending on just how much has changed.

Exclude the following folders when backing up:
```
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
```And, of course, any others that you want excluded.

---

### Post by rng on 2011-11-29
1. I want to backup entire system because I have installed many programs and I will have to reinstall them as well if I do a fresh install.

2. Regarding the folders that I exclude (/proc  /sys etc) - will they be created automatically or do I manually create empty folders with the same name on backup partition. 

3. I want to confirm that I can use rsync to backup the system from within the running system- I do not need a livecd.

---

### Post by nodrog1952iii on 2011-11-29
I have been using rsync to backup my servers (LAMP/Email) as well as my desktops for several years.  No problem at all backing up a live file system and I have recovered from rsync backups multiple times without any issues both on servers, desktops and laptops.

The syntax of my commands are something like this for my servers backing up to a second disk drive:

rsync -vaHx --numeric-ids --delete / /backup_disk/rsync/

or to backup my laptop to a USB device;

rsync -vaHx --numeric-ids --exclude='/home/username/.gvfs' --delete / /media/USB_Device_Name/rsync_from_laptop/

or to backup my laptop to another linux box:

rsync --rsync-path "sudo rsync" -vaHx --numeric-ids --exclude='/home/username/.gvfs' --delete / -e ssh [email]user@domain.tld[/email]:/backup_drive/rsync_from_laptop/

Keep in mind that when you backup to another linux box that you must configure the /etc/sudoers file on the target backup machine for the command to work.

I prefer to back up everything and then invoke most of my exclusions with my recovery command.

FYI,

Gordon

---

### Post by rng on 2011-11-29
@nodrog1952iii: Thanks for the info. What are your recover commands? And you are not excluding /proc, /media, /dev and /sys , as others have suggested.

---

### Post by nodrog1952iii on 2011-11-29
Recovery commands are something like this:

rsync -vaHx --numeric-ids --delete --exclude='proc' --exclude='dev' --exclude='sys' --exclude='media' /media/USB_Device_Name/rsync_from_laptop/ /

Notes: Be careful where your slashes are at the end of your file paths. Also, if you are recovering to a new disk drive (such as after a drive failure), then you need to also exclude /boot and /etc/fstab, however, you need to load the OS and update to the current kernel prior to the recovery.

---

### Post by rng on 2011-11-29
What is the advantage of backing up /proc, /sys and /dev if we are excluding them at recovery? And why do we need to exclude them at all?

---

### Post by nodrog1952iii on 2011-11-30
There is no real advantage to backing up those directories. Also, you don't need to exclude them during recovery operations if you don't want to.  I was merely presenting the commands that I have successfully used in the past.

There are a couple of other issues that I should also point out.

First, using the "x" flag causes rsync to not cross filesystem boundaries.  Therefore, you will need to use a separate rsync command for each partition. For example, it is a common practice to have /, /boot and /home as separate logical partitions. In that case you will then need to execute a separate rsync command to backup each of these partitions.

Secondly, it is quite useful to add the "z" flag (which compresses the data as it is sent to the destination machine) if you are backing up over an internet connection.  The "z" flag can actually slow rsync down over a LAN but typically will speed it up significantly over a WAN.

Also, as I previously  mentioned, if you are recovering a rsync backup to a new disk drive, such as after a disk drive failure, then you need to reinstall your OS and update your kernel to the most recent version prior to your rsync recovery.  Then, your recovery rsync command should exclude /boot and /etc/fstab. This is because each individual hard disk has its own identifying serial number that is embedded in these files for grub to work properly.  Otherwise, grub will not work properly and you will not be able to reboot. In that case, or as an alternative, you will need to boot from your installation/recovery disk and reinstall grub after your rsync recovery operation is complete.

FYI,

Gordon

---

### Post by rng on 2011-11-30
@nodrog1952iii: Thanks for the info.

---

### Post by Paddy Landau on 2011-11-30
> **rng said:**
> 1. I want to backup entire system because I have installed many programs and I will have to reinstall them as well if I do a fresh install.
There is more than one way to do that. You could:

[LIST]
[*]Save a record of the installed programs and, in case of a disaster recovery, have them automatically install on a fresh reinstallation (sorry, I don't know how to do that; it is easy, but I've never had the need to do it so I've never noted how).
[*]Use [FONT=Fixedsys]rsync[/FONT], as you suggested.
[*]Use [CloneZilla]("http://www.clonezilla.org/"), which is reliable and uses less backup space (CloneZilla compresses all data).
[/LIST]

If [FONT=Fixedsys]rsync[/FONT] is your preferred option, then give it a go. You need to test it of course, so this is how I would test:

[LIST=1]
[*]Back up all your data, just in case.
[*]Back up using [FONT=Fixedsys]rsync[/FONT].
[*]Also back up using CloneZilla (in case [FONT=Fixedsys]rsync[/FONT] fails).
[*]Wipe your drive.
[*]Restore from your [FONT=Fixedsys]rsync[/FONT] backup.
[*]If it works, you're done. If it fails, restore using your CloneZilla backup.
[/LIST]
 The advantage of CloneZilla or a fresh installation over [FONT=Fixedsys]rsync[/FONT] is that it will restore your Grub as well.
> **rng said:**
> 2. Regarding the folders that I exclude (/proc  /sys etc) - will they be created automatically or do I manually create empty folders with the same name on backup partition.
Folders such as [FONT=Fixedsys]/proc[/FONT] and [FONT=Fixedsys]/sys[/FONT] are virtual folders. AFAIK, your system should create them automatically. However, when you run your test (step 5 above), you will find out whether or not there is a problem. (The folders that I mentioned in my [post=11498923]previous post[/post] will be created automatically.)

> **rng said:**
> 3. I want to confirm that I can use rsync to backup the system from within the running system- I do not need a livecd.
You don't need a Live CD with [FONT=Fixedsys]rsync[/FONT]. However, there is a chance that some files that are open and locked will be incompletely written due to caching. Of course, running [FONT=Fixedsys]rsync[/FONT] from a running system will necessarily be slower than running CloneZilla.

If you have a requirement to have your system up all the time, making downtime for CloneZilla impractical, I would rather look at running a regular [FONT=Fixedsys]rsync[/FONT] for your data (not your programs), and finding out how to record installed programs to install them automatically should you need a disaster recovery. The big advantage is that your system will not take so long to back up each time you run [FONT=Fixedsys]rsync[/FONT] ([FONT=Fixedsys]rsync[/FONT] over your entire system will slow down your system significantly during its running time).

---

### Post by SeijiSensei on 2011-11-30
I find it easier to use --exclude-from and put the list of exclusions into a file.  

Backing up /proc gains you nothing since it is created anew each time you boot.  It's the structure where the kernel stores needed information about the system and the running processes.  In fact if you try backing up /proc with rsync you'll almost certainly get complaints that directories it intended to back up have vanished.  Usually these are associated with transient jobs that terminated before rsync got to them.

I usually exclude proc, sys, lost+found, and the squid cache on machines where I have that running.

---

### Post by rng on 2011-11-30
Thanks for the details. I think using rsync from a livecd may be the simplest option for backing up entire system.

---

### Post by Orange_and_Green on 2011-11-30
> **Paddy Landau said:**
> 
[*]Save a record of the installed programs and, in case of a disaster recovery, have them automatically install on a fresh reinstallation (sorry, I don't know how to do that; it is easy, but I've never had the need to do it so I've never noted how).


Before reinstalling:


```
dpkg --get-selections > package_list
```

Save the file "package_list" on a partition that you are not going to format or on an external device such as a USB stick.


After reinstalling, open up a terminal, type (without pressing ENTER) ```
sudo apt-get install
``` and copy the packages listed in the file after it, then press ENTER.

---

### Post by Lars Noodén on 2011-11-30
> **Orange_and_Green said:**
> ```
dpkg --get-selections > package_list
```


That accidentally gets all packages, even ones that have been uninstalled.  It also gets the extra column with the status.  To get just the package names, you have to use [awk](http://www.softpanorama.org/Tools/Awk/awk_one_liners.shtml) or an equivalent:

```

dpkg --get-selections | awk '{ if ( $2 == "install" print $1 }' > package_list


```

---

### Post by Orange_and_Green on 2011-11-30
> **Lars Noodén said:**
> That accidentally gets all packages, even ones that have been uninstalled.  It also gets the extra column with the status.  To get just the package names, you have to use [awk](http://www.softpanorama.org/Tools/Awk/awk_one_liners.shtmll) or an equivalent:

```

dpkg --get-selections | awk '{ if ( $2 == "install" print $1 }' > package_list


```

Thanks for pointing that out, I hadn't thought of that :)

I guess another possibility might be then,

```
dpkg --get-selections > package_list
```

save to a safe place, then

```
sudo dpkg --set-selections < package_list
sudo apt-get dselect-upgrade
```

Will change my automatic backup script accordingly... thanks for the tip!!!

---

### Post by Paddy Landau on 2011-11-30
@Orange_and_Green and Lars Noodén: Thank you for the information, which I have duly noted.

There is one missing step: you need to note the non-standard repositories in use from [FONT=Fixedsys]/etc/apt/sources.list[/FONT], and add them before installing the programs.

> **Orange_and_Green said:**
> ```
sudo dpkg --set-selections < package_list
sudo apt-get dselect-upgrade
```
Will that not also deinstall programs marked as such? For example, the results of my [FONT=Fixedsys]dpkg --get-selections[/FONT] includes the line, "[FONT=Fixedsys]akonadi-server deinstall[/FONT]". (Perhaps that is intended?)

There is a potential problem, namely when an application has become obsolete and replaced (such as the proposed change from Banshee to Rythmbox). But that is a minor issue as it is easily fixed.

---

### Post by Orange_and_Green on 2011-11-30
Looking back at the script that I had written 3 years ago or so (and completely forgotten about how I had done it) I've seen that I had used the command:

```
dpkg --get-selections | grep -v deinstall > some_file
```

and appended the first column of the output to apt-get install.

So I guess that packages marked for removal but not uninstalled yet do not get carried over with the method I have been using all this time.

Still, it has always worked for me so far LOL:-\":tongue:

---

### Post by Lars Noodén on 2011-12-01
> **Paddy Landau said:**
> There is one missing step: you need to note the non-standard repositories in use from [FONT=Fixedsys]/etc/apt/sources.list[/FONT], and add them before installing the programs.

I can't think of a way to grab just the extra repositories.  If you have added any, then you'll have to grab the whole [font=Courier new]/etc/apt/sources.list[/font] in your backup plan.

---

### Post by Paddy Landau on 2011-12-01
> **Lars Noodén said:**
> I can't think of a way to grab just the extra repositories.  If you have added any, then you'll have to grab the whole [FONT=Courier new]/etc/apt/sources.list[/FONT] in your backup plan.
Yes, that is correct.

---

