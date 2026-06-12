---
title: "Help a new guy out with partitioning"
date: 2009-12-17
forum: General Help
---

### Post by mkeyes001 on 2009-12-17
how much space should be allocated for root & swap (4gb memory) of a 500g drive.  And should I put home on a separate partition from root?  my current install (my 1st one ever) I used ext3 for root and I had existing data on my other 2 partitions I left as ntfs.  I have to manually mount my other 2 partitions after every reboot, would it be more beneficial to reinstall and use ext3 for all my partitions?  What would be a good layout?

thanks in advance

---

### Post by Darael on 2009-12-17
You shouldn't have to remount every boot - take a look at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
You'll need at least 4G for / unless you're going for a complex setup with /usr on a separate partition. I always put /home on a separate partition, but it's no longer really needed unless you want to multiboot more than one Linux system.  If you do put it on another partition, you probably want to give it most of the drive. Oh, and with that amount of RAM, you don't really need swap unless you want the ability to hibernate, in which case you should probably give it about five gigabytes to ensure there's room for a full RAM dump and space left over.

---

### Post by mkeyes001 on 2009-12-17
Thanks Darael for the link.  So if I do decide to rebuild with /home on its own partition which filesystem type should I use, ext3?

---

### Post by Darael on 2009-12-17
Well, I've been using ext4, since it's got features that make it better for dealing with large files, which are most likely to turn up in /home. But otherwise, ext3 is fine, or you could do a little research and maybe choose another FS. I just wish btrfs was ready...

---

### Post by Leppie on 2009-12-17
i'm using jfs for system partitions and xfs for home (both require modules to be loaded by grub).
it depends a bit on what you're going to put in home.

---

### Post by sgosnell on 2009-12-17
Either ext3 or ext4 should work, but I think ext3 will eventually be obsolete, and I've been using ext4 for everything.  Everything will be obsolete eventually, but with ext4 you should have a useful system for a little longer, and perhaps an easier transition to subsequent filesystems.

I prefer having /home on a separate partition, so I can change the OS, upgrade, or whatever, and still have my data in place without having to worry about it being formatted over.  For the OP, you need about as much swap space as RAM if you plan to use hibernate, and I think that's a good amount for a disk of that size.  You shouldn't miss 4GB of disk space.

---

### Post by audiomick on 2009-12-17
Hallo.
+1 for swap size = RAM size + a little bit. The hibernate/suspend functions write the contents of the RAM into the swap space in order to recall it on wake up. Obviously can't work if swap is too small.

If you make /home separate, which is to be recommended, you should allow between 10 and 15 GB for / , which will have the operating system as such in it. The contents grow with time, depending on what programs you run, and updates. To give you an idea:

I did a fresh install for someone recently. After the install ( 9.10 ubuntu, no extras ) there was about 2.7GB in / . Prior to the install, I had to resize her partitions, because her / was full. I had given it 5GB in the origonal install ( 8.04 LTS ), and it had gotten up to 4.85GB or so, without having had a version update.

My Ubuntu Studio install started at 8.04, and has been upgraded via the upgrade function through to 9.10. I tend to install things just to have a look, and not de-install. I have the complete Ubuntu Studio Install, plus Open Offic, evolution and so on. My / has nearly 6GB in it.

The reason for having /home on it's own partition is, if you managed to shoot down your system, you can do a fresh install, remount your /home without formatting, and, when you get everything re-installed that you had on, you are back where you where before the mishap. Same applies to an upgrade via fresh install.

---

### Post by sgosnell on 2009-12-17
One minor quibble:  With a .5TB disk, I would give at least 10GB to /, probably more.  It's a small percentage, and as you add programs, you can quickly fill up the partition, especially as programs grow exponentially.  If you don't have much available storage, as with a smaller SSD, then you may need to keep / smaller, but with a large HDD you can certainly afford to be a little more generous with /, and avoid potential future problems.

---

