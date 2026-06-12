---
title: "Can't see grub because of a incorrect monitor timings."
date: 2011-04-28
forum: General Help
---

### Post by greg5 on 2011-04-28
I'm using 11.04 and when I boot I see post messages and then when it gets to grub I just see black screen with a monitor timing not supported issue. I have a geforce 6100 nforce 405 video card with a Dell U2311H monitor. It does boot to the desktop eventually, and everything from there on works as expected.

---

### Post by Hedgehog1 on 2011-04-28
Please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by greg5 on 2011-04-28
Thanks for the reply. I made your changes and now it doesn't give me the monitor timing screen. It gives me a solid background color, but I still don't see the grub boot menu.

---

### Post by Hedgehog1 on 2011-04-28
If you are not dual-booting, the solid color is what grub does (there are options for a pretty picture, but lets not worry about that today).

To see the grub menu, when booting hold down the left 'shift' key. This will bring up the grub menu.


***The Hedge***

:KS

---

### Post by greg5 on 2011-04-28
Thanks that was it.

---

