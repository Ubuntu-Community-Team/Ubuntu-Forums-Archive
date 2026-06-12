---
title: "grub: incompatible license on Win7"
date: 2012-01-20
forum: General Help
---

### Post by cjosh on 2012-01-20
I have an Asus UL80vt with a multiboot.

I recently upgraded to Ubuntu 11.10 from 10.04 (I went through 10.10 and 11.04 as well), and I'm having an issue with the bootloader.

When I try to get back into Windows 7 I get a "grub: incompatible license grub rescue>" message and I'm not sure what to do, some help would be appreciated.

---

### Post by Mark Phelps on 2012-01-20
Don't know what that is specifically, but if you read through the Boot-Repair stuff, you may be able to use it to restore Win7 boot:

[http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair")

---

### Post by drs305 on 2012-01-20
Is this *after* selecting something from the Grub menu or at least before Windows boots?

If it's before, the incompatible license message often means that you are using mixed Grub versions. For instance, you may have (partially) installed Grub 1.99 on a previous Grub 1.98 version.

One way to correct this would be to purge Grub 2 completely and reinstall it. It is documented in the 'Chroot' link in my signature line if that is the way you want to go.

---

### Post by cjosh on 2012-01-20
Yeah I've tried Boot-repair but I still can't get into Windows.

For the record there's a partition set aside before the main Windows which is like a Windows recovery disk. I tried fixing the mbr but it keeps going to the recovery disk one instead.

But anyway, yes it's after I select Windows from Grub. I can boot into Ubuntu just fine. I'll try your link.

---

### Post by cjosh on 2012-01-20
Okay I followed those instructions from that link. I restarted my computer but now when I select windows it just loops back to the Grub screen.

---

### Post by drs305 on 2012-01-20
> **cjosh said:**
> Okay I followed those instructions from that link. I restarted my computer but now when I select windows it just loops back to the Grub screen.

It sounds like you have installed Grub on the Windows partition rather than in the MBR. Grub should be installed to the drive but not a specific partition, especially the Windows partition.

If Ubuntu isn't working:
If you can still boot Ubuntu, boot to the Desktop and run Boot Repair again. If you can't and have a bootable Boot Repair CD, it can probably restore things. If you were running Boot Repair from the Desktop, can't boot Ubuntu and don't have a Boot Repair CD, try booting the latest Ubuntu CD (that matches the Ubuntu you are trying to run), install Boot Repair and run it from there.

Again, make sure you install Grub to the booting drive (sda, sdb, etc) and not to a particular partition.

Here is another site that explains what your situation most probably is.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

**Links Added for Windows Repair:**
To repair your Windows partition boot files, you will probably have to run a Windows repair utility. 
[oldfred's Window Repair Links]("http://ubuntuforums.org/showpost.php?p=11031000&postcount=11")
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by cjosh on 2012-01-21
It turns out that Grub was on Windows too and Testdisk fixed everything. Thank you, much appreciated.

---

