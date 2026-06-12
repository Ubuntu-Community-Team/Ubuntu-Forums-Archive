---
title: "Setting up a text-only boot process (11.04)."
date: 2011-12-21
forum: General Help
---

### Post by jbm222 on 2011-12-21
I'm trying to get my machine to drop all the fancy boot splash screens and to show the grub menus and I'm having some trouble with both since I haven't modified a grub config since prior to grub 2.

So any suggestions on what all needs to be done?

BTW, my reason for wanting to do this is that my boot sequence was hanging for a very long time and I had no idea if the computer was bricked or just thinking really hard.  I checked the boot log and it was running fsck, but I'd rather just know right away if that's happening.

---

### Post by emmomalick on 2011-12-21
Try booting your PC by a USB and then update your grub
```
sudo update-grub
```

---

### Post by jbm222 on 2011-12-21
> **emmomalick said:**
> Try booting your PC by a USB and then update your grub
```
sudo update-grub
```
Not sure what 'by a USB' means.  Boot from a different medium?  Will that even work, or is that just a guess?

---

### Post by rbc on 2011-12-21
You want to view all the texts flashing by on the screen, during the boot process? If so, here's this entry:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

From this web site:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by emmomalick on 2011-12-22
Yes try to boot from a Medium e.g CD/DVD or a USB. and then follow the steps from here.

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by MartijnNL on 2011-12-22
> **emmomalick said:**
> Yes try to boot from a Medium e.g CD/DVD or a USB. and then follow the steps from here.

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

I don't think that's the issue here. He doesn't want to see the boot logo. He wants to see all the boot info scroll by.

For that you need to edit /etc/default/grub (as root) and remove " quiet splash" like rbc says.

By the way: to see the GRUB menu press and hold shift as soon as the screen turns black during boot (after the hardware info/logo shown at the beginning, also known as POST).

---

