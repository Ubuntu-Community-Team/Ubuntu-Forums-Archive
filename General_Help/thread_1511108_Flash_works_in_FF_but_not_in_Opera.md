---
title: "Flash works in FF but not in Opera"
date: 2010-06-16
forum: General Help
---

### Post by Lockheed on 2010-06-16
Lucid, 64bit.

I could hear sound, but flash window was purely black in Opera, not evern controls on youtube. Mizuri, Firefox, Chrome all played flash content well.

So, I installed FireFox addon that automatically updates to newest flash version. It updated to the newest flash (but 32bit) and now flash still plays fine in FireFox but behaviour in Opera did not change, instead it broke Midori, which is just showing a blue brick, which I am guessing means "missing plugin".

---

### Post by oracle2b on 2010-06-16
try uninstalling and reinstalling opera, sudo apt-get purge opera. Then install by typing, sudo apt-get install opera.

---

### Post by Lockheed on 2010-06-16
Thanks, but it didn't help.

---

### Post by xefix on 2010-06-16
Don't you have to install the flash plugin separately for every browser? Try going to Opera's or Adobe's website and seeing if they have the Linux/Opera flash plugin available. If I remember correctly from having the same problem months ago, I had to get this plugin from one of those two websites.

---

### Post by Lockheed on 2010-06-16
No, Opera always used FF's flash plugin.

---

### Post by xefix on 2010-06-16
Opera's docs
[http://www.opera.com/docs/linux/plugins/install/](http://www.opera.com/docs/linux/plugins/install/)

---

### Post by elespejo on 2010-06-16
Open Opera and go to menu>settings> preferences> advanced> contents> plugin options> change path> add, then find libflashplayer.so, most likely in /home/yourname/.mozilla/plugins. Not sure about the default plugins location though - I downloaded libflashplayer 64 bit manually and put it there myself.

---

### Post by Lockheed on 2010-06-16
Nope, no joy.

---

### Post by Lockheed on 2010-06-18
I discovered, that it is only youtube that does not work. Other flash content does work in Opera

---

### Post by PinchedNerve on 2010-06-18
If you installed version 10.10, download beta version 10.60. I believe that version works normally

---

### Post by oracle2b on 2010-06-20
Try changing the browser agent to "Identify as firefox" by right clicking on youtube's page and selecting site preferences-->Network.

---

