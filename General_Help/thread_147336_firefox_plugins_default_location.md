---
title: "firefox plugins default location"
date: 2006-03-20
forum: General Help
---

### Post by dmizer on 2006-03-20
how do i determine where firefox looks for the "plugins" folder?

there is a symbolic link to the plugins in my ~/.mozilla/firefox folder (i'm using the 1.5 version of firefox installed per the wiki), but when i look in about:plugins, firefox tells me, "no plug-ins are installed".

edit to remove goofy smily in about:plugins

---

### Post by mikelygee on 2006-03-20
I believe it's /usr/lib/mozilla-firefox/plugins/ (at least that's where it is on my system).

--Mike

---

### Post by dmizer on 2006-03-20
i found it, but it was pretty tricky.  the wiki indicates that you should do the following:

```
cd /opt/firefox/plugins/
 sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
 sudo rm libtotem_mozilla.*
```
however ... that was inneffective.

my fix was to remove the plugins folder from /opt/firefox
i replaced the folder with a symbolic link: sudo ln -s /usr/lib/mozilla-firefox/plugins (no star)

i also edited the mplayerplug_in.conf to include ao=esd per this thread: [http://www.ubuntuforums.org/showthread.php?t=144521&highlight=mplayer+slow](http://www.ubuntuforums.org/showthread.php?t=144521&highlight=mplayer+slow)

here's my box streaming windows media ... whooo baby.

---

