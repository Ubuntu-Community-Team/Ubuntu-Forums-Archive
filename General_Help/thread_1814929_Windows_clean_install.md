---
title: "Windows clean install"
date: 2011-07-30
forum: General Help
---

### Post by DigitalAlcatraz on 2011-07-30
I want to Re install windows 7, but when i do so it removes GRUB making me unable to boot into Ubuntu. Is there any way in which i can install Windows without removing GRUB?:confused::confused::confused:

---

### Post by TeoBigusGeekus on 2011-07-30
> **DigitalAlcatraz said:**
> I want to Re install windows 7, but when i do so it removes GRUB making me unable to boot into Ubuntu. Is there any way in which i can install Windows without removing GRUB?:confused::confused::confused:

No, but you can reinstall grub2 with [this]("https://help.ubuntu.com/community/Grub2#ChRoot") method.

---

### Post by DigitalAlcatraz on 2011-07-30
Could a moderator move this thread to the appropriate category?

---

### Post by DigitalAlcatraz on 2011-07-30
Grub is unable to boot into windows now. It is saying something about no such volume existing in the specified drive/

---

### Post by Mark Phelps on 2011-07-30
You're not telling us much useful ...

So, did you reinstall Win7, and is it booting OK now? Need to know this before we launch into fixing GRUB.

Did you then reinstall GRUB after reinstalling Win7? And, can you now boot into Ubuntu without problems?

IF so, then did you open a terminal and enter "sudo update-grub"?  

If you did, did you see an entry like "Windows 7 (Loader) on ..." during the GRUB menu rebuilding enumeration?

Have you looked at your /boot/grub/grub.cfg file and confirmed that the Windows 7 stanza is there and properly configured?

---

### Post by DigitalAlcatraz on 2011-07-31
> **Mark Phelps said:**
> You're not telling us much useful ...

So, did you reinstall Win7, and is it booting OK now? Need to know this before we launch into fixing GRUB.

Did you then reinstall GRUB after reinstalling Win7? And, can you now boot into Ubuntu without problems?

IF so, then did you open a terminal and enter "sudo update-grub"?  

If you did, did you see an entry like "Windows 7 (Loader) on ..." during the GRUB menu rebuilding enumeration?

Have you looked at your /boot/grub/grub.cfg file and confirmed that the Windows 7 stanza is there and properly configured?

I did reinstall Win7 and it is booting normally if my ST32000542AS(which contains GRUB and Ubuntu) is not set as the boot drive.After reinstalling GRUB Ubuntu is booting normally with the ST32000542AS set as the boot drive.I used the CH root method as recommended by TeoBigusGeekus after which this as happening. Windows can still boot when my WDC5000AADS-00S9B0(containing the Windows BootLoader) is set as my primary boot drive. 

The windows 7 Stanza:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root E4CC629ACC626730
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```
To me it looks like it is configured properly, but i'm not sure if it is.

---

### Post by Mark Phelps on 2011-08-01
That stanza does look correct.  Sorry, don't know what to tell you at this point -- since both Ubuntu and Windows will boot from their respective drives.

---

