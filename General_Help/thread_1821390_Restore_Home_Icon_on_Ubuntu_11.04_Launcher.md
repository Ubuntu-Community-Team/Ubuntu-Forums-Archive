---
title: "Restore Home Icon on Ubuntu 11.04 Launcher"
date: 2011-08-09
forum: General Help
---

### Post by SmLwNaoev7dDUN@ on 2011-08-09
After installing Ubuntu 11.04, I removed the Home Icon from  the launcher by right clicking on the Home Icon and chosing the - Keep  In Launcher option. Then it disappeared. Now I am wondering how do I  restore it, because I think it was not a good idea and I need it now.  Can anyone help me on this?

---

### Post by sinbowden on 2011-08-09
1. [http://ubuntugenius.wordpress.com/2011/02/18/missing-title-bars-in-ubuntu-1-click-restore-of-compiz-fusion-emerald-themed-window-borders/](http://ubuntugenius.wordpress.com/2011/02/18/missing-title-bars-in-ubuntu-1-click-restore-of-compiz-fusion-emerald-themed-window-borders/)



2. use this command at your own risk and only if you really have to. 
Resetting Compiz in Ubuntu 11.04 

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by sikander3786 on 2011-08-09
You don't need to do any of the above command IMO.

Simply click your desktop first and then hover your mouse at the top bar where you normally see the global menu. Under 'Places', open up 'Home'. When the icon appears in the Launcher, simply right click it again and 'Keep in Launcher' ;)

You might also be interested in a few useful Quciklists, BTW.

[http://ubuntu4beginners.blogspot.com/2011/05/top-unity-launcher-quicklists.html](http://ubuntu4beginners.blogspot.com/2011/05/top-unity-launcher-quicklists.html)

---

### Post by SmLwNaoev7dDUN@ on 2011-08-10
Thanks guys for replying, but before I could solve this problem, I installed a new OS, back to 10.10 for some reasons. Thanks for talking your time and responding. :)

---

