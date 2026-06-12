---
title: "admin/root help"
date: 2010-05-20
forum: General Help
---

### Post by Steo_Walsh on 2010-05-20
Ok so basically i want to download a program icon from the internet into my 'usr/share/pixmaps'. However apparently I need to be a root user? I am the only user on the computer and want to know the best way of doing this? Please keep it simple as I'm fairly new to ubuntu. Any help would be hugely appreciated

---

### Post by sanderd17 on 2010-05-20
First of all: in ubuntu, you don't have to donwload apps from the internet, install them from te software center or synaptic.

Answer to your question: Linux is a lot safer than windoze. e.g. not all users have rights to do everything. Even not if you're the only user. Because this way, if a virus gets in you computer it would be able to do a lot of bad. 

But if you're the only user, you have the right to become root (a special user that has all power) to do that, you have to type "sudo" or "gksudo" in front of the command (if you work with commandline). If you don't work with commandline, please say what you do. Do you click a link or so?

Greets,
Sander

---

### Post by eluminBe on 2010-05-20
Download it to your home directory and move with *sudo* prefix.

```
sudo mv ~/icon.png /usr/share/pixmaps
```

---

### Post by sanderd17 on 2010-05-20
sorry, got your question now. You want to donwload a picture file to that folder. Just open nautilus as root. You can do so by hitting ALT+F2 and typing
```

gksudo nautilus

```

than you can do what you want. But if you're don, close nautilus. You don't want to stay root.

---

### Post by Steo_Walsh on 2010-05-20
thanks guys you got it to what i want :) much apprectiated :popcorn:

---

