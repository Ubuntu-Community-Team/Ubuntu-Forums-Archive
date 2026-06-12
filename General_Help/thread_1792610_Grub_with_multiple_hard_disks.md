---
title: "Grub with multiple hard disks"
date: 2011-06-28
forum: General Help
---

### Post by Neville Hillyer on 2011-06-28
I am an ex Mac user and am relatively new to Ubuntu and PC hardware. I am trying to set up a large old Celsius PC to boot a range of disks many of which have Ubuntu - several disks may be connected at once. After spending some time reading about Grub 2 I am still unsure about some critical details.

Am I correct in thinking that multiple Grub instances do not communicate with each other (not mentioned anywhere that I could find) and that the only way to control which Grub instance is used is to control this outside of Grub?

Can Grub instance selection only be done with multiple hard disks by a combination BIOS settings and disk location?

What do others with this requirement normally do?

I am considering putting Grub 2 on a USB stick to control all booting - would this be a good solution?

The BIOS on my old Celsius appears to only control the boot order via class of device ie floppy, optical, USB, SCSI, SATA or IDE etc. It does not appear to define a particular device. Is this normal or is it likely that a later BIOS would have finer control? Can I assume that within a particular class it will always scan in the same order? If so I assume I would only have to ensure that I used the first USB socket.

---

### Post by sanderd17 on 2011-06-28
Every disk has an MBR and the BIOS decides which disk is tried first.

Afterwards, the mbr of that disk points to a specific grub install on a specific partition. Grub needs to get it's configuration files somewhere. That can be from the same disk or from another disk.

So they can all be installed next to each other, if they are on a separate disk, the bios can select between them.

To install GRUB with a debian based distro (like ubuntu), see this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) Look at reinstalling grub from the live CD.

---

### Post by Neville Hillyer on 2011-06-28
As I said, as far as I can determine I am unable to select a particular disk with my BIOS - is this common?

If I have several disks I don't want to have to edit all instances of Grub which is why I am looking for alternatives.

I would appreciate answers to my original questions.

---

### Post by oldfred on 2011-06-28
Old IDE systems only booted from primary master hard drive which was set with jumpers on hard drive. BIOS only controlled by hard drive, CD or floppy.

Newer BIOS that support SATA drives are smarter and let you select boot drive. My BIOS still calls boot drive primary master but I am just selecting in BIOS which drive to boot. SATA drives have no jumpers (best thing ever, well up there with sliced bread;))

Still newer BIOS within last 3 or 4 years let you boot USB devices. My BIOS has many options to boot USB including USB-HDD. But it does not boot USB flash drives from USB selection but from hard drive selection. Took me a while to find that out.

I like to install an operating system on every drive and have the boot loader for that system in the MBR of that drive. But grub2 will find just about every installed system and add it to your menu. So which every drive you boot it lets you boot the operating system on any drive. But once you get more than 2 or3 you start manually reducing options as it can get to be too many. I also manually add chainload entries from one MBR to another in case I forget to change in BIOS and want to boot from another drive as I have turned off the auto prober.

---

