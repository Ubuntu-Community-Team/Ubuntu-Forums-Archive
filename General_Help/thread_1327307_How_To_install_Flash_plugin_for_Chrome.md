---
title: "How To install Flash plugin for Chrome?"
date: 2009-11-15
forum: General Help
---

### Post by patrickpdk on 2009-11-15
I found these extremely well written directions for enabling flash in Chrome:

[http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2](http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2)

And they dont work!

The plugin is in the path specified by the instructions:
[INDENT]patrick@ubuntu:/opt/google/chrome/plugins$ ls
libflashplayer.so
[/INDENT]

Right click on my chrome launcher and the "command" field has:
[INDENT]/opt/google/chrome/google-chrome --enable-plugins %U[/INDENT]

Yet even so, no luck...

---

### Post by Romanrp on 2009-11-15
I installed ubuntu restricted extras.
Then a few days later I downloaded chrome.
Flash worked fine .If you install flash for mozilla ,it should work with chrome.
Btw i have 64bit so it is a mirracle that flash works.

sudo apt-get install ubuntu-restricted-extras

you shouldn't reaaly have to do anything fancy.
are you 32 or 64bit?
and make sure you uninstall existing flash.

---

