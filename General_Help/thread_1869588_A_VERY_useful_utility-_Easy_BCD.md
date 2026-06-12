---
title: "A VERY useful utility- Easy BCD"
date: 2011-10-26
forum: General Help
---

### Post by Fred Doolie on 2011-10-26
Want to run Ubuntu without destroying your Windows MBR? Use "EasyBCD". It's for Vista and Win7. What is does is some kind of voodoo. Using the standard Windows MBR and bootloader it chainloads, among other things, a Grub2 MBR image. In other words you can have your dual-boot system WITHOUT messing up your Windows MBR. 

Why would you want to do this? Well..

1) Maybe you have one of those systems with the special code in the MBR for bringing up a hidden restore partition. You don't want to ruin that by overwriting it with Grub like I did.

2) Maybe your virus checker or BIOS keeps bitching about some "virus" that overwrote your MBR.

3) Maybe you aren't 100% sure you want to keep Linux. With your Win MBR intact removing Linux is super simple.  Just use EasyBCD to remove the Grub2 entry and then use the Windows partitioner to delete/reformat/whatever the Linux partitions and it "never happened".

The only "con" I can think of is that booting into Linux is not automatic anymore. You have to press down arrow and then enter to get the Grub2 menu. However you MAY be able to use EasyBCD to default to the Grub2 entry.

Side Note: It looks like EasyBCD can also create entries for Old Grub and even one for booting into MacOS.

Update:
Strike that "con". The Grub2 entry can be made the default so booting time is only a few seconds longer. That few seconds are spent in the menu where you pick Windows or Grub 2.

Update 2: Even if you already did the Ubuntu install it's not too late (except for #1 up there). EBCD can restore the standard Windows MBR. That's how you uninstall a regular install of Linux.  Use EBCD to put back the Windows MBR and then remove the linux partitions with the Windows partitioner.

---

### Post by Mark Phelps on 2011-10-26
Nice post ... would have been even nicer if you'd told folks WHERE to get EasyBCD.

See link:  [http://neosmart.net/forums/forumdisplay.php?f=7]("http://neosmart.net/forums/forumdisplay.php?f=7")

---

### Post by philinux on 2011-10-26
+1 ^

and this link [http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home) :p

---

### Post by Fred Doolie on 2011-10-30
[QUOTE=Mark Phelps;11395134]Nice post ... would have been even nicer if you'd told folks WHERE to get EasyBCD.

You use a search engine to find it. That way you know the link you click on is legitimate and not a booby-trapped one that leads to a porn site or some virus and trojan-filled spam web page that some butthead put in his post.

---

### Post by FormatSeize on 2011-10-30
EasyBCD is a great tool. It enabled me to install Wubi under Windows 8 Dev Preview (I don't know whether or not it was the UEFI, but the problem was solved with EasyBCD).

---

