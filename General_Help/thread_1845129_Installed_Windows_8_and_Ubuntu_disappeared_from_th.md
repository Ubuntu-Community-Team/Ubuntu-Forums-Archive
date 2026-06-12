---
title: "Installed Windows 8 and Ubuntu disappeared from the boot menu"
date: 2011-09-16
forum: General Help
---

### Post by androidcupcake on 2011-09-16
I installed Windows developers preview to test how it looks. Installed it on a separate 20 GB partition and post-installation, Ubuntu does not appear on the boot menu. 

Is there any way to restore Ubuntu in the boot menu and of course get it working too? 

I'd seriously prefer NOT reinstalling it all the way. 

P.S I have ultimately uninstalled Windows 8 and am back to Windows 7.

EDIT: Had Ubuntu 11.04 prior to the disappearance of the same from the boot menu.

---

### Post by TeoBigusGeekus on 2011-09-16
Win8 overwrote your mbr.
You don't have to reinstall the whole system; just grub2:
[https://help.ubuntu.com/community/Grub2#ChRoot]("https://help.ubuntu.com/community/Grub2#ChRoot")

---

### Post by androidcupcake on 2011-09-16
> **TeoBigusGeekus said:**
> Win8 overwrote your mbr.
You don't have to reinstall the whole system; just grub2:
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Thank you. Don't have the live CD with me right now. Shall download Ubuntu and try the steps.

---

### Post by BigJoe309 on 2011-09-19
I upgraded from 10.10 to 11.04, which went fine. I then did some cleaning up and somehow managed to remove all references to Ubuntu from the boot-up screen so now I can only Access Win7. I dual boot but mainly use Ubuntu (this was my default) at home; W7 is 'just in case' for work things.

Will the above method work for my problem? 11.04 was working till I edited the GRUB2 options (I assume I unchecked the wrong box inadvertently. Note to self, multi tasking is not your strong point).

BTW I tried a Grub repair disc and it sent details here:- [http://pastebin.com/2JaxtvwS](http://pastebin.com/2JaxtvwS) (I'm actually also worried that playing around trying to mend it I may have installed Grub over grub2)

Update: gave up and re-installed 11.04 :(

---

