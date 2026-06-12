---
title: "Two Partitions"
date: 2011-03-20
forum: General Help
---

### Post by sports fan Matt on 2011-03-20
I have two partitions now (one of each) of lucid and maverick. The lucid one is 153 gb which I'd like to give back to Maverick..any idea how I can do this?

---

### Post by Dark_Stang on 2011-03-20
Is there any important data on the partition you want to remove? If so, you should pull that over first. Otherwise, you can just pop in a GParted disk or an Ubuntu Disk, fire up GParted, delete the unwanted partition and expand the other one.

---

### Post by sports fan Matt on 2011-03-20
Not a thing.  Created a backup partition in case this one went south.

---

### Post by sports fan Matt on 2011-03-20
I have a ubuntu lucid disk.  So I guess I delete where the 153 gb space is (cant remember what partition)

---

### Post by sports fan Matt on 2011-03-20
Want to keep SDA5 (Maverick partition) and allocate the lucid partition to maverick)

---

### Post by lmarmisa on 2011-03-20
You could select two different strategies:

1) Delete all the contents of the partition containing lucid and reuse that partition for data (images, documents, music, etc). This is the simplest approach.

2) Using an Ubuntu Live CD/USB and GParted you could remove the lucid partition and then expand the maverick one with the released space of disk. You have to considerer other existing partitions, like those defined for swapping.

You could post the result of this command

sudo fdisk -l

in order to evaluate if this solution is easy or not.

Finally, you would need to update or reinstall grub in both cases.

---

### Post by sports fan Matt on 2011-03-20
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070abe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18614   149511583+   7  HPFS/NTFS
/dev/sda2           18614       60802   338873345    5  Extended
/dev/sda5           32426       60053   221917184   83  Linux
/dev/sda6           60053       60802     6010880   82  Linux swap / Solaris
/dev/sda7           18614       31859   106390528   83  Linux
/dev/sda8           31859       32425     4548608   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by sports fan Matt on 2011-03-20
SDA5 (Maverick partition)

---

### Post by lmarmisa on 2011-03-20
Is /dev/sda6 the maverick swap partition?

---

### Post by sports fan Matt on 2011-03-20
Accordiong to Gparted yes since SDA 7 Is lucid and sda 8 is lucid partition

---

### Post by lmarmisa on 2011-03-20
If you have any doubt about your swap partition, please post the outputs of these commands:

```

cat /etc/fstab
sudo blkid

```

---

### Post by sports fan Matt on 2011-03-20
lucid partition is 101.46 gb
maverick is: 211.64 gb

---

### Post by sports fan Matt on 2011-03-20
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b3492c1e-7b0a-4131-821a-a1e5c4c7aad3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=173c64b1-5256-4017-8781-e710e7c29548 none            swap    sw              0       0


/dev/sda1: UUID="268856BD88568B67" TYPE="ntfs" 
/dev/sda5: UUID="b3492c1e-7b0a-4131-821a-a1e5c4c7aad3" TYPE="ext4" 
/dev/sda6: UUID="173c64b1-5256-4017-8781-e710e7c29548" TYPE="swap" 
/dev/sda7: UUID="e9762333-183b-4741-8d05-38d8e9d0d75e" TYPE="ext4" 
/dev/sda8: UUID="e697fb73-5578-467b-8a57-2e594a7f4a6d" TYPE="swap"

---

### Post by lmarmisa on 2011-03-20
I think you could remove partitions /dev/sda7 and /dev/sda8 and then extend the partition /dev/sda5 using the released space but I would like to be 100% sure.

Could you post a capture (Applications -> Accessories -> Take Screenshot) of GParted showing your partitions?.

---

### Post by sports fan Matt on 2011-03-20
I can

---

### Post by lmarmisa on 2011-03-20
Thanks for the capture.

Yes. I agree. You can remove the two lucid partitions /dev/sda7 and /dev/sda8 using GParted from Maverick.

Then, I highly recommend to make a backup of your system: partitions /dev/sda1, /dev/sda5 and /dev/sda6. The resizing of partitions is a risky procedure. So, make a backup before. Consider to use [Clonezilla Live]("http://clonezilla.org/downloads.php") and an external USB drive for that backup.

When you finish that backup, boot your system into an Ubuntu Live CD/USB, open GParted and extend the partition /dev/sda5 with the free space located at left. Apply the changes.

You should have no problems restarting Maverick.

Type this last command then:

```

sudo update-grub

```

---

### Post by sports fan Matt on 2011-03-20
A usb drive is a no go since I do not have one.  I will run lucid from a live cd "trying" it, get gparted on there long enough to delete it, then be done.  I have tried a few time to remove 7 and 8 and running sudo update-grub but 7 and partition 8 show back up. so i'll try this approach

---

### Post by sports fan Matt on 2011-03-20
Forgot to apply the actions--it always helps :)

---

### Post by lmarmisa on 2011-03-20
> **sox fan Matt said:**
> A usb drive is a no go since I do not have one.  I will run lucid from a live cd "trying" it, get gparted on there long enough to delete it, then be done.  I have tried a few time to remove 7 and 8 and running sudo update-grub but 7 and partition 8 show back up. so i'll try this approach

I recommend you to buy a USB hard drive for backups. This is an excellent investment. All the hard disks will die. It's just a matter of time. If you have no backup, then you will lose all your data. So, consider to make periodical backups of your data.

There is an alternative option to extend /dev/sda5 with no risk. Simply create a new partition (EXT4 or NTFS) using the free space. You will need to add a new line in the file /etc/fstab if you wish to automount that partition in Maverick.

---

### Post by sports fan Matt on 2011-03-20
looks like i'll be up all night.  When I ran the comm,and to update grub, I got a grub error and no response from vista or Ubuntu.  I fear all my things in Vista are gone

---

### Post by lmarmisa on 2011-03-20
What system are you running now?.

What system were you running when you typed the command sudo update-grub?

---

### Post by sports fan Matt on 2011-03-20
Running the live cd of lucid, and was running maverick.  The partitions are still there according to: Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070abe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18614   149511583+   7  HPFS/NTFS
/dev/sda2           18614       60802   338873345    5  Extended
/dev/sda5           32426       60053   221917184   83  Linux
/dev/sda6           60053       60802     6010880   82  Linux swap / Solaris

I ran sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

and am wanting to see if that could fix it :)

---

### Post by lmarmisa on 2011-03-20
I cannot help too much with lilo. I have some knowledge about Grub 2.

---

### Post by sports fan Matt on 2011-03-20
The Master Boot Record of  /dev/sda  has been updated.
This should be a good sign

---

### Post by sports fan Matt on 2011-03-20
That got me back into Windows.  I can always reinstall Ubuntu later or this weekend but for now I am headed to bed.  Thanks for your help!

---

### Post by sports fan Matt on 2011-03-20
I'll check back in the morning to see if anyone has an idea as to the whereabouts of my ubuntu partition.

---

