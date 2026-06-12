---
title: "EXT2 vs EXT3"
date: 2010-04-23
forum: General Help
---

### Post by Flexico on 2010-04-23
I am planning on dual-booting Windows XP and Ubuntu on a new laptop, and because I have a program that lets me mount an ext2 filesystem on Windows, I was thinking of installing Ubuntu with ext2 instead of ext3. I am concerned, however, that it might open up a security risk for my Ubuntu partition. Would this cause a problem? (In case it's relevant, I use AVG Free antivirus in Windows.)

---

### Post by mikewhatever on 2010-04-23
Read this -> [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3).
The major security issue in this setup would be yourself, accidentally trumping some important system files, rather then Windows malware, which doesn't work on Linux. Anyway, the security issue has nothing to do with the choice of ext2 vs ext3.

---

### Post by jerome1232 on 2010-04-23
Also ext3 can be used as ext2. 


Ext3 is basically ext2 with journaling. So when that driver mounts an ext3 partition it simply ignores the journal and uses the ext3 partition as if it were ext2, this works just fine.

---

### Post by psusi on 2010-04-23
Yes, you should use ext3.  Without the journaling your fs can easily become corrupted and will require a lengthy check after a crash or power loss.

---

### Post by oldfred on 2010-04-23
I like to keep things as near to normal as possible to avoid issues. I have seen windows only users recommend a separate data partiton so your data is not in the windows operating system partition (when windows crashes). 
So when I installed Ubuntu I created a shared NTFS partition. In windows I would copy most of my data there ( you also can change to location of my docs if you want but I do not use my docs) and created a .bat file to copy some other stuff as backup. Never had any issues with the shared NTFS partition, but now most of my data is in linux EXT3 data partitions as I do not need it in windows.

---

### Post by sunk8 on 2010-04-23
Man, even ext4 is out since karmic...

---

### Post by srs5694 on 2010-04-23
I recommend *not* giving Windows access to your Linux root (/) filesystem. I also advise not giving Linux access to the Windows boot (usually C:) partition. The reason in both cases is that the files on these filesystems are very sensitive; a mistake in editing one file can render the entire OS unbootable or otherwise badly damaged, and a foreign OS might make such editing mistakes a bit too easy. Non-native filesystem drivers are often a bit flaky, so even if you don't touch a file, errors can creep in. (Such errors seem rare when using NTFS-3g in Linux to access NTFS. I don't know how reliable the Windows ext2 drivers are.) An exception to my rule would be in emergency repair situations; it might be useful to be able to edit some configuration file in another OS if the other OS has already been damaged.

That said, cross-OS data exchange can be valuable. Thus, I recommend creating a data-exchange partition for this purpose. If you have lots of files you want to access in either OS, you can make it a very big partition. If you create a separate /home partition for Linux, you might even use it for that purpose; however, there's always the risk of your damaging Linux user configuration files in Windows if you do that, so you might prefer using something else.

You could forego the ext2fs driver in Windows and use NTFS as the data-exchange partition's filesystem; or you can use the ext2fs driver and use ext2fs or ext3fs as the data-exchange filesystem. If the latter, I'm not sure if Windows will automatically mount the Linux root (/) filesystem as well. To eliminate that possibility, you could use another filesystem (ReiserFS, XFS, or JFS) on your root (/) partition. If you use /home for your data-exchange partition, it must be ext2fs or ext3fs, not NTFS; Linux requires the features of a native filesystem in /home, and NTFS doesn't provide those features.

---

### Post by srs5694 on 2010-04-23
> **psusi said:**
> Yes, you should use ext3.  Without the journaling your fs can easily become corrupted and will require a lengthy check after a crash or power loss.

The journal doesn't do anything to minimize the risk of corruption. All that the journal does is record where the OS had been making filesystem changes, so that in the event of a power loss, system crash, or other unexpected shutdown, the disk check can be restricted to those areas that were being modified, rather than to the whole disk. This is, of course, enough of an advantage that a journaling filesystem is usually advantageous; but it doesn't make the filesystem any safer per se. (A journal can be detrimental on very small filesystems, though -- on them, the disk check time is short, and the size of the journal can become a problem. I wouldn't bother with a journal on anything smaller than several hundred megabytes.)

---

