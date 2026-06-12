---
title: "Fail to mount disk right after system boots"
date: 2010-04-10
forum: General Help
---

### Post by Septi on 2010-04-10
Hi to all, and thanks for making such great distros!

I got a little problem with Xubuntu here. Every time after I boot the system, I find one of my partitions from fstab not mounted where it's supposed to be. I do mount -a, and it replies: "mount: /dev/sdb6 already mounted or /mnt/data busy". Checking lsof of neither device nor mount point gives me nothing, and checking the output of mount I see device isn't mounted anywhere.

It gets better than this: after some time, device can be mounted just fine, this time is from 11 to 12 minutes. If something is doing anything with my device that takes whole 11 minutes, how come I don't know what it is? How can I mount device on boot?

Some more (ir)relevant facts:

1. This partition is the biggest - 376 Gb

2. Here's my fstab line for this device:

```
/dev/sdb6	/mnt/data	ext3	defaults	0	2
```

3. After the installation, I changed the mount point in fstab, and using /dev/sdb6 instead of UUID is a result of blind experimentation

---

### Post by oldfred on 2010-04-10
Welcome to the forums

Do you have another partition that you labeled with 'data'? 

This will show labels & UUID, post this:
sudo blkid

Also a copy your entire fstab.

---

### Post by Septi on 2010-04-10
**oldfred**, here you go.

sudo blkid:
```
/dev/sda1: UUID="34F81065F810281E" LABEL="Windooze" TYPE="ntfs" 
/dev/sda2: UUID="d0a17980-c712-4723-adc8-198fe0e2f5ed" TYPE="ext2" 
/dev/sda3: UUID="4ba1be58-119d-4d02-b9c0-f013f27862dd" TYPE="ext4" 
/dev/sda4: LABEL="Ubuntu" UUID="52c71fa4-fb54-4e18-8893-c7f7afa678f3" TYPE="ext4" 
/dev/sdb1: LABEL="Swap" UUID="59322df3-6996-481d-9b9e-fd064a0e38ee" TYPE="swap" 
/dev/sdb3: UUID="48B0880CB0880324" LABEL="Playground" TYPE="ntfs" 
/dev/sdb5: LABEL="Critical" UUID="9075aa9f-5e79-47f3-950c-f22050e11e28" TYPE="ext3" 
/dev/sdb6: LABEL="Data" UUID="f146bacc-03cf-4779-9a8f-f7638b5ba7ab" TYPE="ext3"
```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=4ba1be58-119d-4d02-b9c0-f013f27862dd /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=d0a17980-c712-4723-adc8-198fe0e2f5ed /boot           ext2    defaults        0       2
# /home/ragnar was on /dev/sdb5 during installation
UUID=9075aa9f-5e79-47f3-950c-f22050e11e28 /home/ragnar    ext3    defaults        0       2
# /home/data was on /dev/sdb6 during installation
#UUID=f146bacc-03cf-4779-9a8f-f7638b5ba7ab /mnt/data      ext3    defaults        0       2
/dev/sdb6	/mnt/data	ext3	defaults	0	2
# /mnt/playground was on /dev/sdb3 during installation
UUID=48B0880CB0880324 /mnt/playground ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/ubuntu was on /dev/sda4 during installation
UUID=52c71fa4-fb54-4e18-8893-c7f7afa678f3 /mnt/ubuntu     ext4    defaults        0       2
# /mnt/windooze was on /dev/sda1 during installation
UUID=34F81065F810281E /mnt/windooze   ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb1 during installation
UUID=59322df3-6996-481d-9b9e-fd064a0e38ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

No other "data" there.

---

### Post by oldfred on 2010-04-10
You probably have two datas. In linux Data is different than data. So it may try to mount it twice once as data, then as Data. Change either your label with disk utility or your fstab so both are the same.

---

### Post by Septi on 2010-04-11
> **oldfred said:**
> You probably have two datas. In linux Data is different than data. So it may try to mount it twice once as data, then as Data. Change either your label with disk utility or your fstab so both are the same.

I'm confused. I don't think my partition is identified by label anywhere at all. It is indeed labeled 'Data', but disk label and the name of mount point don't have to match, do they? In fstab I tried to identify the partiton either with UUID or device filename, never with a label. And the mount point /mnt/data exists. It also wouldn't really explain the 11 minute delay.

Anyway, I can't check whether changing the label would fix anything, because the problem is gone. Today I waited for usual 11+ minutes and, instead of mounting /dev/sdb6, did an e2fsck on it. Some errors were found and fixed, and then, after reboot, device mounted by itself, as it should be.

I don't get it. Does Xubuntu check filesystem in background after boot? Why then doesn't it fix the error and then automatically mount the partition? For now I put 0 instead of 2 to the last field in the fstab next to this partition, so that problem would not return. But that doesn't feel right :\  In Ubuntu you could stop filesystem check if you have no time for it. But in Xubuntu it becomes a showstopper.

Or am I wrong about all that? I'm not marking this thread [solved] just yet.

---

### Post by oldfred on 2010-04-11
When I went back and put labels on partitions that I was not using fstab to mount the label became the default mount. 

I also just noticed on my system I use data, beta, grub, test and they are auto mounted as DATA, BETA, GRUB,  and TEST and they are listed as as available to mount as data, beta, grub and test and lets me mount them again.

I do not see any duplicates with fstab as I mount those in places that are not /mnt nor /media so they do not show up in Nautilus.

---

### Post by Septi on 2010-04-14
Well, seems like disabling disk check totally did it, since for quite a few days it mounts just as it should.

oldfred, you mean automount somehow conflicted with /etc/fstab? Sorry, I don't understand, but AFAIK automount doesn't take action if the device is present in fstab. Also, I thought Ubuntu doesn't mount hard drive partitions automatically when they are not present in fstab, at least by default, only when user first tries to access them via, say, nautilus.

But anyway, thanks for replying. I guess the solution to not check the partition is not perfect, but what can go wrong? ;)

---

### Post by aksx on 2010-04-14
i had a some what same problem so i did the following

```
sudo apt-get install mountmanager
sudo mountmanager
```
 you will get a Window from where you can easily manager your hard disks.:KS

---

