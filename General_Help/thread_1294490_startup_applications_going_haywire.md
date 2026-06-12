---
title: "startup applications going haywire"
date: 2009-10-18
forum: General Help
---

### Post by pjizz on 2009-10-18
I am having weird problems with programs starting and not starting up at login.  Apparently, what I have selected in "Startup Application Preferences" is just a ruse, as Ubuntu launches whatever it wants to.  

I want to launch
[LIST]
[*]CompizFusion Icon
[*]Dropbox
[*]Deluge
[*]GNOME-Do
[/LIST]

What actually launches is
[LIST]
[*]Firefox
[*]Rhythmbox
[*]Last.fm
[*]Dropbox
[*]Deluge
[/LIST]

So some of what I have ticked off in the "Startup Application Preferences" dialog do start, some don't, and some that I don't have enabled (but apparently do) do start.  I do not have the "Remember running applications" option ticked, but none of those apps are running at log off anyway.

The Deluge app is something I recently added on my own to the "Startup Application Preferences" dialog, as a test to see if it would work.  It did, but nothing else I do matters.  I really want to have GNOME-Do start at startup, but even if I put in the full path to /usr/bin/gnome-do it won't start.  I also have tried both ticking and unticking the option within GNOME-Do to have it launch at startup.  Nothing seems to be working.

My initial thoughts are that I have these programs set to run via some other dialog than the System > Preferences > Startup Application Preferences.  Or perhaps something needs to load before GNOME-Do in order for it to launch.  But it always launches when I tell it to, either from the Applications menu or from the terminal.  Also, none of that explains why I have Rhythmbox, Firefox, and Last.fm launching everytime...well, last.fm launches b/c Rhythmbox does, but why does Rhythmbox launch?

---

### Post by pjizz on 2009-10-18
Update:

I'm still playing with this, and I decided to close all the programs but then check off "remember running applications" to see if it would also do the opposite, i.e. remember which applications were not running.  Voila, it did not open firefox or rhythmbox (and last.fm) this time.  Still cannot get GNOME-Do to run.  Reinstalling to try that now.

---

### Post by pjizz on 2009-10-18
Well, reinstalling GNOME-Do is not really a solution, as it doesn't work.  

Also, having to close all running programs to make it remember that Firefox isn't running and thus should not start upon logging back in is an unnecessary inconvenience.

---

### Post by pjizz on 2009-10-19
anyone else experienced this?

---

### Post by pjizz on 2009-10-25
one more desperate bump?

---

### Post by giannisfs on 2009-10-25
> **pjizz said:**
> ...
hi my suggestion
firstly
type cd in your terminal
second

type
ls .config/autostart/

and post **here** what are the files in that directory

**Case 1**
if there are the ones you want 
   open each one in a text editor 
   and change the **X-GNOME-Autostart-enabled=false**
    to **X-GNOME-Autostart-enabled=true**

**Case 2**
if there are the ones you don't want 
    either delete them all (better place them temporarily somewhere for backup)

    or make sure that X-GNOME-Autostart-enabled=false 

Give it a try ;)

---

### Post by pjizz on 2009-10-27
i get this

```
davidian@davidian-desktop:~$ ls .config/autostart/
bluetooth-applet.desktop        gnome-do.desktop
deluge.desktop                  gnome-keyring-daemon.desktop
dropbox.desktop                 print-applet.desktop
evolution-alarm-notify.desktop  seahorse-daemon.desktop
fusion-icon.desktop             vino-server.desktop
gnome-at-session.desktop

```

they open with gedit, e.g. 

$ sudo gedit gnome-do.desktop

however, they do not tab to complete, and are empty when I open them, and then even though I change nothing, when I close it asks me if I want to change anything.  this all leads me to question whether these files actually exist.  i can delete them all, but this wouldn't solve the problem of the programs I want to start starting.

also, when i double-click the icons, it tells me that "The application launcher "dropbox.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe" and asks me if i want to launch anyway, mark trusted, or cancel.

so, any ideas?  and thanks again for helping me out!!

---

### Post by pjizz on 2009-11-02
bumpity BuMp?

---

### Post by pjizz on 2009-11-09
issue persists in 9.10

---

### Post by girto on 2009-11-09
try
```
gksudo gedit ~/.config/autostart/gnome-do.desktop
```

---

### Post by pjizz on 2009-11-11
> **girto said:**
> try
```
gksudo gedit ~/.config/autostart/gnome-do.desktop
```
looks like it should be enabled

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=GNOME Do
Type=Application
Exec=/usr/bin/gnome-do
Terminal=false
Icon=gnome-do
Comment=Do things as quickly as possible (but no quicker) with your files, bookmarks, applications, music, contacts, and more!
Categories=Utility;
Hidden=false
X-GNOME-Autostart-enabled=true
```

---

### Post by pjizz on 2009-11-12
weird thing happened today...i changed themes and restarted (since the theme switch never is complete in ubuntu unless you restart) and noticed that gnome-do was up and running...I was happy until I noticed that my desktop was blank b/c nautilus had not started...ugh.  

restarting gave me back my desktop and took away gnome-do.  i can't win for losing!!

---

