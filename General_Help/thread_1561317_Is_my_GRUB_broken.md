---
title: "Is my GRUB broken?"
date: 2010-08-26
forum: General Help
---

### Post by Neezer on 2010-08-26
Hi,

I have been running 10.04 on a fresh install since it came out. I have never seen the GRUB menu on boot. I turn on my laptop and it goes right to the login screen. I know for a fact that I have more than one kernel to choose from though.

I wonder how GRUB is choosing the proper kernel to use. I'd like to get back the control. I'm have 2.6.33 on in order to get TRIM support for my SSD. Also, is there a way to know if TRIM is actually working? I'm under the impression that as long as you have kernel 2.6.33 or higher it will just automatically run.

Any help and knowledge would be greatly appreciated.

---

### Post by mthalis on 2010-08-26
Using this you can clean Up Ubuntu Grub Boot Menu After Upgrades.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

---

### Post by Sef on 2010-08-26
If you are using only Ubuntu, then you do not see GRUB.

---

### Post by arubislander on 2010-08-26
Your grub is not broken. As long as grub does not find any other OS it will not show the boot menu. If the kernel is updated it will automatically boot from the newest kernel (the one just installed). If you need to boot into a different kernel you should hold down the shift key (either one I think will do, but I habitually hold down the right-shift key) after the BIOS screen disappears.

---

### Post by Neezer on 2010-08-26
Thanks everyone.  Any input about TRIM just working? or should I start another thread on that topic?

---

### Post by dino99 on 2010-08-26
> **Sef said:**
> If you are using only Ubuntu, then you do not see GRUB.

wonder why this is the default, too much users are disturbed by not seeing the grub menu. I think that the "default" might be to see it, and let user to turn it off if they like.

---

### Post by arubislander on 2010-08-26
The idea probably is: Do not present a choice where it is apt to confuse the user. It might also have something to do with the quest for blazingly fast boots.

And indeed, as long as the default option works I don't need to see the grub menu. It kind of detracts from the aesthetics of the boot sequence... but then that's just me.

---

### Post by arubislander on 2010-08-26
> **Neezer said:**
> Thanks everyone.  Any input about TRIM just working? or should I start another thread on that topic?

TRIM is a rather specialized issue, I think it would benefit from it's own thread.

---

### Post by Neezer on 2010-08-26
Thanks everyone for the help. I appreciate your time.

---

