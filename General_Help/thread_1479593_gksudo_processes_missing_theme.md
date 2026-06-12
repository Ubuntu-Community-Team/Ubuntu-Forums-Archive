---
title: "gksudo processes missing theme"
date: 2010-05-10
forum: General Help
---

### Post by Altay_H on 2010-05-10
I couldn't stand the new default theme in Lucid Lynx (Ambiance), so I installed Karmic Koala's theme (Human). Everything is working fine, but I noticed that processes running with root privileges lack the installed theme. What is the correct way to install a theme for root? I'm guessing I need to run gnome-appearance-properties with root privileges and install the Human theme for it, but I'd like to be sure. See attached screenshots for a root process with a normal process behind it.

---

### Post by drewsus on 2010-05-11
run these two commands:
```
sudo ln -s $HOME/.themes /root/.themes
sudo ln -s $HOME/.icons /root/.icons
```

---

### Post by Altay_H on 2010-05-11
They didn't make a difference. My $HOME/.icons directory is empty anyway. My $HOME/.themes directory contains the Human theme I installed, but the symbolic link didn't fix the issue. What's interesting is that the title bar for privileged applications uses the Human theme correctly, it's just the rest of the window that doesn't display correctly. Any other ideas?

---

### Post by Marcelo Ruiz on 2010-06-07
I'm having the same issue. The weird thing is that if running commands with 'sudo' instead of 'gksudo' the right theme is shown... Any ideas on how to solve this?
Thanks!

---

