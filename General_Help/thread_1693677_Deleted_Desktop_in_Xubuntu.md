---
title: "Deleted Desktop in Xubuntu"
date: 2011-02-23
forum: General Help
---

### Post by ppelemoo on 2011-02-23
Ok it's funny, but I've accidentally deleted my desktop and now I don't know how have it back.
I was doing some recovery work from console as root and have rm my desktop.
Now when I log in I have all my Home folders on the monitor instead of the usual desktop.
Creating the folder again doesn't solve the problem.
Any hint?
Thank you

---

### Post by aeiah on 2011-02-23
just seems like you've set your home folder to be the root window. have you tried creating the folder 'Desktop' (case sensitive) and then changing the settings within whatever desktop settings app xfce uses?

---

### Post by ppelemoo on 2011-02-23
I've created a new folder Scrivania (Italian) but could have the desktop back working. I'm quite new to Xfce and don't know where to look for the settings..

---

### Post by aeiah on 2011-02-23
as per [this post]("https://bbs.archlinux.org/viewtopic.php?pid=837881")

do you have the file ~/.config/user-dirs.dirs?

if so, read it's contents. should give you instructions for adding your desktop path back. if it is missing, then issue the command :

```

xdg-user-dirs-update

```

or maybe this first:
```

xdg-user-dir

```

---

### Post by ppelemoo on 2011-02-23
Thank you very much, you've been very helpful and now everything is working (and shining) again.
Thank you!

---

