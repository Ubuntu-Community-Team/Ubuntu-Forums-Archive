---
title: "how to open a partition to transfer files"
date: 2009-08-14
forum: General Help
---

### Post by Andy Donald on 2009-08-14
hello I am new to linux so need some help on basic file transfer please

Could someone please tell me how to transfer files to another partition. That is when I mount the drives I dont have ownership of the drive. I have tried to start nautilus with root permissions but this still does not allow root permissions on the other partitions any help would be most welcome.

---

### Post by soapBAR2 on 2009-08-14
Try manually mounting the drive (in terminal).

```
sudo mount -t FILESYSTEM -o youroptions /dev/yourpartion /mnt/yourmountpoint
```

where:
**FILESYSTEM** is your filesystem. If it's Windows, you want ntfs-3g (probably, might be FAT if it's really old). If it's linux, you want whatever you formatted it as - Ubuntu defaults to ext3

**youroptions** are your mount options. These may include things like user=theusernamefromyouroldpartition,pass=youroldpwd,relatime,ro. Separate options with comma, OR make multiple -o options (your choice). If you don't know what to do here, just put -o ro (read only).

**/dev/yourpartition** is the partition you want mounted (hint: If, in /dev, you have something with no number and something with a number on the end, you want the one with the number - the one without is the hard drive itself, not the partition)

**/mnt/yourmountpoint** is your mount point. Preferably this should be an empty directory. I say preferably because it won't go insane in you have one little file in there, but you won't be able to get to anything in there until you unmount the drive.

---

### Post by Andy Donald on 2009-08-14
Hi soapbar2

thanks for you prompt response !

I just want to move some video files to  a partition to make some more space.  If I click on places I can see my other partitions (eg. 15.4 GB Media) and mount them simply by clicking. however i dont have permissions to transfer the files.

1. How can I find out the path to 15.4 GB Media

2. Mount the drive automatically on start up(with read write permissions)

sorry for being a bit dull its all a bit new

ps i dont have windows at all on the system

---

### Post by XCan on 2009-08-14
> **Andy Donald said:**
> Hi soapbar2

thanks for you prompt response !

I just want to move some video files to  a partition to make some more space.  If I click on places I can see my other partitions (eg. 15.4 GB Media) and mount them simply by clicking. however i dont have permissions to transfer the files.

1. How can I find out the path to 15.4 GB Media

2. Mount the drive automatically on start up(with read write permissions)

sorry for being a bit dull its all a bit new

ps i dont have windows at all on the system

It's strange that you don't have permission after mounting, you can do it the ugly way and simply chown the dir recursively, or use sudo. None of these are very elegant, so I think you should wait a while for someone with more knowledge to tell you how to fix it permanently.

1. You can find the path by looking at where they are mounted in ```
 df 
```
I guess it is mounted inside /media/

2. You can automount the drive at boot by editing /etc/fstab and adding it there, assuming your filesystem is ext3 ```
 /dev/yourdrive /mount/point ext3 default 
```

---

