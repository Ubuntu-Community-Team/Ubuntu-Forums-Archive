---
title: "How to view webpages without pictures"
date: 2010-01-28
forum: General Help
---

### Post by O-pos on 2010-01-28
Hello,

I was wondering if there is a way to view webpages as a text only, without images, flash ads, huge colorful font, etc.. I need a minimalistic way of viewing the information I need to read, especially in the air plane or at work. 

Any ideas?

I would prefer not to use terminal-based viewers. The best would be something with firefox.

Thanks a lot

---

### Post by Leppie on 2010-01-28
isn't it easier to install a text browser? shouldn't occupy much disk space.
try something like elinks, lynx, netrik. have a look here: [http://packages.ubuntu.com/karmic/www-browser](http://packages.ubuntu.com/karmic/www-browser)

---

### Post by Vaphell on 2010-01-28
maybe firefox with noscript (one of the big offenders, pages tend to run dozens of worthless datamining jscripts) flashblock (flash the biggest offender of all) and some adblock filters for removing multimedia types? there is a problem though as you don't know if the gifs or pngs are crucial or not (navigation elements etc)
if your low bandwith mode is related to some defined set of webpages you can certainly tailor them perfectly to your low transfer speed needs using the combination of those three.

---

### Post by x33a on 2010-01-28
open firefox preferences -> content; uncheck load images automatically.

maybe this extension could also help:

[https://addons.mozilla.org/en-US/firefox/addon/232](https://addons.mozilla.org/en-US/firefox/addon/232)

though, i also would opt for a text mode browser for such experience.

---

### Post by goldencako on 2010-01-28
You could take it a step further and remove java and install adblock.

---

### Post by O-pos on 2010-01-28
Thanks guys for so many replies.

I cannot install anything on my work computers - no privileges. Also, I work on multiple computers during the day. Sometimes I have to use mircosoft internet explorer. So I want to use existing web browser to browse online content in one fixed font without all this trash and popups.

---

### Post by Leppie on 2010-01-28
are the machines linux or windows based, or both?

if it's only one type of system, put a browser on a usb stick.

---

### Post by O-pos on 2010-01-28
They are all windows. And I just found that internet settings cannot be changed (I mean unchecking to load images automatically etc..)

---

### Post by O-pos on 2010-01-28
Is it possible to write some kinf of command in the address field before the actual address and this way filter the content?

---

### Post by Overcast32 on 2010-01-28
There are a number of firefox add-ons that can keep images from loading. 

Search the add-ons for "Inline blocked image view" or "ImageBlock", I use those two together as one can outright block all images and the other does something else.. lol, sorry I forget, but they kinda work together a bit. I use it because I RDC into my PC from a remote spot sometimes and it speeds up browsing tremendously.

AdBlock can do the same - for flash as well.

---

### Post by Alex Libman on 2010-01-28
Maybe a text-only proxy like via [proxify.com]("http://proxify.com/") would be an ideal solution?

---

### Post by O-pos on 2010-01-28
proxift.com looks great. Particularly, its text only option. Unfortunately, "text only" still allows different colors and backgrounds, and oversized font, but much better to browse with it than without

---

### Post by adam814 on 2010-01-28
I think the OP means the Group Policy on the domain at work prohibits changing anything under Internet Options.  I'm guessing that includes proxy servers.  Without Administrator privileges on Windows there's likely no installing another browser to circumvent it.

You *might* be able to get away with running Firefox Portable from [http://portableapps.com]("http://portableapps.com")

---

### Post by O-pos on 2010-01-28
proxify.com is the best option so far because sometimes even USB access is blocked on some computers.

---

### Post by adam814 on 2010-01-28
I'd actually agree, I hadn't looked at proxify.com before.  As long as an overzealous sysadmin doesn't block the site that's probably the way to go.

Of course if that does happen and USB access isn't blocked there's another option.

---

### Post by O-pos on 2010-02-04
I found what I was looking for: [www.textise.net](www.textise.net) shows only the text of all the images.

---

### Post by Leppie on 2010-02-04
> **O-pos said:**
> I found what I was looking for: [www.textise.net]("http://www.textise.net") shows only the text of all the images.
an online text browser?

---

