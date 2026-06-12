---
title: "squares for text chain"
date: 2010-03-15
forum: General Help
---

### Post by frkdavid on 2010-03-15
All my desktop content, menus, files names, softwares names, so every text chains have been changed in squares !!! so it became impossible to use my computer (I mean my desktop at least). I did not find yet help on the french forum so I try here (sorry for my bad english).

any ideas to fix that ?

frank, Karmic user.

---

### Post by jdysinger on 2010-03-25
> **frkdavid said:**
> All my desktop content, menus, files names, softwares names, so every text chains have been changed in squares !!! so it became impossible to use my computer (I mean my desktop at least). I did not find yet help on the french forum so I try here (sorry for my bad english).

any ideas to fix that ?

frank, Karmic user.

I'm having the same issue. I was installing the latest versions o glib, gtk+, and their dependencies (ATK, Cairo, & Pango) when my update manager text changed to squares for each character. I did the update anyway, restart the computer, now all text chains are square.

I uninstalled the libs I installed to see if one of them affected the text, but without any love. 

I'm using Jaunty.

---

### Post by frkdavid on 2010-03-28
Hello,

I fix the problem by rename my home directory with usermod

sudo usermod -d /home/new_login -m -l new_login previous_login 

I d'ont know exactly why but it has worked.

frk

---

