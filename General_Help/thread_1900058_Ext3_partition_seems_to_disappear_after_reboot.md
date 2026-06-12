---
title: "Ext3 partition seems to disappear after reboot"
date: 2011-12-25
forum: General Help
---

### Post by BloodPhilia on 2011-12-25
I got a local Ubuntu development server running Ubuntu Server 9.04. (Yes I know it's old!) Anyway, it froze the other day and on reboot it wanted to check the disk, errors were found. Afraid of losing the data I immediately mirrored the drive using Norton Ghost to an image file (.gho) on a backup disk. And surely enough, the drive failed almost immediately after the backup.

Now I've got a working image file that has all the data, nothing seems to be missing. After copying the image to a new drive I wanted to boot, but somehow GRUB didn't get to booting and said "/dev/mapper/hostname-root" (the bootup root) was missing. So I went into the GRUB menu and changed the boot commands so the root was set to "/dev/sda6/" (my root partition) directly.

To my delight, it booted! With just one problem... Whenever I reboot (sometimes it takes two reboots), the root partition seems to be gone! Neither GRUB nor a Ubuntu livecd will detect the partition any longer and it won't boot. If I don't boot the disk after the copying, the livecd WILL detect it and I can even mount it and access my data.

Norton Ghost will see the root partition merged with the swap partition (which is suddenly about 500GB in size) and the livecd won't detect it at all.

I've replicated this about 5 times with 2 different (brand new) drives by writing the .gho image to a new drive.

From running Ubuntu, after boot:
```

admin@WEB-UBUNTU:~$ sudo blkid
/dev/sda5: UUID="cc95c47b-fc1c-4918-9f79-706db2af98fd" TYPE="ext2"
/dev/sda6: UUID="ba898223-7a86-40d3-bb11-267562af4902" TYPE="ext3"
/dev/sda7: TYPE="swap"

admin@WEB-UBUNTU:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro,usrquota,grpquota)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-19-server/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /boot type ext2 (rw,relatime)

admin@WEB-UBUNTU:~$ sudo fdisk -l
[sudo] password for admin:
lege partitie (6) wordt weggelaten [EN: Empty partition (6) is omitted]

Schijf /dev/sda: 500.1 GB, 500107862016 bytes [EN: schijf = disk]
255 koppen, 63 sectoren/spoor, 60801 cilinders [EN: koppen = heads, sectoren = sectors, spoor = track, cilinders = cylinders]
Eenheid = cilinders van 16065 * 512 = 8225280 bytes [EN: Unit = Cylinders of]
Schijf-ID: 0x0001a71a [EN: Disk-ID]

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               2       60801   488376000    f  W95 Uitgeb. (LBA)
/dev/sda5           60770       60801      257008+  83  Linux
```

---

### Post by jsra on 2011-12-25
Hi, dont have solution for this, just one thought.
Try to run: ```
cat /etc/fstab
```
Maybe it will help with further progress.

---

### Post by BloodPhilia on 2011-12-27
> **jsra said:**
> Hi, dont have solution for this, just one thought.
Try to run: ```
cat /etc/fstab
```Maybe it will help with further progress.

It's not the mounting that is an issue. The entire partition isn't detected, mounted or unmounted.

---

### Post by routed on 2011-12-27
Maybe the disk duplication did not work correctly due to it failing?

---

### Post by BloodPhilia on 2011-12-27
> **routed said:**
> Maybe the disk duplication did not work correctly due to it failing?

Very plausible, but it doesn't explain why the copy WILL boot only once and starts the entire OS and then loses the partition all of a sudden after a reboot. More importantly, how do I fix it?

---

### Post by xyzzyman on 2011-12-27
Can you copy the clone onto a new drive, and before booting off the drive fsck it from a live cd/usb? Maybe even open it with gparted and see if any errors are detected? Maybe it copied an error in the structure of something and a mount/unmount is enough to completely corrupt it to the point you're seeing.

Seeing as it's so specific of a repeatable failure I'd assume it's not bad RAM or something but maybe a few passes of memtest wouldn't hurt.

---

### Post by BloodPhilia on 2011-12-27
> **xyzzyman said:**
> Can you copy the clone onto a new drive, and before booting off the drive fsck it from a live cd/usb? Maybe even open it with gparted and see if any errors are detected? Maybe it copied an error in the structure of something and a mount/unmount is enough to completely corrupt it to the point you're seeing.

Seeing as it's so specific of a repeatable failure I'd assume it's not bad RAM or something but maybe a few passes of memtest wouldn't hurt.

If I run an fsck with a livecd before booting the disk, it shows plenty of inode errors and then fixes all of them. After running fsck from the livecd, fsck shows the partition as clean. I then rebooted from the disk and the same behaviour is shown. I can boot only once (or sometimes twice) before it disappears again.

And I already checked and even replaced the memory to no effect. Memtest still shows clean strips after 5 passes.

---

### Post by xyzzyman on 2011-12-27
Sorry to ask about the memory, not always sure if that's been tested. What does gparted or fdisk show on the drive for the partition table before you boot off of it? The fdisk you show has them merged already.

As you seem to already have spare HDD's, my opinion to repair is to recreate the partition structure on a new HDD, and cp the data back over using the -P switch (case sensitive switch, it's the same as --preserve) to preserve all attributes including ownership. Unless it's a hardware failure or a process in your installation re-corrupting if it truly is okay after fsck it should be good.

