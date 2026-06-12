---
title: "Grub AND Bootup screen"
date: 2010-08-26
forum: General Help
---

### Post by RobotGymnast on 2010-08-26
I installed Ubuntu via Wubi, but now when I boot up the computer, it asks me to select Ubuntu or Windows, then after I select Ubuntu, it takes me to the Grub menu, which also asks whether I want Ubuntu or Windows. I've had this on multiple computers, and it's not very useful. How to change this?

---

### Post by bcbc on 2010-08-26
> **RobotGymnast said:**
> I installed Ubuntu via Wubi, but now when I boot up the computer, it asks me to select Ubuntu or Windows, then after I select Ubuntu, it takes me to the Grub menu, which also asks whether I want Ubuntu or Windows. I've had this on multiple computers, and it's not very useful. How to change this?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

That link shows how you can hide the grub menu on a computer with multiple OS's. I've tried it in 10.04.1 and it works. I did get an unknown command: xxxx but it boots straight into Ubuntu.

Although it is possible to do this, I don't recommend changing the windows boot manager to automatically go straight to the grub menu. The reason being, that with wubi, there is a risk of corruption on the root.disk, and if that happens you'll have no menu and no way to boot windows. (Without booting a recovery disk and resetting the windows boot manager).

---

### Post by RobotGymnast on 2010-08-26
> **bcbc said:**
> [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

That link shows how you can hide the grub menu on a computer with multiple OS's. I've tried it in 10.04.1 and it works. I did get an unknown command: xxxx but it boots straight into Ubuntu.

Although it is possible to do this, I don't recommend changing the windows boot manager to automatically go straight to the grub menu. The reason being, that with wubi, there is a risk of corruption on the root.disk, and if that happens you'll have no menu and no way to boot windows. (Without booting a recovery disk and resetting the windows boot manager).

Perfect, thanks!

---

