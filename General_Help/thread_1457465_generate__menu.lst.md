---
title: "generate  menu.lst"
date: 2010-04-18
forum: General Help
---

### Post by TBhX£2760R8@nK7§r on 2010-04-18
I installed ubuntu a few days ago, and finally got around to trying to make windows the default option on the gnu grub bootloader. I managed to edit the grub file in etc so windows was the default, but now I have no idea how to update it. The terminal is confusing to me, as I know the windows terminal. I assume I have to use it on some folder to run the update thing, so explicit instructions would be appreciated.

---

### Post by lisati on 2010-04-18
Which version of Ubuntu and/or grub are you using?

---

### Post by TBhX£2760R8@nK7§r on 2010-04-19
Um. Newest version of ubuntu, and I think grub updated with many other things while it was running.

---

### Post by marshmallow1304 on 2010-04-19
The version of Grub installed on the latest version of Ubuntu does not use menu.lst.  If you've set up Grub by editing /etc/default/grub, you can use
```
sudo update-grub
```
to update grub.  BTW, this is explained at the top of /etc/default/grub.

---

### Post by TBhX£2760R8@nK7§r on 2010-04-19
Oh. I was confused on how to do that. Sorry, and thanks.

*EDIT*
Huh, this raises more questions. I don't think I edited the grub file right.

A website, that I don't have anymore said that having "GRUB_DEFAULT="Windows XP Professional (on /dev/sda1)"" would work. Is this true? Sorry for my complete lack of knowledge about anything not windows(Which I know a fair amount about, but that's irrelevant here.).

*EDIT"S EDIT*
Documentation has solved things.
 ***GRUB_SAVEDEFAULT=***  If set to ***true*** this setting will automatically set the last selected OS from the menu as the default OS on the next boot.

Another edit:
Thanks to those who posted and logic, I finally got it to work. GRUB_DEFAULT=4. Simple solutions work. All in all, I need to learn more about ubuntu. Thanks to those who helped.

If I enable this, it will just have windows be default, yes? Can I just leave out the GRUB_DEFAULT parameter?

---

### Post by zoogTHOMzoog on 2010-04-22
Yeah, you should be able to leave out the GRUB_SAVEDDEFAULT parameter. If you use that parameter your default will change everytime you boot into a different OS.

---

### Post by TBhX£2760R8@nK7§r on 2010-04-22
That didn't work for some reason. Doesn't matter at this point though, I have it working the way I want it to.

---

