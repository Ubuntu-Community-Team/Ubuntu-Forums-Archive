---
title: "Aero-Glass in Ubuntu 11.10 with Gnome-Shell?"
date: 2011-10-23
forum: General Help
---

### Post by Acutical on 2011-10-23
I am used to windows 7 and recently switched to Ubuntu. I have the Zukitwo theme installed and i would like my window boarders to match it. If it's not possible, it's not that big of a deal.

[IMG]http://i.imgur.com/U9OM6.jpg

---

### Post by linuxuser12345 on 2011-10-23
Have you tried using Emerald Theme Manager?

---

### Post by crdlb on 2011-10-23
Emerald only works with compiz.

I'm not aware of any way to get translucent titlebars with GNOME Shell.

---

### Post by oldtimer7777 on 2011-10-23
If you want to match the Window 7 appearance you will need to downgrade to 11.04 and use GTK2 theme Windows 7 kits.. It looks identical on 11.04 with the kits applied.

> **crdlb said:**
> Emerald only works with compiz.

I'm not aware of any way to get translucent titlebars with GNOME Shell.

---

### Post by ully-mick on 2011-11-24
[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Set-Aero-Glass-Effect](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Set-Aero-Glass-Effect)

works in 11.10 with gnome 3 fallback so should work with unity/gnome shell.

---

### Post by werewolves on 2011-11-24
> **ully-mick said:**
> [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Set-Aero-Glass-Effect](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Set-Aero-Glass-Effect)

works in 11.10 with gnome 3 fallback so should work with unity/gnome shell.

Didn't work in Gnome-Shell for me.

---

### Post by ully-mick on 2011-11-25
I think it depends which windows theme you use.
I use GTK+ theme = Ambiance. Window theme = BrushedGnome. and I set the "metacity_theme_active_opacity" to 0.5
that gives me a semi-transparent top. not as shiny as Emerald, but an improvement on the norm.

---

### Post by crdlb on 2011-11-25
That "metacity_theme_active_opacity" setting is for gtk-window-decorator, which is only used with compiz. GNOME Shell does not use compiz, so it will have no effect.

---

