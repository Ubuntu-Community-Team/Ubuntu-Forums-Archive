---
title: "Wine, why wont you work?!"
date: 2010-08-27
forum: General Help
---

### Post by lulzcake on 2010-08-27
Running Linux MINT fluxbox. Very similar to ubuntu, even though the prefix was set to other.


Hey guys, I was playing around with wine, when i came across a forum that had itunes 8.x running in wine. So i figured, hell, why not give it a try, and by god, it worked. Sorta.

Once the installer finished, it said "run itunes", and it opened up nice and pretty, but it was getting late, around 4 am (yes, i dont sleep) so i shut it down, and went to bed.

Today, when I went to itunes in the wine tab, nothing happened. So i figured I'd just remove it...but it wont remove. All it does is reinstall.

Is there any way to remove it, reinstall it, and have it WORK?

---

### Post by lulzcake on 2010-08-29
Bump?

---

### Post by Vaphell on 2010-08-29
do you have many apps installed in wine?
if not you can wipe .wine dir (ctrl+h in filebrowser to show hidden dirs) and it will be recreated in a default state next time wine is run.

Also try running itunes from terminal, maybe something newsworthy will be printed out there
install nautilus-open-terminal in synaptic, restart filebrowser, go to the directory with itunes.exe (.wine/drive_c/....), rightclick and choose 'open in terminal', run wine itunes.exe

---

### Post by lulzcake on 2010-08-30
I installed what you suggested, but there is no run with terminal option. Even with a restart.

---

### Post by lulzcake on 2010-08-31
another bump?

---

### Post by ean5533 on 2010-08-31
> **lulzcake said:**
> I installed what you suggested, but there is no run with terminal option. Even with a restart.

After installing nautilus-open-terminal, you should be able to right-click somewhere in the folder (not on an icon) and pick "Open Terminal Here" which will open a terminal in that directory. From there you should be able to run

```
wine itunes.exe
```

Hopefully some interesting error messages will be shown in the terminal.

---

### Post by realzippy on 2010-08-31
AFAIK itunes does not work in wine correctly....no chance.

---

### Post by lulzcake on 2010-09-01
itunes works just fine. it just wont open through the menu. if i go through wine, in terms of .wine folder, it opens just dandy.

another problem i have is my ipod not mounting now. O.o

---

### Post by borth92 on 2010-09-01
iTunes is a pain to get to work with the iPod under WINE. Use gtk-pod or Banshee and you can manage your iPod just as easily as iTunes in Windows.

---

