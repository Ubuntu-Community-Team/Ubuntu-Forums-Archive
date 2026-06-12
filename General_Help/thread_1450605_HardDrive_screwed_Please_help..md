---
title: "HardDrive screwed? Please help."
date: 2010-04-09
forum: General Help
---

### Post by Hikayu on 2010-04-09
Okay, I think I have a problem of leaving my computer exposed when important stuff, such as upgrading and partitioning, are being done. To the un-tech savvy people. Often leading to devastating results...

So this time its a problem with my partition. I have(had) two partitions. I had a older version of Ubuntu on the smaller one, and the beta version (Lucid Lynx ftw) on the larger side. To cut long crap short, I decided to remove the old one after shifting everything important on it to the newer partition.

[I][B]
Let's do a basic checklist[/B][/I] :)

So I removed the old partition **[RIGHT]CHECK![/RIGHT]**
I prepared to move the new partition to the left **[RIGHT]CHECK![/RIGHT]**
I left the room since it will take seven hours **[RIGHT]CHECK![/RIGHT]**




**And Than...**

Mother/Sister/Father comes in **[RIGHT]CHECK![/RIGHT]**
They go "Wtf?" **[RIGHT]CHECK![/RIGHT]**
Ah, just some experiment... I'll just reboot XD **[RIGHT]CHECK![/RIGHT]**
Computer destroyed **[RIGHT]CHECK![/RIGHT]**




