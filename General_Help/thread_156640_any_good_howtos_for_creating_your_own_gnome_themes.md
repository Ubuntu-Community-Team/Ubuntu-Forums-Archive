---
title: "any good howtos for creating your own gnome themes"
date: 2006-04-07
forum: General Help
---

### Post by syklitengutt on 2006-04-07
Anyone who knows any good tutorials for creating your own gnome theeme...
Icons inst that necessary.
I want to create my own colours on the bars etc...

---

### Post by aysiu on 2006-04-07
These links may help:
[http://ajgenius.us/Gnome/Themes/gnome2-gtk2-themes.html](http://ajgenius.us/Gnome/Themes/gnome2-gtk2-themes.html)
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

---

### Post by curtis on 2006-04-07
[QUOTE=syklitengutt]Anyone who knows any good tutorials for creating your own gnome theeme...
Icons inst that necessary.
I want to create my own colours on the bars etc...[/QUOTE]
Modifying the gtkrc file of your current theme works good.
Running the following commands will achieve that:

```

cp -rf ~/.themes/Human ~/.themes/Your_Theme
nano ~/.themes/Your_Theme/gtk-2.0/gtkrc

```

Then change your theme to your new theme.

---

### Post by syklitengutt on 2006-04-07
Is there any gui apps where you can see what you are changeing?

---

### Post by aysiu on 2006-04-07
[QUOTE=syklitengutt]Is there any gui apps where you can see what you are changeing?[/QUOTE] Sure. Gedit.

Go to your /home directory in Nautilus and press Control-H.
This will show your hidden directories.
Go into the .themes folder and browse around. Double-click anything you want to edit.

---

### Post by syklitengutt on 2006-04-07
ok... Perhaps I expressed myself on a bad way....
What I ment is if you open a themefile in a gui app and edit it, it will show the changes you make....

---

### Post by aysiu on 2006-04-07
[QUOTE=syklitengutt]ok... Perhaps I expressed myself on a bad way....
What I ment is if you open a themefile in a gui app and edit it, it will show the changes you make....[/QUOTE] You could always modify the theme while you have the Theme Manager window open and then unselect and reselect your new theme as you make changes...

---

### Post by syklitengutt on 2006-04-07
I will test this tomorrow...
Im in winhows now...

---

