---
title: "fluxbox help"
date: 2009-10-10
forum: General Help
---

### Post by Psychosoc1al on 2009-10-10
Hi, I'm begginer in fluxbox.
I installed fluxbox but it looks terrible.
I saw this tutorial - [http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)
But I can't do nothing from it :S
I want to make my fluxbox 'cool' and I want to make if is it possible like addon menus.
Thanks.

---

### Post by yabbadabbadont on 2009-10-10
That tutorial is for customizing your fluxbox menu.  If you are having trouble with that part of it, then you should probably post your issue (with the details you left out here...) in the tutorial thread.

As for making fluxbox look good, what have you tried so far?  Fluxbox styles can be found many places.  Two of the best places to browse are [www.box-look.org](www.box-look.org) (the fluxbox section) and [www.tenr.de](www.tenr.de) (the styles section)  The downloaded style should be extracted to your ~/.fluxbox/styles directory.  Example:```
/home/daffy $ ls -l ~/.fluxbox/styles
total 52
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:39 ColorFlux_Brave
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:39 ColorFlux_Dust
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:04 ColorFlux_Human
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:39 ColorFlux_Illustrious
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:39 ColorFlux_Noble
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:39 ColorFlux_Wine
drwxr-xr-x 3 daffy daffy 4096 2009-08-26 12:40 ColorFlux_Wise
drwxr-xr-x 3 daffy daffy 4096 2006-12-15 04:31 dent
drwxr-xr-x 3 daffy daffy 4096 2006-12-15 04:31 looksClear_blue
drwxr-xr-x 3 daffy daffy 4096 2006-12-15 04:31 looksClear_turquoise
drwxr-xr-x 3 daffy daffy 4096 2006-12-15 04:31 slim_darkblue
drwxr-xr-x 3 daffy daffy 4096 2008-10-02 07:27 solaris
drwxr-xr-x 3 daffy daffy 4096 2007-08-08 05:48 solaris_generic

```

If you are having trouble changing the default GTK+ theme, then perhaps the easiest way would be to install lxappearance.  You can use it to configure the GTK+ theme, icon theme, and default application font.  Downloaded GTK+ themes need to be extracted to your ~/.themes directory.  Example:```
/home/daffy $ ls -l /home/daffy/.themes
total 76
drwxr-xr-x 3 daffy daffy 4096 2009-09-25 03:14 Aurora
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancyAncient
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancyEarth
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancyGrass
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancySand
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancySea
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 20:22 MurrinaFancySky
drwxr-xr-x 3 daffy daffy 4096 2009-09-27 21:09 Nimbus-Glossy-Menus
drwxr-xr-x 3 daffy daffy 4096 2009-09-27 21:09 Nimbus-Glossy-Menus-Deep
drwxr-xr-x 3 daffy daffy 4096 2009-09-26 22:29 Shiki-Brave
drwxr-xr-x 4 daffy daffy 4096 2009-09-12 21:42 Shiki-Colors-Easy-Metacity
drwxr-xr-x 4 daffy daffy 4096 2009-09-12 21:42 Shiki-Colors-Metacity
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 21:42 Shiki-Colors-Striped-Metacity
drwxr-xr-x 5 daffy daffy 4096 2009-09-12 21:42 Shiki-Dust
drwxr-xr-x 3 daffy daffy 4096 2009-09-26 22:29 Shiki-Human
drwxr-xr-x 3 daffy daffy 4096 2009-09-12 21:42 Shiki-Illustrious
drwxr-xr-x 3 daffy daffy 4096 2009-09-26 22:29 Shiki-Noble
drwxr-xr-x 3 daffy daffy 4096 2009-09-26 22:29 Shiki-Wine
drwxr-xr-x 3 daffy daffy 4096 2009-09-26 22:29 Shiki-Wise
lrwxrwxrwx 1 daffy daffy   34 2009-08-26 19:53 aud-Default -> /usr/share/audacious/Skins/Default
```
And downloaded icons should be extracted to your ~/.icons directory.  Example:```
/home/daffy $ ls -l /home/daffy/.icons/
total 36
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:43 gnome-brave
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-colors-common
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-dust
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-human
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-illustrious
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-noble
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:44 gnome-wine
drwxr-xr-x 7 daffy daffy 4096 2009-09-12 21:45 gnome-wise
drwxr-xr-x 9 daffy daffy 4096 2009-09-24 03:30 hydroxygen
```

If you need more help, just post back here with the exact problem, including what you have tried and the results (with error messages if any).  :)

---

### Post by mac9416 on 2009-10-10
I've never managed to make Fluxbox look *really* nice, but I've made it tolerable. I use the [Dyne Fluxbox theme]("http://www.box-look.org/content/show.php/Dyne?content=61999"), and the [SlicknesS GTK theme]("http://www.gnome-look.org/content/show.php/SlicknesS?content=71993").

To install Dyne:
[LIST=1]
[*][Download the tarball]("http://www.box-look.org/content/download.php?content=61999&id=1&tan=81370389") .
[*]Extract it with your favorite archive manager to your dekstop. 
[*]Copy it to ~/.fluxbox/styles. 
[*]Right-click the desktop, go to Styles, and click Dyne.
[/LIST]

To install SlicknesS:

[LIST=1]
[*][Download the file]("http://www.gnome-look.org/content/download.php?content=71993&id=1&tan=66722817&PHPSESSID=c21e9ef996ac178bec0cef24fbc93bdb") to your desktop
[*]Right click the file and select extract here, then another archive pops up. Do the same for that.
[*]Open a terminal and run this command:
```
$ sudo cp -r $HOME/Desktop/SlicknesS /usr/share/themes
```
[*]Install the lxappearance GTK theme switcher. Then run it, and select the SlicknesS theme:
```
$ sudo apt-get install lxappearance
$ lxappearance
```
[/LIST]

Sorry, but I've never messed with add-on menus.

It's not beautiful, but it's better. Enjoy!

---

### Post by Psychosoc1al on 2009-10-10
I know about themes, but I want to configure conky and menus, I want to add menus like Firefox, Terminal, aMSN, etc you know.
This is currently my desktop: [http://i35.tinypic.com/f54vg3.png](http://i35.tinypic.com/f54vg3.png)
Thanks.

---

