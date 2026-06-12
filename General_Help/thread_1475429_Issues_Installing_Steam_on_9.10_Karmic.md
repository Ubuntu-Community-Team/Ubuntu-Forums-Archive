---
title: "Issues Installing Steam on 9.10 Karmic"
date: 2010-05-06
forum: General Help
---

### Post by bbqsauced on 2010-05-06
I followed a guide on installing steam for Ubuntu with Play on Linux here:

[http://www.linoob.com/2010/04/steam-platform-for-ubuntu/](http://www.linoob.com/2010/04/steam-platform-for-ubuntu/)

Everything seems to install alright.  When I run steam, it tries to update but never shows a progress bar and always stays at 0%.  If I let it run, it seems to "update" twice.  Afterwards, if I restart it, it just hangs in the panel and doesn't do anything.  If I click it, a tiny window in the middle of my screen appears in the workspace changer, but it doesn't actually appear in the workspace itself.  If I hit enter it just kills the program.

Any idea on how I can get this working?

---

### Post by evil_urna on 2010-05-07
> **bbqsauced said:**
> I followed a guide on installing steam for Ubuntu with Play on Linux here:

[http://www.linoob.com/2010/04/steam-platform-for-ubuntu/](http://www.linoob.com/2010/04/steam-platform-for-ubuntu/)

Everything seems to install alright.  When I run steam, it tries to update but never shows a progress bar and always stays at 0%.  If I let it run, it seems to "update" twice.  Afterwards, if I restart it, it just hangs in the panel and doesn't do anything.  If I click it, a tiny window in the middle of my screen appears in the workspace changer, but it doesn't actually appear in the workspace itself.  If I hit enter it just kills the program.

Any idea on how I can get this working?

I got a similar problem. mine just wont update

---

### Post by evil_urna on 2010-05-07
After endless dickery I got it to install and update.

Purge wine and reinstall just to be sure. Then Install via winetricks
```

wget http://kegel.com/wine/winetricks
sh winetricks steam
```

---

### Post by evil_urna on 2010-05-07
HA HA NEVERMIND!

it did not work after all. It updated and what not but it refused to actually go ahead and open all the way

---

