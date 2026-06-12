---
title: "Finding MBR"
date: 2009-08-17
forum: General Help
---

### Post by PirateChef on 2009-08-17
I'm getting ready to go dual-boot again, but I want to find out which drive has my MBR on it, so I don't accidentally overwrite it before I'm ready.
How do I find out which drive it lives on?

I'm probably overlooking something obvious, again, but better safe than sorry.

---

### Post by HermanAB on 2009-08-17
Howdy,

You can take a look with dd and hexedit if you are adventurous:
# dd if=/dev/sda of=filename bs=512 count=1
# hexedit filename

The more civilized way is with fdisk.
;)

---

### Post by Mirai_-_ on 2009-08-17
Every disk should have a MBR, but if you mean your boot menu then just check your grub.conf or menu.lst.  The 'root' or 'uuid' line gives the location where grub is installed (iirc), but it's trivial to reinstall it where ever you need to.

---

### Post by PirateChef on 2009-08-17
I guess what I'm asking is where GRUB lives. That's the root set in /boot/grub/menu.lst, right?

I have 3 drives, so I'm going to put a VFAT filesystem on one, install Windows on another, and Ubuntu on the third.

I remember from previous experience that Windows doesn't play well with GRUB, and will over-write any previously existing MBRs in order to install its own. So, I was going to install Ubuntu last.

However, for the first step, I didn't want to accidentally delete the MBR I'm booting off of.

Oddly, fdisk -l gives me nothing.

---

### Post by vinnywright on 2009-08-17
> **PirateChef said:**
> I'm getting ready to go dual-boot again, but I want to find out which drive has my MBR on it, so I don't accidentally overwrite it before I'm ready.
How do I find out which drive it lives on?

I'm probably overlooking something obvious, again, but better safe than sorry.

the MBR or master boot record lives in the first 512 bits of the disk your BIOS boot's from.
Usualey the primarey disk.

you say your geting redey to dool boot agin?

dont worey about over righting it befor your readey if your adding linux as it wont get reriten untill you install grub or lilo ..............however if your adding windows to a linux install it WILL get overrote.

insadentley if you nead to restor a windows MBR you can use fdisk from the windows ver. you wish to fix .....like......fdisk /mbr ....... undocumented but true......mabey no space.........it's ben a wile :P  .......but youll know it worked if it dosent complane about unrecognized switch or sutch and just returns the prompt :)

have a look at #4 hear

[http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

VINNY

---

