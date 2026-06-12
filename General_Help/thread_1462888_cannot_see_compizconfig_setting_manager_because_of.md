---
title: "cannot see compizconfig setting manager because of opacity"
date: 2010-04-26
forum: General Help
---

### Post by nilsolaris on 2010-04-26
I cannot see the compizconfig setting manager because of opacity. Ive been trying to figure out how to get transparent windows. Found the opacity, brightness menu. Not sure what i changed but the compiz window is open i cannot see it or anything to fix it! Any suggestions?

---

### Post by stinkeye on 2010-04-26
Hit alt + f2 

Type in
```
metacity --replace
```
and hit enter

You can now fix up your opacity plugin.

or if it's just the ccsm window thats invisible,
in terminal enter
```
gconftool-2 --unset "/apps/compiz/plugins/obs/screen0/options/opacity_matches"
```

This is a common problem because the default setting is 100% transparent
so as soon as you add the window it becomes invisible.

---

