---
title: "DVD help"
date: 2006-05-01
forum: General Help
---

### Post by madddonkey255 on 2006-05-01
I don't know if this is the DVD or totem but when I tried to play a movie(Off the Chain, pretty good documentary about the underworld of dogfighting) with totem the menu would come up but then when I clicked play it said "An error occurred audio device busy could another program be using it?" or something to that effect.  I tried this a few times, including right after I restarted, and it still would come up.  Then I tried to play it on my roomates DVD player and it was only black and white.  Then I ripped it using Acidrip and when it was finished it was fine, no trouble at all.  I'm guessing this DVD is unique but is there something I could do so that I can play the DVD?
Thanks,
Nolan

---

### Post by geek.de.nz on 2006-05-02
I had trouble like that with totem, mplayer etc. The only program that runs nicely on my system is Xine. Try it:

```

sudo apt-get -y install gxine

```

Hope that helps. If it doesn't work look for xine packages with:
```
sudo apt-cache search xine
```
and install the appropriate ones.

---

