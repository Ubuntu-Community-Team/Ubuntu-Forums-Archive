---
title: "formatted Ubuntu + destroyed GRUB"
date: 2010-06-14
forum: General Help
---

### Post by mkham on 2010-06-14
I could never log in to my Ubuntu 4-2008 partition after it broke somehow (with an update?), even though I tried every trick.  So I finally just formated it as NTFS to get more space for the Windows XP on my too full dual boot drive. Duh, you see what's wrong with this story? I deleted the GRUB and now just get "finding stage 1.5, error 17" when I turn it on. It was AMD 64 bit 4-2008 version.

I was trying to clean it up, clear out space, defrag, before copying laptop 80gig drive to bigger 160gig one on USB.

WHAT DO I DO????  Tell me something you KNOW works- maybe with reinstalling 4/2008 Live Ubuntu, though I hate installing an old version. Will it read the remnants of the old Grub, and push the new one farther (and so FU the XP MBR), or just overwrite the old one?  I downloaded 4/2010 Ubuntu- is it safe to install this on the former Ubuntu partition- how will it's GRUB 2 deal with remnants of the old one, will it just overwrite the pointer. That's what i want to do. Should I reformat that old Ununtu partition as EXT3 (which was at the very end of the HD)?

I used SUPERGRUB CD before in saving an unbootable Windows on a bigger new HD but found it very unstable on my system- lappy ACER 5003 80gig HD, Turion 64-ML32 1.8Ghz, 1gig RAM
   ---------------------------------------------------------

June 22:  ANYONE ELSE AGREE THAT installing new Ubuntu overwrites the GRUB legacy on MBR? Can there be any trouble with EXT3 vs bew EXT4?  Got Windows working with SUPERGRUB disk (it insanely uses right arrow as enter, which is why I completely destroyed a Windows installation), but am about to try same thing with replacement bigger HD, using installation of new Ubuntu to find Windows and install proper boot-loader

---

### Post by zvacet on 2010-06-15
Read [this.]("https://help.ubuntu.com/community/DualBoot/Mbr")

---

### Post by elliotn on 2010-06-15
Installing the new ubuntu will install the new grub2 and will overwrite grub legacy

---

### Post by wilee-nilee on 2010-06-15
Post the script in my sig with the code tags.

---

