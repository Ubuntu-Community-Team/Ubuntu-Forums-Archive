---
title: "If I reformat my entire hard drive, would that fix gparted and the Ubuntu installer?"
date: 2010-12-28
forum: General Help
---

### Post by sirspazzolot on 2010-12-28
Long story short, I can't sign in to Ubuntu anymore (GNOME is broken and I can't fix it for the life of me) and I can't reinstall Ubuntu because gparted is broken and the installer crashes because of that. I've been getting increasingly annoyed at my computer because of all of this and I just want Ubuntu to work again. I don't know why gparted is crashing and I really don't care to find out anymore. If I just reformat my whole hard drive to one big partition, would that fix gparted and let me install Ubuntu? I've already backed up everything I need, I just don't want to do this if it won't accomplish anything. I want to be sure beyond reasonable doubt. Thanks in advance.

PS: Don't suggest a gparted liveCD or parted magic, those both don't work either.

Also, if I do reformat, should I do MBR or GUID? I know the difference between the two and I know I'll probably just do MBR since it's what I had and the four-partition cap wasn't an issue, but I suppose more opinions never hurt.

Thanks in advance

---

### Post by sirspazzolot on 2010-12-28
Rats. I meant to make this in Installations and Upgrades, sorry! If a mod thinks this location is bad, feel free to move it.

---

### Post by howefield on 2010-12-28
Having had similar sounding issues installing Ubuntu 10.10 on a laptop recently, I used a 10.04.1 CD instead to create the partitions. 10.10 then installed perfectly to those partitions using the manual option at the partitioning stage, and making sure not to mark them for formatting.

Have you access to something like that ?

---

### Post by sirspazzolot on 2010-12-28
I have an EXT4 partition already, my issue is that the installer crashes before getting to the partitioning stage :P

---

### Post by pricetech on 2010-12-28
Have you tested the disk you're installing from to make sure there's not a problem with it ??

Have you run manufacturer's diagnostics on the hard drive in question to make sure it's okay ??

From there, I see no reason for it to crash if you've already had Maverick installed and working.

---

### Post by sirspazzolot on 2010-12-28
How should I go about testing it? Are there any tools to test for a defect in the drive? It's seemingly working fine, I believe that gparted just hates one of my partitions.

---

### Post by oldfred on 2010-12-28
Gparted would not open my sda which has XP, but saw sdb, & sdc after a long time trying to open sda. My XP booted normally, but after running chkdsk on the NTFS partition gparted immediately opened the sda drive.

I might run chkdsk on all NTFS partitions and e2fsck on all ext3 or ext4 parititons.

You can check hard drive with System, Administration, Disk utililty, click on drive and on right side is Smart Status.

---

### Post by dodo3773 on 2010-12-28
> **sirspazzolot said:**
> How should I go about testing it? Are there any tools to test for a defect in the drive? It's seemingly working fine, I believe that gparted just hates one of my partitions.

To check the installation disks I use md5sum. First I check the ISO then I burn it to a disk. After that create an ISO from the disk you just burned and check that md5 if they all match up right there is probably nothing wrong with the disk. There is a gui program called gtkhash if you do not want to use the command line.

---

### Post by srs5694 on 2010-12-28
I wouldn't recommend wiping everything without understanding the  nature of the problem first. For one thing, it could be a hardware issue, as others have suggested. For another thing, even if it's not a hardware issue, the problem could recur and you'd be back at Square One. If you understand the problem, you can probably fix it more easily than by wiping and re-installing, which will help both now and if the problem recurs. Also, if you understand what's causing the problem, you might be able to prevent a recurrence. (How depends on the cause, of course.)

There are several tools to check a disk's SMART status (SMART being the hardware self-diagnostic tools in modern drives). A text-mode tool is called smartctl; type "smartctl -a /dev/sda" to get a report on /dev/sda. A GUI tool I often use is GSmartControl (program filename gsmartcontrol). Type its name and you'll get a window showing disk devices. Double-click a disk to get a report in a tabbed window.

For more help on diagnosing the problem, please post the output of "sudo fdisk -l", when typed in a text-mode shell on your computer. Post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

As to the MBR-vs-GPT issue, I favor GPT for Linux-only installations. GPT offers a number of advantages over MBR. Most of these are minor, like the presence of a partition name in GPT and the fact that GPT keeps a backup of the important data, which theoretically makes it more robust against certain types of errors. The lack of a primary/extended/logical partition distinction is, IMHO, of moderate importance. The biggest advantage of GPT is its 64-bit sector pointers, which shatter the 2 TiB limit of MBR; but of course this doesn't matter on most hard disks in use today, just on RAID arrays and a small (but increasing) number of high-end models. Thus, the advantages of GPT are minor, but IMHO worth taking if you can. That last phrase is important, though, since Windows can't boot from GPT except on EFI-based systems, so if you dual-boot with Windows, MBR remains preferable (except on non-boot data disks). Also, a few BIOSes are buggy and will give problems with GPT; see [this page](http://www.rodsbooks.com/gdisk/bios.html) of mine for details. For much more on GPT, see [my GPT fdisk (gdisk) documentation.](http://www.rodsbooks.com/gdisk/index.html)

---

### Post by Jerry N on 2010-12-28
Is this an older hard drive?  Trying to install Ubuntu 10.04 (might have been a beta or RC at the time) screwed two of my older drives to the point where no form of gparted would touch them (Ubuntu Live, Parted Magic, etc).  Something to do with partition alignment, according to some information I found.  I had to go back to a Win 98SE boot disk with Windows Fdisk to get them straightened out.  Later Linux installs on those disks were OK.  Other than that, it would seem to me that failure of gparted to recognize the drive would indicate a hard drive problem.  Western Digital and Seagate have downloadable disk diagnostic programs.  Other drive manufacturers probably have those too.

Jerry

---

