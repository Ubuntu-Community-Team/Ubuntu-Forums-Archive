---
title: "Why is this booting to command line????"
date: 2009-12-08
forum: General Help
---

### Post by forsaken_pariah on 2009-12-08
I recently installed Karmic Koala (fresh install) and so far have been having nothing but problems with it. Most of them I've been able to fix, but the last one has me stumped.... Every other time or so that I boot my computer, it boots to a command line (no X) asking for my login. Sometimes if I wait for 5-10 minutes it'll start X, and sometimes it won't, but every time I log in and run startx from the command line, it works for a couple minutes and the screen goes black and I can do nothing but reset the computer, at which time everything boots normally again.

Plz help, this is very frustrating....


thx in advance

Kory X.

---

### Post by 3Miro on 2009-12-08
The next time it happens, go to the command line and type:

```

cat /var/log/Xorg.0.log

```

It will read the file /var/log/Xorg.0.log and some information will hopefully show there. You can also try /var/log/Xorg.0.log.old

I don't know if I will be able to help, but if you post the content of the log, some of the more experienced people might.

---

### Post by forsaken_pariah on 2009-12-11
[LEFT]Ok so I tried that last time but before I got a chance to redirect it to a file, X started. However, I did get a chance to look at it long enough to tell it pretty much looked normal. I think the problem I'm having must be coming up before X ever loads...

Any help please?
[/LEFT]

---

### Post by fancypiper on 2009-12-11
Run the gnome-system-log (System>Administration>Log File Viewer) and examine Xorg.0.log, dmsg and messages for any clues.

Also, examine /home/<user>/.xsession-errors

---

### Post by forsaken_pariah on 2009-12-13
I think I found the pause in the messages file, but I still don't know what's causing it....

```
Dec 13 15:00:17 karmic-koala kernel: [   24.725677] usplash:356 freeing invalid memtype ffffffffc8000000-ffffffffc9000000
Dec 13 15:01:16 karmic-koala kernel: [   84.190027] Clocksource tsc unstable (delta = -159083305 ns)
```

---

### Post by john newbuntu on 2009-12-14
Make sure you have all updates using the update manager.

---

### Post by fancypiper on 2009-12-14
It will probably be fixed with the next kernel update.

[Google search results]("http://www.google.com/search?q=Clocksource+tsc+unstable+%28delta+%3D+-159083305+ns%29&x=0&y=0")

---

