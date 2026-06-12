---
title: "Doesn't Ubuntu 9.04 automatically system-update anymore?"
date: 2009-09-04
forum: General Help
---

### Post by amn108 on 2009-09-04
I recall that all versions of Ubuntu I had prior to this one (9.04) used to periodically show the "System Update available" icon in the panel, which reminded and led me to initiate system updates very often.

I don't recall this happening ONCE on my current setup. I did not tweak anything to my best recollection.

The bad side to this is that since it does not remind me anymore, I myself remember doing updates once every three months or so, which leads me to having to download 150Mb worth of updates. I would much rather it reminded me every week or so...

How does one solve this best way?

Thx.

---

### Post by Zimmer on 2009-09-04
Have you tried adjusting the settings in Update Manager to look for Updates daily etc...?

---

### Post by credobyte on 2009-09-04
By default, update manager will check for updates daily ( and I truly receive them once they are released ). As previously said, maybe you or someone else have changed update manager settings and it's simply turned off ( eg., big delay between update checks ) ?

---

### Post by amn108 on 2009-09-04
Just checked Settings in Update Manager. It said "weekly". Everything seemed to be turned on, that which was relevant I mean.

This is why its kind of strange that it does not work. I have not seen the icon ever since I installed 9.04 (32-bit x86).

Do you guys use the 9.04 version too?

---

### Post by hockeytux on 2009-09-04
Same here. Prompting for daily updates was the default setting (which I never changed), I receive them daily and Im using 9.04 as well, no problems there. Someone must have changed your Update Manager settings...

---

### Post by credobyte on 2009-09-04
> **amn108 said:**
> Just checked Settings in Update Manager. It said "weekly". Everything seemed to be turned on, that which was relevant I mean.

This is why its kind of strange that it does not work. I have not seen the icon ever since I installed 9.04 (32-bit x86).

Do you guys use the 9.04 version too?

I would give a try to system logs .. update might have been initiated, however, there are tons of possibilities, why it didn't completed ( eg., you haven't seen any icons in notification area, etc. ).

P.S. - you can see what we use in our forum profiles ( to the left from our replies ).

---

### Post by nothingspecial on 2009-09-04
Launch gconf-editor and navigate apps > update notifier (note not manager).

Check the auto launch box is checked.

---

### Post by sefs on 2009-09-04
I distinctly remember Jaunty handles updates differently to how previous releases handled updates.  

There is a work around to return Jaunty to the old way of doing updates, which is to prompt you when they actually are updates.

You can read this...

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-doesnt-show-when-updates.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-doesnt-show-when-updates.html)

---

