---
title: "Auto Starting Application only GNOME not in KDE"
date: 2010-06-23
forum: General Help
---

### Post by bhopalino1 on 2010-06-23
Dear Friends,
How Can I ensure that AWN Dock+Compiz start ONLY in GNOME, While they should not autostart when I log into KDE. 
 
Also, Currently I have bunch of applets working in GNOME but they show error in KDE...
 
Any help is appreciated...

---

### Post by 3Miro on 2010-06-23
In KDE got to System Settings and I believe in advanced you will find a list of startup applications.

By default compiz doesn't start under KDE, however, AWM might.

---

### Post by Deadite81 on 2010-06-23
Another way is this, which is handy to know.
In Nautilus or Dolphin or Whatever navigate to the hidden folder /home/you/.config/autostart.  In this folder you should see a bunch of .desktop files.  These are the actual launchers of the applicable programs.

Being launchers, you can't double click them to open them in a text editor, but you can drag and drop them into Gedit/Geany/Kate/Whatever to see and edit their content.

Here is my ~/.config/autostart/awn.desktop file's content:
```

[Desktop Entry]
Name=Avant Window Navigator
Exec=avant-window-navigator --startup
Encoding=UTF-8
Type=Application
X-GNOME-Autostart-enabled=true
Icon=avant-window-navigator
```
Now, if you want it to only start in your Gnome session you can simply add the line:
```
OnlyShowIn=GNOME;
```
Similarly, you can use the lines:
```
OnlyShowIn=KDE;
```
and
```
OnlyShowIn=XFCE;
```
The order is irrelevant, as long as this line is present on it's own line in any of these autostart files it will only appear in the desktop environment you choose.

So my awn.desktop file would look like this:
```

[Desktop Entry]
Name=Avant Window Navigator
Exec=avant-window-navigator --startup
Encoding=UTF-8
Type=Application
X-GNOME-Autostart-enabled=true
Icon=avant-window-navigator
OnlyShowIn=GNOME;
```
This also works on your menu item files in ~/.local/share/applications and /usr/share/applications.

As for the applets, I'm not sure about that one...you mean panel applets?  KDE loads Gnome panel applets?

---

### Post by bhopalino1 on 2010-06-23
Thanks 3Miro and Deadite81!
 
3Miro, 
I did changes in My startup application in KDE but they are also reflecting in GNOME ;( 
 
I will try what Deadite81 suggested...
 
 
Also I am talking about AWN Dock applets --- they do not work in KDE like Stack applet..

---

### Post by Morbius1 on 2010-06-23
Deadite81, That's very interesting.
> Being launchers, you can't double click them to open them in a text  editor, but you can drag and drop them into Gedit/Geany/Kate/Whatever to  see and edit their content.You might try this to expedite this process:
Create a nautilus-script:
```
gedit /home/username/.gnome2/nautilus-scripts/Edit
```With this content:
```
#!/bin/sh
exec gedit "$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)"
```Make the script executable.

Now you can right click on ~/.config/autostart/awn.desktop > choose Scripts > Edit and it will load the file into gedit.
I don't know if there is a KDE counterpart to this.

---

### Post by Deadite81 on 2010-06-23
> **Morbius1 said:**
> Deadite81, That's very interesting.
You might try this to expedite this process:
Create a nautilus-script:
```
gedit /home/username/.gnome2/nautilus-scripts/Edit
```With this content:
```
#!/bin/sh
exec gedit "$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)"
```Make the script executable.

Since I deal with these files a lot that's exactly what I do!  I have a script for Mousepad (simple & quick), Gedit, and Jedit.  I also have scripts to open these text editors as root, to avoid the command line or having to open a root Nautilus:
```

#!/bin/bash
gksudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS

```
VERY convenient!

---

