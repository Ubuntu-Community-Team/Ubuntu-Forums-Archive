---
title: "File undelete (recovery) program"
date: 2009-11-23
forum: General Help
---

### Post by Crumbles on 2009-11-23
What do you guys think is the best file undelete program fir ubuntu out there? I want to be able to plug in external hard drives and scan them for recoverable files. Suggestions? Any of them have a GUI?

---

### Post by Crumbles on 2009-11-23
There has to be something! :)

---

### Post by Zorael on 2009-11-23
There's a bunch listed over at the [DataRecovery wiki page](https://help.ubuntu.com/community/DataRecovery), but I don't think any of them have a GUI. [Other](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html) [sites](http://www.brighthub.com/computing/linux/articles/34156.aspx) seem to promote Foremost (and Scalpel) in particular. There's also [Testdisk](http://www.cgsecurity.org/wiki/TestDisk) in the repositories.

And no need to bump it after only two hours. If it's very urgent, try the irc channels. (#ubuntu, irc.freenode.net)

---

### Post by Crumbles on 2009-11-24
> **Zorael said:**
> There's a bunch listed over at the [DataRecovery wiki page]("https://help.ubuntu.com/community/DataRecovery"), but I don't think any of them have a GUI. [Other]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html") [sites]("http://www.brighthub.com/computing/linux/articles/34156.aspx") seem to promote Foremost (and Scalpel) in particular. There's also [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") in the repositories.Thanks for your replies, I'll check it out.

[quote=Zorael]And no need to bump it after only two hours. If it's very urgent, try the irc channels. (#ubuntu, irc.freenode.net)[/quote]Actually there is a need to bump it.  No one ever helps you unless you do.

See point 1 [http://ubuntuforums.org/showthread.php?t=1316879](http://ubuntuforums.org/showthread.php?t=1316879)
See point 2 [http://ubuntuforums.org/showthread.php?t=1301887](http://ubuntuforums.org/showthread.php?t=1301887)
See point 3 [http://ubuntuforums.org/showthread.php?t=1286772](http://ubuntuforums.org/showthread.php?t=1286772)

---

### Post by kircher on 2009-11-24
Testdisk is good for most file systems other than ext3. For ext3, there is ext3grep, which is in the repositories. It doesn't always work the way you want it to though. Make sure that if you plan to use it, mount the partition that has the deleted data as read only, and make sure the partition that you're writing the deleted data to is big enough to take it all. With ext4, I think you're on your own. I haven't come across any information for undeleting data on ext4 partitions. Tips when using ext3grep: Make sure you specify a time in unix time. Example if you deleted something accidentally on the 5th November 2009 at 10 am, you would convert that into unix time using one of the online calculators (you have to first convert it to Greenwich Mean Time), and then get ext3grep to recover all files deleted after 9am. The important thing is to read as much information about it as possible. Make sure you unmount the file system that you deleted the data on as soon as possible after you made the mistake so you don't over-write the newly acquired free space.

---

### Post by Zorael on 2009-11-24
> **Crumbles said:**
> Actually there is a need to bump it.  No one ever helps you unless you do.

See point 1 [http://ubuntuforums.org/showthread.php?t=1316879](http://ubuntuforums.org/showthread.php?t=1316879)
See point 2 [http://ubuntuforums.org/showthread.php?t=1301887](http://ubuntuforums.org/showthread.php?t=1301887)
See point 3 [http://ubuntuforums.org/showthread.php?t=1286772](http://ubuntuforums.org/showthread.php?t=1286772)
I'm not saying "don't bump ever", just saying that two hours isn't long enough for the thread to drop very far back. :3

---

### Post by Crumbles on 2009-11-24
> **kircher said:**
> Make sure that if you plan to use it, mount the partition that has the deleted data as read onlyShockingly I had never even thought of that to mount it as read only!  Thanks for the tip.

I got pretty much everything I wanted done today. My goal was to have a way to plug in hard drives to my laptop via USB and do work on them.

I ended up going with photrec/testdisk since I was used to that from Windows anyway. So, I can use that to perform recovery on them. I only really care about FAT32 and NTFS since 99% of the hard drives that people will bring to me are going to be Windows stuff anyway.

I also got ntfsclone to backup hard drives to images. I also use dd to backup the MBR of the hard drive and have a few tricks to use dd as a total cloner if I want to.

I got avast installed to scan the hard drive for Windows viruses. I started with AVG but DAMN does AVG suck in ubuntu! WTF is with the -l (clean) option being disabled!!!

I also installed ddrescue (not dd_rescue) and plan on playing around with that tomorrow on a hard drive a friend has that's all messed up.

All in all everything seems to be going well. I'm really enjoying ubuntu. I'm a hardcore Windows user and just started messing with ubuntu a few months ago. I forced myself to make it my main machine so I can learn it. Been having a lot of fun.

---

### Post by Crumbles on 2009-11-24
> **zorael said:**
> i'm not saying "don't bump ever", just saying that two hours isn't long enough for the thread to drop very far back. :3ok. :d

---

