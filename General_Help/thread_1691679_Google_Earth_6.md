---
title: "Google Earth 6"
date: 2011-02-20
forum: General Help
---

### Post by TheRevS on 2011-02-20
Howdy good people!

I just installed Google earth 6 on Ubuntu, and I get this weird problem... The program doesn't display text correctly as shown in the image below.

So I wonder if I'm just missing some library ? I would appreciate your help please! thanks.

---

### Post by TheRevS on 2011-02-20
a little bump! :popcorn:

---

### Post by Vaphell on 2011-02-20
i had similar screwup and it went away when i uninstalled msttcorefonts. No idea why that happens though.

---

### Post by emarkay on 2011-02-21
See: [http://ubuntuforums.org/showthread.php?t=1677610](http://ubuntuforums.org/showthread.php?t=1677610)

---

### Post by IWantFroyo on 2011-02-21
Have you run the following:
> sudo apt-get lsb-core?
It will most likely fix it.

---

### Post by Wtower on 2011-02-21
As Vaphell and emarkay suggested, ttf-mscorefonts-installer will do the trick.

---

