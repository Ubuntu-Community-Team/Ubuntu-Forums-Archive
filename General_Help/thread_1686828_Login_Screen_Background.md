---
title: "Login Screen Background"
date: 2011-02-12
forum: General Help
---

### Post by Xia Johan on 2011-02-12
I'm trying to change the background of the login screen. I have copied the pictures in a (.jpg) format over to /usr/share/backgrounds/ and brought up the config window using:

```
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow
```The issue that I'm having is that it won't recognise the file. Using the exact same one I've used in the past, it's still not picking it up. Instead when I click "add" find the wallpaper, click "open" (or what ever that option is) it just shows a blank ba
ckground that will allow me to change the color. 

Any thoughts as to what's causing this? 

(Sorry if this is posted in the wrong area.)

EDIT: I'm running Ubuntu 10

---

### Post by Foxheadz on 2011-02-12
Not sure whats causing it but you can easily do this using ubuntu tweak. It's an app filled with easier ways to do simple tasks [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Xia Johan on 2011-02-12
Awesome, thank you very much. Saved some of my hair there.

---

### Post by Foxheadz on 2011-02-13
Lol no problem, trust me that app will save you lots of time.

---

### Post by Xia Johan on 2011-02-13
Well... New problem! The app didn't work. It's almost like ubuntu messed up somewhere in the install? Cause it won't take the picture, or the png that I changed the small image to as a test. Tweak shows the change, but ubuntu doesn't. It just does that same blank screen, and the icon is still the desktop.

EDIT: When all else fails, reinstall and see if the same thing happens! haha

---

### Post by Foxheadz on 2011-02-13
Oh wait, do you mean the initial login screen or the suspend screen? cause from what I know you can't easily change the one on the suspend screen.

---

### Post by Xia Johan on 2011-02-13
I mean the initial login screen. Which is what's got me so confused...

---

### Post by Xia Johan on 2011-02-13
Wonderful, so after I reinstalled and installed tweak. It's still not working...

---

### Post by BigCityCat on 2011-02-13
I use these commands and are you updating initramfs when your done?

> gksudo nautilus
copy and paste the picture into usr/share/backgrounds.

> gksudo -u gdm dbus-launch gnome-appearance-properties

Then add the picture. I'm using png without any issues. 

Then to get rid of the accessibility icon.

> gconftool-2 -t bool -s /desktop/gnome/accessibility/keyboard/enable false

Then update initramfs 

> sudo update-initramfs -u

---

### Post by stinkeye on 2011-02-13
> **BigCityCat said:**
> Quote:gksudo -u gdm dbus-launch gnome-appearance-properties

Doesn't work for me
```
glen@MavMusic:~$ gksudo -u gdm dbus-launch gnome-appearance-properties
No protocol specifiedNo protocol specified
Cannot open display: 
No protocol specified

(gnome-appearance-properties:13207): Gtk-WARNING **: cannot open display: :0.0
```


> **Xia Johan said:**
> I'm trying to change the background of the login screen. I have copied the pictures in a (.jpg) format over to /usr/share/backgrounds/ and brought up the config window using:

```
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow
```The issue that I'm having is that it won't recognise the file. Using the exact same one I've used in the past, it's still not picking it up. Instead when I click "add" find the wallpaper, click "open" (or what ever that option is) it just shows a blank ba
ckground that will allow me to change the color. 

Any thoughts as to what's causing this? 

(Sorry if this is posted in the wrong area.)

EDIT: I'm running Ubuntu 10
Does it work if you try to change to a different wallpaper?


This works for me without moving anything to /usr/share/backgrounds.

When gnome-appearance-properties pops up at the GDM I click add and
navigate to where my wallpapers are at /home/glen/Pictures/wallpaper

---

### Post by Xia Johan on 2011-02-16
So I finally got it working. I had copied the files over from the Windows partition. Somehow they got corrupted, cause when I redownloaded the picture, it worked fine using tweak, and the other way I had been doing it(terminal). Same thing with the icon that Tweak lets you play with. For some reason, everything copied from Windows will let me do anything I want to it, but use it as a log in background. That has to be fresh on Ubuntu.

---

