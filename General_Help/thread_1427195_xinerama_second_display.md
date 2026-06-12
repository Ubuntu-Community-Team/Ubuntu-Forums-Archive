---
title: "xinerama second display"
date: 2010-03-11
forum: General Help
---

### Post by sharpdust on 2010-03-11
So I've got xinerama working just fine. I have a question. I understand that xinerama treats dual monitors as if they were one single monitor, but is there a way for it to tell which window is on which screen?
Like I want to boot an application on my second monitor, but this command:
```
setenv DISPLAY ${HOST}:0.1
```
says 
```
xdpyinfo:  unable to open display "beryllium:0.1".
```
which makes sense because xinerama doesn't know what the second display is. I was just wondering if there was some other way to get around this? I feel like there should be since it can snap windows when it gets close to the edge of a monitor.

Thank you so much for you time.

---

### Post by Intrepid Ibex on 2010-03-11
The message means that xdpyinfo can't find your display (beryllium:0.1). It in itself has nothing to do with video editing apps like xinerama. Also the term "display" should not be confused with the term "monitor". In Unix world the term "display" simply means a connection between an X client and an X server.

---

### Post by sharpdust on 2010-03-11
> **Intrepid Ibex said:**
> The message means that xdpyinfo can't find your display (beryllium:0.1). It in itself has nothing to do with video editing apps like xinerama. Also the term "display" should not be confused with the term "monitor". In Unix world the term "display" simply means a connection between an X client and an X server.

Uhh...I think you may be confused. xinerama is not a video editing app.
And I understand the difference between a display and monitor. I guess the correct term would be screen since that's what they're called in the xorg.conf file.

So basically, how would I do something like setenv SCREEN $HOST:0.1?

Quick example (xinerama not enabled):

setenv DISPLAY ${HOST}:0.1
xterm

Will launch xterm on the second screen. How can I do the same thing with xinerama enabled?

Thanks

---

### Post by sharpdust on 2010-03-11
bueller...

---

