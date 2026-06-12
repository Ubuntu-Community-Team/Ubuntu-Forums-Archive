---
title: "Past solutions out-of-date to add applications to Xfce menu"
date: 2009-07-25
forum: General Help
---

### Post by Smoke.Static on 2009-07-25
I want to add an application to the Xfce menu in Xubuntu.  I can see no straightforward way to do this.  I have tried several different solutions on this sight, some of which actually broke the menu and forced me to reinstall it altogether.  I have even tried finding the menu file and editting it manually but I have been unable to find it.  It is not in /etc/xdg/xfce folder like i have been told it is.  Yes, i have hidden files set to be shown.  I found similar files while searching but none are helpful.  Everone tells me to do two things, generally.  First, try right clicking on applications in the panel and go to edit...  Right clicking on applications only brings up options for the panel, not the menu.  Second, I have been told to use Add/Remove at the top of the menu.  That's useless because the application is not available on synaptic package manager.  Also, I have been told to navigate to Applications>Settings>Preferences.  There is no Preferences selection in the Settings tree.  Also, two others on IRC have tried to help me via terminal.  sudo f*d-up --myinstallation severely the last time and I had to reinstall xubuntu.  Is there any way to add an application not available through synaptic to the Xfce menu??  I would appreciate any help with this issue.  I apologize if there is already a recent solution to this, I failed to locate it.

---

### Post by kerry_s on 2009-07-25
**gksudo mousepad /usr/share/applications/the-program.desktop**

put:

```
[Desktop Entry]
Name=the-name-you-want-in-menu
Exec=your-program
Categories=where-you-want-it
```

---

### Post by Smoke.Static on 2009-07-25
Wow, Thanks!  I see now.  I just need to create the desktop file and choose the name, generic name, icon path, etc.  Thanks Kerry_S that saved me alot of time and headache.

---

### Post by Smoke.Static on 2009-07-25
I created a mupen64.desktop file and put the following:
[Desktop Entry]
Name=Mupen64
Comment=N64 emulator
Exec=/home/nick/bin/mupen64-0.5/mupen64
Icon=/home/nick/bin/mupen64-0.5/mupen64_icon.png
Categories=Games

But it does not seem to work.
Tells me the path is wrong.  What should I put instead of nick(my username)?
I've tried ~/bin/mupen64-0.5/mupen64 ( anything I didnt install via synaptic i put in ~/bin that i created.)

---

### Post by kerry_s on 2009-07-25
> **Smoke.Static said:**
> I created a mupen64.desktop file and put the following:
Name=Mupen64
Comment=N64 emulator
Exec=/home/nick/bin/mupen64-0.5/mupen64
Icon=/home/nick/bin/mupen64-0.5/mupen64_icon.png
Categories=Games

But it does not seem to work.

you have to have "[Desktop Entry]", so it should be:

```
**[Desktop Entry]**
Name=Mupen64
Comment=N64 emulator
Exec=/home/nick/bin/mupen64-0.5/mupen64
Icon=/home/nick/bin/mupen64-0.5/mupen64_icon.png
Categories=Games
```

---

### Post by Smoke.Static on 2009-07-25
> **kerry_s said:**
> you have to have "[Desktop Entry]", so it should be:

```
**[Desktop Entry]**
Name=Mupen64
Comment=N64 emulator
Exec=/home/nick/bin/mupen64-0.5/mupen64
Icon=/home/nick/bin/mupen64-0.5/mupen64_icon.png
Categories=Games
```

sorry i failed to copy and paste that part.  I did include the [Desktop Entry].  I went back and edited my post to reflect that but not in time :).  The thing is it tells me the path is wrong.  What should i use rather than my user name or ~?

---

### Post by wojox on 2009-07-25
Open a terminal:

```
whereis mupen64
```

Just to be sure.

---

### Post by Smoke.Static on 2009-07-25
Okay never mind.  It's always something simple.  Whoever named the folder used an o rather than a 0 :(
Thanks again for your help.  Hopefully this will help anyone else trying to add apps to the Xfce menu :D

---

### Post by Smoke.Static on 2009-07-25
Bleh, sorry, one more question.  what should i put for category to get it into the games tree rather than the other tree?


Ah, I got it.  I used:
Categories=Gnome;Game;Emulator

i needed to specify that it was a game and what type

is the Gnome parameter necessary?

---

### Post by kerry_s on 2009-07-25
> is the Gnome parameter necessary?

nope, you just need the main stuff.
i did a quick test, just the minimal lines. see pic

---

