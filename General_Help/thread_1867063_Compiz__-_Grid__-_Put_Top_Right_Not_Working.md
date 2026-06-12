---
title: "Compiz  - Grid  - Put Top Right Not Working"
date: 2011-10-22
forum: General Help
---

### Post by fusionex on 2011-10-22
I'm using a System76 Pangolin Performance 7 and Ubuntu 11.10 with Unity.

Ctrl-Alt-Numpad 9 does a Put Top rather than a Put Top Right. I've tried reassigning the action to a different key combination, but the effect is the same.

Does anyone know why this is happening and how it might be fixed?

Thanks,
Josh

---

### Post by harijay on 2011-10-23
I am seeing the same thing. CTRL-ALT-9 does not work as it was with Natty. In Oneiric CTRL-ALT-9 puts a window on the Top.
  
Also trying to re-specify the key combination in "grid" plugin settings in CSSM ( compiz settings manager) and entering CTRL-ALT-9 , the 9 key is recognized as a Page up. But regardless even pressing this key combination does not do the right thing.

I know the numerical keypad "9" key is recognized as  a 9 because the keyboard viewer does indeed map it to a 9.

So it seems like the Grid plugin - Top right placement is broken.

---

### Post by franz.maulwurf on 2011-10-25
Same here, top right corner not working, instead puts it just top.

However, the function was working properly until I activated and afterwards deactivated some compiz settings.

In addition, it did not work after updating form 11.04

---

### Post by 10o on 2011-10-25
Same here, ctrl+alt+9 now does the same as ctrl+alt+8...

---

### Post by heathman001 on 2011-10-25
This worked for me in Natty, but after upgrading to Oneiric it doesn't work. I have the keys remapped since I'm on a laptop without a numpad, but I'm getting the same results. Put Top-Right results in the window being put on the top half and Put Bottom-Right puts the window on the bottom half. The result is the same whether I use key-bindings or edge bindings. All other locations work properly.

I think I'll go see if a bug report has been opened on launchpad.

Edit: Bug Report: [https://bugs.launchpad.net/compiz-grid-plugin/+bug/876591](https://bugs.launchpad.net/compiz-grid-plugin/+bug/876591)

Looks like someone has included a PPA with a fix:

ppa:lbrulet-8/ppa (compiz-plugins-main) :
[https://launchpad.net/~lbrulet-8/+archive/ppa](https://launchpad.net/~lbrulet-8/+archive/ppa)

---

### Post by fusionex on 2011-10-26
> **heathman001 said:**
> This worked for me in Natty, but after upgrading to Oneiric it doesn't work. I have the keys remapped since I'm on a laptop without a numpad, but I'm getting the same results. Put Top-Right results in the window being put on the top half and Put Bottom-Right puts the window on the bottom half. The result is the same whether I use key-bindings or edge bindings. All other locations work properly.

I think I'll go see if a bug report has been opened on launchpad.

Edit: Bug Report: [https://bugs.launchpad.net/compiz-grid-plugin/+bug/876591](https://bugs.launchpad.net/compiz-grid-plugin/+bug/876591)

Looks like someone has included a PPA with a fix:

ppa:lbrulet-8/ppa (compiz-plugins-main) :
[https://launchpad.net/~lbrulet-8/+archive/ppa](https://launchpad.net/~lbrulet-8/+archive/ppa)

Thanks, heathman001! This PPA worked for me.

---

### Post by birdsarah on 2011-11-06
Worked for me too - many thanks!

---

