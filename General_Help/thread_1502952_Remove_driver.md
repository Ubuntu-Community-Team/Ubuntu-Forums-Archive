---
title: "Remove driver"
date: 2010-06-06
forum: General Help
---

### Post by deeppow on 2010-06-06
Running 10.04 LTS.  I added an available graphics driver for my card and now it won't boot up (well it does boot but the display remains blank).  How can I remove the driver? :confused:

Thanks.

---

### Post by KeyserSoze93 on 2010-06-06
Does it show the Ubuntu loading screen, before failing to show the login screen?

If so, try pressing CTRL-ALT-F1, logging in, and running:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo /etc/init.d/gdm restart

```

This should cause Ubuntu to default to the generic graphics drivers, after which you should be able to operate as normal.

Of course, this won't solve the problem of not having the drivers installed and giving you the best performance from your GFX card, but it should give you a GUI back.

What model is the card? I assume it's NVidia or ATI, since I haven't had Ubuntu offer to install any drivers for other cards.

There is a console and GUI tool called envyng, which you could also try to install the correct drivers.

---

### Post by deeppow on 2010-06-06
I was in troubleshooting mode as root so just executed your commands.  Worked like a charm.

Many thanks!  :popcorn:

---

