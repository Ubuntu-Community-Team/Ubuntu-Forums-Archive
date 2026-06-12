---
title: "Hosed my gnome-screensaver slideshow"
date: 2011-01-22
forum: General Help
---

### Post by johncc on 2011-01-22
I have managed to frustrate myself trying to change the location of the pictures used in the slideshow.  This is on a fairly fresh vanilla install of 10.04.

I sort of had it working, but I have done something such that now it is not running slideshow at all: 

when I select a screensaver such as "Fuzzy Flake" in preview, I get:

```
john@vaio:~$ ps -ef | grep screens
john      1963     1  0 14:01 ?        00:00:00 gnome-screensaver
john      2040     1  1 14:14 ?        00:00:00 gnome-screensaver-preferences
john      2058  2040  2 14:14 ?        00:00:00 /usr/lib/xscreensaver/fuzzyflake
```
But when I select "Pictures folder" (slideshow), I would expect to see /usr/lib/gnome-screensaver/gnome-screensaver/slideshow running (as I had before), but now it is not:
```
john@vaio:~$ ps -ef | grep screens
john      1963     1  0 14:01 ?        00:00:00 gnome-screensaver
john      2040     1  2 14:14 ?        00:00:00 gnome-screensaver-preferences
john      2057  1343  0 14:14 pts/0    00:00:00 grep --color=auto screens
```

If I run /usr/lib/gnome-screensaver/gnome-screensaver/slideshow manually it does display pictures in the window.  I have tried restarting gdm and rebooting-- no help.  I also tried dpkg-reconfigure gnome-screensaver.

I had tinkered with adding --location to the exec line in the file /usr/share/applications/screensavers/personal-slideshow.desktop, but at this point I would like to get slideshow working again at all.  This is the current contents:

```
[Desktop Entry]
Name=Pictures folder
Comment=Display a slideshow from /AllPix
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver
```
Which log file might show some error in its startup? Should I uninstall and reinstall gnome-screensaver (or is there a way to just "refresh to the installed state").

Thanks,
John

---

