---
title: "ubuntu (or windows) will not reconise flash drive"
date: 2009-08-30
forum: General Help
---

### Post by epicwallpaper on 2009-08-30
suddenly for no reason both of my usb flash drives quit working. What can I do to fix them or at least see what happened so that way I can provide you with more information to solve this problem.

---

### Post by t0p on 2009-08-30
Both drives quit working at the same time?  That sounds more like a hardware issue to me.  Have you checked the USB port(s) on your computer?  ie plug in another USB device and see if *that* has "stopped working" too?

---

### Post by epicwallpaper on 2009-08-30
it is my (uneducated) assumption that is is not the usb drives them self but the flash drives as my external hard drive and usb mouse still function

---

### Post by t0p on 2009-08-30
Okay, unplug the flash sticks. Then open a terminal (**Applications > Accessories > Terminal**) and type in the command

```
tail -f /var/log/messages
```

Now, keeping the terminal window open, plug in one of the flash sticks.  Have some more lines of info been output in the terminal?  If so, post them here.  If not... well, tell us.

---

### Post by epicwallpaper on 2009-08-30
never mind i figured out the problem. you are foing to laugh your *** of at this one :P i converted the enire film of alien to jpegs for a old art project that i had forgot about so that way I could draw it the only thing is that I converted the ENTIRE FILM :) so right now nadulas is working more than a fat man on a unicycle
 sorry for wasteng your time ](*,)

---

