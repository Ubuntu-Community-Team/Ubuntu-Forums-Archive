---
title: "Installing Linux Causes XP to BSOD on boot"
date: 2010-06-06
forum: General Help
---

### Post by fiddler616 on 2010-06-06
Hello,

I recently put Crunchbang Linux  onto my sister's netbook. Everything went absolutely fine (except for the display driver, but that's neither here nor there), and everyone was happy. Then she decided to boot into Windows. The XP option appeared in Grub, she selected it, it showed the splash screen...and then flashed (so fast I can't even read a word) the BSOD before rebooting. Trying again brings up Windows' recovery screen, and the Safe Mode, Last Known Good, and Normal XP options all result in the same error. What's happening, and how should I fix it?

Thanks in advance.

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
When you partitioned off a chunk for linux did you defrag before shrinking the windows partition?

---

### Post by fiddler616 on 2010-06-06
> **Sin@Sin-Sacrifice said:**
> When you partitioned off a chunk for linux did you defrag before shrinking the windows partition?

...No, but the only thing that had been added to Windows was Skype and Chrome (it's a new computer), and out of the 250GB HD, I gave 10 to Linux.

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
I would try to run chkdsk regardless...

---

### Post by fiddler616 on 2010-06-06
> **Sin@Sin-Sacrifice said:**
> I would try to run chkdsk regardless...

Don't I need windows to run that?

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
Recovery prompt... google...

---

### Post by fiddler616 on 2010-06-06
> **Sin@Sin-Sacrifice said:**
> Recovery prompt... google...

It's a netbook, so there's no CD-ROM, and the recovery partition throws strange errors.

I'll see if I can dig up a USB CD-ROM though.

And actually just now it's running memtest to make sure that's OK.

---

### Post by bildr on 2010-06-06
you can put the recovery CD on a thumbdrive and boot from that, but I don't use windows recovery.  Acronis and Paragon fix more problems automagically.

i don't think it is needing chkdsk, but better safe then sorry.

make sure your boot.ini file is right, did you put the linux partition at the beginning or end of the disk?

I have an acer aspire working properly on dual-boot so it is possible.

---

### Post by fiddler616 on 2010-06-06
> **bildr said:**
> you can put the recovery CD on a thumbdrive and boot from that.

I have the .iso of XP Pro, and the netbook runs XP Home, but that doesn't matter, right? A recovery console is a recovery console, no?

> 
i don't think it is needing chkdsk, but better safe then sorry.

Yeah...
> 
make sure your boot.ini file is right, did you put the linux partition at the beginning or end of the disk?

I'll check that once memtest finishes. And Linux is at the end of the partition.

---

### Post by fiddler616 on 2010-06-06
```
C:\>chkdsk

The volume appears to contain one or more unrecoverable problems.

C:\>
```

---

### Post by oldfred on 2010-06-06
Sometimes this works:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

