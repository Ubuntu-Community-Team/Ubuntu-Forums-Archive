---
title: "Compiz and Radeonhd driver"
date: 2009-09-07
forum: General Help
---

### Post by AlejandroDelLoco on 2009-09-07
I've been looking for solutions with no avail. I'm using an ATI 3200 HD on my new Aspire 5517 laptop. I whitelisted the radeonhd driver, I've messed infinitely with the xorg.conf... Is there hope?

```
~$ '/home/alex/Downloads/compiz-check' 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
 Driver in use:         radeonhd
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```

---

### Post by Mark Phelps on 2009-09-08
This is the open source Radeon driver, right? Which means you're not using hardware acceleration. Which is probably why you're seeing the error message.

You should be able to use the ATI restricted drivers with that card.

---

