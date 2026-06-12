---
title: "Mounting Internal Partitions"
date: 2009-11-26
forum: General Help
---

### Post by nicknefarious on 2009-11-26
G'day anyone and everyone.

I have a few problems I have been trying to understand and/or sort out but have been having no luck.

I am trying to mount partitions from my internal HDD at startup - which seems to be happening - despite a number of errors that break through my splash screen at startup. However, I cannot move anything into them. When I try to, it tells me I don't have the required permissions to create the file or folder in this location. I have tried a number of different solutions including PySDM and manually editing the fstab file myself. To no avail. I have tried a number of different mount options for the drives, someone also suggested trying the chown command for ownership. This did not work either. At some stage one of the drives permissions changed and allowed me in but the others still do not. Is there anyway I can reset any config files I may have changed, to their defaults, and start again with some advice here? Also I am trying to understand exactly how the filesystem works and why for example /media contains a number of folders for my CD/DVD Drive and generally two different types of icons for each drive partition? How do these folders work or link to the drive partition, how are they set up there and how can I delete them? Will deleting them cause problems? I really would like to read more about Ubuntu/Linux - Can anyone recommend something that is easy to come by and pretty fresh?

2 - Best and easiest way to disable nVidia splash screen in Karmic?
3 - Usplash error on boot - failed 1152x864 using 1024x768 anyone can give me further info about this?

Thousands more questions... hence the request for the book but I'll leave it at that for now.

Any assistance, guidance much appreciated.

Thanks, 

Nick

---

### Post by lexfati on 2009-11-26
Do you know what type of filesystem(s) you are trying to mount (ntfs, hfsplus, ext4, etc...)?  Is the HDD (or partition) used by another operating system, if so which?

What are the permissions of the directory on which you are trying to mount your filesystem(s)?   
The output of the command below will give you the permissions for the files and directories in the directory you are currently in.```
ls -l
```

---

### Post by nicknefarious on 2009-11-26
The OS is installed on ext4 and I am trying to mount four partitions created as ext4 and one that is NTFS. Currently no other OS installed. ls -l output below. And why three entries for CD?

total 56
drwxr-xr-x 7 XXXX XXXX 4096 2009-11-25 10:32 Audio_Store
lrwxrwxrwx 1 root root    6 2009-11-19 10:29 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-11-19 10:29 cdrom0
drwxr-xr-x 2 root root 4096 2009-11-19 10:29 cdrom1
drwx------ 1 XXXX XXXX 8192 2009-11-01 15:37 FreeAgent Drive
drwxr-xr-x 3 root root 4096 2009-11-23 15:22 Library_Docs
drwxr-xr-x 2 root root 4096 2009-11-24 23:27 sda4
drwxr-xr-x 2 root root 4096 2009-11-24 23:27 sda5
drwxr-xr-x 2 root root 4096 2009-11-24 23:27 sda6
drwxr-xr-x 2 root root 4096 2009-11-24 23:27 sda7
drwxr-xr-x 2 root root 4096 2009-11-24 23:27 sda8
drwxr-xr-x 3 root root 4096 2009-11-23 15:24 Video_and_Torrents
drwxr-xr-x 2 root root 4096 2009-11-23 23:15 VM and VHDD
drwxr-xr-x 4 XXXX XXXX 4096 2009-11-25 18:45 VM_and_VHDD

The x's above are where my user name appeared. You can see there are a number of folders for the same drive. eg VM and VHDD, VM_and_VHDD and also the sdaX folder for the same drive. How can I tidy this up. Also you can see the permissions. sda4 is an NTFS primary partition. The real drives are the ones with the underscores in the label.

---

### Post by nicknefarious on 2009-11-26
Sorry... do I have to mount in /media or can I mount them anywhere I want? What is the best way to go about this?

Thanks,

Nick

---

### Post by StuartN on 2009-11-26
> **nicknefarious said:**
> And why three entries for CD?

cdrom is just a link to cdrom0, so media applications can access the default drive.

If you always want your other partitions accessible then add a line for each to your fstab. Open a terminal and run blkid to determine the UUID of each partition, for instance

```
/dev/sda2: UUID="BCECDD93ECDD47F2" TYPE="ntfs"
```

And then add a line using that UUID, which for this NTFS partition might be:

```
# Windows NTFS partition /dev/sda2 BCECDD93ECDD47F2
UUID=BCECDD93ECDD47F2 /home/username/Windows ntfs user 0 0
```

The ext partitions will use parameters more like the existing entries.

---