So, in current circumstances, I can actually mount the hard-drive and view everything. But it just doesn't boot. Here's a pic on what gparted says *(I'm **SURE** there's something fishy. I just don't know _what_.)*:

[[img]http://www.freeimagehosting.net/uploads/th.7a0b0b14f7.png[/img]](http://www.freeimagehosting.net/image.php?7a0b0b14f7.png)

---

### Post by Hikayu on 2010-04-09
Bump. Dire situation. :(

---

### Post by ibuclaw on 2010-04-09
So I take it that you ran a filesystem check from the LiveCD and everything returned OK?

Righto, next thing to do then is check the UUID of the partition.

```
sudo blkid /dev/sda5
```
And then compare the UUID printed to the UUID present in /etc/fstab for the partition.




Sometimes, setting a temp password on the LiveUser account and locking the screen is the best thing to do. ;)

---

### Post by ibuclaw on 2010-04-09
> **Hikayu said:**
> Bump. Dire situation. :(

Bumping after 12 minutes? This isn't realtime support, and patience is a virtue.

---

### Post by Hikayu on 2010-04-09
> **ibuclaw said:**
> So I take it that you ran a filesystem check from the LiveCD and everything returned OK?

Righto, next thing to do then is check the UUID of the partition.

```
sudo blkid /dev/sda5
```
And then compare the UUID printed to the UUID present in /etc/fstab for the partition.




Sometimes, setting a temp password on the LiveUser account and locking the screen is the best thing to do. ;)


I'm getting somewhere here. So, in fstab I have this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ccefcf87-ef89-4f80-bd92-02fbb4aafe1c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e3e19a4d-8ebd-4b2f-81a9-8bb636e38e6f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Which do i replace with the current UUID? Also, about the lock, it's pointless if they simply switch off the power. :lolflag:

(Added after editing)
I just noticed that the UUID is the same (-_-") and that I didn't read the

> So I take it that you ran a filesystem check from the LiveCD and everything returned OK?

part. I'll do a check now.

---

### Post by Hikayu on 2010-04-09
Seems that the test came back ok.

```

root@bt:~# fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 287715/15130624 files, 5876891/60500782 blocks

```

---

### Post by mikewhatever on 2010-04-09
I don't think Gparted shows anything unusual. When you say 'it just doesn't boot', it's not very useful. What does happen? Any errors?

---

### Post by Hikayu on 2010-04-09
> **mikewhatever said:**
> I don't think Gparted shows anything unusual. When you say 'it just doesn't boot', it's not very useful. What does happen? Any errors?

No errors whatsoever. Just doesn't boot. Stops just before Ubuntu's logo should be shown.
Also, I think that sda5 should be OUTSIDE sda2. That's what I meant by the "fishiness"

---

### Post by ibuclaw on 2010-04-09
> **Hikayu said:**
> No errors whatsoever. Just doesn't boot. Stops just before Ubuntu's logo should be shown.
Also, I think that sda5 should be OUTSIDE sda2. That's what I meant by the "fishiness"

Does GRUB menu show?

Hold down SHIFT when you boot the computer, then select "Recovery Mode", that will output alot more information, and will give an indication as to where it goes wrong.

Regards
Iain

---

### Post by Hikayu on 2010-04-09
> **ibuclaw said:**
> Does GRUB menu show?

Hold down SHIFT when you boot the computer, then select "Recovery Mode", that will output alot more information, and will give an indication as to where it goes wrong.

Regards
Iain

I think by saying "It just doesn't boot", I meant that the GRUB bootloader doesn't even initialize. It just stops (not freeze mind you) at that point, like as if there's no OS on the hard drive. Like it's booting from the wrong partition or searching for the OS in the wrong spot.

I'll try "holding shift" while booting now though.

---

### Post by Hikayu on 2010-04-09
> **Hikayu said:**
> I think by saying "It just doesn't boot", I meant that the GRUB bootloader doesn't even initialize. It just stops (not freeze mind you) at that point, like as if there's no OS on the hard drive. Like it's booting from the wrong partition or searching for the OS in the wrong spot.

I'll try "holding shift" while booting now though.

After holding shift, "GRUB" appears in the console. But there's nothing after that. In a normal boot several hours ago, the text "GRUB" would appear without me holding shift and that would extend to "GRUB started" or something similar, blurting out the version of GRUB shortly after and proceeds to clearing the screen and asking which OS I would like to boot.

---

### Post by trundlenut on 2010-04-09
looking at the screenshot you have one extended partition that isn't shown as bootable.  Can you change it to a primary partition and set it as bootable.

Presumably Grub is looking at the drive for a bootable primary partition.

---

### Post by ibuclaw on 2010-04-09
> **Hikayu said:**
> After holding shift, "GRUB" appears in the console. But there's nothing after that. In a normal boot several hours ago, the text "GRUB" would appear without me holding shift and that would extend to "GRUB started" or something similar, blurting out the version of GRUB shortly after and proceeds to clearing the screen and asking which OS I would like to boot.

Okie doke. Probably just a re-installation of GRUB then on your system.

In the LiveCD
```

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C

```

Then
```

dpkg-reconfigure grub-pc

```
Select the standard options available, although give each menu a good read before hand, incase you spot anything that shouldn't be.


And once finished with that, optionally clean up your doings.
```

umount /dev/pts
umount /sys
umount /proc
exit
sudo umount /mnt/dev
sudo umount /mnt

```

And then try booting into your system.

Overblown method, yes - but ensure all failsafes are covered.

Regards

---

### Post by Hikayu on 2010-04-09
> **ibuclaw said:**
> Okie doke. Probably just a re-installation of GRUB then on your system.

In the LiveCD
```

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C

```

Then
```

dpkg-reconfigure grub-pc

```
Select the standard options available, although give each menu a good read before hand, incase you spot anything that shouldn't be.


And once finished with that, optionally clean up your doings.
```

umount /dev/pts
umount /sys
umount /proc
exit
sudo umount /mnt/dev
sudo umount /mnt

```

And then try booting into your system.

Overblown method, yes - but ensure all failsafes are covered.

Regards


DAMN! I just noticed that my /home directory isn't there. Seems that most data was lost because it was cancelled midway. ****. All my games were there. All my work files were there. OMG. I hate partitioning. I hate partitioning when it takes long like that. And now I hate life.

I guess I should just reinstall everything. And than blame my family. Is there anyway I can restore everything?

---

### Post by Hikayu on 2010-04-09
I could've made a backup. Sheesh. My bad.

---

### Post by Hikayu on 2010-04-09
So in other words: Thread solved. HardDrive screwed. Jeez. I wasn't able to save anything.

---

### Post by ibuclaw on 2010-04-09
> **Hikayu said:**
> So in other words: Thread solved. HardDrive screwed. Jeez. I wasn't able to save anything.

Look up testdisk, you can install it in the LiveCD, and use it for partition recovery.

Regards
Iain

---

### Post by trundlenut on 2010-04-09
Try something like systemrescue cd which includes testdisk.  Your data may well still be there but not visible anymore.

---

### Post by Hikayu on 2010-04-09
Well, it's too late. I've reformatted my HardDrive. Well, happy birthday, new Ubuntu.

---

