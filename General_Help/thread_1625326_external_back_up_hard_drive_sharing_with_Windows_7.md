---
title: "external back up hard drive sharing with Windows 7 and Linux files."
date: 2010-11-18
forum: General Help
---

### Post by hpng on 2010-11-18
Hello:

I am a beginner to Ubuntu / linux.
I plan to partition my laptop (HP pavilion ) for Windows 7 and Linux ( ubuntu).

Can I backup both Linux and Windows 7 files to a single external USB hard drive?  ( Obviously, they will be in seperate directories. )

If yes, how do I do that?

If not, what are my alternatives?

I assume Ubuntu will recognize a USB hard drive as an external flash drive, right?

I also notice external SATA hard drive docking stations with USB interface are available, and I have not use them before.  The devices takes  internal SATA hard drive.

If you have use them before, let me know how did you format it using UBUNTU or Windows7 while the drive is attached to the station.

Thanks.

---

### Post by hpng on 2010-11-18
I was able to find some answers online on formatting an external hard drive using Win 7.  But I still do not know how to share one back up hard drive with Win 7 and Linux OS files.    See my other questions posted earlier.

---

### Post by PhilGil on 2010-11-18
> **hpng said:**
> Can I backup both Linux and Windows 7 files to a single external USB hard drive?  ( Obviously, they will be in seperate directories. )

Yes. Format the external drive as NTFS. Ubuntu can read and write to Windows-formatted drives out of the box.

> **hpng said:**
> If yes, how do I do that?

In Ubuntu, you can back up both Windows and Ubuntu using one of the Linux backup solutions. There's many posts here on the forum describing and comparing backup options. I use Back in Time for daily automated backups and rsync/grsync for manual backups. Be aware that the Linux file system is different than the Windows file system. I think it's more intuitive and logical but it can be confusing to someone who's new to Linux.

> **hpng said:**
> I assume Ubuntu will recognize a USB hard drive as an external flash drive, right?
In Ubuntu, USB drives mount automatically when you plug them in.


> **hpng said:**
> I also notice external SATA hard drive docking stations with USB interface are available, and I have not use them before.  The devices takes  internal SATA hard drive.

If you have use them before, let me know how did you format it using UBUNTU or Windows7 while the drive is attached to the station.

I usually format using gparted in Ubutu.

---

### Post by Quackers on 2010-11-19
Clonezilla may be another option.

---

