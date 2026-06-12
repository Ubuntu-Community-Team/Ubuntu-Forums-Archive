---
title: "Hard drive won't boot but works?"
date: 2011-03-14
forum: General Help
---

### Post by egx on 2011-03-14
Hi, it's been 10 hours and more working on that one and can't find the solution. I hope you guys can help.

I have that old tower computer with a 80 GB WD Hard drive. Everything worked fine but then I tried to delete everything on the hard drive. Booted from the live CD, installed Ubuntu, and never booted..

I can boot on the Live cd just fine but it won't boot on the hard drive. I don't know if I messed with the MBR or something while formating and I don't know how to fix it... 

I'll rewrite the sudo fdisk -l here since the wireless adapter doesn't seem to work with the live CD anymore...
When I mount the hard drive from the live CD, I can navigate through it and everything is working fine.
Edit: wireless working again! So I have internet working on the live CD from the tower!

Sudo fdisk -l

Disk /dev/sda: 80.0 GB 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk Identifier: 0x00082eea

Device    Boot          Start         End       Blocks         ID         System
/dev/sda1 *              1              9539       76614656   83        Linux
/dev/sda2               9539           9730       1533953      5        Extended
/dev/sda5                9539           9730       1533953      82     Linux swap / Solaris


Thanks for your help! I'll try anything.... I don't have any data on the hard drive.

---

### Post by Hugh971 on 2011-03-14
Sounds like it could be something in the boot options in the bios.  Check that boot from the hard disk is enabled. 

Do you get an error when trying to boot?

---

### Post by egx on 2011-03-14
> **Hugh971 said:**
> Sounds like it could be something in the boot options in the bios.  Check that boot from the hard disk is enabled. 

Do you get an error when trying to boot?

Hard disk boot is first in the boot sequence. Although, when booting, it just:
Verifying DMI pool
Boot from CD ROM:

As if it skips the hard drive booting. 

I earlier had 2 hard drives and it was 
Verifying DMI pool
Read error
Boot from CD ROM:

Since I took off the second hard drive and changed the jumper from the master harddrive, no more read error, but still no booting from HDD.

I'm pretty sure it's enabled, i'm going to check this right now but I don't know how to check this? Where do I?

---

### Post by egx on 2011-03-14
So I just tried with another hard drive and they now both give me READ ERROR just after the DMI Pool data at the boot. None of them will boot. 

Boots #1 from the live cd...

The problem might not be the hard drives?

---

