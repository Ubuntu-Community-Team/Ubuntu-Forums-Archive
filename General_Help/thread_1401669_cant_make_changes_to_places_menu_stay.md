---
title: "cant make changes to places menu stay"
date: 2010-02-08
forum: General Help
---

### Post by rock4christ on 2010-02-08
im trying to remove some things from the places menu(documents, music, pictures etc.) but they come back after every restart.

---

### Post by Leppie on 2010-02-08
try removing them from your .gtk-bookmarks file.

---

### Post by rock4christ on 2010-02-08
> **Leppie said:**
> try removing them from your .gtk-bookmarks file.

gets added back in on restart

---

### Post by rock4christ on 2010-02-08
bump

---

### Post by Leppie on 2010-02-08
have you tried the gconf tool?

---

### Post by rock4christ on 2010-02-08
> **Leppie said:**
> have you tried the gconf tool?

don't see anything in there that would be relative. am I overlooking something?

---

### Post by Leppie on 2010-02-08
i use xubuntu myself, so gconf editor doesn't do much for me.
however, they say it's like a registry editor so i figured that it should be possible to modify such things with gconf editor as well.

anyways, try editing your user-dirs.dirs:
```
gedit ~/.config/user-dirs.dirs
```

---

### Post by rock4christ on 2010-02-11
> **Leppie said:**
> i use xubuntu myself, so gconf editor doesn't do much for me.
however, they say it's like a registry editor so i figured that it should be possible to modify such things with gconf editor as well.

anyways, try editing your user-dirs.dirs:
```
gedit ~/.config/user-dirs.dirs
```

they restored on boot

---

### Post by mechro on 2010-02-11
What happens if you open Nautilus then **Bookmarks > Edit Bookmarks > Remove**?

---

### Post by rock4christ on 2010-02-11
> **mechro said:**
> What happens if you open Nautilus then **Bookmarks > Edit Bookmarks > Remove**?

they disappear, but come back after reboot.

---

### Post by mechro on 2010-02-11
It could be a bug...

[https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/389317](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/389317)

It says it's fixed in Karmic.

---

### Post by rock4christ on 2010-02-11
doesn't seem to be

---

### Post by rock4christ on 2010-02-12
is there any other possible method?

---

### Post by mechro on 2010-02-12
Edit: See post below...

---

### Post by mechro on 2010-02-12
Right, I think I've worked it out...

Places is generated from two sources; the XDG system at Log-in and GTK bookmarks.

Edit your /.config/user-dirs.dirs as follows...

Using the Music bookmark as an example change **XDG_MUSIC_DIR="$HOME/Music"** to read **XDG_MUSIC_DIR="$HOME"**

Then delete the Music bookmark by either editing bookmarks in Nautilus or by editing your gtk-bookmarks file.

Log-out, Log-in.

---

### Post by rock4christ on 2010-02-12
thanks. that did it!

---

