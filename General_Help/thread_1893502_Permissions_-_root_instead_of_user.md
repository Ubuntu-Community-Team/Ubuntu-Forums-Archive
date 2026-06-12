---
title: "Permissions - root instead of user"
date: 2011-12-10
forum: General Help
---

### Post by carlbelmonte on 2011-12-10
I am perfectly new to Ubuntu and like it a lot even if it took a bit of time to get used to it. Now, I try to spend most of my time in Ubuntu instead of Windows, but unfortunately I cannot remove my Windows installation because of legacy applications.

I have a 1.5 TB disk in 5 volumes:
sda1 - Windows XP
sda5 - XP image
sda6 - future backups
sda7 - various sundry files off the system volumes
sda8 - Ubuntu root
sda9 - Ubuntu swap

Also, an external hd in two volumes:
sdb1 - another XP image, you can never have too much backup for Windows since it breaks down so often
sdb2 - backup of various and sundry files

Anyway, initial installation worked fine, but then Windows corruption (perhaps from the Ubuntu installation mishandled by me) forced me to repair the NTFS file system, wiping out GRUB. Since I had no idea how to fix GRUB at the time, I simply re-installed Ubuntu (the ignorant user's solution, but then that is me. But, I am trying to learn.)

The result was that I no longer had permissions for the external hd (sdb1 and sdb2). Or rather, root has permissions and I could access those volumes and read and write but they would appear as
"Image_" instead of "Image" for sdb1
"Backup_" instead of "Backup" for sdb2

A puzzler for me, although not a problem since I did still have read/write access to the volumes.

I have read dozens of posts in this forum, Ask Ubuntu, and other places and tried the proposed remedies without completely understanding (since, in large part, people who answer do not really explain what is going on, and as usual in public forums there are a certain amount of contradictory or different responses making it hard to know what is right or wrong.) A sure recipe for disaster.

Nothing has worked.

Then, last night, I ran NTFS-config, the NTFS configuration tool, and tried to give myself read/write privileges for all volumes.

But, now I no longer have read/write privileges for the File System, although I do for the Home directory. The File System is now owned by root - how did that happen?

And in the File Manager (is that what is called Nautilus?), my sdb volumes do appear as "Image" and "Backup", but when accessed from within an application, such as Transmission, they appear as "Image_" and "Backup_".

Also, now all the sda volumes are automatically mounted when starting Ubuntu, and that is not what I wanted, only to have read/write permissions instead of root having them.

I can still read fstab, but since root owns the File System directory, I can no longer modify that file - here are the contents:

```
#Entry for /dev/sda8 :
UUID=1eaf11d9-194d-4eac-981d-291d89e50926    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb2 :
UUID=84E89A5EE89A4DF4    /media/Backup_    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda7 :
UUID=7EE06E77E06E3615    /media/Downloads    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=7AB48240B481FF3F    /media/Image_Drive    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=6E3CACF2E000E1C3    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=0CAC18BBAC18A0EE    /media/M:    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=3FD858256B620DE3    /media/Windows_XP    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda9 :
UUID=afe9af1c-3b18-49b8-8ff1-08b292b96f9f    none    swap    sw    0    0

```I would be very grateful for help in untangling this mess. What I would like to do:

1. recover read/write permissions for my user account for all volumes instead of root having them.

2. recover read/write permissions for all directories, including File System, instead of root having them.

3. not have the sda volumes mounted at launch except for the Ubuntu volume ( "sda8" )

4. have the sdb volumes mounted at start, but with full read/write permissions for my user, instead of root

What I cannot do:

1. re-format all the volumes to ext4 - sorry, I need Windows, unfortunately, and the external hd must be accessible to Windows, obviously, so they must remain NTFS.

What I would appreciate:

If any kind souls answer, would they please explain in sufficient detail? I would like to understand and learn, and not just blindly follow instructions. And generally, that is what has gotten me in this mess, in the first place.

Thanks to all in advance.

Carlos

---

### Post by dabl on 2011-12-10
That's a lot of complexity, and consequently a lot of issues for a new user to throw himself at.  Not only do you have the issues associated with mounting and using external storage devices, and the issues of sharing NTFS storage partitions between Windows and Linux, but also lack of understanding of file and directory ownership and permissions.  No surprise at the consequences ....

I doubt you're going to get tutorials on Linux System Administration 101, 102, and 103 via forum posts.  You'll have to research and learn about file permissions in Linux, partition/filesystem management, configuration options for /etc/fstab, etc. etc. if you're going to try to control your setup.

[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

FWIW, hard drive file systems are owned by root, by default, and for good reasons -- you should not try to change that.  What you want to do is make your needed _directories_ that are on the filesystems owned by the user.  For example, suppose your user name is "carl" and you have a "MUSIC" directory on /dev/sda7 that you want to be able to use, and suppose that /dev/sda7 is the partition you have mounted at /media/Local_Disk.  In a terminal

```
sudo chown carl:carl /media/Local_Disk/MUSIC
```

That will set carl as the owner of all the music in the directory, and you can add, delete, and play files in there.

I hope this gets you started.

---

### Post by carlbelmonte on 2011-12-10
Thank you very much for the link and the tip.

I would like to have read/write permission for the File System directory so that I can change fstab.

Since this directory does not appear in the Media directory (as it is root) I don't quite see how that would be done.

Thanks.
Carlos

---

### Post by WorMzy on 2011-12-10
Why have you got these in your fstab?

```
UUID=84E89A5EE89A4DF4    /media/Backup_    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
UUID=7EE06E77E06E3615    /media/Downloads    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=7AB48240B481FF3F    /media/Image_Drive    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=6E3CACF2E000E1C3    /media/Local_Disk    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=0CAC18BBAC18A0EE    /media/M:    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
UUID=3FD858256B620DE3    /media/Windows_XP    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
```

You can't possibly need every single one of these NTFS filesystems mounted at every boot up, can you? My advice is to remove all these from your fstab, then use nautilus to mount them ad hoc.

So long as they're being mounted at boot time, with the arguments they have currently, root will always own the mounted file systems. The reason for that is that the NTFS filesystem doesn't understand or support UNIX file permissions, so when the mountall process runs when Ubuntu boots, it tells the filesystems that they're owned by root and blankets all the files with one set of permissions.

What happens when nautilus mounts the partitions, is that nautilus tells the udisk helper to mount the filesystems as *your* user, with blanket permissions. That gives you access to the files and folders.

> **carlbelmonte said:**
> I would like to have read/write permission for the File System directory so that I can change fstab.

If you want to edit fstab, run a text editor with root permissions.

e.g.

```
gksudo gedit /etc/fstab
```

---

### Post by carlbelmonte on 2011-12-11
Thank you very much for your reply and help.

I did not create the auto mount for those NTFS volumes - they appeared after running NTFS-config. I only wanted to have read/write permissions for all my volumes when I ran that tool, but it seems to have added them to the fstab file automatically, which is, obviously, not what I wanted.

Thank you for showing me how to edit a root file  - very useful information and I have now eliminated all those NTFS files from fstab.

I am sure that I previously had read/write permission for the entire File System directory, whereas now it is root. Am I mistaken? Is this always root or can I somehow assign those permissions?

Best regards.
Carlos

---

### Post by coffeecat on 2011-12-11
> **carlbelmonte said:**
> I am sure that I previously had read/write permission for the entire File System directory, whereas now it is root. Am I mistaken? Is this always root or can I somehow assign those permissions?

WorMzy did, in fact, explain this, but let me try another way. Your files appear to be owned by root in your NTFS filesystems because NTFS is a Microsoft filesystem which does not support Linux permissions and ownership. However, a NTFS filesystem, if correctly mounted, will be accessible read and write by all users even though the files appear to be owned by root.

But to add, if you previously had read-write access and you now only have read access, check that you have the package ntfs-3g installed. This is the userspace read-write ntfs driver and some people have inadvertently removed it by unnecessarily installing ntfsprogs - which you do not need in Ubuntu 11.10. Without the ntfs-3g driver, the system defaults back to the read-only kernel ntfs driver. If you do not have ntfs-3g installed, install it. It will remove ntfsprogs in 11.10 - that's quite OK.

> **carlbelmonte said:**
> I did not create the auto mount for those NTFS volumes - they appeared after running NTFS-config. I only wanted to have read/write permissions for all my volumes when I ran that tool, but it seems to have added them to the fstab file automatically, which is, obviously, not what I wanted.

I recommend you uninstall ntfs-config. It is a buggy, flawed app, unmaintained for years. If you remove the fstab lines as WorMzy suggests, make sure you have ntfs-3g installed, then you should be able to mount all your NTFS partitions on an as-needed basis from Nautilus.

---

### Post by scarleo on 2011-12-11
I think you by "File System directory" means everything in / or root partition, where your Ubuntu install is, no you should not own that, root is the owner of (almost) everything there. If you need to edit something in root use 'sudo' or 'gksu' and be careful and read through everything you change twice before committing.

This is the permissions from / on a fresh install:

```

drwxr-xr-x   2 root root  4096 2011-12-10 11:38 bin
drwxr-xr-x   3 root root  4096 2011-12-10 11:48 boot
drwxr-xr-x   2 root root  4096 2011-12-10 11:15 cdrom
drwxr-xr-x  16 root root  4140 2011-12-11 13:46 dev
drwxr-xr-x 143 root root 12288 2011-12-11 16:30 etc
drwxr-xr-x   5 root root  4096 2011-12-10 11:15 home
lrwxrwxrwx   1 root root    33 2011-12-10 11:44 initrd.img -> /boot/initrd.img-3.0.0-14-generic
lrwxrwxrwx   1 root root    32 2011-12-10 11:23 initrd.img.old -> boot/initrd.img-3.0.0-12-generic
drwxr-xr-x  21 root root  4096 2011-12-10 11:41 lib
drwxr-xr-x   2 root root  4096 2011-10-12 16:27 lib64
drwx------   2 root root 16384 2011-12-10 11:12 lost+found
drwxr-xr-x   2 root root  4096 2011-12-11 13:47 media
drwxr-xr-x   2 root root  4096 2011-10-09 09:31 mnt
drwxr-xr-x   3 root root  4096 2011-12-11 09:09 opt
dr-xr-xr-x 174 root root     0 2011-12-11 13:46 proc
drwx------   7 root root  4096 2011-12-11 00:18 root
drwxr-xr-x  20 root root   780 2011-12-11 16:36 run
drwxr-xr-x   2 root root 12288 2011-12-10 11:43 sbin
drwxr-xr-x   2 root root  4096 2011-06-21 20:45 selinux
drwxr-xr-x   2 root root  4096 2011-10-12 16:26 srv
drwxr-xr-x  13 root root     0 2011-12-11 13:46 sys
drwxrwxrwt  18 root root  4096 2011-12-11 16:39 tmp
drwxr-xr-x  11 root root  4096 2011-12-10 11:23 usr
drwxr-xr-x  13 root root  4096 2011-12-11 12:27 var
lrwxrwxrwx   1 root root    29 2011-12-10 11:44 vmlinuz -> boot/vmlinuz-3.0.0-14-generic
lrwxrwxrwx   1 root root    29 2011-12-10 11:23 vmlinuz.old -> boot/vmlinuz-3.0.0-12-generic

```

Don't mess with permissions on / unless you really know what you are doing.

---

### Post by carlbelmonte on 2011-12-11
Thanks to both of you for that information. I did, in fact, understand WorMzy's explanation - it was clear, concise, and simple. What was missing was the part about ntfs-config being the problem.

I have now removed that tool and everything is back to normal, or at least to the way it was before.  As a beginner, I must put my faith in what I read in this forum and somewhere in here there is the recommendation to install ntfs-3g and ntfs-config, which I did, in order to have permissions for my external NTFS hdd (sdb).

Many thanks to all of you and I shall now mark this thread as Solved. On to the next problem.

Best regards.
Carlos

---

### Post by WorMzy on 2011-12-11
> **carlbelmonte said:**
> I did, in fact, understand WorMzy's explanation - it was clear, concise, and simple.

Really? Normally my explanations look like a load of waffle to me. :P


Glad you got it all sorted in any case.

---

