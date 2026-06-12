---
title: "Changing wallpaper via command line?"
date: 2012-10-09
forum: General Help
---

### Post by Stonecold1995 on 2012-10-09
How do I change wallpapers via command line in Kubuntu 12.04 (KDE 4.9), with the same effect as right-clicking the desktop and pressing "Next Wallpaper"?  Maybe through using Dbus or something?

```
alex@kubuntu:~$ plasma-desktop --version
Qt: 4.8.2
KDE Development Platform: 4.9.1
Plasma Desktop Shell: 0.4
```

---

### Post by Aide9aic on 2012-10-10
This might be useful...

[http://distrowatch.com/weekly.php?issue=20120730#qa](http://distrowatch.com/weekly.php?issue=20120730#qa)

---

### Post by Stonecold1995 on 2012-10-11
> **steveriley said:**
> This might be useful...

[http://distrowatch.com/weekly.php?issue=20120730#qa](http://distrowatch.com/weekly.php?issue=20120730#qa)

I tried the instructions but running this gave no output:
```
kreadconfig --file plasma-appletsrc --group Containments --group 1 --group Wallpaper --group image --key wallpaper
```

---

### Post by Aide9aic on 2012-10-11
Did you restart the Plasma desktop after running the command? The article indicates that this is necessary...

---

### Post by Stonecold1995 on 2012-10-16
I have my wallpapers set to rotate in a random slideshow, and I want to be able to trigger the "next wallpaper" event through command line, not change the location of the wallpaper image.

---

### Post by Stonecold1995 on 2012-10-23
bump

---

### Post by Stonecold1995 on 2012-11-15
bump

---

