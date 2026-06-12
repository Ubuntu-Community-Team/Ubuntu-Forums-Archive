---
title: "Need help with desktop effects"
date: 2010-04-29
forum: General Help
---

### Post by Scari on 2010-04-29
I go to preferences/appearance to set my visual effects at extra and get an arror message: desktop effects could not be enabled, I tried normal with the same result. Thanks

---

### Post by Scari on 2010-04-29
I guess I should add I'm a very new user of linux/ubuntu so I'm still learning.

---

### Post by SnickerSnack on 2010-04-29
Do you have Compiz installed?  (That's the software that handles the effects.)

You can either look for it in the 'Ubuntu Software Center', in Synaptic (System>Administration>Synaptica Package Manager), or run this command at the command line terminal:

```
sudo apt-get install compiz
```

---

### Post by Scari on 2010-04-29
> **SnickerSnack said:**
> Do you have Compiz installed?  (That's the software that handles the effects.)

You can either look for it in the 'Ubuntu Software Center', in Synaptic (System>Administration>Synaptica Package Manager), or run this command at the command line terminal:

```
sudo apt-get install compiz
```
Yes I did install that, thanks

---

### Post by Scari on 2010-04-29
ok ran a test the result:
 Distribution:          Ubuntu 9.10
  Desktop environment:   GNOME
  Graphics chip:         ATI Technologies Inc Radeon HD 3870
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
So I assume the fail is the reason.....

---

