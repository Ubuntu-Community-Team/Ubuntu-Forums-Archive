---
title: "Doesn't open new windows in front"
date: 2011-02-13
forum: General Help
---

### Post by Adrianzr1 on 2011-02-13
I really don't know if this is a common problem but when i try to open a new application or a new folder or something, ubuntu doesn't open it at front, it open it behind other windows, puts me the actual window like if it was unselected, but the new one doesn't put it in the front.

Any help??


Found the answer by myself, sorry for posting that =)

Solution:
in terminal
> gconftool-2 --recursive-unset -a /apps/compiz

---

### Post by Adrianzr1 on 2011-02-13
NO, the problem continues, just work the first time i put that in terminal, but next doesn't work anymore, any ideas??

---

### Post by jerrrys on 2011-02-13
is this really compiz related ?   turn off compiz and see if it persist

---

### Post by Adrianzr1 on 2011-02-13
how i supposed to turn it off?

System > Preferences > Appearance > Visual Effects > None ???

it is already in that option

---

### Post by jerrrys on 2011-02-13
this appears to be a new install, has it been this way since install?

---

### Post by Adrianzr1 on 2011-02-13
not at all, when i installed ubuntu the last time i had the avant window navigator bar without this problem, then i quit the awn because ubuntu crashes every time, then i let just one panel, and was when the problem begans.


have to say. I have ubuntu in my netbook aspire one, i dont like netbook remix.

---

### Post by jerrrys on 2011-02-13
see if this will do anything
sudo apt-get purge avant-window-navigator

---

### Post by Adrianzr1 on 2011-02-13
it put me that

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gambas2-gb-form gambas2-gb-desktop libdesktop-agnostic0 gambas2-gb-info
  fortunes-min libdesktop-agnostic-cfg-gconf konqueror-nsplugins
  linux-headers-2.6.35-22 fortune-mod dolphin libkde3support4
  linux-headers-2.6.35-22-generic librecode0 libdesktop-agnostic-vfs-gio
  gambas2-runtime libkonq5 gambas2-gb-image gambas2-gb-qt
  libdesktop-agnostic-fdo-glib libkonqsidebarplugin4a kfind gambas2-gb-qt-ext
  gambas2-gb-qt-opengl libkonq5-templates libqt3-mt gambas2-gb-gtk
  gambas2-gb-gui gambas2-gb-opengl gambas2-gb-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded

and still the same

---

### Post by jerrrys on 2011-02-13
Use 'apt-get autoremove' to remove them

did you do this

---

### Post by Adrianzr1 on 2011-02-13
i did it right now, still the same =/

---

### Post by jerrrys on 2011-02-13
just to be sure i understand...

everything was ok until you remove AWN

if this is so, then may want to reinstall and use a different method to remove

---

### Post by Adrianzr1 on 2011-02-13
since i installed ubuntu i installed awn too, so i really don't know if the problem was before awn, but i noticed it after stop using awn and with awn i didn't had this problem.

---

### Post by jerrrys on 2011-02-13
here's a thought

lets reset compiz again and turn it back on

gconftool-2 --recursive-unset -a /apps/compiz

---

### Post by Adrianzr1 on 2011-02-13
that is what i was trying since the beginning of this thread, but just worked the first time, i tried to open a new window and it worked good, but it didn't work with the next window that i opened

---

### Post by jerrrys on 2011-02-13
at this point i would just reinstall; im out of suggestions

---

### Post by Adrianzr1 on 2011-02-13
really appreciate your help, will continue trying, thank you.

---

### Post by Johnny420 on 2011-02-13
try disable compiz windows rules
at the bottom of compiz

---

### Post by Adrianzr1 on 2011-02-13
that option it's already disable

---

### Post by stinkeye on 2011-02-13
> **Adrianzr1 said:**
> how i supposed to turn it off?

System > Preferences > Appearance > Visual Effects > None ???

it is already in that option

Which means your having this problem when running Metacity as your 
window manager.
This will tell you your current window manager.
```
gconftool-2 --get /desktop/gnome/applications/window_manager/current
```


So try 
```
gconftool-2 --recursive-unset -a /apps/metacity
```

or

Switch to compiz as your window manager (If you have installed the proprietary driver for your gfx card).
```
compiz --replace
```

