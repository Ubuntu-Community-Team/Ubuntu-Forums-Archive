---
title: "How to get smooth (anti-aliased?) fonts in (sun) Java"
date: 2009-10-30
forum: General Help
---

### Post by sexyclient on 2009-10-30
I've been flip-flopping between various OS's and linux distros, but after a long few months of primarily using Windows Vista I'm now very pleased with Ubuntu 9.10 Karmic Kaola.

That being said, I downloaded PS3MEDIASERVER - a very easy-to use, high-quality, and generally exquisite java-based dlna media server that, I feel, should be in the ubuntu repositories somewhere.  I used it on windows where I didn't even realize that it was java at all, but when I switched to Ubuntu I knew something was off:  The fonts in this app are nowhere near identical to my system standards.  A bit more experimenting showed that all java apps' fonts look like crap.  Fix please?

Tidbits: I installed java from ubuntu restricted extras in the (sweet) software center, and I'm using 64-bit 9.10.

---

### Post by sexyclient on 2009-10-30
Anyone?

---

### Post by sexyclient on 2009-10-31
Bump 2 (of 3) ... Anyone??

---

### Post by P4man on 2009-10-31
Not sure if this helps but have a look:
[http://ubuntuforums.org/showthread.php?t=909327](http://ubuntuforums.org/showthread.php?t=909327)

---

### Post by P4man on 2009-10-31
Also, I just noticed java fonts are not installed by default if you install java. Try

```
sudo apt-get install sun-java6-fonts
```

---

### Post by sexyclient on 2009-11-01
Sweet lead!  The links in pose #2 are dead now, though, so I can't rely on that.  It's a shame because it seems that's exactly what I want to do...  Now, though, I know where I can get answers so I'll go ask questions over on the java.net communities.  Hopefully things go well there.

---

### Post by bjtuna on 2009-11-03
I've been looking for an answer to this all day, because subpixel smoothing just isn't working in Netbeans (works fine in Eclipse). I'm starting to suspect that it's just broken.

---

