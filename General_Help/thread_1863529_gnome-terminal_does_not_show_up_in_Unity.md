---
title: "gnome-terminal does not show up in Unity"
date: 2011-10-17
forum: General Help
---

### Post by FuturePilot on 2011-10-17
gnome-terminal is missing in Unity for some reason in 11.10. If I search for "terminal" gnome-terminal does not show up. It is installed though and I can launch it from Alt+F2 but why won't it show up in Unity?

---

### Post by stinkeye on 2011-10-17
If your using the dash check you haven't filtered the results.
It retains the filter setting until reboot/logout.

---

### Post by FuturePilot on 2011-10-18
> **stinkeye said:**
> If your using the dash check you haven't filtered the results.
It retains the filter setting until reboot/logout.

No filters. Still won't show up.

---

### Post by mc4man on 2011-10-18
if you'd like run this, copy & post the contents in a code box
```
gedit /usr/share/applications/gnome-terminal.desktop
```
The Dash shows .desktops, maybe something is wrong in it, maybe not.

When you run the command you are running the binary

If you were to add to your launcher & it disappeared after a log out/in that could also indicate an issue in the .desktop

---

### Post by FuturePilot on 2011-10-18
Here's the .desktop file

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.0.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;Unity;
X-Ayatana-Desktop-Shortcuts=New
X-Ubuntu-Gettext-Domain=gnome-terminal

[New Shortcut Group]
Name=New Terminal
Exec=gnome-terminal
TargetEnvironment=Unity
```

---

### Post by mc4man on 2011-10-18
Well - that looks fine, exactly as supplied
So there is no good reason that it doesn't show in a Dash search

Maybe try as suggested - either run from Alt+f2 & then add to the launcher or go to /usr/share/applications and Drag & Drop onto the launcher
Then do a log out/in & see if it shows

The other thing you could try is this (& log out/in after
```
cp /usr/share/applications/gnome-terminal.desktop ~/.local/share/applications/
```

---

### Post by andrecardoso on 2011-10-20
I've had the same problem after upgrade for 11.10. 

Just did the copy of .desktop files as mc4man suggested and it worked! :D

Thank you!

---

### Post by FuturePilot on 2011-10-24
I figured it out. Funny, the fix was actually the opposite of copying the .desktop file. There was already a gnome-terminal.desktop in ~/.local/share/applications that was somehow confusing Unity. I just deleted it and now it shows up in Unity.

---

