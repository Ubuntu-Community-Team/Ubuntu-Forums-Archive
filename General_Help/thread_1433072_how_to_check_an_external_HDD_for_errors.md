---
title: "how to check an external HDD for errors?"
date: 2010-03-18
forum: General Help
---

### Post by X1R1 on 2010-03-18
Here is the deal, I have en external HDD that Im sure has some bad sectors and I want to recover all the info in it. But whe I boot Windows (Drive has NTFS filesystem) and run chkdsk it just hangs.

Is there a way to check and fix errors in ubuntu?

If that doesnt work, Can I clone this drive with clonezilla without problems (no damaged files)?

Disk get recognized by fdisk in /dev/sdc, but when I try to check it with fdisk I get an error, maybe cause filesystem is NTFS.

any help?

regards

---

### Post by ram2500 on 2010-03-18
I would format it after copying the files over. A complete formatting will mark the bad sectors while doing the format. Copy the files, make the format, and from then on,* never* rely on your external drive as your only backup. I am being scientific, but anything mechanical is going to fail at some point (friction, heat and wear!) A hard drive is going to fail sooner or later, and bad sectors are a giveaway of the fact. Back up the drive to an optical medium CD/DVD.

---

### Post by X1R1 on 2010-03-18
Its not an external hard drive per se, let me explain a little. Im a computer technitian and one client came on to me with a laptop hard drive saying it was faulty and that he wanted to save the info in it. So I put the laptop hard drive in an [enclosure]("http://en.wikipedia.org/wiki/Disk_enclosure") so it will read as an external HDD, but the drive sounded pretty weird (many clicks), and copying sometimes doesn't work or ends with error, but weird enough, after I posted this i was able to copy the required files to my ubuntu partition, So I will format the drive now :D

Thanks for your help!

---

### Post by ram2500 on 2010-03-18
There's not much you can do if the data fails to copy and the drive is making strange sounds (the drive is dying or is dead). You are going to have to invest a somewhat large sum of money, perhaps around $500-900, for data recovery services.

---

