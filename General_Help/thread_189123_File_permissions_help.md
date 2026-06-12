---
title: "File permissions help"
date: 2006-06-04
forum: General Help
---

### Post by notoriouslou1022 on 2006-06-04
hey i want to place a new icon in usr/share/pixmaps and when i copy it in there it says i need to permission. how do i login into root to place that icon in there?

---

### Post by xXx 0wn3d xXx on 2006-06-04
[QUOTE=notoriouslou1022]hey i want to place a new icon in usr/share/pixmaps and when i copy it in there it says i need to permission. how do i login into root to place that icon in there?[/QUOTE]
You have a number of ways to do this.

1. Open a terminal and type:
> gksudo nautilus
Then go to /usr/share/pixmaps and drag the file that you want in there.

2. I prefer non-gui so if your like me do this:
> cd /directoy/where/picture/is
> sudo cp filename /directory/where you/want it/
Make sure there is a space between the file name and the directoy.

If you want more into read [ this. ](https://wiki.ubuntu.com/FilePermissions)

---

### Post by bswilson on 2006-06-04
Your best bet is to copy the icon you want into /usr/share/pixmaps by invoking **sudo.**  This way, you don't need to modify any permissions, and you don't have to actually log in as root.

```
sudo cp /home/whatever/your-icon.png /usr/share/pixmaps
```

You'll be prompted to enter **_your_** password; upon doing so successfully you'll be rewarded with a new icon file in the directory you want.

---

### Post by meng on 2006-06-04
instead of typing
mv whatsis.ico /usr/share/pixmaps

or
cp whatsis.ico /usr/share/pixmaps

you should type
sudo mv whatsis.ico /usr/share/pixmaps

or
sudo cp whatsis.ico /usr/share/pixmaps

You will be asked for a password, use your regular user password.

---

### Post by professor_chaos on 2006-06-04
Please read this. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

