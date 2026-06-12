---
title: "Filesystem for access by both Ubuntu 9.10 and Windows 7"
date: 2009-12-13
forum: General Help
---

### Post by Jaded Misanthrope on 2009-12-13
I'm soon to install Ubuntu 9.10 on my desktop alongside a pre-existing installation of Windows 7, and while I'm confident with actually installing the OS in a dual-boot and so on, I need a partition that can be reliably accessed by both Windows 7 and Ubuntu.

I'm probably going to make this partition the /home mountpoint, if only because I don't see the point in scattering my files across various partitions unless I really have to (e.g. in my experience games, which are the main reason I have both this desktop and Windows 7 only work well if they're on the same partition as the OS trying to run them). Nothing much will go on here -- music, videos, work files; just the kind of things that I'll access while using both Ubuntu and Windows -- but what filesystem works best for access by both OSes? 

A year or two ago, on my laptop, I had a similar setup with Ubuntu 8.04 and Windows Vista and the shared partition worked fine as ext3 (though I can't remember what program I installed on the Windows Vista partition for it to recognise it), but does this still apply to Windows 7 and Ubuntu 9.10 or do I have to use a different filesystem for reliable and quick access to the partition from both OSes?

---

### Post by 0cton on 2009-12-13
there is an ext3 driver for windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ram2500 on 2009-12-13
Right click on Computer, select Manage...(all from the Start menu), and then go to the Disk Management snap-in within the Microsoft Management Console. You can create a partition to store all your files to use between Windows and Ubuntu. The advantage of having a separate partition for your files are that your files are independent of the OS and if either fails, you could just take out the drive and copy your files to another drive, provided the drive didn't fail. 

The ext3 driver (in my experience) wasn't very good as I couldn't get it to access (and read) the ext3 partition, and have heard of some reliability problems from other users. I'd say partitioning is the easiest thus far, and it's completely safe as it is done within Windows. If you don't want to go that route, just create a folder somewhere on the Windows partition, perhaps in the root of the C: drive (right along with \Windows, \System and others) and create shortcuts on both Windows and Ubuntu desktops.

---

### Post by Jaded Misanthrope on 2009-12-13
Thanks, ram, but I think you misread my question; all I need to know is a filesystem (e.g. ext3, ext4, NTFS) that can be accessed by both Ubuntu 9.10 and Windows 7 reliably (possibly with additional software).

---

### Post by Jerry N on 2009-12-13
Ubuntu reads and writes NTFS just fine.

Jerry

---

### Post by QIII on 2009-12-13
Since have to do work to get Windows to recognize ext3 (and it will run away screaming at ext4 right now), just use an NTFS partition.  No fuss.  No muss.

---

### Post by Primefalcon on 2009-12-13
> **Jerry N said:**
> Ubuntu reads and writes NTFS just fine.

Jerry
Ubuntu reads and writes to both fat and NTFS just fine,the drivers are actually in the kernel which means any modern Linux system wont have a problem.

Myself I haven't had much luck with reading ext3/4 from Windows, not that I'd really want it to anyhow, I don't trust windows with viruses and and whatnot having access......

What I do is I create a separate NTFS partition and use that as a large data dam for both if you will.

---

### Post by Jaded Misanthrope on 2009-12-13
Thanks; I wasn't too sure on how Linux handled NTFS but I think I'll just make the /home partition NTFS now I know.

---

### Post by john newbuntu on 2009-12-14
I am not sure on making /home an ntfs partition.  I wonder if it will play well with permissions from the linux end.  Perhaps this is something that can be tweaked later I guess.
I'd probably still have /home as an ext4 partition and have a separate mount point to the ntfs partion that would be automounted on startup.

---

