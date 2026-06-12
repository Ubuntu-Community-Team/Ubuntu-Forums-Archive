---
title: "Best Terminal Font"
date: 2012-09-26
forum: General Help
---

### Post by Mooh Bear on 2012-09-26
I have tried several monospace fonts for the terminal and for programming, but the best by far is the old "Screen" font from SGI (see sample below).

It is a bitmapped font that comes in all point sizes in the range from 7 to 18. Even at the smallest sizes it is amazingly readable. If you are a fan of small fonts, you can routinely use it at 9 or 10.

Ubuntu 12.04 has support for bitmapped fonts disabled by default, unfortunately. The following steps will get you the font installed.

Download the font from [http://scribusstuff.org/content/show.php/SGI+Screen+Fonts?content=103348](http://scribusstuff.org/content/show.php/SGI+Screen+Fonts?content=103348)

Unzip it and remove an extraneous file:
```
tar xzvf 103348-sgi.tgz
rm sgi/Scr15.pcf
```Move the fonts to the common fonts directory:
```
sudo mv sgi /usr/share/fonts/
```Enable bitmapped fonts:
```
cd /etc/fonts/conf.d
sudo rm 70-no-bitmaps.conf
sudo ln -s ../conf.avail/70-force-bitmaps.conf .
sudo fc-cache -fv
```In your applications look for the font called "Screen". That's it, enjoy!

In case you change your mind later, here is how to reverse the changes you made:
```
cd /etc/fonts/conf.d
sudo rm 70-force-bitmaps.conf
sudo ln -s ../conf.avail/70-no-bitmaps.conf .
sudo rm -r /usr/share/fonts/sgi
```[IMG]https://dl.dropbox.com/u/60111571/sgi-screen.gif[/IMG]

---

### Post by HiImTye on 2012-09-27
I like Ubuntu Mono 9, it's very readable and just the right size on a 22" 1080p display

---

### Post by jerrrys on 2012-09-27
That is a nice front :)

---

### Post by oldos2er on 2012-09-27
I like Terminus.

---

### Post by Slim Odds on 2012-09-27
Adobe just released a free font called "Source Code Pro". It looks pretty good. I haven't tried it on my linux machine yet.

News here: [https://blogs.adobe.com/typblography/2012/09/source-code-pro.html](https://blogs.adobe.com/typblography/2012/09/source-code-pro.html)

Download here: [http://sourceforge.net/projects/sourcesans.adobe/](http://sourceforge.net/projects/sourcesans.adobe/)

---

### Post by matt_symes on 2012-09-27
> **oldos2er said:**
> I like Terminus.

I would +1 this font. The nicest i have ever used in the command line.

---

### Post by Gerie Langeveld on 2012-09-28
Thanks for the instructions.
I like this font.

---

### Post by Statia on 2012-09-28
Droid Sans Mono looks pretty good too.

---

