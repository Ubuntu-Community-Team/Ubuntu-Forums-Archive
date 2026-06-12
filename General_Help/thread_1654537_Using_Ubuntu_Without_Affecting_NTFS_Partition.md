---
title: "Using Ubuntu Without Affecting NTFS Partition"
date: 2010-12-28
forum: General Help
---

### Post by kellyapproved on 2010-12-28
I have a new laptop that is running XP (soon to upgrade to Win7).  Since it is for business, I'd prefer not to make any changes to the hard drive such as dual boot setup.

What I was wondering was if I install Ubuntu on a USB stick and boot off of the stick, is there any way to prevent Ubuntu from seeing the Windows partition on the hard drive so that there is no risk of data transfer (eg virus) to that drive.

---

### Post by karthick87 on 2010-12-28
Just dont mount your NTFS drives.

---

### Post by theozzlives on 2010-12-28
You can't transfer a Windows virus to an Ubuntu system. Linux doesn't have any viruses to write home about so you're safe there as well.

---

### Post by kellyapproved on 2010-12-28
@karthick87 I'm still quite green with Ubuntu.  Since I don't know how to mount it, is it safe to assume that it doesn't mount on its own when I boot into Linux?

@theozzlives It's not so much worried about a virus moving from Windows to Linux, but rather the other way, Linux to Windows.  I wouldn't want to spread any malware, virus, or most importantly, spyware because the Windows partition is used for business.

---

### Post by iShurtugal on 2010-12-28
> **kellyapproved said:**
> @karthick87 I'm still quite green with Ubuntu.  Since I don't know how to mount it, is it safe to assume that it doesn't mount on its own when I boot into Linux?

@theozzlives It's not so much worried about a virus moving from Windows to Linux, but rather the other way, Linux to Windows.  I wouldn't want to spread any malware, virus, or most importantly, spyware because the Windows partition is used for business.

Ubuntu will only automount the / partition (and /home partition if you made it) automatically, so your windows partition is safe.  also, viruses can't go from ubuntu to windows, because ubuntu doesn't have viruses, malware, or spyware.  Plus, windows can't read the linux filesystem (ext4) without special programs.

---

### Post by Mark Phelps on 2010-12-29
> **kellyapproved said:**
> I have a new laptop that is running XP (soon to upgrade to Win7).  Since it is for business, I'd prefer not to make any changes to the hard drive such as dual boot setup.
OK, so when you install Ubuntu, make sure you do NOT write GRUB to the MBR of the internal drive.  I believe that the default is to write GRUB to the MBR of the "first" hard drive -- which is likely to be the internal drive.

> What I was wondering was if I install Ubuntu on a USB stick and boot off of the stick, is there any way to prevent Ubuntu from seeing the Windows partition on the hard drive so that there is no risk of data transfer (eg virus) to that drive.
When you install Ubuntu, it generally has the ability to "see" all the hard drives and partitions in the PC -- even if they are NOT mounted.  If you then go into Places and click on the icon for your Windows partition, Ubuntu will automount it.  So, as long as you do NOT do that, and do not mount it any other way (e.g., using fstab), nothing will be done to your MS Windows partition.

As to transferring Viruses, if you accidentally download some malware while in Ubuntu, and you save that to your Ubuntu partition, MS Windows (without the installation of special drivers) can not "see" that partition, so there's no way that malware could then be transferred.

But, if you have a shared data partition, and the malware gets downloaded to there, if you access that partition while in MS Windows, you run the risk of infecting your MS Windows OS.

---

