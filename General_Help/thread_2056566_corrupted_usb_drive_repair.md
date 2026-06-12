---
title: "corrupted usb drive repair?"
date: 2012-09-11
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-09-11
Hi All,

I have a Seagate 250 GB HDD with usb interface.

However, the drive is not recognized when I plug it in. 

Gparted shows it is there though.

When the drive is unmounted, it shows up as being present (as a listing in the sidebar of the home directory).

As soon as the drive is mounted, it disappears from the sidebar in the home directory.

Basically, I can't use the drive.

Is there a software solution that might be used to make the drive recognizable???

The problem occurred after I changed the permissions on the drive in order to make it more accessible by other computers and users.

It is formatted to ext4 and I'm running Xubuntu 12.04 . 

TIA

Art

---

### Post by critin on 2012-09-11
> The problem occurred after I changed the permissions on the drive in  order to make it more accessible by other computers and users.Recheck** all **of the permissions.  I know you've probably done that, but I'd do it again.  Something may not have taken.

Use another usb port, those do go bad.

> 
When the drive is unmounted, it shows up as being present (as a listing in the sidebar of the home directory).

This is just strange.

---

### Post by goodbye-windows(tm) on 2012-09-11
When I changed the permissions, I did so to the entire drive with -R. Is it possible some of the existing seagate files related to how the drive performs should not have permissions changed???

I know it is common practice to delete everything all the files from a USB drive, so I didn't think changing the permissions of the seagate file(s) would make any difference.

---

### Post by critin on 2012-09-11
Does it show in Disk Utility?

I'm afraid this is over my head.  I can easily add disks and partitions with standard Share abilities, but using codes/terminal is something I've not tried to do yet.

Someone else will come along and get you fixed up.  Sorry.

---

### Post by varunendra on 2012-09-12
> **goodbye-windows(tm) said:**
> Is it possible some of the existing seagate files related to how the drive performs should not have permissions changed?No. Those seagate files are just part of an autosync/backup program for windows. They do not (and can not) control how the disk should communicate with any OS. So don't worry about that.

Your description of the problem sounds familiar, but is a bit unclear. Is it that -

[LIST]
[*]when you plug-in the drive, it shows up as unmounted? (normally usb drives get auto mounted as soon as connected).
[*]Then, when you 'try' to mount (by clicking or right-clicking the drive) it, it disappears?
[/LIST]
When the drive disappears, does it still show up in gparted? (refresh 'devices' if gparted is already open before it disappears). Does gparted recognize its partition type and size correctly?

When it gets disappeared, please run the following commands in a terminal and post their outputs:
```
dmesg | tail
sudo fdisk -l
mount
```
(while posting, please wrap the outputs in [noparse]```
..and..
```[/noparse] tags to preserve their formatting).

---

### Post by goodbye-windows(tm) on 2012-09-12
> **critin said:**
> Does it show in Disk Utility?



It does show up in Disk Utility, I had to install it as it is not supplied with Xubuntu.

Details:

Fresh boot, plug in drive after logging in to my account.

Nothing happens, no 'drive detected' pop up, no listing of the drive in the left hand sidebar of the home folder. Icon for drive does not appear on the workspace area.

When I open 'disk utility', drove des show up. It is the Seagate drive in the attached screen capture.

-----------------

I should also say I tried to do a 'data recovery' in gparted (using gpart). After spending more than 2 hours searching the drive, gparted said that no detectable file systems were found.

TY.

Art

---

### Post by goodbye-windows(tm) on 2012-09-12
> 
Your description of the problem sounds familiar, but is a bit unclear. Is it that -

[LIST]
[*]when you plug-in the drive, it shows up as unmounted? (normally usb drives get auto mounted as soon as connected).
[*]Then, when you 'try' to mount (by clicking or right-clicking the drive) it, it disappears?
[/LIST]
Yes and no..........

If I boot up with the drive connected, it acts exactly as you  describe, appearing on the workspace and the home folder as an unmounted drive initially.

