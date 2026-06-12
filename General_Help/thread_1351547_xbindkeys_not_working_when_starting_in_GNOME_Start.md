---
title: "xbindkeys not working when starting in GNOME Startup Applications"
date: 2009-12-10
forum: General Help
---

### Post by nunovi on 2009-12-10
Hi,

I've installed xbindkeys to map my multimedia keys to VLC in Karmic. The script is working fine when I launch it on a terminal window. I'm using the default location so I just execute xbindkeys. In order to have this launched automatically, I've created an entry on startup applications, so it's launched automatically when ubuntu starts up.
I can see xbindkeys is launched successfully in the System Monitor but there's no reaction to the keypresses. In a terminal window I run xbindkeys -s and I get the correct mappings. If I then launch xbindkeys again from the terminal, everything works fine. 

It seems for some reason when xbindkeys is launched from the startup applications it doesn't receive any of the keyboard events.

I've searched in the forums for hours but couldn't find any solution for this.

Anybody has any ideas on how to solve/troubleshoot it? It's driving me nuts.

Thanks,

Nuno

---

### Post by Pimterry on 2009-12-10
Yeah, I have this exact problem too. No idea why! I'm fairly sure it didn't happen when I used xbindkeys before, about a year back...

---

### Post by nunovi on 2009-12-11
Well, I'll wait a bit to see if anyone has any ideas otherwise I'll file a bug report.

Nuno

---

### Post by loloboho on 2009-12-11
I use xbindkeys all the time and it was working last week. Now nada, zip when I press a configured key.

I run Linux Ubuntu release 8.04 (hardy) with kernel 2.6.24-26.28 and gnome 2.22.3

System Monitor says the process is running and I get the correct mappings too like nunovi. 

But unlike nunovi, it still does not work when launched in the terminal for me.

Since I upgraded the kernel on 12/06/09, I booted the old one, 2.6.24-25, but with the same problem. Xbindkeys worked with the old kernel in the past but not now so I guess it is not a kernel problem. Could it be some other upgrade package?? I am running Hardy and numovi is running Karmic.

UPDATE:

I just remembered I installed VLC Media Player this week!! I did not map any keys specifically to VLC but VLC is a common factor with nunovi. Related??

Robert

---

### Post by nunovi on 2009-12-13
Have you tried starting xbindkeys in a terminal window in verbose mode and see if the keys are detected?
 
```
xbindkeys -v
```

---

### Post by loloboho on 2009-12-14
Yes, from the terminal: xbindkeys -v
All my configured keys in /home/robert/.xbindkeysrc are detected but the keystrokes are not echoed.

I also installed the latest xbindkeys version 1.8.3 from savannah.org (and compiled from source):
[http://www.nongnu.org/xbindkeys/xbindkeys.html#download](http://www.nongnu.org/xbindkeys/xbindkeys.html#download)
but still the same problem.

It seems that the mechanism for actually binding the keys in the looping process is not working. I don't understand how that works but it may be that xbindkeys is doing its job and the problem is with one of the dependencies or something more elemental.

I also uninstalled VLC Media Player but that didn't help either. It must be related to an update or package I installed this last week because it worked fine before that.

Robert

---

### Post by loloboho on 2009-12-24
I found my problem. As I suspected, the cause was not with xbindkeys.

The problem was that the program xvkbd got uninstalled somehow (during an update)??  All the action commands I had given xbindkeys were using xvkbd to send key commands to the active window (gnome). Without the xvkbd program nothing happened when I pressed the keys, duh.

I installed xvkbd again and everything works. (Somehow the new xvkbd was a little different and I had to modify my commands.)

Thanks
Robert

---

