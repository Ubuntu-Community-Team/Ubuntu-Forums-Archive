---
title: "Text based web browser while in console mode?"
date: 2006-04-15
forum: General Help
---

### Post by infiniti029 on 2006-04-15
Read the title ^

And if so, how do you use it?

I've used "links google.com" in Fedora, so I was wondering if Ubuntu had something similar.

---

### Post by Mustard on 2006-04-15
Sure.  You could install links from the repositories.  I found a 'links' and a 'links2'.  I'm not sure what the differences are between them.

You would use it just as you have described...

Open a terminal and type in ..

```
links http://google.com
```

---

### Post by infiniti029 on 2006-04-15
sudo apt-get links?

Dosn't work.

---

### Post by az on 2006-04-15
w3m is there by default.

w3m is lynx but with utf suport (I think)

---

### Post by Harold P on 2006-04-15
[QUOTE=infiniti029]sudo apt-get links?

Dosn't work.[/QUOTE]


sudo apt-get install links

Try that.

---

### Post by infiniti029 on 2006-04-15
it works, thanks.

Ahhh the wonders of text-based web browsing ;)

---

### Post by Mustard on 2006-04-15
I've just installed links2 to have a look at it.  It looks pretty good really.  I tried this option with links2...

```
links2 -g google.com
```

This opens up a graphical interface for the browser, not unlike any normal browser.

[quote=from the manual on]
**The -g option**

-g     Run  Links2  in  graphics mode. If not given, Links2 will run in text mode.  Running in graphics mode means that Links2 will probe all compiled&#8208;in graphics devices and run on the first found. If none  found,  links2 will not run in text mode. This option works only if &#8208;&#8208;enable&#8208;graphics was given to ./configure.
[/quote]

I just tried the -g option in the virtual terminal....eeewwww...what a mess. :)  Lots of blue lines and nothing readable.

---

### Post by nanotube on 2006-04-15
by the way, "elinks", which is also installable from the repositories, is a much more full-featured text-mode browser than links. it's great, give it a try. ;) ("sudo apt-get install elinks")

---

