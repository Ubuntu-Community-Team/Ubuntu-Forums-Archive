---
title: "Two drives-both have different partition info?"
date: 2011-09-08
forum: General Help
---

### Post by Shazaam on 2011-09-08
I have a dual boot system...
1. Ide hard drive with WinXP
2. SATA hard drive with swap, an extended partition containing Karmic and Natty.
Windows drive has it's own MBR bootloader. Ubuntu drive has grub2 installed in it's MBR. The bios is set to boot cdrom first, SATA second, and the Win drive last. All drives/partitions boot.
I recently noticed a blurb flash by while booting Natty that said that it was unable to mount the swap partition. It would do this on an irregular basis. After multiple edits of fstab and initramfs-tools' conf.d; updating same; purging and reinstalling grub2; deleting/re-making the swap partition swap finally has been auto-mounted on a regular basis (for the last two days).
What bugs me is that Karmic and Natty STILL show different partition info (both on the same drive). Is there a known bug with grub/upstart/mountall etc. that causes this? I have attached two screenshots to help whoever has an idea about what's going on.
BTW, boot-info-script's Results.txt shows the same goofy info when run on Natty.

---

### Post by dcstar on 2011-09-09
> **Shazaam said:**
> 
.........
What bugs me is that Karmic and Natty STILL show different partition info.


You are booting two **different** OSs (separated by **years**) that are showing exactly what each **different** OS is supposed to.

Things change over time, you know?

---

### Post by fdrake on 2011-09-09
> **Shazaam said:**
> I have a dual boot system...
1. Ide hard drive with WinXP
2. SATA hard drive with swap, an extended partition containing Karmic and Natty.
Windows drive has it's own MBR bootloader. Ubuntu drive has grub2 installed in it's MBR. The bios is set to boot cdrom first, SATA second, and the Win drive last. All drives/partitions boot.
I recently noticed a blurb flash by while booting Natty that said that it was unable to mount the swap partition. It would do this on an irregular basis. After multiple edits of fstab and initramfs-tools' conf.d; updating same; purging and reinstalling grub2; deleting/re-making the swap partition swap finally has been auto-mounted on a regular basis (for the last two days).
What bugs me is that Karmic and Natty STILL show different partition info. Is there a known bug with grub/upstart/mountall etc. that causes this? I have attached two screenshots to help whoever has an idea about what's going on.
BTW, boot-info-script's Results.txt shows the same goofy info when run on Natty.

did you install karmic before windows?

---

### Post by mcduck on 2011-09-09
They look pretty much the same to me, apart from the 1MB of unallocated space, which is most likely related to alignment of partitions to cylinder/block boundaries and isn't really relevant.

The different OS versions seem to assign different device names to the drives, which is quite normal on certain hardware, the names are assigned based on the order the devices are recognized, and some computers & BIOS versions can detect devices in different order on each boot. I suppose this might have been the reason for your swap problems, especially if you at any point had defined your swap in /etc/fstab using the device name. And this is pretty much the reason why it's recommended to use the UUID instead of device name.

---

### Post by Shazaam on 2011-09-09
What I was getting at was the fact that Karmic shows the Ubuntu drive as sdb while Natty shows it as sda.

mcduck...
```
can detect devices in different order on each boot
```
I had a hunch about the bios doing that but Natty was the first version of Ubuntu that I have installed that ended up this way. Weird.
Ok, so it's normal so I will mark the thread as solved. Thanks everyone for your help.

---

### Post by Shazaam on 2011-09-22
Update...
Wiped Karmic and installed Lucid in its place. Lucid is controlling grub. So far all is good. :)
(hmm, edited the thread title but it didn't stick)

---

