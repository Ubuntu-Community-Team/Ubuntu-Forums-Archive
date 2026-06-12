---
title: "I have realy serious problem: &quot;error loading os&quot;"
date: 2009-10-28
forum: General Help
---

### Post by Qazjap11 on 2009-10-28
I tried to install Win XP in adition to ubuntu. First i tried to make partition in the HD through the install but pressing "c" just did nothing. Then i tried to do it in ubuntu, i created new partition and wanted to check the result. I booted XP again and then recognized the size of the new partition was zero. I deleted this partition and rebooted. Unfourtanatly i saw the message "Error loading operating system". Now i'm writing from Live CD whithout recover function.
Any suggests?
From where can i download recover disk?
:(

---

### Post by Giblet5 on 2009-10-28
I'm afraid that you are running from the Recovery Disk.

Not to fear (yet).

Open a terminal window and enter ```
sudo fdisk -l
``` and post the output here.

---

### Post by teward on 2009-10-28
A thought: What if the main partition table on his drive got messed with to the point it's not readable?  Wouldn't that pose a small problem, which would need the partition table to be reset?

-----
TrekCaptainUSA

---

### Post by Giblet5 on 2009-10-28
> **TrekCaptainUSA said:**
> A thought: What if the main partition table on his drive got messed with to the point it's not readable?  Wouldn't that pose a small problem, which would need the partition table to be reset?

-----
TrekCaptainUSA

There is no evidence of that.........yet but it's a possibility.

Let's see what fdisk has to say first.

---

### Post by Qazjap11 on 2009-10-29
It says:
>  
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78ab78ab
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59483   477797166   83  Linux
/dev/sda2           59484       60801    10586803+  82  Linux swap / Solaris
I have one installed VirtualBox on it (WIN XP)

---

### Post by Giblet5 on 2009-10-29
> **Qazjap11 said:**
> It says:
I have one installed VirtualBox on it (WIN XP)

So, from the liveCD, you should be able to fix this via:

Open a terminal window.

```
sudo bash
mount /dev/sda1 /mnt -text
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
grub-install /dev/sda
sync;sync
reboot
```

You should have your grub menu back and be able to boot Ubuntu.

If you got errors, please repeat the process and post them here.

---

### Post by Qazjap11 on 2009-10-29
> **Giblet5 said:**
> So, from the liveCD, you should be able to fix this via:

Open a terminal window.

```
sudo bash
mount /dev/sda1 /mnt -text
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
grub-install /dev/sda
sync;sync
reboot
```

You should have your grub menu back and be able to boot Ubuntu.

If you got errors, please repeat the process and post them here.
Yes! it worked!!!
Thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you
:)
And last question: How to make safely a partition for WIN XP will be installed on it?

---

### Post by Giblet5 on 2009-10-29
> **Qazjap11 said:**
> Yes! it worked!!!
Thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you thank you
:)
And last question: How to make safely a partition for WIN XP will be installed on it?

Great!

It looks to me like you're using that entire 500GB disk drive for Linux (477GB on /, and 9+GB for swap).

I don't think there's enough room.

You can look at resizing the linux partition down to free up some space, but that's usually dangerous...

I'd add a second disk drive and install XP on that.

(You'll have to repeat the fix instructions when you're done cuz XP will overwrite grub's MBR)

---

### Post by Qazjap11 on 2009-10-29
> **Giblet5 said:**
> Great!

It looks to me like you're using that entire 500GB disk drive for Linux (477GB on /, and 9+GB for swap).

I don't think there's enough room.

You can look at resizing the linux partition down to free up some space, but that's usually dangerous...

I'd add a second disk drive and install XP on that.

(You'll have to repeat the fix instructions when you're done cuz XP will overwrite grub's MBR)
Why not enough space?
I use only ~70 GB from 477...

---

