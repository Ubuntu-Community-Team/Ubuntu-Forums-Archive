---
title: "flash 10 not working with opera 9.64"
date: 2009-07-10
forum: General Help
---

### Post by trailofdead on 2009-07-10
I just did a clean install of jaunty.  
i was using hardy and everything was working great.  
i installed flash with ```
sudo apt-get install flashplugin-nonfree
```

flash **works in firefox**.  i copied the flash plugin to /usr/lib/opera/plugins for opera.  here is a screen of my opera:plugins page

why isnt flash working for opera??

opera 9.64
32 bit flash 10,0,22,87

---

### Post by lovinglinux on 2009-07-10
I haven't copied any plugins to /usr/lib/opera/plugins (it's empty) and it works just fine. That

Maybe you have conflicting plugins installed.

---

### Post by trailofdead on 2009-07-10
I deleted the plugin from /usr/lib/opera/plugins, restarted opera and it didnt detect a flash plugin.  copied it back, it detected the plugin, but flash still doesnt work.  

btw i'm trying to watch videos on youtube, but the adobe flash test page doesnt work either.

forgot to mention i'm using 32 bit flash 10,0,22,87

---

### Post by trailofdead on 2009-07-10
tried using the synaptic packet manager to reinstall the flash plugin.  didnt copy the plugin over to /usr/lib/opera/plugins.  opera found /usr/lib/flashplugin-nonfree/libflashplayer.so, but flash still doenst work in opera.  still works in ff though.

reinstalled opera.  copied ~/.opera, so opera would build a new one.  didnt help, and i lost my original ~/.opera due to careless error.

---

### Post by trailofdead on 2009-07-11
anyone have a solution for me?

i'm considering trying opera 10 if i cant find a way for this to work.

---

### Post by trailofdead on 2009-07-12
when i run opera in a terminal i get ```
Not GTK2 toolkit (got 0).
``` whenever i visit a site with flash content.  

after doing some research, it seems that in flash 10, Adobe forced the browser to use GTK window and containers to load a swf file in Linux.  i guess this is the problem, but what's the fix??

---

### Post by trailofdead on 2009-07-13
I gave in and installed Opera 10 beta.  Flash 10 works in Opera 10 beta, but my original problem with 9.64 isnt solved.

---

