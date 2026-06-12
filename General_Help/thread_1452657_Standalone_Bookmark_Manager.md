---
title: "Standalone Bookmark Manager"
date: 2010-04-12
forum: General Help
---

### Post by EMCGFX on 2010-04-12
I'm looking for standalone bookmark manager, firefox bookmark manager is slow when you have thousands of bookmarks. I found php-based bookmark scripts but no good software bookmark manager for Ubuntu. Any help is appreciated. Thank you.

---

### Post by kellemes on 2010-04-12
Maybe not what you want..
Couple of years ago I've found [Delicious]("http://delicious.com/"), never looked any further!

---

### Post by EMCGFX on 2010-04-12
Thank you, kellemes. The Delicious is good online service. But I'm looking for **software** that runs on Ubuntu.

I've just found "WebMarX" @ Softpedia it might be what I need. If you know any other, please share here :-)

---

### Post by EMCGFX on 2010-04-12
WebMarX is the best one I found so far, that does the job. :P Unfortunantly deb package for ubuntu is not working properly, you need to install from source. Which is not that big of a deal.

```
How to install WebMarX from source:
1. Download source package from;
http://linux.softpedia.com/get/Utilities/WebMarX-44978.shtml

2. tar xvf WebMarX-1.0.src.tar.gz

3. cd WebMarX-1.0.src

4. ./setup.py build

5. sudo ./setup.py install
```

In case some one else wants to use this too :)

---

### Post by VCoolio on 2010-04-12
You don't need sudo in step 4 (it will change permissions on the files, so better leave it out); otherwise thanks for the tip.

---

### Post by EMCGFX on 2010-04-12
> **VCoolio said:**
> You don't need sudo in step 4 (it will change permissions on the files, so better leave it out); otherwise thanks for the tip.

Yeah, I noticed that too ;-) Thanks.

---

### Post by lovinglinux on 2010-04-12
Have you tried to to optimize your bookmark database file? I don't know how many bookmarks I have, but I have a lot (at least a couple hundred) and Firefox deals with them pretty fine.

See [[COLOR="Sienna"]**Database Optimization**[/COLOR]](http://www.webgapps.org/firefox/database-optimization) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by EMCGFX on 2010-04-12
Firefox works ok if you don't re-arrange your bookmarks. Ones I start moving bookmarks from one folder to the other, its very slow. Try selecting 20 bookmarks and move it to another folder, you will see what I mean. I found another solution, I'm using Opera browser for all my bookmarks now. It works very fast when I organize them there.

---

### Post by lovinglinux on 2010-04-12
> **EMCGFX said:**
> Firefox works ok if you don't re-arrange your bookmarks. Ones I start moving bookmarks from one folder to the other, its very slow. Try selecting 20 bookmarks and move it to another folder, you will see what I mean. I found another solution, I'm using Opera browser for all my bookmarks now. It works very fast when I organize them there.

Moving bookmarks is one of the things that make the database slow. You just need to optimize it of you do a lot of moving or deleting. I just moved more than a hundred bookmarks (with tags) and it wasn't slow. Obviously, that is not instant, since it is an sqlite operation, but the browser itself doesn't freeze and it takes only a couple of seconds to see all the bookmarks disappear. Looks like the Bookmark manager first add them to the new location (you see a counter) and then delete them from the current location.

Anyway, if Opera works for you, then go for it.

---

### Post by EMCGFX on 2010-04-12
Yes Opera seems to work very good for me for bookmarks. What I will probably do is, organize all my bookmarks there then export it and import it in Firefox :lolflag: But I'm impressed how far Opera moved from version 9 since I've last used it. The new Unite feature is amazing, is there something like that in Firefox ?

---

### Post by lovinglinux on 2010-04-12
> **EMCGFX said:**
> But I'm impressed how far Opera moved from version 9 since I've last used it. The new Unite feature is amazing, is there something like that in Firefox ?

I'm glad no :)

But there are countless extensions for doing what unite does. Besides, that service is a copyright claim time bomb :)

---

### Post by kellemes on 2010-04-13
> **lovinglinux said:**
> I'm glad no :)

But there are countless extensions for doing what unite does. Besides, that service is a copyright claim time bomb :)

What isn't these days..

---

### Post by EMCGFX on 2010-04-28
@kellemes, +1 :lolflag:

---

