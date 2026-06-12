---
title: "Help with advanced desktop effects to work"
date: 2009-12-01
forum: General Help
---

### Post by jibby_1 on 2009-12-01
hi all, I am reading a online tutorial on how to get compiz working. So the first thing it says is to go to advanced visual effects and click extra. Then a message comes up and says visual effects can not be enabled. So I run a check and I get one fail, here is the code
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Device 9710
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


```                                 can anyone help me. Thanks

---

### Post by spiderbatdad on 2009-12-01
to get compiz working open synaptic package manager and install "compizconfig-settings-manager" After it installs, open it through System>>Preferences>>Compizconfig-Settings-Manager
Then choose your options like Desktop Cube and Rotate Cube, or whatever...configure the bindings etc.

---

### Post by jibby_1 on 2009-12-01
> **spiderbatdad said:**
> to get compiz working open synaptic package manager and install "compizconfig-settings-manager" After it installs, open it through System>>Preferences>>Compizconfig-Settings-Manager
Then choose your options like Desktop Cube and Rotate Cube, or whatever...configure the bindings etc.

thanx dude got it working

---

### Post by jibby_1 on 2009-12-01
ok i justed updated to drivers using envyng, but i do not have a Rendering method is that really gonna effect me heres the code:
```

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Device 9710
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

---

