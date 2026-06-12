---
title: "What is the best, most resource friendly way to take a screenshot?"
date: 2011-12-31
forum: General Help
---

### Post by birdfoot on 2011-12-31
...in Lubuntu? :confused:

---

### Post by haqking on 2011-12-31
> **birdfoot said:**
> ...in Lubuntu? :confused:

press the PrtScn Key which works in almost anything

---

### Post by nothingspecial on 2011-12-31
If you press prt sc you will have a screenshot in your home directory.

---

### Post by Rodney9 on 2011-12-31
[http://ubuntuforums.org/showpost.php?p=11547661&postcount=358](http://ubuntuforums.org/showpost.php?p=11547661&postcount=358)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by andrew.46 on 2011-12-31
I believe that using Print Screen (under Lubuntu) is using scrot, pretty resource friendly...

---

### Post by MG&amp;TL on 2011-12-31
Scrot is pretty good, if you're thinking of programming.

```
sudo apt-get install scrot #not necessary in Lubuntu
man scrot
``` 

Or if not, if you add the Lubuntu desktop PPA, you can get lxscreenshot, very easy, light GUI.

---

### Post by andrew.46 on 2012-01-02
You may be interested in my standard full-screen + resize screencapture using scrot:

```

scrot -d 5 -q 100 '%Y.%m.%d.png' \
      -e 'convert $f -resize 800x600 $f'

```

The -d option gives a delay in seconds, the -q option manipulates the quality of the output image ((default 75), and the convert command (using imagemagick) resizes the capture.

This is a pretty basic usage but I am a pretty basic sort of guy :).

---