### Post by lexfati on 2009-11-26
> Sorry... do I have to mount in /media or can I mount them anywhere I want? What is the best way to go about this?

You don't have to mount your filesystems in /media, but you must have a separate mount point for each.

If you create the mount point in your home directory, you shouldn't  have to worry much about changing permissions, provided only you will be accessing the drive.

I create my mount points in /media as root
```
sudo mkdir /media/mountpointname
```

and then change the permissions to make it accessible by all as if they were root.
```
sudo chmod a=u /media/mountpointname
```

Then add the line(s) to /etc/fstab as indicated by StuartN

---

### Post by nicknefarious on 2009-11-26
Thanks Stuart - when I tried your suggestion I got an error saying the mountpoint didn't exist. To use your method do I need to create a new directory or folder in the /home/username folder?

Is fstab the only file that controls the mounting of partitions and their permissions once mounted?

And can I delete all existing folders in /media (without any problems) and then mount the partitions/drives in the home folder? Is mounting them in the home folder a safer, more stable option? Or no difference?

Thanks

---

### Post by lexfati on 2009-11-26
I should explain, the chmod example I gave makes that mount point read/write accessible to any user account on your machine, maybe that's not what you want.

In any event its a good place to start to make sure you can read and write files to your newly mounted partition.  

If you want to learn about adjusting the permissions differently, [[COLOR="Blue"]this tutorial[/COLOR]]("http://catcode.com/teachmod/index.html") does a nice job of explaining permissions and chmod step by step.

---

### Post by lexfati on 2009-11-26
> Thanks Stuart - when I tried your suggestion I got an error saying the mountpoint didn't exist. To use your method do I need to create a new directory or folder in the /home/username folder?
You need a separate, empty directory for each filesystem you wish to mount - so in the case of Stuart's example, a directory named Windows would have to be created in the /home/username directory
```
mkdir /home/username/Windows
```

or alternatively

```
mkdir ~/Windows
``` *Note: Windows is case sensitive*

Whether you create your mount points in /media or in the home directory depends on whether or not you need to share this configuration with other users.  If you are the only person who uses your computer, you should be fine creating the mountpoints in your home directory.

If you create them outside of your home directory, you will have to use sudo, which gives root ownership of the new folders, so the permissions have to be changed for others to use the folder.

While /etc/fstab is the configuration file that mounts filesystems, the chmod command can be used to change permissions of their respective mount points.

---

### Post by nicknefarious on 2009-11-26
I have been reading up and am getting a much clearer picture. Cheers to both of you lexfati and StuartN for your help with the drive mounting.

Anybody who can help me further with the other two issues.

I have manually installed 190.42 driver from nVidia. What do I have to do to make sure things are updated correctly when a new kernel comes along? What is the best and easiest way to disable nVidia splash screen in Karmic?

Usplash error on boot - failed 1152x864 using 1024x768 anyone can give me further info about this? I have seen a bug report or two floating around but nothing in the shape of a fix...

---

### Post by lexfati on 2009-11-26
nicknefarious - glad I could be of assistance with the drive mounting.  Since that is the title of this thread, you should close this thread as solved, and then open a separate thread for the Nvidia issue, since anyone searching thread titles will see this one is about mounting partitions.  It will also indicate to anyone else searching the forums trying to figure out how to mount partitions that this thread helped.

That being said, I haven't had to  mess with manually installing graphics drivers in Kubuntu (9.10), but from Debian experience I recall two different ways to manually install (Debian way vs. Nvidia way).  From your description, it sounds like you chose the latter, but you'll want to make certain before you start another thread in order to get the right help.  

[[COLOR="Blue"]This Debian wiki[/COLOR]]("http://wiki.debian.org/NvidiaGraphicsDrivers") got me up and running on Debian (Debian way), and should be able to provide more information about upgrading with the kernel, etc.

---

### Post by Zimmer on 2009-11-26
And if you want a quick way to mount drives without an entry in fstab... right click on the Gnome panel > Add to Panel   and add the Disk Mounter... this will put a graphic of the drives connected to the computer in the panel and you can mount and umount them by clicking on the icons.. removeable drives will also appear there as icons when connected...

---

### Post by nicknefarious on 2009-11-30
For anyone else who is interested I disabled the nVidia splash screen at start up by adding an entry to the xorg.conf file in this way...

> ```
sudo gedit /etc/X11/xorg.conf
```

and then adding the entry 

```
Option 	   "NoLogo" "True"
```

as shown below from my xorg.conf file

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option 	   "NoLogo" "True"
EndSection
```

---

