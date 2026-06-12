---
title: "Boot problem: Karmic won't start, dropping into initramfs"
date: 2010-01-23
forum: General Help
---

### Post by johnerskine2010 on 2010-01-23
I'm running Karmic on an AMD 64 on Efficient PC (Re-badged Asus Anubis), with Nvidia Corporation MCP51 High Definition Audio card.

In recent days my system has been freezing, although this has generally been solved with a reboot.

Now, however, GRUB is failing to start Karmic, and is dropping me into initramfs.

I have tried a systemrescue cd (see here [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)), which when I switch on slows down at

[I]ATA1 port is slow to respond
forcing hard reset
comreset failed errno=-16
srs failed errno=-19
limiting SATA speed to 1.5gbps[/I]

Once I've got the system rescue cd running, I can't mount the either of my partitions /sda1 (ext3) or /sda2 (swap) to run fsck

booting in recovery mode gives me

[I]mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/dev failed: no such file or directory
Done
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg[/I]

Running dmesg | tail shows

[I][2.540798] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 384 not in group (block 4023357247)!
[2.540937] EXT3-fs: group descriptors corrupted![/I]

On the basis of this I think that I either have a corrupted filesystem, or more seriously, I have a hard disk problem.

The first thing I want to do is to try to run fsck on sda1 to try to repair any filesystem damage - how can I do this. I've got both a systemrescue dc and a Knoppix disk. 
   
Suggestions welcome!

---

### Post by n0dix on 2010-01-23
Post your partitions numbers:
```
sudo fdisk -l
```

---

### Post by johnerskine2010 on 2010-01-23
Now managed to sort this, with help on another forum. 

See here [http://kubuntuforums.net/forums/index.php?topic=3109680.0](http://kubuntuforums.net/forums/index.php?topic=3109680.0)

The filesystem was corrupted, but opening a console in Knoppix and running

*sudo e2fsck -C0 -p -f -v /dev/sda1 *

sorted it 

Thanks for the suggestion however. 

With Linux, one is never alone!

---

### Post by n0dix on 2010-01-23
> **johnerskine2010 said:**
> 
With Linux, one is never alone!

yeah, this is the truth!! ;)

---

