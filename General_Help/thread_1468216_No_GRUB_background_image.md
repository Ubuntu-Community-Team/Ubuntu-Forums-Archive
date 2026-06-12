---
title: "No GRUB background image"
date: 2010-05-01
forum: General Help
---

### Post by chriswyatt on 2010-05-01
I just updated my Dad's laptop to Lucid, on my laptop I got the nice shiny new background that came with Lucid but on my Dad's laptop it still has the standard black background.

I checked desktop-base and the directory's empty.  It should contain this file: /usr/share/images/desktop-base/moreblue-orbit-grub.png

Does anyone know if there are any packages I should install / reinstall to try and get this file here, or should I just copy the file over from my laptop?

Thanks!

---

### Post by dino99 on 2010-05-01
you can find lot of grub+themes around there

---

### Post by chriswyatt on 2010-05-01
Nevermind.  I figured it out myself.

```
sudo aptitude install desktop-base
sudo update-grub
```

It's still a mystery why desktop-base wasn't installed in the first place.

---

### Post by dino99 on 2010-05-01
the ubuntu-desktop cant installed everything by default, its a user choice

---

### Post by chriswyatt on 2010-05-01
I see, I guess on my laptop I had installed something before that depended on desktop-base.  Thanks for clearing it up.

---

### Post by SteveBates on 2010-05-14
> **chriswyatt said:**
> Nevermind.  I figured it out myself.

```
sudo aptitude install desktop-base
sudo update-grub
```

It's still a mystery why desktop-base wasn't installed in the first place.

Mine was not installed either and I used this to fix it - I had upgraded to 10.04 from 8.04 and also manually upgraded my Grub to grub2.

---

