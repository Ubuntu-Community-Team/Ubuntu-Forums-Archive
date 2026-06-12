---
title: "Partitioning issue"
date: 2010-10-10
forum: General Help
---

### Post by mickeoliver on 2010-10-10
Hello,

I recently installed ubuntu alongside windows 7 on my machine.

I ardly know anything about partitions, but I managed to shrink the windows partition to make space, abd then use the ubuntu installer to create the ubuntu partition.

But I hadn't realized that there were actually 3 Windows partitions - "Acer C:", "Recovery", and "System, Active, Primary Partition".

So I didn't know that I should have made the ubuntu partition "Extended", which means that I can't make new partitions anymore.

Is there anything I can do without reinstalling ubuntu?

Sorry if this is a stupid question - I'm learning.

---

### Post by srs5694 on 2010-10-10
The easiest and safest way is probably to re-install Ubuntu; however, if you've spent a lot of time customizing Ubuntu and are willing to risk losing it, post the output of "sudo fdisk -lu" (typed in a Terminal window), preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. Depending on the results, there may be a way to convert your partition to a logical partition without too much risk.

---

### Post by mickeoliver on 2010-10-11
It took me more than a week to install ubuntu - countless issues with hard drives and the monitor. I really want to avoid going though all that again!

Here's the output:

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x099063f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Unknown
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS
/dev/sda3        27469824  1268881407   620705792    7  HPFS/NTFS
/dev/sda4      1268894025  2930276351   830691163+  83  Linux

