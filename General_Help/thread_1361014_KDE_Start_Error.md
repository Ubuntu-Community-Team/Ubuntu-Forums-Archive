---
title: "KDE Start Error"
date: 2009-12-21
forum: General Help
---

### Post by HalfEmptyHero on 2009-12-21
I'm running Kubuntu 9.10 with kde 4.4, and after installing some updates today kde doesn't seeming to be fully starting. The splash screen goes away while the kde logo is still transparent and then goes to a black screen. KRunner still works though, and I can use it to load any program it seems. The network manager is still connecting to my wireless as well, but I don't know how to get rid of the black screen and see my desktop, panel, and all the plasmoids and stuff.

---

### Post by nerdy_kid on 2009-12-21
that'd sound like plasma-desktop.

run
```

plasma-desktop

```
in KRunner and that should do the trick.  If not....well
wipe KDE config: (i.e. all plasmoids wallpapers customizations etc)
```

rm -R ~/.kde

```

or if you want a backup:
```

mv ~/.kde ~/.kde_old

```


up to this has 4.4 been stable, considering its in Beta?  and were is the ppa for it? thnks :D

---

### Post by HalfEmptyHero on 2009-12-21
Somehow I didn't have plasma-desktop installed, but after installing it everything seems to be working, although my icons are all messed up. But other than this problem, 4.4 has been running real smoothly.

---

### Post by nerdy_kid on 2009-12-21
> **HalfEmptyHero said:**
> Somehow I didn't have plasma-desktop installed, but after installing it everything seems to be working, although my icons are all messed up. But other than this problem, 4.4 has been running real smoothly.

wow KDE without plasma LOL

---

