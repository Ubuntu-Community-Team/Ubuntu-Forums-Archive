---
title: "Remove Docky Lag With nVidia"
date: 2010-02-24
forum: General Help
---

### Post by DanPiazza on 2010-02-24
I've already Googled this problem, and it seems that the only solution is running:

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```

in the terminal. However, this barely helped me.

I've heard it's a problem Docky has with nVidia drivers, which I use.

Does anyone have a solution? Docky is so slow it is essentially unusable at this point. Cairo dock seems too glitchy, so I guess it's back to AWN.

---

### Post by fabounet on 2010-02-25
Cairo-Dock works perfectly with most NVidia cards.

---

### Post by DanPiazza on 2010-02-25
> **fabounet said:**
> Cairo-Dock works perfectly with most NVidia cards.

I'm getting the hang of it. Docky just seemed so much nicer, if it worked properly with nVidia cards. There currently is no solution for this problem?

---

### Post by hojgaard on 2010-03-10
> **DanPiazza said:**
> I'm getting the hang of it. Docky just seemed so much nicer, if it worked properly with nVidia cards. There currently is no solution for this problem?

Its strange cause gnome-do docky was so fast with nvidia, but i experience a lot of lagging now...

---

### Post by stinkeye on 2010-03-10
I am using a GeForce 9400 card with the  NVIDIA 195.36.03 drivers and no problems.
[_**[COLOR="DarkRed"]How To Install Nvidia 185.xx, 190.xx and 195.xx Drivers In Ubuntu, From A Launchpad Repository[/COLOR]**_]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html")

I also use the [**_[COLOR="DarkRed"]Docky Development PPA[/COLOR]_**]("https://launchpad.net/~docky-core/+archive/ppa")

---

### Post by Anach23 on 2010-08-08
I had the same problem after I installed Lucid and set the driver to version 173 and changing it to the "current" version (System->Hardware Drivers)  helped.

---

