---
title: "Boot error after deleting Ubuntu"
date: 2011-05-10
forum: General Help
---

### Post by owenstyles on 2011-05-10
Hello everyone,
 
I recently removed the Ubuntu partition in Windows 7.
 
When I try to reboot I am faced with the the grub rescue error where it says no such partition..
 
I have tried booting Windows 7 from disc and I have even went into my BIOS and it says CD-ROM boot priority.. boot ready then says the grub rescue error again, stating that there is no such partition.
 
This is really annoying as all the tutorials on the internet say insert Windows 7 then use the recovery tools but I can't even boot any operating system. I have set the BIOS to boot from my CD drive.. tried everything.
 
Any help would be great!
 
Thanks in advanced

---

### Post by Buntumatic on 2011-05-10
I fail to see what this has to do with Linux.

Windows users using custom bootloaders should restore Windows MBR from within Windows before removing the bootloader. GRUB has nothing to do with Linux, either.

---

### Post by wilee-nilee on 2011-05-10
> **Buntumatic said:**
> I fail to see what this has to do with Linux.

Windows users using custom bootloaders should restore Windows MBR from within Windows before removing the bootloader. GRUB has nothing to do with Linux, either.

Thanks for being so helpful.;)

Thread starter follow these instructions, notice the W7 forum link for a visual look. **Find the per-session boot key to boot the W7 disc mine f12.**

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If there ant any problems after this; from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by The Cog on 2011-05-10
That was a singularly unhelpful answer. I wonder what the point of posting it was.

You will definitely need to boot from a CD, because your hard disk is currently unbootable. I'm no windows expert, but Googling for "restore windows bootloader" turned up this useful looking page: [http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)

---

### Post by Buntumatic on 2011-05-10
> **The Cog said:**
> That was a singularly unhelpful answer. I wonder what the point of posting it was.
The point of my posting was asking help for another OS is off-topic here. I'm sure microsoft.com can help out here. Like this one [http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)
I still fail to see what this has to do with Linux.

---

### Post by owenstyles on 2011-05-10
Thanks The Cog and wilee-nilee for the help, got it working :D!

---

### Post by wilee-nilee on 2011-05-10
> **owenstyles said:**
> Thanks The Cog and wilee-nilee for the help, got it working :D!

Yay is what I say.;)

---