---

### Post by BloodPhilia on 2011-12-27
> **xyzzyman said:**
> What does gparted or fdisk show on the drive for the partition table before you boot off of it? The fdisk you show has them merged already.

How is it possible it shows them merged, even though the partition IS already mounted? (See mount)

---

### Post by BloodPhilia on 2011-12-27
> **xyzzyman said:**
> Sorry to ask about the memory, not always sure if that's been tested. What does gparted or fdisk show on the drive for the partition table before you boot off of it? The fdisk you show has them merged already.

As you seem to already have spare HDD's, my opinion to repair is to recreate the partition structure on a new HDD, and cp the data back over using the -P switch (case sensitive switch, it's the same as --preserve) to preserve all attributes including ownership. Unless it's a hardware failure or a process in your installation re-corrupting if it truly is okay after fsck it should be good.

Can you explain how I would go about creating an exactly the same, new structure? I'm relatively new to extensive partitioning.

---

### Post by xyzzyman on 2011-12-27
> **BloodPhilia said:**
> How is it possible it shows them merged, even though the partition IS already mounted? (See mount)

```
admin@WEB-UBUNTU:~$ sudo fdisk -l
[sudo] password for admin:
lege partitie (6) wordt weggelaten [EN: Empty partition (6) is omitted]

Schijf /dev/sda: 500.1 GB, 500107862016 bytes [EN: schijf = disk]
255 koppen, 63 sectoren/spoor, 60801 cilinders [EN: koppen = heads, sectoren = sectors, spoor = track, cilinders = cylinders]
Eenheid = cilinders van 16065 * 512 = 8225280 bytes [EN: Unit = Cylinders of]
Schijf-ID: 0x0001a71a [EN: Disk-ID]

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               2       60801   488376000    f  W95 Uitgeb. (LBA)
/dev/sda5           60770       60801      257008+  83  Linux
```

Oh, I'm reading it wrong. You actually appear to have had SDA5 and SDA6 inside of an extended partition (SDA1).  I thought you also had a win95 partition on sda1.

---

### Post by xyzzyman on 2011-12-27
> **BloodPhilia said:**
> Can you explain how I would go about creating an exactly the same, new structure? I'm relatively new to extensive partitioning.

Use gparted on the new HDD and create an ext3 partition and a swap partition. It's all GUI and you can click and delete/create. Also restore a drive but don't boot off it as we want your data accessible.

Then mount the partitions and at a prompt (Changing the names of where they're mounted accordingly):
```
 
cp -P /mount/olddrive/* /mount/newdrive/*

```

You will then have to edit the /etc/fstab file on the new drive to point to the UUID's or /dev/sda#'s as the UUID's will have changed. If you use /dev/sdaX then also adjust accordingly as you will be using just /dev/sda1 and /dev/sda2 now probably. You can get UUID's by right-clicking and choosing 'Information' in gparted. 

If you get that done, then we will look into chrooting into the install to reinstall grub or you can use boot-rescue.

If I'm missing something or if I'm being a dunce and this won't work someone please chime in.

---

