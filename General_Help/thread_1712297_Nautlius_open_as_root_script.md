---
title: "Nautlius open as root script"
date: 2011-03-22
forum: General Help
---

### Post by j_talbain on 2011-03-22
Hello all. Here is simple solution if you don't want to log in as root all the time to edit files while in Nautilus. Just open the text editor and add this ```
#!/bin/sh
gksudo nautilus
exit
```

Save as "filename".sh and then change the property under permissions to "Allow executing file as program." 
If you prefer the terminal then use ```
chmod +x /location/and/filename
```
I added a link to my top panel to have easy access to the script. If you have the default settings for nautilus if will always ask if you want to open the file in the text editor or run the script. you can disable this open if you like. Its under Edit>Preferences then choose the Behavior tab. The option is under Executable text files.

Hope this helps someone.


As usual if this post is in an inappropriate location feel free to move it.

---

### Post by QLee on 2011-03-22
You might also want to have a look at the nautilus-gksu package, it adds an , open as administrator to the right click menu.

---

### Post by Krytarik on 2011-03-22
@QLee: Thanks for the tip about "nautilus-gksu", that's fairly cool!

You could also place a launcher with the following content into "/usr/share/applications":

nautilus-browser-root.desktop:
```
[Desktop Entry]
Name=File Browser - Super-User
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=gksudo "nautilus --no-desktop --browser"
Icon=system-file-manager
Terminal=false
StartupNotify=true
Type=Application
NoDisplay=false
Categories=GNOME;GTK;System;Utility;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus
```That was used to my preferred way, you could do the same with "gedit" or whatever else.

Greetings.

---

### Post by QLee on 2011-03-22
[QUOTE=Krytarik]@QLee: Thanks for the tip about "nautilus-gksu", that's fairly cool!...[/QUOTE]
You're welcome. I use it often, don't have to mess with extra launchers or Alt+F2, just work from the file manager I already have open, it works on directories too.

---

### Post by kerry_s on 2011-03-22
i just use nautilus scripts for root stuff.

---

### Post by WorMzy on 2011-03-22
What on earth are you doing in the system directories? I think I've used Alt+F2+"gksu nautilus" twice in the past three years, you shouldn't need a launcher for it, and you should never "log in as root" in the first place. :/

---

### Post by Krytarik on 2011-03-22
> **WorMzy said:**
> What on earth are you doing in the system directories? I think I've used Alt+F2+"gksu nautilus" twice in the past three years, you shouldn't need a launcher for it, and you should never "log in as root" in the first place. :/
Then you are either not doing too much administrative stuff or you handle all the respective files/dirs from the command line. Kudos if you do the latter! ;-)

---

### Post by j_talbain on 2011-03-24
Thank you for the tip about the gksu package. 

As to why I created the launcher I'm a windows user. I am accustomed to working in a gui and having admin rights to do what I want to. I've been attempting to build a linux file server in ads and to do so I have to edit .conf files. Its a pain to do that kind of editing though the terminal. So I just launch nautilus as root navigate to where I need to be and just open my files w/o having to go through any other annoying steps. Nautilus as root makes it easy to set permissions through gui as well.

---

