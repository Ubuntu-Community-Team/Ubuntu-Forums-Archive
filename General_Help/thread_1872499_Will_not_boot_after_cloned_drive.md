---
title: "Will not boot after cloned drive"
date: 2011-10-30
forum: General Help
---

### Post by xluke on 2011-10-30
Hello,
I recently cloned a drive (dual boot ubuntu 11xxx and windows 7) with Acronis Disk Director (which should have copied the MBR).  When I choose to boot off of the new cloned drive the system simply re-posts and boots with the original drive.  My guess is that GRUB isn't working on the new cloned drive -- how can I go about repairing this so that it will work?

Thanks!

---

### Post by WasMeHere on 2011-10-30
Hi xluke,

Do you boot your system with both drives in the computer, the original one as well as the clone? This will make the system confused, because the disk UUID (identification) are the same.

If you have only the clone (attached) in your computer, it should boot exactly as if it were the original. Otherwise the cloning process failed.

Have fun finding out :-)
Olle

---

### Post by xluke on 2011-10-30
I would like to leave the other drive in the box and just change the boot order -- is it not possible to change the ID?  Also, acronis did have an option to copy NT record, which I did not do as they warned of exactly that, conflicting drive IDs...

Thanks!

---

### Post by WasMeHere on 2011-10-30
What if you swap the cables to the drives?

If you change the UUID, make sure to adjust the references that could be found in grub files and fstab (and maybe somewhere else)! Otherwise the cloned disk will not boot properly. It is messy, I would *not* recommend that.

Why do you want to run your system with two clones at the same time? Maybe there is another solution for what you want.

---

### Post by xluke on 2011-10-30
Thanks for your thoughts!

I'm moving my HDD content to a new SSD which I want to run my OSes and basic applications from in the interest of efficiency.  The old HDD will serve principally as storage (0.5TB HDD vs 128gb SSD) but it would be nice to leave its boot record intact so that if something fails with the SSD I can simply boot my HDD backup.  

I appreciate any suggestions.

Thanks!

---

### Post by WasMeHere on 2011-10-31
Say that you have or make a data partition with documents and media files etc. Then I think that you can have an image of your system partitions including the master boot record instead of a clone. This can be accomplished with Clonezilla (a linux based live system).

In your particular case, I think you can make your present clone on the SSD to the 'original' and wipe your system partitions on your hard drive. But of course be sure to leave your data partition!!!

Then you can use your cloning software to make an image instead of a clone. Usually an image is compressed, which is an advantage. The disadvantage is that it takes some time to restore it (compared to just replacing the drive), but you should not need it very often.

It is even better to make images regularly as backup on an external disk, that is stored separated from the computer.

---

### Post by dcstar on 2011-10-31
> **Olle Wiklund said:**
> 
Do you boot your system with both drives in the computer, the original one as well as the clone? This will make the system confused, because the disk UUID (identification) are the same.
.........

Correct, you need to manually change the UUID of the new partition(s) and then fix the new /etc/fstab to use then new UUID(s) as well.

---

### Post by xluke on 2011-10-31
Update:  Removal of the primary drive resulted in the same booting to flashing cursor then returning to post.  I presume this suggests this is not a UUID issue but rather a problem with the mbr or grub?

Thanks for your continued help!

---

### Post by dcstar on 2011-10-31
> **xluke said:**
> Update:  Removal of the primary drive resulted in the same booting to flashing cursor then returning to post.  I presume this suggests this is not a UUID issue but rather a problem with the mbr or grub?

Thanks for your continued help!

You need to boot off the original drive and then use **gparted** to look at the partition layouts of both drives. If they are not virtually identical then you will have issues.

You can change the UUID on the new drive now (and change the /etc/fstab entry), and then do this so you can test boot off the new system:

```
sudo update-grub
```
Reboot and select the new system, then once it boots up:
```
sudo dpkg-reconfigure grub-pc
```
To install Grub correctly on the new disk.

---

### Post by xluke on 2011-10-31
Hello,
Odd, gparted sees the SSD as "Unallocated space" and further states that "can't have overlapping partitions."  In contrast, Acronis shows the SSD to be well partitioned and the only difference between the drives is that the linux partition is moved ahead of the windows "sysdrive" partition in the clone...

Thanks!

---

### Post by WasMeHere on 2011-10-31
I wonder if Clonezilla would have changed the order of the partitions. Would you be prepared to make another attempt to clone your MBR and your system partitions?

Maybe the problem is that you clone from a bigger to a smaller drive. That way there cannot be a perfect clone, since there is not space for everything. Or that Acronis is running from Windows, and cannot manage linux stuff well enough?

It might be faster to make a fresh install instead of copying and trying to fix some inconsistent data. Because of the commercial nature of Windows, maybe you should clone the Windows installation (the first part of the hard drive to the first part of the SSD using ***dd*** (low level copying each byte including the MBR). This is risky though, so I would strongly recommend a separate backup before you start doing that. See ```
man dd
```

---

