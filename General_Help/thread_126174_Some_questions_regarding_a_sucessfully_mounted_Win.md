---
title: "Some questions regarding a sucessfully mounted Windows NTFS partition."
date: 2006-02-05
forum: General Help
---

### Post by Levdir on 2006-02-05
Alright, I hunted about in the forum archives until I found something that pointed me towards what I needed to configure my 56k modem; along the way, I learned how to mount my Windows partition. However, this partition is NTFS and therefore read-only. I seem to be able to copy things off the Windows partition and into the Ubuntu partition, but they remain read-only. Is there a workaround for this?

Also, a weird glitch: my keyboard is a Microsoft wireless unit, and it doesn't work in GRUB. That's fine if I'm booting Ubuntu, but if I want to boot Windows (the fourth item on GRUB's list), I have to go get the wired keyboard off the other computer, and that's an unneccessary hassle. Anyone else had this problem?

---

### Post by o_fortuna on 2006-02-05
[QUOTE=Levdir]Alright, I hunted about in the forum archives until I found something that pointed me towards what I needed to configure my 56k modem; along the way, I learned how to mount my Windows partition. However, this partition is NTFS and therefore read-only. I seem to be able to copy things off the Windows partition and into the Ubuntu partition, but they remain read-only. Is there a workaround for this?

Also, a weird glitch: my keyboard is a Microsoft wireless unit, and it doesn't work in GRUB. That's fine if I'm booting Ubuntu, but if I want to boot Windows (the fourth item on GRUB's list), I have to go get the wired keyboard off the other computer, and that's an unneccessary hassle. Anyone else had this problem?[/QUOTE]
If you want read-write support, try [captive.]("http://www.jankratochvil.net/project/captive/") It's slow, but it's the only way to safely read and write from Ubuntu.

EDIT: Oh, I misread. Listen to RAOF, for he is wise. ;)

---

### Post by RAOF on 2006-02-05
[QUOTE=Levdir]Alright, I hunted about in the forum archives until I found something that pointed me towards what I needed to configure my 56k modem; along the way, I learned how to mount my Windows partition. However, this partition is NTFS and therefore read-only. I seem to be able to copy things off the Windows partition and into the Ubuntu partition, but they remain read-only. Is there a workaround for this?

Also, a weird glitch: my keyboard is a Microsoft wireless unit, and it doesn't work in GRUB. That's fine if I'm booting Ubuntu, but if I want to boot Windows (the fourth item on GRUB's list), I have to go get the wired keyboard off the other computer, and that's an unneccessary hassle. Anyone else had this problem?[/QUOTE]
Copying will, by default, preserve the owner/permissions of a file.  So, since all the files on the NTFS drive don't have write permissions, the copies don't have write permissions.

From the console you can copy without preserving permissions:
```
cp --no-preserve=owner,mode <from> <to>
```will copy <from> to <to>, changing the owner to you, and giving it the default mode (read & write privs).

As for the wireless keyboard - It's probably USB, yes?  Does your bios have an option "enable support for USB keyboards" or "USB keyboard emulation" or some such?  Try turning that on - grub doesn't (and can't) load the requried USB drivers to get a non-emulated keyboard to work.

---

### Post by aysiu on 2006-02-05
NTFS is read-only.
That's how it's supposed to be.
Projects like CaptiveNTFS are experimental right now.
If you want read/write, make a FAT32 partition.

---

### Post by Levdir on 2006-02-05
Excellent, I'll play around with that. Thanks again, these forums are rather awesome for support.

---

