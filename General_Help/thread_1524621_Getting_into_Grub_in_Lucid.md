---
title: "Getting into Grub in Lucid"
date: 2010-07-05
forum: General Help
---

### Post by apesa on 2010-07-05
Hello, I have been struggling to get into Grub during boot. No matter how many times I reboot and hit the "esc" key.. runs right past Grub and into the splash screen. Every blue moon it will catch the esc and I get the grub menu. I have fixed my original issue by reinstalling the ATI support, but would like to know of any similar issues with Grub.

TIA,
Pat

---

### Post by oldfred on 2010-07-05
If you are using escape key you have an upgrade and are still running old grub legacy.

I believe you do not press the escape key once or twice but hold it down from BIOS boot until the menu appears. With grub2 it is the shift key.

---

### Post by libssd on 2010-07-05
There is fairly extensive documentation on Grub2 here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If I want to see the Grub2 menu, I normally hold down the Shift key, although I think any key will work. Check the GRUB_TIMEOUT= value in grub; I have mine set for 2 seconds, which requires a fairly quick stab at the keyboard to interrupt grub. I think the default value is 10.

```
$ sudo gedit /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=2**

```

---

### Post by -humanaut- on 2010-07-05
> **libssd said:**
> There is fairly extensive documentation on Grub2 here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If I want to see the Grub2 menu, I normally hold down the Shift key, although I think any key will work. Check the GRUB_TIMEOUT= value in grub; I have mine set for 2 seconds, which requires a fairly quick stab at the keyboard to interrupt grub. I think the default value is 10.

```
$ sudo gedit /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=2**

```

You'll want to change the GRUB_HIDDEN_TIMEOUT to 2 also so you have a second to hit escape Grub2 does use the esc key.

---

### Post by apesa on 2010-07-06
Thanks for all replies. I remember reading here that the shift key was a possible shot, but it did not work.

---