---

### Post by Adrianzr1 on 2011-02-13
> **stinkeye said:**
> Which means your having this problem when running Metacity as your 
window manager.
This will tell you your current window manager.
```
gconftool-2 --get /desktop/gnome/applications/window_manager/current
```


So try 
```
gconftool-2 --recursive-unset -a /apps/metacity
```

or

Switch to compiz as your window manager (If you have installed the proprietary driver for your gfx card).
```
compiz --replace
```

wiiii switching to compiz fixed the problem, i just hope it don't crash like in the past, not a good graphic card i think.

thank you.

---

### Post by Adrianzr1 on 2011-02-17
Hey guys, i used that command 
> compiz --replace 
and used too
> compiz --replace &

But every time that i shut down the computer it goes back to metacity. Any command to make it permanent??

---

### Post by stinkeye on 2011-02-17
use alt+F2
```
compiz --replace
```
and hit run.

Install fusion-icon
```
sudo apt-get install fusion-icon
```

Will find it in menu > system tools > compiz fusion icon

Sits in the notification area with right click options.

Add it to startup applications with **fusion-icon** as the command.

---

### Post by Adrianzr1 on 2011-02-17
> **stinkeye said:**
> use alt+F2
```
compiz --replace
```
and hit run.

ok i hope that works. Thank you

i was using it in terminal.

---

### Post by stinkeye on 2011-02-17
> **Adrianzr1 said:**
> ok i hope that works. Thank you

i was using it in terminal.

Using Alt+F2 and running **compiz --replace**
is basically the same as running **compiz --replace &** in the terminal
and won't fix your boot problem.

Adding fusion-icon to startup applications will though as it loads your last 
used window manager.

On maverick I have to have this in startup applications else it boots into Metacity.

Why??? Buggered if I know.

---

### Post by Adrianzr1 on 2011-02-17
> **stinkeye said:**
> Using Alt+F2 and running **compiz --replace**
is basically the same as running **compiz --replace &** in the terminal
and won't fix your boot problem.

Adding fusion-icon to startup applications will though as it loads your last 
used window manager.

On maverick I have to have this in startup applications else it boots into Metacity.

Why??? Buggered if I know.

i will try that option, lets reboot to see if it works

---

### Post by Adrianzr1 on 2011-02-17
Ok i just fixed it this way.

In startup applications just add one, I called it "Compiz" and in the command line I write "compiz --replace". Now every time I turn on the computer it starts with compiz.

Any way i will install fusion-icon Thank you again.

---

### Post by stinkeye on 2011-02-17
Try this.
Open gconf-editor
```
gconf-editor /desktop/gnome/session/required_components/windowmanager
```

The entry for windowmanager should be **gnome-wm** as shown in pic.

If it doesn't show this, right click on the windowmanager entry and choose unset key.

Untick compiz from startup applications log out/in and see if compiz starts.

---

### Post by Adrianzr1 on 2011-02-17
it says metacity =) i think this is the problem =)



ok now it says gnome-wm but it still the same, I will let it the other way with the compiz command in the startup applications

---

### Post by stinkeye on 2011-02-17
> **Adrianzr1 said:**
> it says metacity =) i think this is the problem =)
Yep only just found this and mine also said metacity and after changing to
**gnome-wm** it now boots into compiz without the aid of fusion-icon.

P.S. If this is now working for you, and if you do install fusion-icon,
add it to startup applications with the command
```
fusion-icon -n

```

The **-n** flag will tell it not to load a window manager.

---

### Post by stinkeye on 2011-02-17
> **Adrianzr1 said:**
> 
ok now it says gnome-wm but it still the same, I will let it the other way with the compiz command in the startup applications

OK, you know how to fix it now anyway.

One last gconf setting you can compare with mine is
```
gconf-editor /desktop/gnome/applications/window_manager/default
```

When altering settings in gconf make bookmarks so you can find easily.

Good luck.

---

### Post by Adrianzr1 on 2011-02-17
mine was set to /usr/bin/metacity now i change it and put /usr/bin/compiz i quit the compiz command for startup applications and now it looks like everything is working good. Thank you

---

### Post by stinkeye on 2011-02-17
No problem. Took a while, but we got there.
Adiós

---

