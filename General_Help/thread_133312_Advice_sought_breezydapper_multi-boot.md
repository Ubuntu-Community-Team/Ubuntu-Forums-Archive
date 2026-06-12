---
title: "Advice sought: breezy/dapper multi-boot"
date: 2006-02-19
forum: General Help
---

### Post by Lux Perpetua on 2006-02-19
I have the space, so I want to have one stable OS (Breezy) and one experimental one (Dapper). Basically, I want to know the best way to partition my drive. Assume I have around 50 GB to play with. Here's roughly the current layout:

NTFS partition ~ 12 GB (Windows XP)
ext3 partition ~ 50 GB (Ubuntu Linux)
swap partition ~ 2 GB
FAT32 partition ~ 5 GB (?) (IBM service)

I want to do it more carefully the second time around. My current idea is to replace my single Linux partition with the following:

/home ~ 30 GB
Ubuntu Breezy ~ 10 GB
Ubuntu Dapper ~ 10 GB

-> I don't have a good sense of how much swap I should have (I have about 2 GB of actual RAM). 
-> Is this a reasonable layout? Since the order of partitions is significant, is any particular ordering preferable to this? I put /home first because it seems to allow the greatest flexibility down the line if I want to change the number of operating systems. 
-> I don't *think* this is an issue, but does it matter which sections go into primary or extended partitions?

Any help is appreciated, and thanks in advance!

---

### Post by RAOF on 2006-02-19
With 2 GB of ram, you might not even need a swap partition.  If you still want some swap, 500MB - 1GB should be ample.

That layout looks fine, although you can probably cut some of the space from your root partitions.  A bit more than 5GB is probably fine.

Finally, I'd recommend using the LVM options of the installer.  That way, you don't actually need to care how your partitions are laid out - you set up an LVM volume-group, and make logical volumes on that.  If you want to remove the breezy root, you can just add it to your Dapper volume, or maybe to your home volume.  Plus, if you later add a hard-drive, you can add that to your volume group and extend your logical volumes onto it.

---

### Post by Lux Perpetua on 2006-02-20
[QUOTE=RAOF]
Finally, I'd recommend using the LVM options of the installer.  That way, you don't actually need to care how your partitions are laid out - you set up an LVM volume-group, and make logical volumes on that.  If you want to remove the breezy root, you can just add it to your Dapper volume, or maybe to your home volume.  Plus, if you later add a hard-drive, you can add that to your volume group and extend your logical volumes onto it.[/QUOTE]Cool, I didn't know about this. Thanks for your help!

---

### Post by RAOF on 2006-02-20
Actually, in case you want any help with configuring LVM in the installer, what you do is:

1) Set up a partition - mark it as "use for LVM"
2) Go to the "finish partitioning & set up LVM" option.
3) Create a volume group, and add the partition to it.  You're done setting up the volume group
4) Create the logical volumes on the volume group.  You can even give them useful names, like dapper-root, shared-home, swap etc :)
5) Finish setting up LVM, and back at the partitioner you should see all your logical volumes, and be able to assign them to /, /home, etc. as normal.

---

### Post by Lux Perpetua on 2006-02-20
Thanks. I read through a lot of the LVM howto ([http://www.tldp.org/HOWTO/LVM-HOWTO/)](http://www.tldp.org/HOWTO/LVM-HOWTO/)), but one thing I'm still not clear on is how the booting would work, i.e., what I would need to do to be able to boot either of the two operating systems.

[To clarify, the way I have it set up now is that the Windows NT boot loader is on the MBR, which is set up to boot Windows and Linux (GRUB is on my Linux partition). If possible, I would like to avoid modifying the MBR.]

---

### Post by RAOF on 2006-02-20
[QUOTE=Lux Perpetua]...
[To clarify, the way I have it set up now is that the Windows NT boot loader is on the MBR, which is set up to boot Windows and Linux (GRUB is on my Linux partition). If possible, I would like to avoid modifying the MBR.][/QUOTE]
Oh, really?  I've never actually tried doing this.  I seem to recall some sort of howto lying around somewhere, though...  I use GRUB on my MBR to load windows, and it's always worked fine for me.

Oh, and another thing: if you're going the LVM route, /boot **must** be on a separate partition.  Sorry I didn't mention that.  The GRUB can't boot from LVM, so it needs a small (~50MB) ext3 partition to store the kernel(s) you use.

---

### Post by Lux Perpetua on 2006-02-20
Okay, so if I were to go the LVM route, here is my impression of what I would put on the disk:

- small /boot partition
- big LVM volume group with everything else: Breezy root, Dapper root, shared /home, and swap

The way I understand it, /boot can be shared between two operating systems. I would (1) install one of the operating systems (say, Breezy), partitioning the disk and also installing GRUB to /boot or the MBR; (2a) install the other OS to a logical volume, but don't install a bootloader, just have the right kernel in /boot; (2b) add an entry to /boot/menu.lst for the second OS. (I'm not sure of the exact syntax for this, but I'm not very worried about that if this is the right approach.)

---

### Post by RAOF on 2006-02-20
[QUOTE=Lux Perpetua]Okay, so if I were to go the LVM route, here is my impression of what I would put on the disk:

- small /boot partition
- big LVM volume group with everything else: Breezy root, Dapper root, shared /home, and swap

The way I understand it, /boot can be shared between two operating systems. I would (1) install one of the operating systems (say, Breezy), partitioning the disk and also installing GRUB to /boot or the MBR; (2a) install the other OS to a logical volume, but don't install a bootloader, just have the right kernel in /boot; (2b) add an entry to /boot/menu.lst for the second OS. (I'm not sure of the exact syntax for this, but I'm not very worried about that if this is the right approach.)[/QUOTE]
That's the right approach.  I currently have Dapper & Breezy (which I incidentally never boot into ;)) sharing a /boot partition, and exactly your setup - four logical volumes: breezy-root, dapper-root, shared-home, swap.

---

### Post by Lux Perpetua on 2006-02-21
RAOF, thanks for the help. My setup appears to be working smoothly. :)  Someone should start a how-to for this, since some parts were a bit nontrivial. (If one doesn't pop up, I may volunteer...)

---

### Post by David Valentine on 2006-02-21
I would be interested in seeing such a howto as well.  I'm eager to try out dapper, but too much of a newbie to trust myself to do it right.  Plus, I'd like to start putting /home on its own partition so I can try different OS configurations without so much hassle.

---

### Post by archis on 2006-02-21
Hope you'll get the chance to write it up, Lux Perpetua. I for one would appreciate it lots. I will try to use LVM the next time around as well.. I already have the single allowed extended volume tied up on the HD but still want to break up my Ubuntu install into logical volumes.

---

### Post by soonindallas on 2006-02-21
I second the PP: I would like to see such a howto.  my thread with the same question had no takers.

this solution seems more elegant and flexible than what I had imagined, though a little more complex since there is a need for a /boot partition because of the grub/LVM incompatibility.

I have an Ipod I can put my /home on to while I mess with the rest but I'd appreciate seeing the procedure...

---