However, if I boot, then plug in the drive, the drive never shows up anywhere, except in grarted and Disk Utility.

> Does gparted recognize its partition type and size correctly?


Yes, gparted knows the drive is there, has the correct size, the correct label, the correct amount of used space on the drive. I have attached a screen capture of the gparted display.

> When it gets disappeared, please run the following commands in a terminal and post their outputs:OK, please note, the info below is from a fresh boot, drive doesn't show up on workspace, or in the left sidebar of the home folder.

```
artie@superuser-System-Product-Name:~$ dmesg | tail
[   84.252783] sd 6:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[   84.253912] sd 6:0:0:0: [sdb] No Caching mode page present
[   84.253922] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   84.257033] sd 6:0:0:0: [sdb] No Caching mode page present
[   84.257043] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   84.315763]  sdb: sdb1
[   84.319144] sd 6:0:0:0: [sdb] No Caching mode page present
[   84.319155] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   84.319163] sd 6:0:0:0: [sdb] Attached SCSI disk
[   84.744991] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
artie@superuser-System-Product-Name:~$ 
```

```
artie@superuser-System-Product-Name:~$ sudo fdisk -l
[sudo] password for artie: 

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000abec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    46284799    23141376   83  Linux
/dev/sda2        46286846    62531583     8122369    5  Extended
/dev/sda5        46286848    62531583     8122368   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b14eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488396799   244197376   83  Linux
artie@superuser-System-Product-Name:~$ 
```

```
artie@superuser-System-Product-Name:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/artie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=artie)
/dev/sdb1 on /media/Master type ext4 (rw,nosuid,nodev,uhelper=udisks)
artie@superuser-System-Product-Name:~$ 
```

I can give the output of the commands with a fresh boot with the drive plugged in beforehand if you like. Basically, the drive never shows up when it is plugged in after a fresh boot. But, it does show up as an unmounted drive if the drive (and goes poof if I try to mount it) is plugged in before boot up. 

Regards,

Art

---

### Post by varunendra on 2012-09-13
Both the screenshots as well as the command outputs show everything to be fine. The drive seems to be mounted in "/media/Master" directory. Can you list the drive contents using commandline? :
```
ls /media/Master
```
(make it **ls [COLOR=Red]-a[/COLOR] /media/Master** if nothing shows up)

Or, what if you manually tell nautilus (the default file-browser) to go into that directory. In nautilus:
**Go > Location... >***(enter the address-)*** /media/Master > ***press*** 'Enter'**

---

### Post by goodbye-windows(tm) on 2012-09-13
> **varunendra said:**
> Can you list the drive contents using commandline?

OK, ls -a /media/Master and ls media/Master produce the same output.  

In both cases, there is a list for every folder and every file in the root directory. But, every single line ends with 'permission denied'.

Then,  the second half of the output lists every folder and file in the root directory. 

I'm happy to give you the entire output here, if needed.

Here's a single folder output, with other folders and files omitted.

```

artie@superuser-System-Product-Name:~$ ls /media/Master
ls: cannot access /media/Master/all_data_old: Permission denied
.
.
.
.
.
all_data_old
.
.
.
.
.


```

The dots show that some files and folders were not listed.

If I do a sudo ls /media/Master, I get a list of all files and folders without the 'permission denied' lines.

I think nautilus is for gnome and unity. Although I have a very modern (and relatively fast) punchbox, I choose to run Xubuntu. So, I only have Thunar available.

I looked through the file menus in Thunar, there doesn't seem to be a 'go' option.

And, last night I logged in as the superuser and tried to access the drive. I got identical error, drive shows up when it is unmounted, but the icon goes away as soon as the mounting is attempted.

Since I can list the files and folders with a command line, does that mean I can change permissions of the folders and files via the command line?

It occurred to me that the bizarre behavior might be because every single file and folder has improper permissions?? Maybe that's why the drive goes 'poof' when I try to mount it?

