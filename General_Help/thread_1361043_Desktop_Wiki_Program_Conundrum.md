---
title: "Desktop Wiki Program Conundrum"
date: 2009-12-21
forum: General Help
---

### Post by Kozar on 2009-12-21
I'm looking to make a personal wiki-type database on my computer to keep track of a wide array of information from projects to school notes to just a ton of misc information about my life to feed my ocd personality traits. I don't plan on having this be online, just on my computer.

I know there are programs specialised for this, like zim, that seem to be only text based. But I just don't know how to proceed. Should I keep searching for something like that or can I download a type of wiki engine and just run it on my desktop? I just want something that will behave in the same manner as the wikipedia sites do. Out of ideas, please help.

---

### Post by lykwydchykyn on 2009-12-21
There's no reason you can't install a LAMP server on your desktop and just run mediawiki, if you want it to be just like wikipedia.

See instructions here: [https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

---

### Post by Kozar on 2009-12-21
Ok I put in the code to install the lamp server and got this

```
desktop:~$ sudo tasksel install lamp-server
tasksel: aptitude failed (100)
```

---

### Post by jrothwell97 on 2009-12-21
It sounds like MediaWiki is overkill for this situation: you may find that using Tomboy, or Microsoft OneNote or Evernote under WINE, may be a more appropriate solution.

---

### Post by nixclusive on 2009-12-21
Or perhaps you can use [BasKet Note Pads](http://basket.kde.org/) for simpler setup.

---

### Post by lykwydchykyn on 2009-12-21
> **Kozar said:**
> Ok I put in the code to install the lamp server and got this

```
desktop:~$ sudo tasksel install lamp-server
tasksel: aptitude failed (100)
```

Does aptitude work otherwise, I mean can you do:
```

sudo aptitude update && sudo aptitude upgrade

```

---

