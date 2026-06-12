---
title: "FF crashes constantly"
date: 2010-07-03
forum: General Help
---

### Post by whitegoddess on 2010-07-03
So im new to ubuntu and i have been having serious troubles getting firefox to work properly, since i change the operating system FF crashes almost every 5 min, more frequently when i open a page that it uses flash but i recall a couple of times that flash wasn't involved, i have tried everything, here are some of the codes i got, hope that helps, thanks in advance. 

(firefox:9594): GLib-WARNING **: g_set_prgname() called multiple times
Segmentation fault

GLib:ERROR:/build/buildd/glib2.0-2.22.3/glib/gmain.c:1963:g_main_dispatch: assertion failed: (current->dispatching_sources == &current_source_link)
Aborted

---

### Post by SmokeyThePanda on 2010-07-03
I also experienced this just before my clean install of karmic a few days back. I didn't really find a solution for the problem, but I did receive a bit of advice from a friend. 

What you should try first is running firefox in safemode. 

*firefox -safe-mode*

This will force all of your plugins off(I think). If safemode doesn't load, you could manually turn off all of your plugins. The purpose of this is that one of your plugins could be crashing firefox. After you turn them off, turn them on one at a time while browsing normally. When it starts crashing again, you know you have at least one of the plugins causing it. When you find one that causes it, uninstall or disable it. Do this for all of your plugins. 

If this does not work, I am not sure how to fix the problem. I ended up switching to Chromium, then to Opera. 

Hope the above helps.

---

### Post by Silent Warrior on 2010-07-03
Are you using Firefox from the Ubuntu-repositories, or Mozilla dailies? Using the RGBA-mod? I had the same crash when I tried the RGBA-thing - uninstalling that made the problem go away then.

---

### Post by lovinglinux on 2010-07-04
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

