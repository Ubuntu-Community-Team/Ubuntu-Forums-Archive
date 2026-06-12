---
title: "Gnome terminal true tranparency with metacity"
date: 2010-04-01
forum: General Help
---

### Post by basilebasilic on 2010-04-01
Hello,

I can't get to have "true transparency" in gnome terminal. When I active it in profile settings (Transparent Background) I just have the background wallpaper not the window behind the terminal.

So, I activate "compositing window" in metacity, I reboot (to be sure) but I don't have true transparency in gnome terminal.

Some info to help me please on my config.
What could I do ? (I sure that my graphical card work because on ubuntu full standard install the true transparency work).

I have a minimal install with alternate cd (10.04 beta1).

Then I have installed (without recommended package) :

[INDENT][LIST=1]
[*]xserver-xorg
[*]gnome-core
[*]xinit
[*]gtk2-engines
[*]gconf-editor (to check on compositing window)
[*]mesa-utils (to check glxinfo |grep "direct")
[/LIST]
[/INDENT]

My graphical card is :

```
lspci |grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
glxinfo |grep "direct"
direct rendering: Yes

```

Thanks.

---

### Post by basilebasilic on 2010-04-01
I find it.

But I don't understand why now it's work. I have true transparency.

If you want activate "compositing window" you have the GUI or the CLI choice.

I do it with the GUI but not effect (perhaps with my minimal install it's missing package to reliate the change in the gconf-editor to gnome desktop).

Then I try with the cli :
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

and then it's work now ...strange.

---

