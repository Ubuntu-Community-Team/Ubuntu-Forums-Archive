---
title: "Is it possible to change icon ot a desktop shortcut in lubuntu?"
date: 2010-08-06
forum: General Help
---

### Post by jlunse on 2010-08-06
**Note!** This is about Lubuntu 10.04 and not Ubuntu 10.04.

I have a few shortcuts on my desktop with images that doesn't look so good, not sure why and if it's possibly to configure it.

Any ideas?

---

### Post by cavalier911 on 2010-08-06
Open the *programname*.desktop file in text editor,the default location is /usr/share/applications
For example this is aqualung.desktop

[Desktop Entry]
Name=Aqualung
Comment=Gapless audio player
Exec=aqualung
Icon=aqualung.xpm
Categories=GTK;AudioVideo;Audio;Player;
Terminal=false
Type=Application
Encoding=UTF-8

For a different image aka icon change Icon=*path to new icon*

---

