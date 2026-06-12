---
title: "Monitor doesn't work after upgrade to 11.04"
date: 2011-04-29
forum: General Help
---

### Post by someitalian123 on 2011-04-29
Before ubuntu can even boot I get this on my monitor

Out of range Please set to 1280x1080 60Hz

I get that a grub. I'm not even sure if ubuntu can even boot because my monitor won't let me see anything. I'm using the driver off the nvidia website, not the stock one that came with ubuntu.

---

### Post by Hedgehog1 on 2011-04-30
You can boot while the bad display is going on.  You may have to arrow down and count until you finally boot into Ubuntu.

Once you are in Ubuntu, please do this:

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

