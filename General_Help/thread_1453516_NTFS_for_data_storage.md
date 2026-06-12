---
title: "NTFS for data storage"
date: 2010-04-13
forum: General Help
---

### Post by adam.ec on 2010-04-13
Hi guys,

I'm now having to access a lot of data on a portable hard drive on a regular basis. The drive needs to be used with three different Windows systems, three Ubuntu machines and two slackware units.  The data is backed up once per week.

I have been using Ext2IFS to access the data (stored on Ext3) from Windows but keep having problems. Obviously Ubuntu and Slack have no trouble reading or writing to the drive. Additionally, some sensitive data will be put onto the drive shortly and I would like to encrypt it.

What is the best solution here? Is NTFS reliable enough and is data access and writing reliable enough from Linux? Can I encrypt NTFS and still leave it accessible by Linux? What is the best software to encrypt the drive with (if I can) that is accessible by both Windows and Linux?

Any help much appreciated.

---

### Post by bumanie on 2010-04-13
Read/write to ntfs from linux is very stable - can't answer the question about encryption. But look at [truecrypt]("http://www.truecrypt.org/") - it may do what you wish - read the documentation.

---

### Post by adam.ec on 2010-04-13
Thank you, re-inspired my confidence in the read/write systems. When I started with Ubuntu NTFS support was shakey to say the least so glad that it has improved. I'll give truecrypt a go as it seems to work on Windows too.

Is NTFS actually a reliable filing system? I mean is it comparable with Ext3 these days or does it still suffer corruption issues?

---

### Post by prodigy_ on 2010-04-13
These issues have nothing to do with NTFS itself. It's just prior to Vista non-server version of Windows didn't have journaling enabled by default. Read, for example, [this](http://zachsaw.blogspot.com/2009/06/ntfs-journaling-file-system.html).

NTFS with journaling enabled is no worse than any other modern filesystem.

---

### Post by dannyboy79 on 2010-04-13
> **adam.ec said:**
> Hi guys,

I'm now having to access a lot of data on a portable hard drive on a regular basis. The drive needs to be used with three different Windows systems, three Ubuntu machines and two slackware units.  The data is backed up once per week.

I have been using Ext2IFS to access the data (stored on Ext3) from Windows but keep having problems. Obviously Ubuntu and Slack have no trouble reading or writing to the drive. Additionally, some sensitive data will be put onto the drive shortly and I would like to encrypt it.

What is the best solution here? Is NTFS reliable enough and is data access and writing reliable enough from Linux? Can I encrypt NTFS and still leave it accessible by Linux? What is the best software to encrypt the drive with (if I can) that is accessible by both Windows and Linux?

Any help much appreciated.
how much data are we talking about? if it's under 2GB, put it in the CLOUD. ubuntu one or dropbox. it's free and accessible from anywhere you have a internet connection. otherwise got with fat32, limitiations on file size (no larger than 4gb) however. good luck

---

### Post by sebastianabate on 2010-04-13
NTFS-3G do not support encrypted NTFS partitions, but partially support compressed NTFS partitions (you can read and write compressed files, but you can't overwrite them).

---

