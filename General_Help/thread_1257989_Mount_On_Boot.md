---
title: "Mount On Boot"
date: 2009-09-04
forum: General Help
---

### Post by anderskitson on 2009-09-04
I have been attempting to mount a hard drive with two partitions on it.

Here is my fdisk
> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099e60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          67       93786   752805900   83  Linux
/dev/sda3           93787      182401   711799987+  83  Linux

gparted tells me the mount points are respectively 
> 
/media/Projects_Design
/media/Media

and the that the file system is ext2

I added these lines to my fstab

> /dev/sda2 /media/Projects_Design ext3 default 0 0
/dev/sda3 /media/Media ext3 default 0 0

However when I run sudo mount -a I get the error that the mount points do not exist and after adding the fstab lines I cant mount the drives by clicking on them I have to delete the fstabs lines I added before I can mount. 

Any Ideas?

---

### Post by falconindy on 2009-09-04
> /dev/sda2 **/media/Projects_Design** ext3 default 0 0
/dev/sda3** /media/Media** ext3 default 0 0Do those directories exist? You need to create them before you can use them as a mount point. Also, danger Will Robinson. If gparted tells you they're ext2, don't try and mount them as ext3.

Personally, if you're going to be adding new drives, I would specify (create) a mount point outside of the /media directory. I've made myself mount points in / for my 3 extra HDDs.

---

### Post by drs305 on 2009-09-04
Make the mount points and make yourself the owner:
```

sudo mkdir /media/Projects_Design  /media/Media 
sudo chown -R *yourusername:* /media/Projects_Design  /media/Media 
*then*
sudo mount -a

```

And in fstab, it's **defaults**, not **[COLOR="Red"]default[/COLOR]**

---

### Post by anderskitson on 2009-09-04
I had forgot to mention that when I right clicked on each drive while they were mounted and checked there properties they said file type extension:ext3

So I tried ext2 first and then ext3 to no avail

---

### Post by anderskitson on 2009-09-04
I had tried before making the directories never tried making myself the owner, but I still end up with a different error I got before

> mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and then I cant mount the drives by clicking on them until I delete there directories.

It may help to know that I had renamed the drive partitons before, I cant remember how I did it but the 

Projects_Design and Media are there labels that I named them

---

### Post by aysiu on 2009-09-04
If you plug in a manually mount a drive through Nautilus (the file manager), a mount point will automatically be created for it and then automatically deleted once you unmount the drive.

If you want it permanently mounted, you need to manually create the mount point: ```
sudo mkdir /media/Projects_Design
sudo mkdir /media/Media 
sudo mount -a
```

---

### Post by anderskitson on 2009-09-04
I am able to create a directory and it stays when I restart, However when even I add the lines to my fstab the drives wont mount on boot or when I try to mount them in nautilus. In nautilus I get the error 

> Cannot Mount volume
you are not priviledged to mount the volume

---

### Post by drs305 on 2009-09-04
They should mount during boot. You can allow mounting by users via Nautilus by changing the fstab lines to:
```

/dev/sda2 /media/Projects_Design ext3 defaults,users 0 2
/dev/sda3 /media/Media ext3 defaults,users 0 2 

```

I have added "users", which allows users to mount/unmount devices. Also note it is "defaults" and that I changed the fsck option from 0 to 2 so the drives are checked periodically. If you don't want them checked, change the value back to 0.

---

### Post by anderskitson on 2009-09-04
I knew it was going to be a stupid error on my part fstab didnt like the fact the i put "defualt" instead of "defaults" now they mount perfectly its always a spelling mistake.

Thanks! Everyone

---

