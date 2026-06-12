---
title: "Rockbox w/ ipod trouble"
date: 2010-02-10
forum: General Help
---

### Post by smithpercussion on 2010-02-10
I am trying to install rockbox on my ipod.

I opened the utility and it isn't finding able to read the mountpoint.

I try to give it my mountpoint and it says ```
No mountpoint given
```

Here's my fstab output for my ipod
```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

```


Ubuntu is reading my ipod just fine at /media/ipod So i'm not sure why I am getting this error.

Please let me know if I can give you any extra information and Thank you in advance for your assistance!

---

### Post by smithpercussion on 2010-02-10
Here is the bit from my fstab.. I think here is where the problem is but I am still not sure what is wrong

```
/dev/sdb /media/ipod vfat user,noauto,umask=000 0 0
```

---

### Post by darolu on 2010-02-10
/dev/sdb may be the drive, but you are not specifying a partition; it should be "/dev/sdb1"; I prefer to use UUID instead though, this way you make sure it mounts y our ipod and your ipod only (not a external HD or USB Flash memory than can be assigned to sdb).

Before editing your fstab file, find your ipod's UUID with (if you are sure it is sdb1):
```
$ sudo blkid /dev/sdb1
```
It should return something like:
```
/dev/sdb1: UUID="49B723546D64AA24" LABEL="Media" TYPE="ext2"
```
Use this UUID number instead /dev/sdb on your fstab file. For example:
```
UUID=49B723546D64AA24   /media/Media    vfat defaults,user,exec,rw   0       3
```

Also make sure you have created the mount point directory:
```
$ sudo mkdir /media/ipod
```

---

### Post by smithpercussion on 2010-02-10
Thank you! I did find the correct partition. However, there seems to still be something wrong. It ended up being sbd3, after adding this I am getting this message when I try to access it

 ```
unable to mount: special device /dev/sbd3 does not exist
```


I had already created the directory

It appears in the file browser twice. One seems to be finding the device, but the other is returning the same unable to mount.

It seemed like a problem with ownership. I tried chown but it is still saying it's read only. I'm not sure if this matters.


bklid output for the player is this

```
/dev/sdb3: UUID="ba1a995c-510c-3abb-b0c3-66ebed0beee2" LABEL="ipod" TYPE="hfsplus" 

```

---

### Post by Rockin_GodEater on 2010-02-10
```

/dev/sdb3: UUID="ba1a995c-510c-3abb-b0c3-66ebed0beee2" LABEL="ipod" TYPE="hfsplus"

```

Rockbox will not install on a Mac formatted Rockbox. The type "hfsplus" above indicates that this is the case for your iPod, and so you will have to reformat it as a FAT32 device for Rockbox to install and run on it.

We have a page here with details on how to do this here [www.rockbox.org/wiki/IpodConversionToFAT32]("http://www.rockbox.org/wiki/IpodConversionToFAT32").

Note, converting from one file system to another is a destructive process so **BACKUP YOUR MUSIC FIRST - IT WILL ALL BE DELETED FROM THE IPOD**

---

