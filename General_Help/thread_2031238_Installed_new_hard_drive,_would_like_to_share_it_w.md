---
title: "Installed new hard drive, would like to share it with user account"
date: 2012-07-21
forum: General Help
---

### Post by abelundercity on 2012-07-21
I use 11.04.  I lucked into a second hard drive from a co-worker who was getting rid of his old computer.  I installed it and formatted it just fine, and set it to automount.  All seems to be running well.

I'd also like to share this drive with my wife, who has a user account on the same computer.  If anyone has any information on how I might do that, I would appreciate it.  Thank you.

---

### Post by sudodus on 2012-07-21
- Do you want to share the drive only inside the same computer or via the LAN from another computer?

- Do you want to share it from linux or from Windows or some other OS?

- How did you format the drive? It would help if you post the output of the commands ```
sudo fdisk -lu
``` and ```
df
```

---

### Post by abelundercity on 2012-07-21
> **sudodus said:**
> - Do you want to share the drive only inside the same computer or via the LAN from another computer?

Only inside the same computer.

> - Do you want to share it from linux or from Windows or some other OS?

The computer is Ubuntu-only.

> - How did you format the drive? It would help if you post the output of the commands ```
sudo fdisk -lu
``` and ```
df
```

Respectively:

```
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ee9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    78156224    39078081   83  Linux 
```

and 

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36875340  30288716   4713448  87% /
none                   1023440       692   1022748   1% /dev
none                   1030068       496   1029572   1% /dev/shm
none                   1030068        76   1029992   1% /var/run
none                   1030068         0   1030068   0% /var/lock
/dev/sdb1             38464340    180120  36330316   1% /media/sdb1

```

sdb1 being the drive in question.  There's nothing on it as of yet so if reformatting is needed that won't be a problem.

---

### Post by sudodus on 2012-07-22
It looks good :-)

Now what you need is to make sure that your wife can also read it. Let us look at the permissions. Please post the output of 
```
ls -l /media
```
(I guess that only you have access to that partition, when you have auto-mounted it, but we'll check with the output.)

So what you probably need to do is to create a line in the file ***/etc/fstab*** to make it mount when booting, and then to give its directories read and write permissions

For example, I have a partition for multimedia data, that I mount with the following line in /etc/fstab. Run the command
```
sudo nano /etc/fstab
``` to do the editing.

```
# /dev/sdb1
UUID=a4e3f4a3-2f6e-4e4f-8e1a-c2f0de792f83 /mnt/data ext3    defaults 0       2
```

[COLOR="Red"]You need to run ```
sudo blkid
``` to find the UUID or your partition /dev/sdb1 and the file system (maybe ext4 instead of ext3). (Use UUID without quotes.)[/COLOR]

If you create one directory for each of you where to put your files and subdirectories, then you can read and write your own files, but only read your wife's files and vice versa.

First create the mount point ```
sudo mkdir /mnt/data
```
Then reboot and check with ```
df
``` that /dev/sdb1 is really mounted to /mnt/data.

Then 'goto' the directory on the new drive ```
cd /mnt/data
``` and create directories ```
sudo mkdir husband wife
```
And set the permissions
```
sudo chmod 755 husband wife
```
I tested it in my computer, so it should work unless I forgot to write or explain some step in the process.

Now both of you should be able to use these directories on the new drive via the file browser as well as via terminal commands.

---

### Post by abelundercity on 2012-07-22
That did it! The output for the ls command was as you surmised, and now my wife and I both have desktop links to the new drive.

Thank you very much!

---

