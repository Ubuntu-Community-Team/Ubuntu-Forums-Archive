---
title: "Where to install GRUB?"
date: 2011-04-28
forum: General Help
---

### Post by CLVPX on 2011-04-28
Having not used ubuntu for over a year, and having never used GRUB 2, I attempted an install of 10.10 early this year, in a dual boot with W7, and as expected GRUB took priority. Currently downloading 11.04 to try it out, but I can recall when I used to use 9.10 that if you installed GRUB to a specific partition as opposed to the disk, booting would take you straight to W7. This would be my preferred method, and I would edit the BCD to point to GRUB. Question is where exactly should I install GRUB to effectively make it useless unless its pointed at directly?

EDIT: forgot to mention its an install to a seperate HDD

---

### Post by tredegar on 2011-04-28
I just put grub2 on the MBR of my first HDD.

It is easy to configure grub2's "default OS to boot" to be windows (or anything else), if that's what you'd like.

If you want to use window's boot to load linux then** [this link ]("http://blogs.technet.com/b/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx")** might help you.

---

### Post by grahammechanical on 2011-04-28
If you installed Grub to the MBR of the first hard disc, the one with Windows on it, then Grub would load every time. But if you installed Grub to the MBR of the second hard disc, the one with Ubuntu on it, then Grub will not load unless you have some way of telling the boot process to look in the MBR of the second disc. Is this the idea? Could you do that?

I have read on these forums that some are able to activate a BIOS menu to select the hard disc to boot from. Can you do this? Does Windows 7 use some kind of boot menu that will let you select another hard disc?

Regards.

---

### Post by CLVPX on 2011-04-28
I will try installing to the MBR of the second disc, and setting the bios to look to the first hard drive first. As I remember easyBCD will allow you to select another hard disc to add to the boot menu. Wish me luck.

---

### Post by tredegar on 2011-04-28
Did you read the link I gave you at post #2? These forums do not seem to highlight links very obviously. I will edit that post to make it a little more obvious (maybe) that there is a link.

Luck is pre-wished.

---

