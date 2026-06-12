---
title: "nVidia Driver problem"
date: 2012-03-04
forum: General Help
---

### Post by reebzor on 2012-03-04
Hey so I just installed 11.04 and got everything up and running. I decided to use update manager which updated my kernel from 2.6.38-8 to 2.6.38-13, now I get stuck with a purple screen when the machine boots up.

The machine boots fine, I can ssh to it. I figure this issue has something to do with my nVidia 8400GS and the drivers associated with it. I've tried so many things: uninstalling nvidia drivers, installing -current, -173, nouveau. Nothing I do seems to work. Still stuck with a purple screen.

How can I install nVidia drivers and get my desktop back?

Thank you

---

### Post by reebzor on 2012-03-04
Ok so a little update, removed all nvidia drivers by ```
sudo apt-get remove --purge nvidia*
```

Then I tried the following:
nomodeset: doesn't work, locks up at the splash screen with the dots

failsafeX: also doesn't do anything.

---

### Post by reebzor on 2012-03-04
Alright well I guess I got it working. I think I forgot the remove my xorg.conf and the old conf was messing it up.

---

