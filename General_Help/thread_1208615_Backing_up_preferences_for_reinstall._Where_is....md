---
title: "Backing up preferences for reinstall. Where is...?"
date: 2009-07-09
forum: General Help
---

### Post by mxdxj.86 on 2009-07-09
Hi Guys,

I've been working on Ubuntu Jaunty 32bit and I'm going to reinstall to the 64bit version so it makes better use of the resources I've got available. Anyway I've done quite a bit of customisation and found most of the things I need on my system, but I'm not sure where to find the custom theme I've saved

When creating a custom theme and clicking 'save as' in System > Preferences > Appearances, where do they get saved?

Also other than the home/name folder and my menu.lst file can you think of any other areas I may need to backup to keep my Preferences, such as Compiz Settings?

---

### Post by CatKiller on 2009-07-09
Themes are saved in ~/.themes. Icon themes are saved in ~/.icons. Compiz settings are stored as GConf keys, so in ~/.gconf.

You might want to use the dpkg --get-selections trick to generate a list of your installed applications so that you can automatically install them again later. It's been mentioned many times on this forum.

---

### Post by mxdxj.86 on 2009-07-09
Thanks CatKiller.

I looked through the forums, couldn't seem to find anything on themes. But thanks :-)

---

### Post by CatKiller on 2009-07-09
It's not themes, it's **all** the packages that you have installed, so that you don't need to remember what you've installed to re-install them again. [This]("http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/") is an outline of the process.

---

