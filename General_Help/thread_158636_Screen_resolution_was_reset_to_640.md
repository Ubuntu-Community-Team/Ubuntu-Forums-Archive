---
title: "Screen resolution was reset to 640"
date: 2006-04-11
forum: General Help
---

### Post by NoteMe on 2006-04-11
I am dual booting with Windows, and have been using Windows for a week. Now I had some time to look at Ubuntu again, but when I started it up, the screen resolution was suddenly 640*480. What happen? It was 1280*1024 last time I booted it up? I am really new to Linux, so can anyone please give me some tips to where I should start look at this problem?

PS: Going to screen resolution on the menu doesn't help. I can't choose anything else then 640*480 there for some reason. It's like the drivers is not there anymore.

PPS: I have a ATI 9800 PRO card if that helps.

Thanks in advance
- ØØ -

---

### Post by Ramses de Norre on 2006-04-11
I have that sometimes too and just restarting gdm solves it.
ctrl+alt+F1
sudo /etc/init.d/gdm restart

---

### Post by Blarion on 2006-04-11
Check out your x11 settings to see if you enabled resolutions over 640. /etc/x11

---

### Post by NoteMe on 2006-04-12
[QUOTE=Ramses de Norre]I have that sometimes too and just restarting gdm solves it.
ctrl+alt+F1
sudo /etc/init.d/gdm restart[/QUOTE]
Wow. Believe it or not, that fixed it. Now that seems like a feauture that would be nice to get uninstalled..:p

---

### Post by Ramses de Norre on 2006-04-12
Uninstall gdm? gdm is the program that gives you a graphical login screen etc and is part of gnome, so I wouldn't uninstall it.
I don't know what causes this erroneous resolution, I get it myself sometimes (not very often) and restarting gdm always helped.

---

### Post by NoteMe on 2006-04-13
Hehe...It was a joke, and I refered to the feauture (bug) that switched the resolution not gdm it self. Sorry for the confusion..:)


- ØØ -

---

### Post by quvil on 2006-04-13
[QUOTE=NoteMe]I am dual booting with Windows, and have been using Windows for a week. Now I had some time to look at Ubuntu again, but when I started it up, the screen resolution was suddenly 640*480. What happen? It was 1280*1024 last time I booted it up? I am really new to Linux, so can anyone please give me some tips to where I should start look at this problem?
[/QUOTE]

Setting HorizSync/VertRefresh correctly in "Monitor" section in /etc/X11/xorg.conf fixed the problem for me (your monitor's manual should list those values under refresh rates, if I am not mistaken). Usually X is able to determine those values correctly automatically, but sometimes it doesn't work (maybe slow responce from a monitor or something like that?), so X plays it safe and defaults to the lowest resolution/refresh rate.

---

