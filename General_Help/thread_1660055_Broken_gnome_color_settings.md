---
title: "Broken gnome color settings"
date: 2011-01-04
forum: General Help
---

### Post by geoffjay on 2011-01-04
I (perhaps foolishly) installed the RGBA PPA and packages on 10.04 right after I installed it and pretty much ever since I haven't been able to easily change the gtk theme. I installed gtk-theme-switch and that seemed to work for some themes but not the one that I'm trying now.

I disabled RGBA and ran ppa-purge on the it then removed all related packages, but that didn't help. Then I deleted all .gtkrc* directories and removed gtk-theme-switch and that didn't do anything either.

The two screenshots that are attached are for the system I'm having problems with (10.04) and another that has the theme the way that it should be shown (10.10).

Thanks.

---

### Post by geoffjay on 2011-01-04
Nevermind. I blew every setting away with
$ rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and started fresh.

---

