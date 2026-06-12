---
title: "Re-do dual boot"
date: 2010-05-30
forum: General Help
---

### Post by TXbirder on 2010-05-30
I have two hard drives with Win7 on one and, until today, Ubuntu on the other.  While doing a Win7 back up to an external hard I also copied the back up to the Ubuntu drive.  I don't want any trace of Win7 on the #2 drive.  So I think I need to uninstall Ubuntu and reinstall, letting the reformatting wipe out the Win7 data.   How do I uninstall Ubuntu? Is there an uninstaller I can download?  Will this do what I hope it will do?   John

---

### Post by bttf on 2010-05-30
If you just reinstall Ubuntu on the 2nd drive, you will have the option to completely reformat the drive. That will erase everything on it, and give you a fresh Ubuntu install

---

### Post by wilee-nilee on 2010-05-30
> **TXbirder said:**
> I have two hard drives with Win7 on one and, until today, Ubuntu on the other.  While doing a Win7 back up to an external hard I also copied the back up to the Ubuntu drive.  I don't want any trace of Win7 on the #2 drive.  So I think I need to uninstall Ubuntu and reinstall, letting the reformatting wipe out the Win7 data.   How do I uninstall Ubuntu? Is there an uninstaller I can download?  Will this do what I hope it will do?   John

I would say that it is probably pretty easy to find the MS backup, and just delete it. A better description might be helpful if you want to just fix the Ubuntu OS. A reinstall though as suggested will wipe everything, and reload the MBR. I assume you are aware of how to install grub to the appropriate MBR only.

---

### Post by TXbirder on 2010-05-31
I seem to have shot myself in the foot.  I deleted (I thought) the Win7 backup.  It was easily located because there was a new icon on my screen that wasn't there before.  I sent it to Trash and restarted the computer.    
But I can't restart the computer.  Restart begins and then I get "BOOTMGR is missing. Press Ctrl+Alt+Del to restart.
I do that and come right back to BOOTMG is missing.

John

---

### Post by oldfred on 2010-05-31
Now if you cannot boot run this to see what is still there.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by TXbirder on 2010-05-31
I can't get past **BOOTMGR missing** so I can't run anything.

John

---

### Post by lisati on 2010-05-31
If booting from your hard disk(s) is problmeatical, sometimes booting from a Live CD can be of help getting the repairs underway.

---

### Post by wilee-nilee on 2010-05-31
> **TXbirder said:**
> I can't get past **BOOTMGR missing** so I can't run anything.

John

@lisati nice spelling of problematical, are you still using pho-net-iks. ;)

Thread starter the script is run from a live cd. Post it in code tags; there are two ways to do this you can paste the results into a reply highlight the text and hit the # in the reply panel or,[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by TXbirder on 2010-06-01
I'll try the bootinfoscrript but first I'll have to install Ubuntu in to this laptop so I can download the script.
More later.
John

---

### Post by TXbirder on 2010-06-01
Wait a minute!  I can't download this into my inop desktop.  I can download it into my laptop.  Can I then make a CD or thumbdrive copy and run it on the desktop?
John

---

### Post by TXbirder on 2010-06-01
2nd wait minute!  Is BOOTMGR part of BIOS?  I have the Gigabyte BIOS installation CD. 
If BOOTMGR is part of BIOS can I reinstall BIOS without wiping out everything on the computer?

I'm going to ask Gigabyte, but last time I sent them a question it took a couple of weeks for an answer.

John

---

### Post by TXbirder on 2010-06-01
Correction-  NOT a BIOS CD- just a utility disc.
John

---

### Post by oldfred on 2010-06-01
Use a liveCD on the system you have having touble with and run the boot info script from that computer. I doubt that the motherboard mfg will have any direct help. Bootmanager is part of windows but we cannot help without knowledge of your system.

---

### Post by TXbirder on 2010-06-02
The bad computer does not see the CDs.  Nothing has changed.

---

### Post by yetiman64 on 2010-06-02
> **TXbirder said:**
> The bad computer does not see the CDs.  Nothing has changed.

Have you set the boot order in BIOS to look to boot the cd drive first and not the non working HDD.

---

### Post by TXbirder on 2010-06-03
Sorry for the delayed response. I tried to reset BIOS to boot from the disc but the normal F keys to get into the Gigabyte BIOS weren't all working. With trial and error I found a backdoor into the boot settings and got the problem fixed with my Win7 CD.
The Repair function on the Win7 CD is nice.
 
But now, when I start up, I get no screen that asks me whether I want Ubuntu or Win7 so I'll probably have to reinstall Ubuntu.
 
Thanks for all your help.
 
John

---

### Post by oldfred on 2010-06-03
If grub2 did not initially find windows and just has Ubuntu it does not show the menu.

If it is grub2 you have to hold the shift key from the end of BIOS boot until it comes up. If grub legacy it is the escape key.

---

