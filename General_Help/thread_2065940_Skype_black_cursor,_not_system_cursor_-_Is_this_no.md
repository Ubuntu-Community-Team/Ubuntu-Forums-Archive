---
title: "Skype: black cursor, not system cursor - Is this normal?"
date: 2012-10-03
forum: General Help
---

### Post by MrsUser on 2012-10-03
Just installed Skype via terminal on a fresh install of Ubuntu 12.04.1. After starting Skype, I noticed that the mouse cursor changes to black when I hover over Skype's app window. Is this normal?

Somehow I wonder if something went wrong while installing this. In terminal I observed a lot of i386 stuff being installed. And I wondered, because I run 64-bit. Maybe Skype installed the wrong 32-bit version instead of 64-bit?

By the way, how can I find out if the Skype I run is 32-bit or 64-bit? In 'About' it says nothing about this.

EDIT:
Ok, strange. The black cursor is gone. After having installed more software, it is now gone. Perhaps Skype was missing some library still. At least, on a fresh install of Ubuntu 12.04, Skype has a black cursor. Don't know what the problem there was.

---

### Post by poomerang on 2012-10-07
I had the same problem, but it didn't solve automatically after restart.
However, manually installing the package "libxcursor1:i386" (sudo apt-get install libxcursor1:i386) did the trick
Skype is still unable to detect the desktop theme and uses the default cleanlooks theme, but I'm confident I'll find another package that fixes that too

---

