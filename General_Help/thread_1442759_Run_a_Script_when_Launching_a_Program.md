---
title: "Run a Script when Launching a Program"
date: 2010-03-30
forum: General Help
---

### Post by dadgetboy on 2010-03-30
Hey everyone!

I'd like to know if I would be able to run a command/script when launching a program (Rhythmbox). You see, I have a partitioned hard drive, and I like to keep all of my media files on a separate partition. Any tips?

If this is not possible, is there a way that I can set Ubuntu to auto-mount a partition on boot?

---

### Post by prodigy_ on 2010-03-30
I think the second option will actually be easier because you just need to edit **/etc/fstab** adding any partition you want to automount.

If you need guidance, post the output of ```
sudo fdisk -l
```, ```
cat /etc/fstab
``` and ```
sudo blkid
``` commands.

---

### Post by voja15 on 2010-03-30
Not sure for the first question, but partitions can be auto-mounted on boot. You'll need to edit fstab file. So, open terminal and type:
```
sudo gedit /etc/fstab
```

Add the following line to the end of the file:
```
/dev/sda5                                  /media/sda5    ntfs         defaults                                                0  0  
```

Where /dev/sda5 is your partition location, /media/sda5 is the mount point, and nfts is the partition type.
Of course, you'll need to replace these values with corresponding values for your partition.

---

### Post by dadgetboy on 2010-03-31
Hey, I tried the /etc/fstab edit and it's a  no-go. However, I did notice some progress. At first when I used

```
/media/sda1
```

as the mount point it would not allow me to mount the drive at all.

Then when I used

 ```
/mnt/sda1
```

as the mount point I could not see the drive.

Any suggestions? I think we;re getting closer/I might be missing something here. ;)

---

### Post by akakingess on 2010-03-31
Also, you could always reference this and see if it helps - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by darolu on 2010-03-31
> **dadgetboy said:**
> Any suggestions? I think we;re getting closer/I might be missing something here. ;)

First, you need to identify the hard drive you want to mount at boot. Are you sure it is /dev/sda1?

You can find this with the fdiks -l command **prodigy_** told you; run it with (in case you have a tricky font, it is a lowercase L, not a - number one-):
```
$ sudo fdisk -l
```
It will print a list of your hard drives, identify your hard drive guiding by size, file system and number of device (sda, sdb = hd0, hd1).
I recommend you to write down your device **UUID**, so you can use it in your fstab file instead of '/dev/sdXX', is safer (i.e. it will still work if you add an extra HD or partition):
```
$ sudo blkid
```
Before editing your fstab file, you may want to create the mount point first:
```
$ sudo mkdir /media/<yourmountpoint>
```
Many distros use /mnt/ directory to create their mountpoints, even when you can do it in Ubuntu too, I suggest you to use the default /media one so you can keep all your mountpoints under a single directory.

After this you can edit your fstab file; you need this info to edit it: UUID of your device, a mount point, filesystem (type) of your device and the desired mount options. For a full list of options, read mount manual with:
```
$ man mount
```
I suggest you to use: "defaults,user,exec,rw", to guarantee full access to your device.

Your fstab line should look like:
```
#My music disk
UUID=49B723546D64AA24 	/media/music 	ntfs-3g 	defaults,user,exec,rw 	0 	0
```
If your disk/partition's filesystem is NTFS I strongly suggest to use "ntfs-3g" so you can write files in it; the final numbers (0 0) stand for dump and pass; 0 - 0 is highly recommended.

Read the link akakingess gave you or this one for more info: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by dadgetboy on 2010-03-31
Awesome! Thank for all your help!

I managed to get the partition to auto-mount with this configuration:

```
UUID=A2BAA89BBAA86D8B  /media/sda1  ntfs-3g defaults,root,exec,rw 0 0
```

As you can see, I changed "user" to "root" in the options. With the option "user" being there I was not able to mount the drive at all; Ubuntu said that it needed root privileges. Changing "user to "root" solved everything; and the now the drive auto-mounts on boot.

Thanks for the help/tips/documentation.:p

PS: I think I'll change the title of this thread ;)

---

