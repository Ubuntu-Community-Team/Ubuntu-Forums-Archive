---
title: "Problems with dosbox emulator (up, down, left &amp; right)"
date: 2009-08-25
forum: General Help
---

### Post by colobix on 2009-08-25
Hey.
The arrow keys up, down, left and right doesnt work in dosbox which makes the emulator very useless for gaming. How do I fix this problem? or is there any other dos emulators available?

---

### Post by StooJ on 2009-10-09
From [http://ubuntuforums.org/showpost.php?p=6724643&postcount=3](http://ubuntuforums.org/showpost.php?p=6724643&postcount=3)

> **cdEWoozy said:**
> From dosbox.com:

> 
If you are running DOSBox on Ubuntu 8.10 (or some other distro that uses the evdev driver in X) you will notice that some keys don't work, most noticiable the arrow keys.

This is because Ubuntu changed something related to the scancodes, we are working on it, but as none of us runs Ubuntu 8.10 it is not top priority. If you have an English/American keyboard layout then (and only then!) you can use the following workaround. Open a console and enter the following command:
echo -e "[sdl]\nusescancodes=false\n" >>~/.dosboxrc
We will have it fixed in the next version though.



---

