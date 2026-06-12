---
title: "Firefox Unity Icon is a Question Mark"
date: 2011-10-23
forum: General Help
---

### Post by Gyo on 2011-10-23
In a Oneiric Ocelot "refreshed" installation after some upgrades and a change of theme (from Ambiance to Radiance) and after a restart, the Firefox icon in my Unity bar become a question mark.
Looking in the Dash Firefox icon was simply blank.

Googling for this I just found this thread, sadly unuseful:
[http://ubuntuforums.org/showthread.php?t=1823286](http://ubuntuforums.org/showthread.php?t=1823286)

This is how I solved. I write this down hoping it could help someone.

1. Install Gnome classic desktop ```
sudo apt-get install gnome-panel
```
2. Run Alacarte (should be auto installed by gnome-panel) from the dash or just typing in term ```
alacarte
```
3. Find Firefox menu item (it should be into Internet directory) and Revert/Restore to its default settings.
4. Close session and reenter
5. I think now you can uninstall Gnome classic. I keeped it.

Bye!

---

### Post by Jake9999 on 2011-10-26
Thanks alot! You made my day.

This has been bugging me since 10.10 and now thanks to you was finally able to fix it.

Gr,

Jake

---

