---
title: "Broken fstab file"
date: 2010-03-23
forum: General Help
---

### Post by Springy182 on 2010-03-23
Hi,

I resized my Ubuntu partition from 3.9GB to 6.8GB, in gparted on a live CD after downsizing my swap partition some, now it wont mount my swap partition automatically on bootup, but it mounts in gparted perfectly.

So I looked it up and thought to edit my fstab file to delete the swap entry, then delete and recreate the partition, after editing my fstab I got the following:

mount: / not mounted already, or bad option
mountall: mount / [497] terminated with status 32
mountall: Filesystem could not be mounted: /
init: mountall main process (488) terminated with status 4
Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system

My swap partition was HDA2, my Windows partition HDA3 and my Linux boot HDA1, I think that's all the information needed, I can paste my fstab file if needed.

Thanks.

---

### Post by prodigy_ on 2010-03-23
Most probably it's one of the following: 
- wrong (old) UUIDs are listed in your fstab file;
- incorrect syntax in fstab file;
- broken partition table.

So. Boot into Live CD. Use these commands: 
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```
If you won't get any errors, use:
```
cat /etc/fstab
fdisk -l
blkid
```
commands and post the output here.

---

### Post by prodigy_ on 2010-03-23
[del]

---

### Post by Springy182 on 2010-03-23
--bind /dev /mnt /dev gave me errors, so I did --bind /dev /mnt

cat /etc/fstab gave me

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0 

blkid  and fdisk -l didnt say anything

I tried to follow a different article and tried to make a new entry, didnt work.

I'm getting a different error on bootup.

sameline
mountall: mount / [517] terminated with status 32
same line
init: mountall main process (508) terminated with status 4
rest of the lines are the same

---

### Post by prodigy_ on 2010-03-23
Really sorry, there was an extra whitespace in "mount --bind" command. That's why it errored out. I edited that message, now it should work.

---

### Post by Springy182 on 2010-03-23
sudo mount --bind /dev /mnt/dev gives me:
mount: mount point /mnt/dev does not exist

---

### Post by prodigy_ on 2010-03-23
Did you repeat all steps from the beginning?

---

### Post by Springy182 on 2010-03-23
Every single step.

Here's my fstab file, I cant see any problems but I've never successfully edited one so I dont know.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=e47fa332-905b-4b67-8f8c-ea45841e484a /               ext4       sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/*swap*     swap            swap    pri=1           0       0

The last line I edited in after trying to fix it.

---

### Post by prodigy_ on 2010-03-23
Err. Where's "blkid" output? Where's "fdisk -l output"? Anyway, **assuming that root UUID in your fstab is right/current**, the line should look like:
```
UUID=e47fa332-905b-4b67-8f8c-ea45841e484a / ext4 errors=remount-ro 0 1
```
And for swap partition:
```
UUID=<your_**current**_swap_UUID> none swap sw 0 0
```

---

### Post by Springy182 on 2010-03-23
fdisk -l took a few seconds, drive spun back up.
blkid didnt give me any output

How would I go about finding my swap UUID?

---

### Post by prodigy_ on 2010-03-23
Very strange. When you chroot to your installation you should have root rights. But alright: ```
sudo blkid
``` and ```
sudo fdisk -l
```

---

### Post by egalvan on 2010-03-23
> **Springy182 said:**
> **fdisk -l **took a few seconds, drive spun back up.
**blkid** didnt give me any output

How would I go about finding my swap UUID?

Both of these need root in order to get some output...

```
sudo fdisk -l
```
```
sudo blkid
```

as an example, here is my *blkid*

```
~$ sudo blkid
/dev/sda1: UUID="805424F85424F318" TYPE="ntfs" LABEL="gx280-xp" 
/dev/sda5: UUID="0933d680-d893-40fa-a01d-3c819f0b2ea3" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="3119f61a-7ab2-4b91-b9c8-44fa795dfae5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" LABEL="swap" UUID="7f9f938e-90da-4c2d-a75a-bd680b97aa4e" 

```

---

### Post by Springy182 on 2010-03-23
sudo blkid gives me the UUID of my NTFS/EXT4 partitions, but the swap says "TYPE="swap" instead of UUID=

Nevermind, remade it in gparted. I'll try editing the fstab now.

---

### Post by Springy182 on 2010-03-23
I tried editing fstab, this time it worked!

In fact it fixed the problem I was trying to fix of the swap not mounting automatically.

Thank you both for your help.

---

