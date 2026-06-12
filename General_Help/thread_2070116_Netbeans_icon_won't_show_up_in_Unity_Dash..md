---
title: "Netbeans icon won't show up in Unity Dash."
date: 2012-10-12
forum: General Help
---

### Post by stchman on 2012-10-12
Hello all, I installed Netbeans 7.2 and the icon REFUSES to show up.

The netbeans7-2.desktop file is as follows:

```

[Desktop Entry]
Encoding=UTF-8
Name=NetBeans IDE 7.2
Comment=The Smarter Way to Code
Exec=/bin/sh "/opt/netbeans-7.2/bin/netbeans"
Icon=/opt/netbeans-7.2/nb/netbeans.png
Categories=Development;
Version=1.0
Type=Application
Terminal=0

```I have tried 

```

sudo update-desktop-database

```with no success.

Does anyone have ANY ideas?

Thanks.

---

### Post by DarkAmbient on 2012-10-12
If nothing else goes, you can do it yourself.

Save that launcher-information in a textfile named netbeans.desktop to your homefolder.

Then open a terminal (ctrl+alt+t) and paste this:

sudo mv ~/netbeans.desktop /usr/share/applications/netbeans.desktop

---

### Post by stchman on 2012-10-12
You can also create a Unity launcher by using the alacarte package, I was just wanting to see if there was a fix for this.  By all means that .desktop file should work.

---

