---
title: "flash cyrillic and Ubuntu"
date: 2010-02-27
forum: General Help
---

### Post by gabrielcik on 2010-02-27
Hola!

I have this issue: i can't write in Cyrillic inside my flash application:
[http://en.ukrlandia.com.ua/transliterator-ukrainian/](http://en.ukrlandia.com.ua/transliterator-ukrainian/)

I can't write if i type from keyboard. At the place of normal characters i get some strange ones.
If i use the virtual keyboard included in my program, it works properly.

How to solve this problem? (now i use Karmic, but this problem there was also in previous editions)

I think should be something about fonts, but i don't know exactly what to do.

any help? Thx!

---

### Post by Alexandre Putt on 2010-02-27
I don't know whether this is an Ubuntu issue, but would love to hear about a solution myself. Flash seems to be a crappy application, and I heard it also had some problems under Windows.

Here is a possible temporary solution:

[http://www.actionscript.org/forums/showthread.php3?t=223492]("http://www.actionscript.org/forums/showthread.php3?t=223492")

Alternatively, you may try complaining to Adobe.

---

### Post by gabrielcik on 2010-03-01
I asked Adobe... they don't give support for Linux for Flash Pro and for the Flash player they only give help for to install it.

So nothing.

---

### Post by Alexandre Putt on 2010-03-01
Are you developing it yourself? Try googling, I think there may be some workarounds. This appears to be an encoding problem. I have an impression it is also present under Windows (but can't confirm as I don't use it), so there should be generic solutions for that.

---

### Post by gabrielcik on 2010-03-01
Hola,

I made this small program about 1 year ago... on windows and mac it works without any particular issue. Only with Ubuntu doesn't display Cyrillic (and this not only with Karmic but at least also on Hardy).

---

### Post by Alexandre Putt on 2010-03-02
> **gabrielcik said:**
> Hola,

I made this small program about 1 year ago... on windows and mac it works without any particular issue. Only with Ubuntu doesn't display Cyrillic (and this not only with Karmic but at least also on Hardy).

Do Windows & your program use utf-8 by default?

---

### Post by gabrielcik on 2010-03-02
I use utf-8.

The funny thing is that if u type using the integrate keyboard inside my program, flash will display everything in perfect way... but if you try to digit directly from the keyboard of your pc, u get such characters: ÓÑÑÑ&#8224;Ñ&#402;Ñ&#8224;Ð²Ñ&#8249;Ð²Ñ&#8249;Ð°Ñ&#8249;Ð²Ð¿Ð° 

I will try to change the fonts inside my flash app and see what happen...

---

### Post by gabrielcik on 2010-03-02
I tried and nothing has changed...

Anyway seeking on the net i have found that this problem should be solved with the new release of flash player:
[http://labs.adobe.com/technologies/flashplayer10](http://labs.adobe.com/technologies/flashplayer10)

I don't know if it really works.

---

### Post by gabrielcik on 2010-03-02
I tried it, It really works!!!!!!!!! :)

remember to remove the previous version of flash and then install the beta one.
Extract (tar -zxvf) it on the directory .mozilla/plugins (create it if doesn't exist).

So thread solved:) 
Lets hope the definitive version will stay the same.

---

