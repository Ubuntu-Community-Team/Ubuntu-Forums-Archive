---
title: "File Manager Doesn't work in Docky"
date: 2010-08-31
forum: General Help
---

### Post by CoolJohnB on 2010-08-31
Having got Docky to do everything I want, I now find the icon for File Manager doesn't do anything!  Well it bounces to indicate that it's working but the File Manager/Browser does not come up!

Does anyone know of a solution to this?

Any help will be much appreciated, Thanks.

---

### Post by juil on 2010-08-31
Probably a simple bug...
Try removing the file manager and then docking it again.
Try closing and re-opening your docky
Try uninstalling and reinstalling...
Try resetting your computer...

---

### Post by CoolJohnB on 2010-09-01
None of the above works!  Everything else works in Docky just not the file manager, very strange!

---

### Post by svin21 on 2010-10-04
Having a similar problem ...... I can'e find anything that makes it work:(
could someone please look into it.

---

### Post by natronite on 2010-11-28
I recently installed Ubuntu 10.10 (haven't been using Linux much up until now) and run into the same problem. I did the following.

in the file /usr/share/applications/nautilus.desktop I changed the following line
    Exec=nautilus

to Exec=nautilus /home/<username>

this worked on my machine... let me know if it helps

oh and you can use gconf-editor to make sure that Docky uses nautilus.desktop

---

### Post by CoolJohnB on 2010-11-29
Thanks for that, although I found in 10.10 by dragging the home folder onto Docky it works fine.

---

### Post by natronite on 2010-11-29
well I haven't tried that :)

and one problem with my solution suggested in my previous post is, that on every start up nautilus would open. I have found another solution but dragging the home folder seems like the easiest way...

---

### Post by 4jask22 on 2010-12-26
none of those worked on my computer please reply :popcorn:

---

### Post by txducker on 2011-01-15
I am using 10.10 64 bit. I also could not open nautilus from docky with the command: "nautilus". I had to change the command to "nautilus /home/[user name]

What worked for me was...
1. created a panel shortcut for my home folder
1.1 rt click on panel (brings up menu) and select "Add to Panel"
1.2 choose "Custom Application Launcher"
1.2.1 for field "Name": [type in any description you want]
1.2.2 for field "command": nautilus /home/[user name]
1.2.3 for field "comment": [type in anything you want]
1.3 Drag new shortcut icon to Docky

---

### Post by Rodu on 2011-01-21
> **txducker said:**
> I am using 10.10 64 bit. I also could not open nautilus from docky with the command: "nautilus". I had to change the command to "nautilus /home/[user name]

What worked for me was...
1. created a panel shortcut for my home folder
1.1 rt click on panel (brings up menu) and select "Add to Panel"
1.2 choose "Custom Application Launcher"
1.2.1 for field "Name": [type in any description you want]
1.2.2 for field "command": nautilus /home/[user name]
1.2.3 for field "comment": [type in anything you want]
1.3 Drag new shortcut icon to Docky



This worked for me. Cool! Thanks.

---

### Post by rylleman on 2011-02-03
There is a much easier way to add nautilus in the docky which I just found out.

1. open Nautilus
2. drag your home folder (or any other of your choice) from the adress bar onto Docky dock.

---

### Post by plucho on 2011-05-27
> **natronite said:**
> I recently installed Ubuntu 10.10 (haven't been using Linux much up until now) and run into the same problem. I did the following.

in the file /usr/share/applications/nautilus.desktop I changed the following line
    Exec=nautilus

to Exec=nautilus /home/<username>

this worked on my machine... let me know if it helps

oh and you can use gconf-editor to make sure that Docky uses nautilus.desktop

sudo gedit /usr/share/applications/nautilus-docky.desktop 
Paste :
[COLOR="Blue"][Desktop Entry]
Name=Docky File Browser
Comment=Browse the file system with the file manager
TryExec=nautilus
Exec=nautilus ""
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
X-GNOME-Bugzilla-Version=2.32.2.1
X-Ubuntu-Gettext-Domain=nautilus[/COLOR]

Then 
- remove "File Browser" icon from your dock
- open "applications folder"
- drag and drop the new "Docky File Browser" onto your dock

---

