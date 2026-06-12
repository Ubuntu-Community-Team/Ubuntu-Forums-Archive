---
title: "Flash trouble in Firefox AND Opera"
date: 2009-07-27
forum: General Help
---

### Post by nandnor on 2009-07-27
In firefox, flash works fine, except maximizing it(ie like in a youtube video full screen) causes firefox to crash. In opera, flash doesnt work, just shows a white blank in place of the flash object even when plugin is installed and visible in opera plugins menu.

Tried reinstalling opera, deleting, reinstalling flash, didnt help.
H E L P!!!!

---

### Post by nandnor on 2009-07-27
up

---

### Post by iNaitvad on 2009-07-27
did you manually installed flash?

---

### Post by TDurden1937 on 2009-07-27
You might try using WINE to install the Windo$e version of Firefox and Flash Player. I couldn't get screwattack.com flash player to work until I did this. Now it works . . . but with a not too annoying flicker at the bottom half of the video . . . but at least it works.

I you have questions about how to do this ask with a reply or send me a PM and I'll walk you through it. It is really easy.

---

### Post by LexMortis on 2009-07-27
I couldnt get flash to get to work in Opera 9.6, even though it found the plugin. Tried numerous settings and tweaks, but nothing..

It does (albeit laggy) in Opera 10b. Perhaps try 10b / latest 10 snapshots.
Those can be found at [http://deb.opera.com](http://deb.opera.com)

---

### Post by nandnor on 2009-07-27
Installed flash both ways, manually dragging the .so file to /usr/lib/mozilla/plugins and auto with the .deb file. flash works with windows firefox version through wine but thats pretty messed up to not use native app when its available.. :)

---

### Post by moster on 2009-07-27
Stop borking your installation. :) Answer is here.
[http://ubuntuforums.org/showthread.php?p=7487421](http://ubuntuforums.org/showthread.php?p=7487421)

In short you have to add ```
LD_PRELOAD=/usr/lib/libGL.so.1 firefox-3.6
```  If you get lost then tell me exact firefox version and we will find it together.

---

### Post by TDurden1937 on 2009-07-27
> **nandnor said:**
> Installed flash both ways, manually dragging the .so file to /usr/lib/mozilla/plugins and auto with the .deb file. flash works with windows firefox version through wine but thats pretty messed up to not use native app when its available.. :)

Absolutely . . . I agree. I was desperate to watch Angry Video Game Nerd on screwattack.com . . . lol. So I stooped to the level of installing a Windoze version of Firefox.

Later I think in this thread is the right way to do it using the command line to indicate the libGL.so.1 to Firefox. i didn't see that. Much more elegant a solution than mine. Maybe that flicker will go away.

---

