---
title: "Is there any way to make the root account mirror themes?"
date: 2009-07-03
forum: General Help
---

### Post by Vunutus on 2009-07-03
This is a very minor issue, but I've noticed that whenever I sudo/gksudo some program, the color schemes are all messed up. The window decoration settings are taken from my main desktop user's settings, but everything inside the window seems to be using some bland default color scheme/icons.

I assume that this is because the root user doesn't have themes set up by default, and when programs are run as root they try to grab root's theme settings which don't exist.

Is there any easy way to fix this? I'm looking for some way to mirror the current user's theme settings to the root account so running programs as root is truly seamless. It seems like the most obvious way to solve this is to copy my user's theme directory over to root's home, but that isn't exactly a dynamic solution and would require work each time I changed themes. Would it be possible to solve this by making root's theme directory a symlink to my user's theme directory?

---

### Post by shae on 2009-07-03
You are probably using a theme downloaded from somewhere like gnome-look.

You need to copy the theme to /usr/share/themes and then your windows opened with gksu/sudo will use it.  Unfortunately you cannot really use a link to get it to work.

---

### Post by aysiu on 2009-07-03
Pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) should do it: ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

