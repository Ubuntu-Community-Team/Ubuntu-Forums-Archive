---
title: "How stable is the NTFS support?"
date: 2010-10-03
forum: General Help
---

### Post by eurostyle360 on 2010-10-03
I was just wondering how stable is the NTFS support in the most recent builds of ubuntu?  I'm coming back after a couple years and wanted to see how things have progressed.  Being a windows user I of course have a lot of ntfs partitions that need to be accessed regularly.  How safe is it reading and writing data all the time?

---

### Post by kahlil88 on 2010-10-03
NTFS support has been pretty good for the past few years. The only problem I've come across is not being able to access an NTFS volume which has a Windows system that wasn't shut down properly, which requires a CHKDSK to be flagged as good.

---

### Post by oregonbob on 2010-10-03
It is excellent. I routinely mount NTFS filesystems for just about everything.

---

### Post by eurostyle360 on 2010-10-03
Alright so I guess I should be good to go.  I just don't want to break any of my NTFS partitions as I do keep slightly less than a TB of data on them and I can't afford to create a reason for me to back them up.

---

### Post by WorMzy on 2010-10-03
I have a terabyte drive, formatted as NTFS, which I use as my main data storage. It gets mounted every boot time (regardless of whether Windows shut down properly) and gets written to very regularly as it contains my cross-platform Firefox profile, and my ~/Documents, ~/Downloads, etc are all bound to folders on the NTFS partition.

The only shortcoming is the lack of permissions support. NTFS partitions have to have the permissions set for everything on the partition at mount time. One set of permissions for everything.

---

### Post by oregonbob on 2010-10-03
> **eurostyle360 said:**
> Alright so I guess I should be good to go.  I just don't want to break any of my NTFS partitions as I do keep slightly less than a TB of data on them and I can't afford to create a reason for me to back them up.

If you are only accessing data on it I recommend you mount it read-only. If you mount it read-write, be sure it is properly unmounted when you shut the system down.

---

### Post by srs5694 on 2010-10-04
I recommend *not* accessing the Windows boot drive from Linux if you can avoid it. If you need to do so but don't need to write, mount it read-only, as oregonbob suggests. The reason is two-fold:


[list]
[*]Although the NTFS-3g drivers used by Ubuntu seem pretty reliable, they are a reverse-engineered NTFS implementation, created without any official documentation from Microsoft. Thus, they could easily overlook or misinterpret some subtle and seldom-used, but critical in rare conditions, data structure or other feature. If you run into such a bug, it'd be bye-bye data. Since Windows is very fussy about its boot disk, you should be particularly wary of doing anything that might cause Windows to sulk rather than boot. (In my experience, Windows is very good at sulking rather than booting!)
[*]Windows and Linux have very different filesystem security models, so Linux doesn't honor the security features that Windows uses on NTFS. Thus, if you mount your NTFS boot volume read/write and give yourself full read/write access to it in Linux, it's easy to accidentally delete or damage critical system files in ways that Windows would not permit if you'd been using Windows.
[/list]


The second of these issues is, IMHO, the more important one. That said, people do routinely access their Windows boot partitions read/write without problems. Doing so, however, is like driving without a seat belt -- you can get away with it for a long time, but you're taking an unnecessary risk. Given enough people who work like this, sooner or later some of them will get into trouble because of it.

These problems, and particularly the second one, are less important when using a non-boot data partition. If you need dual-OS access to music, videos, word processing files, or whatever, creating a separate NTFS data partition can be a good way to do it. Alternatively, there are Windows drivers for ext2 and ext3, so you could use one of them for shared data; but it sounds like you've already got lots of data in NTFS, so it's simpler to stick with it, at least for the moment.

Of course, filesystem access is imperfect, even when using OS-native tools (accessing NTFS from Windows or ext3fs from Linux, say). For this reason, backups are important. If you can't (or don't) back up your data, you're gambling.

---

### Post by Morbius1 on 2010-10-04
+1 What oregonbob and srs5694 said:
> Thus, they could easily overlook or misinterpret some subtle and  seldom-used, but critical in rare conditions, data structure or other  feature.If you'd like an example of that follow coffecat's discovery on timestamps:

[http://ubuntuforums.org/showthread.php?p=9917436#post9917436](http://ubuntuforums.org/showthread.php?p=9917436#post9917436)

At the moment it's not clear ( to me anyway ) if the bug is in ntfs-3g itself or in something else.

---