```

---

### Post by srs5694 on 2010-10-11
As it happens, there's space between /dev/sda3 and /dev/sda4. This means it's possible to convert /dev/sda4 into a logical partition that resides inside a new extended partition. (What's now /dev/sda4 will become /dev/sda5, and a new /dev/sda4 extended partition will be created.)

The problem is that I don't know of any tool that's designed to do this conversion. I know of three ways to do it:


[LIST]
[*]**fdisk** -- You can launch fdisk *with the -u option* (as in "sudo fdisk -u /dev/sda4"), delete /dev/sda4, create a new extended partition that fills the space at the end of the drive, and create a new logical /dev/sda5 partition *that starts and ends at the same location as the current /dev/sda4.* If you're comfortable with fdisk, this should be a snap to do, but of course there's always the risk of an error, so you should work carefully an don't use the "w" option to save your changes until you're absolutely positive you've done it right.
[*]**sfdisk** -- The sfdisk utility can write your existing partition table to a disk ("sudo sfdisk -d /dev/sda > parts.txt"). You can then edit that listing in a text editor and write the changes back to disk ("sudo sfdisk /dev/sda < parts.txt"). The editing you'd need to do would be to change the number of /dev/sda4 to /dev/sda5 and then create a new /dev/sda4 that starts anywhere between the end of /dev/sda3 and one sector before the start of /dev/sda5. It must be large enough to hold all of /dev/sda5, plus at least one sector before /dev/sda5.
[*]**GPT fdisk (aka gdisk)** -- This program is designed for editing GPT disks, but it includes both MBR-to-GPT and GPT-to-MBR conversion capabilities, and the latter enables you to assign disks to be primary or logical. Thus, it can be used for the conversion. To do so, launch it on the disk ("sudo gdisk /dev/sda"; this automatically converts the in-memory representation to GPT), type "r" to enter the recovery & transformation menu, and type "g" to convert to MBR form. This will show you a summary of partitions. Unless I've overlooked something, they'll all be primary partitions at this point, so you'd type "4" to edit partition 4 and type "l" to change it to logical. You'll then need to change its type code: type "4" again, type "t" and then type "83". You'll also want to set the active flag on partition 2, so type "2" and then "a". The display should now match what you desire. (Be aware that the partition numbers still reflect the GPT partition numbers, so the Linux partition will still be partition 4. They'll also have "GPT Name" columns that are irrelevant, so you can ignore that column.) Type "0" to accept the settings and convert the disk. A problem: I just ran through this procedure and discovered that gdisk 0.6.12 (the latest version) has a bug that's preventing it from working. There's a workaround, but it's confusing. I'll try to release a new version that'll work in the next day or two, so if you want to try it this way, keep an eye out for version 0.6.13.
[/LIST]


It's entirely possible (even probable) that you'll need to re-install your boot loader after using any of these methods.

---

### Post by mickeoliver on 2010-10-12
Using GPT fdisk seems easiest, I'll wait for the update.

EDIT: this? [http://sourceforge.net/projects/gptfdisk/](http://sourceforge.net/projects/gptfdisk/)

---

### Post by srs5694 on 2010-10-12
What timing! I just released GPT fdisk 0.6.13. Check the [Sourceforge downloads page.](http://sourceforge.net/projects/ms-sys-free/) Be sure to grab the version for your architecture (i386 or amd64). It should install by double-clicking the icon, or you can use dpkg ("sudo dpkg -i foo.deb", where "foo.deb" is the complete filename).

---

### Post by mickeoliver on 2010-10-12
Thanks, I'll try that tomorrow.

---

### Post by mickeoliver on 2010-10-13
I tried using gdisk, it worked, but now I'm unable to start my computer in any OS!

When I turn it on, there's just a black screen with the text "GRUB".

I probably should have reinstalled GRUB straight away!

What should I do now? I had a GParted Live CD, and I'm able to use that to see the drives.

Please help!

---

### Post by srs5694 on 2010-10-13
I generally use [Super GRUB Disk](http://www.supergrubdisk.org/) for this sort of thing. If your GRUB configuration uses UUIDs rather than partition numbers, it should boot right up. If your GRUB configuration relies on partition numbers, you'll need to tweak them using GRUB's edit mode (select an entry and type "E" to edit it). This is a rather primitive text-based editor, and it does *not* save changes to disk (it's just good for one boot), but it'll get you going if you know what you need to change. In your case, if you're using GRUB 2, you'd probably need to change all references to (hd0,4) to (hd0,5), assuming you've successfully converted /dev/sda4 into a logical /dev/sda5.

Once you're booted into your regular system, run update-grub and grub-install to update and re-install GRUB.

---

### Post by mickeoliver on 2010-10-14
It worked!

EDIT: I am unable to boot Windows, it tells me to insert recovery disk. Grub's "Windows Recovery" option does work, however.

I'm afraid to use the recover option, would that mean I won't be able to use ubuntu until I (re)install GRUB or something?

---

### Post by srs5694 on 2010-10-14
The Windows recovery tool might or might not render Ubuntu unbootable, depending on what it decides needs fixing. If it does render Ubuntu unbootable, using Super GRUB Disk and re-installing GRUB again, as you just did, should fix it.

I've a sneaking suspicion the problem may be the disk identifier number (0x099063f4 in your earlier fdisk output). If you run fdisk again and it shows as something else, try entering fdisk ("sudo fdisk /dev/sda"), type "x", and then type "i" to enter a new value. With that done, type "w" to save the changes. If that doesn't help, type "sudo fdisk -lu" and post the output again. Maybe I'll be able to spot some subtle change that could account for the problem.

---

### Post by mickeoliver on 2010-10-14
I tried changing the disk identifier number, but it didn't help.

When I try to start Windows, it says "A required device is inaccesssible." Is that any help?

Output of sudo fdisk -lu
```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a2695b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Unknown
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS
/dev/sda3        27469824  1268881407   620705792    7  HPFS/NTFS
/dev/sda4      1268894024  2930276351   830691164    f  W95 Ext'd (LBA)
/dev/sda5      1268894025  2930276351   830691163+  83  Linux

```

Well, I think that I'll just use the recover tool anyway.

---

### Post by srs5694 on 2010-10-14
Is the fdisk output you posted from before or after you changed the disk identifier? Because it doesn't match what you showed earlier (in post #3 in this thread). IIRC, Windows does store this information and use it, so it's plausible that it would give you the "device is inaccessible" error if the ID number had changed.

If the current ID number matches what it was before, then using the Windows recovery tool is probably your best bet at this point. As far as I can tell, everything else about the Windows partitions is identical to what they were before, unless perhaps the CHS values have changed during the conversion. (They're not reported by fdisk on this page, and since GPT doesn't use CHS values, they get discarded and then re-created in the conversion you used, so it's possible they've changed.)

Unfortunately, the error you've reported isn't very diagnostic. I've seen it several times myself, and in reference to very different problems.

---

### Post by mickeoliver on 2010-10-15
I reinstalled Windows (painful) and GRUB, now it is working prefectly!

Thank you so much for your help!

[IMG]http://questgarden.com/72/60/1/081205162959/images/thank-you.jpg[/IMG]

---

