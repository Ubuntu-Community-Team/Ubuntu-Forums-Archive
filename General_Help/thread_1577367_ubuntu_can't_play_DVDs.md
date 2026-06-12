---
title: "ubuntu can't play DVDs?"
date: 2010-09-18
forum: General Help
---

### Post by princeofnam on 2010-09-18
I get an error whenever I try to play DVDs in either VLC or movieplayer in Ubuntu.  However Windows plays them just fine in either VLC or Windows Movie Player.  Any explanation?

---

### Post by mc4man on 2010-09-18
Open up a terminal, copy and paste this in and run (press enter) - will install libdvdcss2 for you. 
Otherwise post the error

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by davrosuk on 2010-09-18
Look at adding the Medibuntu repos too: [http://medibuntu.org/]("http://medibuntu.org/")

---

### Post by lisati on 2010-09-18
> **davrosuk said:**
> Look at adding the Medibuntu repos too: [http://medibuntu.org/]("http://medibuntu.org/")

Don't need to anymore. Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by davrosuk on 2010-09-19
I didn't know that! Its still needed for WMVs though right - surely I can't be that out of date?

---

### Post by weblordpepe on 2010-09-19
Isnt it just a package you install with synaptic?

---

### Post by princeofnam on 2010-09-19
libdvdcss2 worked perfectly with   VLC.  is there any reason why it wasn't included with a fresh install of ubuntu?

---

### Post by davrosuk on 2010-09-19
> **princeofnam said:**
> libdvdcss2 worked perfectly with   VLC.  is there any reason why it wasn't included with a fresh install of ubuntu?

deCSS isn't shipped with Ubuntu because, well, its a whole can of worms. Depending on where you stand on the planet its either completely legal or highly illegal. 

[http://en.wikipedia.org/wiki/DeCSS]("http://en.wikipedia.org/wiki/DeCSS")

---

