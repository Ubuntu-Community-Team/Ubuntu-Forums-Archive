---
title: "Slow program load and wait time workaround ???"
date: 2011-10-24
forum: General Help
---

### Post by Bobhuber on 2011-10-24
OK guys
May be someone can shed some light on this subject. I'm using 11.10 with gnome 3 (fresh install) and have it set to auto login into gnome 3 ( sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell). The program load times from the main launcher have always been terrible with the hourglass wait taking forever to turn into a usable mouse along with increased CPU usage etc. etc. on a high end system.. Much to my surprise I found out that anything launched via Cairo-Dock  didn't do this ?? Windows opened much quicker , normal mouse etc.Got to looking a bit further to see if I could duplicate the improvement without launching from CD. If the apps are launched using  Alt + F2 (not the side launcher or main application (s) screen) the problem disapears. If I disable the auto login leaving the default to Gnome 3 and manually login the problem disappears. I have no clue as to what is causing this behavior.

---

### Post by sanderd17 on 2011-10-24
Especially the last line "If I disable the auto login leaving the default to Gnome 3 and manually login the problem disappears." makes me think of a gnome-keyring problem.

Could you look a bit further into that direction? But messing with the keyring can cause some problems (like having to fill your password twice). So I don't have clear advise for you.

PS. Please change your title from lubuntu to ubuntu

---

### Post by Bobhuber on 2011-10-24
> **sanderd17 said:**
> Especially the last line "If I disable the auto login leaving the default to Gnome 3 and manually login the problem disappears." makes me think of a gnome-keyring problem.

Could you look a bit further into that direction? But messing with the keyring can cause some problems (like having to fill your password twice). So I don't have clear advise for you.

PS. Please change your title from lubuntu to ubuntu

The keyring is set to a blank password other than the user login.

---

