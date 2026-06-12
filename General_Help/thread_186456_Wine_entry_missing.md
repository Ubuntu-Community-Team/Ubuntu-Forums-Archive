---
title: "Wine entry missing"
date: 2006-06-02
forum: General Help
---

### Post by castusalbuscor on 2006-06-02
SO I got the book "Beginning Ubuntu Linux from Novice to Professional" by Keir Thomas.

And I tried to install Wine, I followd the procedure word for word but I cant find winetools.

What I did

I went to system>Administration>Synaptic Package Manager. Clicked Settings>Repositories

Clicked Add, then custom button then typed:
```
deb http://wine.sourceforge.net/apt/ binary/
```

Then clicked Add repository button

I searched for Wine and I found it, but it seems I need Winetools which I cant find.

Any help would be nice.

Thanks

---

### Post by RAOF on 2006-06-02
From what I've read, the Wine devs don't like people using winetools (it installs a **whole lot** of unnecessary stuff, and makes it more difficult to improve wine).  It's not necessary to use winetools anyway - you can run "winecfg" to set up wine's settings.

---

### Post by castusalbuscor on 2006-06-02
But it is possible to download winetools? if so where do I get it from?

And how similar is winecfg to winetools?

---

### Post by DaveRowell on 2006-06-02
I would suggest forgetting 'winetools'.  It's old stuff.

Install 'wine'.
Then in a terminal just type 'winecfg'
You'll get a tabbed window with your configuration choices but most importantly your '.wine' folder will be set up where and as 'wine' expects it.  You can change anything necessary - probably nothing.

---

### Post by castusalbuscor on 2006-06-06
Thanks it worked. Winamp works, though I havent tried to play anything on it...
Thanks for the help

---

### Post by msak007 on 2006-06-06
Seeing as nobody answered your original question, WineTools can be downloaded [here]("http://www.von-thadden.de/Joachim/WineTools/"). I've used it before and find it useful, but there are other ways to do what you wanted as suggested in earlier posts. Looks like you got it working already though so this is just for your info.

---

