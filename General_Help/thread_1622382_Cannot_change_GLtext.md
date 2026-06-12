---
title: "Cannot change GLtext"
date: 2010-11-15
forum: General Help
---

### Post by drz4007 on 2010-11-15
Hello. I tried changing the GLtext following various threads ([http://www.linuxquestions.org/questions/ubuntu-63/changing-the-gltext-screensaver-in-ubuntu-635208/](http://www.linuxquestions.org/questions/ubuntu-63/changing-the-gltext-screensaver-in-ubuntu-635208/)), ([http://ubuntuforums.org/showthread.php?t=1476079](http://ubuntuforums.org/showthread.php?t=1476079)) and others, but i cannot do it. The text insist on staying the same. It displays my kernel. My OS is Ubuntu 10.10. Does anybody have a clue? It has become really frustrating...

---

### Post by ddjolley on 2011-01-23
I'm having the exact same problem.  The procedure for configuring the gltext screensaver to display date and time is copiously documented (including an exact example in the man page) and seems to be extremely straight forward.  However, I seem to be unable to get the change to take effect.  I sort of feel like I need to send someting a SIGHUP. :)  Even a full re-boot doesn't fix the problem.  Any ideas what I can do?  Thanks for any input.

           ... doug

---

### Post by stinkeye on 2011-01-23
Try using the full path in your 
**/usr/share/applications/screensavers/gltext.desktop** file

eg my gltext.desktop file to show time and date while remaining static.
```
[Desktop Entry]
Name=GLText
Exec=[COLOR="Magenta"]/usr/lib/xscreensaver/gltext[/COLOR] -no-wander -no-spin -root -text "%A%n%d %b %Y%n%l:%M:%S %p"
TryExec=[COLOR="#ff00ff"]/usr/lib/xscreensaver/gltext[/COLOR]
Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;
```

Then choose another screensaver and back to see effect.


If your interested in an analogue clock screensaver, look her:
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?p=10357188#post10357188[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=10357188#post10357188")

---

### Post by ddjolley on 2011-01-23
> Try using the full path in your 
**> /usr/share/applications/screensavers/gltext.desktop** file

Out of the box my gltext.desktop file used full paths.

As an experiment I tried using "-program date" both with date enclosed in quotes and without quotes.  Same result.  This thing seems to be hung up on the default and I can't seem to jar it loose.  It's as if I am editing the wrong config file.  I'm very much at a loss.  Thanks for your input.

           ... doug

---

### Post by stinkeye on 2011-01-23
Try this deb file.
It will install 4 gltext .desktop files, all with different configs for time and date.
They will display in screensaver preferences as  simple-clock-gl...

[**_[COLOR="DarkRed"]http://download.tuxfamily.org/gericom/maverick/simple-clock-gl_5.11-gericom2_all.deb[/COLOR]_**]("http://download.tuxfamily.org/gericom/maverick/simple-clock-gl_5.11-gericom2_all.deb")

---

### Post by stinkeye on 2011-01-23
Although I don't seem to have to, someone on another thread
suggested, after you edit a .desktop file you need to refresh the desktop cache with:
```
sudo dpkg-reconfigure python-gmenu
``` 
and that you you still may need to log out/in.


Other than that the only thing I can suggest is possibly reinstall
the **xscreensaver-gl** package.
It works for me. I simply need to change to another screensaver and back to see the changes.

---

### Post by ddjolley on 2011-01-23
> Although I don't seem to have to, someone on another thread
> suggested, after you edit a .desktop file you need to refresh the desktop cache with:
 
>       Code: sudo dpkg-reconfigure python-gmenu

> and that you you still may need to log out/in


That someone seems to know what they are talking about.  It worked like a charm.  It seems that I do not need to log out/in.  Just doing the reconfigure seems to get things working.  I'd say that's important information to know.  Also, Stinkeye, the alternative screensavers that you suggested are a nice alternative to know about.  They work just great.  I'm just happy to know what the problem is with gltext.  It would have bothered me to have left this issue without understanding this problem.  Thanks to all hands.

          ... doug

---

### Post by SabreWolfy on 2011-06-21
> **ddjolley said:**
> > Although I don't seem to have to, someone on another thread
> suggested, after you edit a .desktop file you need to refresh the desktop cache with:
 
>       Code: sudo dpkg-reconfigure python-gmenu

> and that you you still may need to log out/in


That someone seems to know what they are talking about.  It worked like a charm.  It seems that I do not need to log out/in.  Just doing the reconfigure seems to get things working.  I'd say that's important information to know.  Also, Stinkeye, the alternative screensavers that you suggested are a nice alternative to know about.  They work just great.  I'm just happy to know what the problem is with gltext.  It would have bothered me to have left this issue without understanding this problem.  Thanks to all hands.

          ... doug

Thanks. The reconfigure worked for me too.

---

### Post by linux.girl on 2011-10-25
Hi, I am also trying to edit my gltext, with no success :-(

First, I made it an executable file so it can be edited, then, I edited it like this:

[Desktop Entry]
Name=GLText
Exec=/usr/lib/xscreensaver/gltext **[COLOR=Red]'MyText' [/COLOR]**-root
TryExec=/usr/lib/xscreensaver/gltext
Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;

I did the dpkg as suggested, also chose a diff screen saver AND restarted...but it still shows the regular gltext text, i.e., the linux generic version.

Any ideas on what I can do?

Thanks in advance,

Linux.Girl

---

### Post by stinkeye on 2011-10-25
I don't think this worked before or the setting was not in the gnome-screensaver gui, but I just went into 
xscreensaver > gltext > settings > advanced
and changed the command line to
```
gltext -root -text "MyText"
```
and it changes instantly.

---

### Post by linux.girl on 2011-10-28
> **stinkeye said:**
> I don't think this worked before or the setting was not in the gnome-screensaver gui, but I just went into 
xscreensaver > gltext > settings > advanced
and changed the command line to
```
gltext -root -text "MyText"
```and it changes instantly.

WOW! It worked!!! Many thanks!!!

:D:D:D:D:D:D:D:D

---

