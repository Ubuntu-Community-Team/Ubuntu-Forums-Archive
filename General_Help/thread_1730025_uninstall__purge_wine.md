---
title: "uninstall / purge wine"
date: 2011-04-15
forum: General Help
---

### Post by dragonfly41 on 2011-04-15
How can I uninstall / purge wine and any wine installed windows programs?

I've tried deleting .wine (hidden folder)

but in /usr/bin/

there are a number of wine related files.

And wine sub menu still appears in Applications menu

so I need a purge command.

```

[COLOR=Blue]dpkg --list | grep wine
ii  wine1.2                               1.2.2-1ubuntu1~maverick2                        Microsoft Windows  Compatibility Layer (Binary Emulator and Library)
ii  wine1.2-gecko                         1.0.0-0ubuntu4                                  Microsoft Windows  Compatibility Layer (Web Browser)
ii  winetricks                            0.0+20110402~ppa1                               Microsoft Windows  Compatibility Layer (winetricks)[/COLOR]

```

---

### Post by seawolf167 on 2011-04-15
```
sudo apt-get purge wine
```? This will remove all files, settings and configuration files for wine

If you just want to remove it but keep your configs/settings, use this instead

```
sudo apt-get remove wine
```

---

### Post by dragonfly41 on 2011-04-15
```

sudo apt-get purge wine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]Package wine is not installed[/COLOR], so not removed
0 upgraded, 0 newly installed, 0 to remove and 326 not upgraded.

```


??

---

### Post by RodneyBowler on 2011-04-16
I seem to have the same issue. I am using ubuntu 10.10 and have/had installed winetricks. Small issues had appeared (i.e. MS Visio 2007 stopped working, WINE would hang etc), so I attempted to remove / purge. Same result: 

CODE:

root@rod-laptop:/home/rod# sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It's still visible under applications. What to do?

Thanks,

Rod.

---

### Post by dragonfly41 on 2011-04-16
I'm still trying to figure out how to tidy up the Applications menu after uninstalling Wine.

This is what I tried ..

reinstall wine (1.2.2)

sudo apt-get install wine



Then with Wine freshly installed I went to Applications > Ubuntu Software Center

Installed Software > Provided by Ubuntu

Remove (by selecting and clicking on Remove button):


[LIST]
[*]Wine Microsoft Windows Compatibility Layer
[/LIST]

[LIST]
[*]Wine Microsoft Windows Compatibility Layer (Beta release)
[/LIST]

Looked at History in same menu to see if wine has been removed

However .. looking at Applications drop down list

I still see a partial wine menu .. including links to old windows programs which were removed.


And

```

dpkg --list | grep wine
rc  wine1.2    1.2.2-1ubuntu1~maverick2     Microsoft Windows Compatibility Layer (Binary Emulator and Library)

```

---

### Post by WorMzy on 2011-04-16
This should sort out your menus:

(From the [Wine FAQ]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa"))
```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}
```

If you have winetricks installed, you may need to remove that with
```
sudo apt-get purge winetricks
```

---

### Post by dragonfly41 on 2011-04-16
Thanks for the FAQ link ..

I tried those commands

but it still didn't  totally wipe out orphan items in Applications menu

I had to right click on "Applications" in top panel > then "Edit Menus" and remove them there.

See screenshot.

The orphan wine menu items have gone now.   Thanks.

---

### Post by anxean on 2012-09-01
winetricks steam


fixes it all bros

---

### Post by sffvba[e0rt on 2012-09-01
*Old thread **closed**.*


404

---

