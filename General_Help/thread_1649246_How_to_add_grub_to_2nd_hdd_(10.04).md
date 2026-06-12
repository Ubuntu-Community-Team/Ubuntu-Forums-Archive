---
title: "How to add grub to 2nd hdd? (10.04)"
date: 2010-12-19
forum: General Help
---

### Post by Paco62 on 2010-12-19
My comp has two hard drives, both now loaded with clean installs of  10.04. I spent a lot of time configuring both with tweaks and installs  etc. and both are identical.  I use the first hdd regularly and the  second just to update it.  My intention is to be able to switch  immediately to the second hdd when the first one finally fails. The bios  is set to boot from the first hdd, and then the grub dialog comes up  which enables me to choose from 1st or 2nd hard drive.  So I conclude  that grub is located on the first hdd.  However, when I use the bios  startup dialog to choose to boot directly from the 2nd hdd, there is  just a blinking cursor and nothing happens.  So I conclude that there is  no grub on the 2nd hdd.  (I know very little about linux or ubuntu) .  Obviously this means that if the first hdd fails, I am out of luck.  So  is there a way I can add grub to the second hdd?  Thanks in advance.

---

### Post by oldfred on 2010-12-19
Boot into your install on the second hard drive. Confirm that it is sdb.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then after rebooting:
sudo update-grub

That should also find your install in sda and let you boot that. 

If you want to know what is installed where. I run this before & after changing things on my system to make sure I did what I really wanted to do. It is one tool that also shows what is installed to the MBR, but sometimes either grub or the script misidentify drives, so if it says same drive, it may not be true.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

