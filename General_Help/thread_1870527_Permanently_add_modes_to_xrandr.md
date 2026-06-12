---
title: "Permanently add modes to xrandr"
date: 2011-10-27
forum: General Help
---

### Post by lykwydchykyn on 2011-10-27
I just got an Optiplex 745 for my kids with an Intel q965 video chipset in it.  It only has DVI output, and I only have VGA monitors, so I'm using an adapter.

When Xorg does its own thing, I only can get 1024x768.  I found that I can generate a mode line with cvt and manually add that with xrandr and get 1280x1024, which is what I want.

I know I could just script this and run it at log in, but is there a clean, system-wide way to add a mode like this?  I tried adding this to xorg.conf:
```

Modes "1280x1024"

```

Under the correct depth section, but it didn't work.

---

### Post by dcstar on 2011-10-29
> **lykwydchykyn said:**
> I just got an Optiplex 745 for my kids with an Intel q965 video chipset in it.  It only has DVI output, and I only have VGA monitors, so I'm using an adapter.

When Xorg does its own thing, I only can get 1024x768.  I found that I can generate a mode line with cvt and manually add that with xrandr and get 1280x1024, which is what I want.

I know I could just script this and run it at log in, but is there a clean, system-wide way to add a mode like this?  I tried adding this to xorg.conf:
```

Modes "1280x1024"

```

Under the correct depth section, but it didn't work.

Post the **whole** xorg.conf file.

---

### Post by lykwydchykyn on 2011-10-29
I decided not to go the xorg route.  It appears that using a DVI to VGA converter makes the monitor appear as a separate output to xrandr, and I can't use xorg.conf to configure it.

I decided to create a little script that looks like this:

```

xrandr --newmode 1280_1024 109.00  1280 1368 1496 1712  1024 1027 1034 1063
xrandr --addmode VGA1 1280_1024
xrandr --output VGA1 --mode 1280_1024

```

Then I call that script from /etc/lightdm/lightdm.conf like so:
```


display-setup-script=/usr/local/bin/add_1280_1024.sh
session-setup-script=/usr/local/bin/add_1280_1024.sh


```

It works great.

---

