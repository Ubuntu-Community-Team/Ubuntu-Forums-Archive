---
title: "kolourpaint - long start up"
date: 2010-05-26
forum: General Help
---

### Post by bitches_brew on 2010-05-26
Hello,

I faced strange problem with 10.04 , which didn't occur in 9.04
```
$ kolourpaint
kolourpaint(3318): Couldn't create index file "/var/tmp/kdecache-stachu/kpc/kde-icon-cache.index" 
QFile::remove: Empty or null file name
QClipboard: Unable to receive an event from the clipboard manager in a reasonable time
Starting KolourPaint on a 24-bit screen...
kolourpaint(3317): Couldn't create index file "/var/tmp/kdecache-stachu/kpc/kde-icon-cache.index" 
QFile::remove: Empty or null file name
^C

```...and its loading for about 15 seconds ;/

other KDE apps works fine (except of qtcreator, which is buggy).

I'm using xubuntu/xfce....

does your kolourpaint also runs so slowly?

---

### Post by syntr on 2011-09-23
This was still present in Natty, but I've finally tracked down a solution for it:

```
killall xfce4-settings-helper
``` fixed it for me.

[URL="https://bugzilla.xfce.org/show_bug.cgi?id=6521"]It's bug 6521 in Xfce.
[/URL] 
[s]So far I haven't noticed any adverse effects from killing the "settings helper", but your mileage may vary :)[/s]

Nevermind, killing the settings helper makes it so your custom keyboard shortcuts don't work and may cause other problems, so I wrote the following hack to "fix" it:

```
#!/bin/sh
killall xfce4-settings-helper
kolourpaint &
# You may need to increase "5" depending on how slow your computer is, i.e. how long it takes kolourpaint to normally start without the QClipboard issue
sleep 5
nohup xfce4-settings-helper &
rm $HOME/nohup.out

```Save this in your home directory as .kolourpaint.sh (the . is for my sanity so I don't have to see it all the time ;) )

Then, to make your menu shortcut work:

```
$ mkdir ~/.local/share/applications/kde4
$ cp /usr/share/applications/kde4/kolourpaint.desktop ~/.local/share/applications/kde4
```Open the file in a text editor...

```
$ vim ~/.local/share/applications/kolourpaint.desktop
```Change line 8 (it starts with Exec) from

```
Exec=kolourpaint %u
```to

```
Exec=sh /home/yourusername/.kolourpaint.sh
```With any luck your Kolourpaint will now start quickly. (mine starts almost instantly)

---

