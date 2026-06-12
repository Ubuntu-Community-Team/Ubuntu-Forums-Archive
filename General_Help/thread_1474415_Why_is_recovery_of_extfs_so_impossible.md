---
title: "Why is recovery of extfs so impossible?"
date: 2010-05-06
forum: General Help
---

### Post by summersab on 2010-05-06
So, I was moving partitions the other night to get ready for a fresh install of Lucid. I used a Lucid live USB drive and GParted. Right in the middle of a move and resize of my /home ext4 partition, the system locked up. This has happened once before. That time, I simply let the disk activity light go until it stopped, restarted, and everything was fine. This time, I restarted, and the partition had been moved, not resized, and GParted recognized it as "Unknown." After using Testdisk, e2fsck, mke2fs -S, and a piece of software by Stellar Phoenix, I'm completely frustrated, and I think my data is gone. I know it got moved, but I simply cannot make any program see the data on the disk.

My frustration is simple: ext2, 3, and 4 are open source. FAT and NTFS are closed source. I have used tools numerous times in the past that have discovered full directory trees of files from corrupted Microsoft partitions. Some of them were free, others were not. Even still, those partition types are closed source - I imagine it took a bit of reverse engineering to figure out how to rebuild and find that data. Linux partitions are OPEN SOURCE. We, the community, own it and the code. Why is there not a good tool to find straight up raw data on a disk? I know my data is on my drive, but the partition containing it is broken. So? The stinkin' physical magnetic patterns aren't gone. Is there really no way to scan for patterns and rebuild a tree? I know there is Photorec, but it just finds and dumps files - I'd REALLY like my directory trees back. If this is all open source, why aren't there a dozen tools that do this?

This question isn't necessarily rhetorical - I'd actually like a good explanation if there is one. Also, if you have any direction on how to get my files back, I'd be forever in your debt.

---

### Post by nitstorm on 2010-05-06
Maybe one of these could help? Never had that problem so thought I'd find links to help ya.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd](http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd)

---

### Post by dcstar on 2010-05-06
> **summersab said:**
> So, I was moving partitions the other night to get ready for a fresh install of Lucid. I used a Lucid live USB drive and GParted. Right in the middle of a move and resize of my /home ext4 partition, the system locked up. This has happened once before. That time, I simply let the disk activity light go until it stopped, restarted, and everything was fine. This time, I restarted, and the partition had been moved, not resized, and GParted recognized it as "Unknown." After using Testdisk, e2fsck, mke2fs -S, and a piece of software by Stellar Phoenix, I'm completely frustrated, and I think my data is gone. I know it got moved, but I simply cannot make any program see the data on the disk.
.........
This question isn't necessarily rhetorical - I'd actually like a good explanation if there is one. Also, if you have any direction on how to get my files back, I'd be forever in your debt.

Make a note of the partition start and end positions, (for safekeeping) find a partition table editor and see if you can manually set the partition table type.

Use this to set the Partition Type to 83:

```
sudo cfdisk
```

---

### Post by summersab on 2010-05-06
@David, it's odd. fdisk -l shows it as Linux (type 83) - that was my first instinct, too. However, GParted shows it as unknown. I don't know what that means.

@nitstorm, AWESOME page. It's bedtime, but I'll give it a shot in the morning and post any results. Thanks, man!

---

### Post by rnerwein on 2010-05-06
hi
i really don't now if it works ( i've ) never tried it by myself but  give it a shot:
--> photorec - Recover lost files from harddisk, digital camera and  cdrom  ( see man pages )
good luck

ciao

---

### Post by bumanie on 2010-05-06
Testdisk should recover the entire partition, if not, as stated above, try photorec, it recovers 100+ files types and is filesystem independent - ie it recovers stuff off the raw hard drive. They both work well in their respective functions.

---

### Post by dcstar on 2010-05-06
> **summersab said:**
> @David, it's odd. fdisk -l shows it as Linux (type 83) - that was my first instinct, too. However, GParted shows it as unknown. I don't know what that means.


Gparted gets its partition information from a different place, a system can still boot and work even if gparted has issues.

There are other posts that have resolutions to this sort of problem, I think that they use a ext2fs tool to get the partition entry fixed up.

Anyway, have a read: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by dino99 on 2010-05-06
test with the latest partedmagic: [http://partedmagic.com/](http://partedmagic.com/)

have you forced a fsck ? : sudo shutdown -F -r now

---

