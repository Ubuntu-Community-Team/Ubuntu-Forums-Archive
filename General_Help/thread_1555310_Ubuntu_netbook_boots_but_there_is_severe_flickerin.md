---
title: "Ubuntu netbook boots but there is severe flickering and I can't get past logging in"
date: 2010-08-17
forum: General Help
---

### Post by chaorace on 2010-08-17
My OS is  Ubuntu net-book lucid linx (newest version not sure which)
video card is intel chipset (made 2 years ago)
I had just changed the graphics effects to extra and reboot. To my surprise the entire screen is flickering and even though I "can" login the menu doesn't appear and I continue to experience rapid flickering
I do have a ubuntu DVD

---

### Post by chaorace on 2010-08-18
Bump...
I seriously needhelp I mean this is my go-to operating system!

---

### Post by kerry_s on 2010-08-18
netbook & compiz don't pay well together, thats why it's not installed default.

your best bet is to uninstall compiz. just switch to a tty, log in & uninstall it.

press-> ctrl+alt+f1
type-> sudo apt-get purge compiz
type-> sudo reboot

---

### Post by chaorace on 2010-08-19
I found a workaround.
I went to the switch users screen and went to ubuntu netbook 2d and then upgraded to maverick meerkat alpha 3, it uses a unity interface instead so it handles effects better!

also I would like to know which visual effects will work in netbook if possible


note:
maverick meerkat  is an alpha release only install if you are willing to accept that loss of data or OS may occur and all alpha releases are not meant to be installed on production computers

---

