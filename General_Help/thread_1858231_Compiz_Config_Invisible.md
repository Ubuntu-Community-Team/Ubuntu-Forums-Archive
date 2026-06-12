---
title: "Compiz Config Invisible"
date: 2011-10-11
forum: General Help
---

### Post by gpanterov on 2011-10-11
Hi all,

I was playing around with the opacity option in the Compiz Config Settings Manager. Suddenly the Compiz window became invisible. I can see that it is open in the lower panel and I can move it around in different workspaces but I can't see the window itself. 

Is there anyway I can restore the defaults and/or remove the opacity settings that made the whole thing invisible?


I tried several things I found online like restoring default settings by typing in the terminal :
gconftool-2 --recursive-unset /apps/compiz

and playing around with the gconf-edit /app/gwd options but nothing helped.

Any help would be much appreciated

Thanks

:w /home/gpanterov/Documents/temp.txt

---

### Post by abhi90 on 2011-10-12
open terminal and type ccsm.
it open compiz config window.

---

### Post by stinkeye on 2011-10-12
If your opacity plugin in ccsm is set to defaults you should be able to hover over where you think the window is and hold down alt while moving the mousewheel up to increase the opacity.

Also for natty you may use this to remove the window from the opacity matches
```
gconftool-2 --unset "/apps/compiz-1/plugins/obs/screen0/options/opacity_matches"
```

---

