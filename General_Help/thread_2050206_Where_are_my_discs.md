---
title: "Where are my discs?"
date: 2012-08-30
forum: General Help
---

### Post by theKuch on 2012-08-30
My system has 3 physical hard discs, partitioned into 4.

When I boot up, I can only see the disc via which I booted.

If I "Open File" on any application, I see all the discs. Just touching my cursor onto the disc entries seems to mount them. They now appear in the toolbar.

How do I get them to mount on boot?

Thanks

---

### Post by dcstar on 2012-08-31
> **theKuch said:**
> My system has 3 physical hard discs, partitioned into 4.

When I boot up, I can only see the disc via which I booted.

If I "Open File" on any application, I see all the discs. Just touching my cursor onto the disc entries seems to mount them. They now appear in the toolbar.

How do I get them to mount on boot?

Thanks

Do a search for the hundreds of posts that already exist on this subject.

---

### Post by theKuch on 2012-08-31
> **dcstar said:**
> Do a search for the hundreds of posts that already exist on this subject.

Thanks for your response.

I actually did do a search before I wrote on this forum but didn't find anything useful. Perhaps my search was badly constructed. I just now did searches for "disc not mounting" and "mount on boot" both which managed to yield this thread high on the very list.

The main problem I found discussed referred to mounting Windows network discs on boot. As other posters said, it worked "automatically" on previous OS versions.

But I find it strange that you say there should be so many posts. This indicates that many people have similar problems. I'm sorry to say, that to me, this implies a problem at quite a low system level. Surely the default on any operating system should be mount all local drives, if not all network drives too.

---

### Post by plucky on 2012-08-31
Go [Here](https://help.ubuntu.com/community/Fstab) and learn how to use /etc/fstab to mount your Linux and Windows partitions at boot time.

Good Luck

---

### Post by spjackson on 2012-08-31
In order for a partition to be mounted at boot time, an entry must exist for it in /etc/fstab.
The following command shows you what is currently mounted.```
mount
```Once a partition is mounted, it appears to most programs as being part of the homogenous filesystem, i.e. it just looks like a folder, subfolders and files somewhere below /.

If you need to edit /etc/fstab to create new entries, then this can be tricky to the uninitiated. If you need help doing that, then post your existing /etc/fstab and the output of
```

sudo fdisk -l

```Then it's just a matter of knowing what you want mounted and where. For any partition that isn't a native Linux partition, typically FAT or NTFS, then additional options may need tweaking depending on what you want to achieve.

A word of caution: if you put something in /etc/fstab to be automatically mounted, and it cannot be mounted at boot time, then it won't boot into a GUI.

Unfortunately, I don't know of a GUI tool that will manage the necessary changes to /etc/fstab for you (apart from the Ubuntu installer).

---

### Post by LewisTM on 2012-08-31
Clicking an umounted drive will make Ubuntu call the GIO/GVFs subsystem to mount it in /media. You can automate this at login by adding startup applications with commands like
```
gvfs-mount -d /dev/sdXX
```
Where sdXX is the drive listed by [FONT="Courier New"]sudo fdisk -l[/FONT]
GVFS takes care of detecting the filesystem type and adds the necessary parameters. You may have to go the fstab way if you have specific needs for the drive. If clicking the drive lets you access the files like you expect, the gvfs-mount way is simpler.

Cheers!

---

### Post by theKuch on 2012-08-31
Thanks everyone.

My question is, is why this isn't the default? Who would "normally" want to not mount drives if they are available?

I would go as far as to say that if there was a network running, those disks too should not need manual mounting.

And as pointed out by others, these were default behaviour in previous implementations.

---

### Post by LewisTM on 2012-08-31
You definitely don't want to mount ALL available network shares at boot, that would be impractical in any network of a reasonable size. 

But yeah, I agree for local drives. At least make it an option and let the user disable the drives he/she wants out of the way. 

In fact you *can* set each drive to its own mount point at boot during the OS install procedure but you have to pick the Manual Partition option and any drive or partition added susbsequently are not given that treatment.

---

### Post by oldfred on 2012-08-31
I have lots of partitions on my drive, many are just other installs of Ubuntu. I do not normally want those mounted. I can easily mount each of those with Nautilus as they are shown in left panel. I label them with gparted or Disk Utility to make it easier to know which is which.

to mount on reboot you do need to add to fstab.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

