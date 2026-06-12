---
title: "Blank the screen from command line"
date: 2011-12-01
forum: General Help
---

### Post by edm1 on 2011-12-01
Im using 11.10 and would like to add an icon to the Unity launcher that blanks the screen when i press it. Does anyone know a command that blanks the screen? I think i could take it from there. Thanks.

---

### Post by carranty on 2011-12-01
Well, pressing Ctrl - Alt - L will cause the screen to go straight to your screensaver, so you could choose a blank one.  However this will also lock the screen and require your user password to unlock.  

If that's not what your looking for compiz might have something.  Have you compiz config settings manager installed?  For example the 'Paint fire on screen' effect cab be triggered (and disabled) with any command you like, set background brightness to zero and you'll essentially have a blank screen.  This is a bit of a long winded way of doing it, and theres probably a much simpler way - but I don't know what it is.

EDIT : Ignore that last paragraph, I don't think compiz works well with Unity.

---

### Post by hakermania on 2011-12-01
```
xset dpms force standby
```

---

### Post by carranty on 2011-12-01
> **hakermania said:**
> ```
xset dpms force standby
```

^ This

---

### Post by edm1 on 2011-12-01
Thanks guys, perfect. For anyone interested, I will post how to add your own launcher icon when i get round to doing it. It is pretty simple.

---

### Post by edm1 on 2011-12-01
Anyone wanting to do what i was trying achieve just

```
gedit ~/.local/share/applications/blankscreen.desktop &
```

then paste this in

```

[Desktop Entry]
Version=1.0
Name=Blank Screen
Exec=xset dpms force standby
Terminal=false
Icon=/usr/share/pixmaps/gnome-term-night.png
Type=Application
MimeType=application/x-blankscreen;
Categories=System;
GenericName=Blank Screen
Comment=Blank Screen on press
Name[en_GB]=blankscreen.desktop
```

Then drag the file ~/.local/share/applications/blankscreen.desktop to the launcher (may need to hit Ctrl+H to see hidden .local file).

---

