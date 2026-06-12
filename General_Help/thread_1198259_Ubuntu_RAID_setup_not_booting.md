---
title: "Ubuntu RAID setup not booting"
date: 2009-06-27
forum: General Help
---

### Post by BSSPenfold on 2009-06-27
For a couple of years, I've had a home server running Mythbuntu 7.10, with a RAID 5 array on it (4 x 500GB).

Recently, I was copying a large number of files to another Ubuntu 9.04 PC, over my LAN. Then the file transfers froze, and I couldn't use my server at all. When I reset it, The BIOS showed the following message:

[HTML]Detect Drives Done, No Any Drives Found[/HTML]

After this message, it got to GRUB, auto-selected the latest kernel, but then, instead of seeing the usual booting progress bar, I had a blank screen, which after a few minutes showed the following:

[HTML]BusyBox v1.1.3(Debian 1.1.1.3-5 ubuntu 12)
Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/HTML]

I tried a few things to fix it after searching online, but not being an expert on Ubuntu/Linux, I didn't get very far. Also worth noting, was that there was no hard drive activity noise, as there usually would be when booting - just silence.

I checked the BIOS, and it still recognised the 4 drives. I could boot from the Ubuntu 9.04 Live CD, and it too could see the 4 drives, though it could not mount any of them, due to them being setup for RAID5.

Eventually, due to what would be a fairly minimal and acceptable data loss (I had backups of what I needed), I decided to format the drives and install Ubuntu 9.04, with a slightly different (better than previous) RAID setup:

[HTML]RAID 1
/dev/sda1 1GB /boot
/dev/sdb1 1GB /boot

non-RAID
/dev/sdc1 1GB (swap)
/dev/sdd1 1GB (swap)

RAID5 (for Ubuntu OS)
/dev/sda2 5GB /
/dev/sdb2 5GB /
/dev/sdc2 5GB /
/dev/sdd2 5GB /

RAID5 (for file storage)
/dev/sda3 494GB /data
/dev/sdb3 494GB /data
/dev/sdc3 494GB /data
/dev/sdd3 494GB /data[/HTML]

All previous partitions and RAID arrays were deleted, so as to start afresh, and setup went as planned (BrightEyesDavid helped me set it up in a similar fashion to his server), and Ubuntu installed fine, told me to remove the CD, then hit enter as usual to reboot.

Hopes were high, but I got the same blank screen again. I don't even get the 'Detect Drives Done, No Any Drives Found' message first, and it never reaches the BusyBox prompt.

The BIOS still recognises the 4 drives, and as far as I know, there is a perfectly installed Ubuntu setup on the 4 drives (partitioned as above) on them. The problem just seems to be that it isn't seeing either the drives and/or the bootloader somehow.

This is why we were wondering if this is a motherboard/BIOS issue. Do you think that flashing/reinstalling the latest firmware would help? Or does this sound like another kind of problem?

The motherboard is an ASUS M2N-SLI Deluxe.

Any help would be much appreciated, thanks.

---

### Post by BrightEyesDavid on 2009-06-27
Just to add to Penfold's description of the reinstall, the RAID is software RAID (as was his previous installation), set up using the alternate install CD.

I don't understand why we can install Ubuntu across RAID in this way but not boot into it.

---

### Post by ronparent on 2009-06-27
There appears to be a bug in 9.04 affecting both 'fakeraid' and software raid that in certains instance will not allow you to boot to a raid or, for that matter, allow automounting. The bug is probably hardware related and doesn't affect everyone or in the same way. You might find a work around for the software raid in the server section of this forum.

---

