---
title: "Messed my Compiz animations  :-("
date: 2010-03-06
forum: General Help
---

### Post by the lemming on 2010-03-06
Some how I've messed up my animations for when the screens, minimise, expand and shut down.

Does anybody have any tips on how to restore the default settings,

or

How to set them up properly to begin with?

Cheers

---

### Post by flippo on 2010-03-06
Try ```
mv ~/.compiz ~/.compiz_bup
```
Should restore all of the default settings (and backup your old ones).

---

### Post by coldraven on 2010-03-06
Hi flippo, would you have to reboot after that?

---

### Post by flippo on 2010-03-06
You just need to restart your gnome-session: log out and log back in, restart X, reboot, etc...

---

### Post by the lemming on 2010-03-07
> **flippo said:**
> Try ```
mv ~/.compiz ~/.compiz_bup
```
Should restore all of the default settings (and backup your old ones).

Sorry but this did not change anything.

I even logged out and then rebooted my computer to see if that helped.

---

### Post by howefield on 2010-03-07
Do you have compizconfig-settings-manager installed ?

If so, try loading it up and click on the Preferences link, then on "Reset to defaults" button.

---

### Post by SecretCode on 2010-03-07
> **the lemming said:**
> 
How to set them up properly to begin with?

Cheers

Install compizconfig-settings-manager (ccsm) as recommended above. (Optionally also install fusion-icon which allows handy access.)

Launch ccsm, go to the Animations plugin (in the Effects section), then under the various tabs select the animation you want, the duration, etc. (You may have multiple 'window match' lines already. The first one is usually the one applying to regular application windows. Single-click > Edit, or just double-click.)

---

