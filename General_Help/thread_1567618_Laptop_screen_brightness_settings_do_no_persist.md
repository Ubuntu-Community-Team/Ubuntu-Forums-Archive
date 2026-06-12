---
title: "Laptop screen brightness settings do no persist"
date: 2010-09-04
forum: General Help
---

### Post by austinium on 2010-09-04
Hi,

I am using Ubuntu 10.04 64bit on an Acer laptop. The graphics card details are:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

Each time i restart my computer or login after logging off, the screen brightness gets rest to maximum, how can i make the settings persist?

thanks

---

### Post by austinium on 2010-09-07
^bump^

---

### Post by jongkind on 2010-09-07
[LIST]
[*]Open the configuration Editor
[*]Browse to apps/gnome-power-manager/backlight
[*]Adjust the brightness_ac and brightness_dim_battery to your preference.
[/LIST]

---

### Post by lUffy_10.04 on 2010-09-08
Hey, I'm having a similar issue. I have an Acer Aspire 5741 and nothing I do seems to work.

The brightness is always on max (I checked). The FN keys toggle the brightness bar but nothing changes. I tried the brightness applet but that doesn't work either. I tried adding all sorts of things in /etc/default/grub and still nothing.

Anyone have any more ideas or ways to fix this?? I've been reading that this might be a kernel issue (w/e that is, I'm a noob) but apparently it's deeper than just changing some parameters. Still, any fix would be better than having to burn my eyes every time I run ubuntu, lol.

Oh and ):P I'm new here

---

### Post by jongkind on 2010-09-08
lUffy_10.04: it would help if you report whether my suggestion did work for you....

---

### Post by austinium on 2010-09-08
I tried what you said jongkind, the brightness still gets reset to maximum after a restart although the *entries* under gconf-editor apps/gnome-power-manager/backlight persist.

---

### Post by lUffy_10.04 on 2010-09-08
Ahh I'm sorry, I thought it was implied in my message. 
I tried your suggestion but the brightness remains at maximum regardless of the value I enter for brightness_ac and brightness_dim_batter. They are set to about 70 and 45 right now, respectively, but the brightness doesn't change.

---

