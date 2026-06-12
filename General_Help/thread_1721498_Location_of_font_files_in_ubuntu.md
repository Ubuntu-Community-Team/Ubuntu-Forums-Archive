---
title: "Location of font files in ubuntu"
date: 2011-04-04
forum: General Help
---

### Post by ntesla123 on 2011-04-04
Where are the font files located in ubuntu? I have installed truetype fonts in ubuntu, but I don't know the location of the font files.

---

### Post by lithopsian on 2011-04-04
Font files are all over the place!  The prime location is in directories under /usr/share/fonts but there are utilities, caches, and stuff all over including in your user profile.  X or various font library utilities will bring them all together at run time.

---

### Post by AlphaLexman on 2011-04-04
There are both user fonts and system fonts. Which are you looking for?

---

### Post by coffeecat on 2011-04-04
System-installed ttf fonts in /usr/share/fonts/truetype. User fonts in /home/username/.fonts.

---

### Post by Dry Lips on 2011-05-16
> System-installed ttf fonts in /usr/share/fonts/truetype. User fonts in /home/username/.fonts.    Where did my user font directory go?  I can't find any folder named
/home/myusernamehere/.fonts. Have they changed this in 11.04?
There is, however, a directory named /home/myusernamehere/.fontconfig
that is used for some kind of cache files.

---

### Post by coffeecat on 2011-05-16
> **Dry Lips said:**
> Where did my user font directory go?  I can't find any folder named
/home/myusernamehere/.fonts. Have they changed this in 11.04?
There is, however, a directory named /home/myusernamehere/.fontconfig
that is used for some kind of cache files.

It didn't go anywhere. You have to create it yourself, or it will be created for you if you simply double-click on a .ttf file, which is the easiest way to install ttf fonts.

---

### Post by Dry Lips on 2011-05-16
duh! #-o


Thanks a lot coffeecat! :)

---

### Post by coffeecat on 2011-05-16
You're welcome. :)

---

