---
title: "Add program to Unity?"
date: 2010-10-13
forum: General Help
---

### Post by mb_webguy on 2010-10-13
So I'm trying out the new netbook edition, and it has potential, but I've run into one major snag.  I have a few scripts and 3rd-party apps that I normally add to the applications menu using Alacarte (or Add Launcher to a Gnome panel).  But neither of those methods work in Unity.

I used the method described in [this thread]("http://ubuntuforums.org/showthread.php?t=1578379") to add a program to the Unity launcher bar, but the program *only* shows up in the launcher bar, and not Unity's applications menu.  I don't use most of these programs often enough to warrant adding them all to the launcher bar, but I do want to be able to access them through the desktop rather than the terminal.

Not being able to add custom programs is pretty much a dealbreaker for a desktop environment, and I'm sure a convenient way to do so along the lines of Alacarte will become available in the future, but how are we supposed to do it until then?

---

### Post by kerry_s on 2010-10-13
have you tried logging out & back in, unity menus don't update till after.

---

### Post by mb_webguy on 2010-10-13
Yep.  I had to do that to get it to show up on the Unity launcher bar.  But the same program isn't showing up on the Unity Applications screen.  For this particular program, it doesn't matter since I use it frequently.  But for some others, I don't need them on the launcher bar, but I'd like to be able to start them without opening the terminal.

Just in case it helps, for this program (a simple bash script that initiates a VNC connection over ssh), I created the following desktop file called "/usr/share/applications/vnc_archive.desktop":```
[Desktop Entry]
Name=Remote Desktop (Media Server)
Comment=
Exec=/home/matt/bin/vnc_archive
Icon=vinagre
Terminal=false
Type=Application
StartupNotify=true
```
It seems like that should have been enough to have it show up on the Applications screen (after starting a new session), but it didn't.  However, once I created the "~/.gconf/desktop/unity/launcher/favorites/app-vnc_archive.desktop" folder and edited the xml files, it showed up on the launcher bar (after starting a new session).  It's still not showing up in the Applications menu, though, which is the problem.

I've tried creating desktop files in /usr/share/applications for my other scripts and programs, but nothing ever shows up in the Unity Applications screen.

---

### Post by mb_webguy on 2010-10-13
Ok...  I seems like I've solved the problem.  Unity apparently requires desktop files to have a Category parameter in order to show up on the Applications screen.  It doesn't seem to matter what the Category is, as long as it's there.  Once I added a Category line to my desktop files and logged out, everything was fine.

---

### Post by Anessen on 2010-12-02
I'm having the same problem. My .desktop file is even a direct copy of another one that works, with the file name and the program name changed. It still won't show after relogging!

---

