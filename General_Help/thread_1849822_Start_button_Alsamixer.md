---
title: "Start button Alsamixer"
date: 2011-09-25
forum: General Help
---

### Post by ash-shaibani on 2011-09-25
I want to make a button run Alsamixer.
Created a file Alsamixer.desktop on your desktop with the following contents:

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=alsamixer
Name=Alsamixer
Icon=

```Click on the button, but nothing happens, alsamixer not start.
In Ubuntu everything works, but in Lubuntu does not work. Why?

---

### Post by ash-shaibani on 2011-09-28
OK! Let not the alsamixer. Who ever made &#8203;&#8203;a shortcut to run in Lubuntu terminal applications (Terminal = true)?

 PS
 Checked in Xubuntu shortcut works. And what about Lubuntu?

---

### Post by SteveDee on 2011-09-30
> **ash-shaibani said:**
> ...in Ubuntu everything works, but in Lubuntu does not work. Why?

I don't know why it doesn't work, but this does work:-
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=lxterminal --command alsamixer
Name=Alsamixer
Icon=

```

---

### Post by ash-shaibani on 2011-09-30
Thank you! It really works!
 I still revered man lxterminal, added title and icon. Here is the final result:
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=lxterminal -t alsamixer -e alsamixer
Name=alsamixer
Icon=gnome-mixer

```

---

