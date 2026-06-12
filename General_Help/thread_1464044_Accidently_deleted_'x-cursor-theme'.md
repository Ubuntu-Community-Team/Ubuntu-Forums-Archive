---
title: "Accidently deleted 'x-cursor-theme'"
date: 2010-04-27
forum: General Help
---

### Post by Adam's AI on 2010-04-27
Hi, I deleted x-cursor-theme in update alternatives and I'm wondering:
a) how to get it back? and
b) if that's going to be a problem for my system?


If you're wondering why I accidentally did this, read below.

I recently installed KDE-Desktop on top of my vanilla ubuntu installation but this had the effect of changing my default pointer in gnome from DMZ-White to oxygen. I tried changing the cursor using update alternatives but this only changed the cursor shown over application windows, not the default cursor always displayed over the panel menus.

I tried changing the symbolic link on x-cursor-theme from oxygen.theme to DMZ-White's index.theme, but it refused to change. So I thought maybe I have to 'remove' the link to oxygen before I can re-direct it.

Being a newcomer to linux, I googled 'how to remove symbolic links' and wound up with the answer 'the way you do with any other file: delete it." So that's what I did. It didn't take me too long to realize that the file was not "only a symbolic link" but a binary containing additional information. (Assuming I now understand it properly, which is not a given :P )

-Adam

---

### Post by Adam's AI on 2010-04-30
Any ideas?

---

### Post by Adam's AI on 2010-05-22
It seems the file has magically re-appeared. Can anybody explain what might have happened or if there would be any problems without the file? I know it's not super important, but I would still like to understand.

Thanks,
Adam

---

### Post by war.ace on 2011-02-16
mine's gone too :( how did you get yours back? I can't get mine back

---

### Post by asmoore82 on 2011-02-16
"x-cursor-theme" *is only* a symbolic link:
```
**ls -l /etc/alternatives/x-cursor-theme**
lrwxrwxrwx 1 root root 39 2010-08-06 12:48 /etc/alternatives/x-cursor-theme -> /usr/share/icons/DMZ-White/cursor.theme
```

If you need to re-create the link:
```
**sudo ln -sf /usr/share/icons/DMZ-White/cursor.theme /etc/alternatives/x-cursor-theme**
```

If you need to find the package that owns the real file and re-install it:
```
**dpkg-query -S cursor.theme**
dmz-cursor-theme: /usr/share/icons/DMZ-Black/cursor.theme
dmz-cursor-theme: /usr/share/icons/DMZ-White/cursor.theme
**sudo apt-get install --reinstall dmz-cursor-theme**
```

---