And the error did happen after I tried to loosen up the permissions via the command line-is it possible a typo resulted in this error?

Thanks so much for the help, I appreciate it immensely.

Art

---

### Post by cjhabs on 2012-09-13
To make the permissions wide open on all the files under the /media/Master mount point just do:
sudo chmod -R 777 /media/Master/*

---

### Post by critin on 2012-09-13
> I looked through the file menus in Thunar, there doesn't seem to be a 'go' option.

The word "GO" is in the menu along the top of file manager.
I know there is a TAKE OWNERSHIP located somewhere in disk dialogue, but I've only had to do it once and can't remember where it is.  Perhaps it was an old version of disk utility.

---

### Post by goodbye-windows(tm) on 2012-09-13
> **cjhabs said:**
> To make the permissions wide open on all the files under the /media/Master mount point just do:
sudo chmod -R 777 /media/Master/*

OK, I did a

```
sudo chmod -R 666 /media/Master/*
```

command instead. After the process was done, I checked to see if the icon for the drive was visible. It was not. There were no errors. 

I rebooted the computer and found the icon for the drive on the workspace and in the left sidebar of home.

When I double clicked to open the drive, the icon went away again. It's now invisible, but appears to be there when checked with terminal.

It appears nothing has changed, despite doing the chmod command. I used cut and paste, so there were no typos in the entered command.

I just don't know what to do next.

Regards,

Art

---

### Post by cjhabs on 2012-09-14
What are the permissions on the /media/Master folder itself? Compare it to the other mount points in /media

---

### Post by varunendra on 2012-09-14
> **goodbye-windows(tm) said:**
> OK, I did a

```
sudo chmod -R 666 /media/Master/*
```
Firstly, I don't think * is of any use if you are already using the -R option, but I may be wrong. Anyway -
6 = 110b means "rw_" (x missing)
Executable bit is necessary on directories to enable their content listing. No executable bit = No directory listing.

Hence, you can do either 755 or 777 (assuming you don't want to prohibit anyone from directory listing). At least make the first bit 7:
```
sudo chmod -R 777 /media/Master
```

If you are not already the owner, also do:
```
sudo chown -R <your user id> /media/Master
```

Sorry I totally missed that you are using Xubuntu (only noticed thread prefix which is Ubuntu). But there must be some option to manually enter an address. If I got enough time, I'll try it myself on a VM and post back if found something useful.

---

### Post by goodbye-windows(tm) on 2012-09-14
> **varunendra said:**
> Executable bit is necessary on directories to enable their content listing. No executable bit = No directory listing. 

This was a revelation for me, I would have never thought that prohibiting executables would cause the directory not to be listed. Since everything on the drive had a 666, I guess that made the whole drive off limits. A classic example of me (unknowingly) shooting myself in the foot.........

I did the following:

```
sudo chmod -R 755 /media/Master
```

and 

```
sudo chown -R artie /media/Master
```

After executing both commands, there was no change in the listing of the drive on the workspace or in the left hand sidebar of the home directory.

After I rebooted, the drive showed up on the desktop and double clicking it allowed me to see it's contents!!!! I was never so happy to see the contents of that drive as I was just a few moments ago!!!!!!

I need to thank everyone who contributed to this thread. Without the forum and it's contributors, I do not think ubuntu would be viable (for me).

I'll go ahead and play a little with the drive and see how it acts, but this thread will probably end up being marked as 'solved' real soon.

Again, ty to all you contributed technical expertise.

Art

---

### Post by varunendra on 2012-09-16
> **goodbye-windows(tm) said:**
> This was a revelation for me
I myself found this and a lot more info about different permission modes in some article or wiki page once that I dug up out of curiosity (what's the business of 'x' with folders:confused: What is that 'fourth' bit doing there in some directories like /tmp ..??:-k... etc). It was a really interesting read.

Anyway, congratulations for solving the prob. and learning something new..!

---

