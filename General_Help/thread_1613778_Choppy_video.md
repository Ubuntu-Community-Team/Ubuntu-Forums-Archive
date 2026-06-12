---
title: "Choppy video ?"
date: 2010-11-04
forum: General Help
---

### Post by grahamz on 2010-11-04
I have Ubuntu 10.04 fresh install, when i watch you tube or other vids it gets real choppy in full screen, being new I have no idea what to do. 

Thanks in advance....

J

---

### Post by Foxheadz on 2010-11-04
Do you have the right drivers for you graphics processor?

---

### Post by grahamz on 2010-11-04
I belive so how do i check that in ubuntu im lost lol

---

### Post by Foxheadz on 2010-11-04
It skips my mind right now but you can just Google it

---

### Post by luisito on 2010-11-04
I want to believe it is not because of your internet connection.

For the drivers, go to Administration/Additional drivers. In case that there are better drivers available, they will appear there.

Flash video is particularly choppy on Linux if you run it on old computers. The reason is that Adobe decided not to use the xv video extensions. Supposedly, it is accelerated with OpenGL, but all the acceleration gets turned off if compiz is on. You can set up youtube to use html5 instead of flash and it may work better for you in some browsers (try it on Chromium).

---

### Post by lovinglinux on 2010-11-04
> **luisito said:**
> I want to believe it is not because of your internet connection.

For the drivers, go to Administration/Additional drivers. In case that there are better drivers available, they will appear there.

Flash video is particularly choppy on Linux if you run it on old computers. The reason is that Adobe decided not to use the xv video extensions. Supposedly, it is accelerated with OpenGL, but all the acceleration gets turned off if compiz is on. You can set up youtube to use html5 instead of flash and it may work better for you in some browsers (try it on Chromium).

+1

Additionally make sure you have the latest version of flash from Adobe and not the alternatives.

These might help you solve you problem:

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by grahamz on 2010-12-16
Thanks ! it has helped doing the addons. .

---

