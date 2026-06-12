---
title: "PPA repository adding by one click -  with FF addons + bash"
date: 2010-01-05
forum: General Help
---

### Post by sevoir on 2010-01-05
```
gconftool-2 -t string -s /desktop/gnome/url-handlers/ppa/command 'ppa.sh "%s"'
gconftool-2 -s /desktop/gnome/url-handlers/ppa/needs_terminal true -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/ppa/enabled true

mkdir -p ~/.gnome2/vfolders/applications
nano ~/.gnome2/vfolders/applications/ppa.desktop
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=PPA adding
Comment=ppa protocoll linker
Exec=ppa.sh
Icon=none.png
Terminal=false
Type=Application
Categories=Application;Internet;

sudo su
echo '#!/bin/sh' > /usr/bin/ppa.sh
echo 'gksu add-apt-repository $1' >> /usr/bin/ppa.sh
echo 'gksu apt-get update' >> /usr/bin/ppa.sh
chmod +x /usr/bin/ppa.sh
exit
```

**Firefox extension link:** [add-apt-repository from html]("https://addons.mozilla.org/hu/firefox/addon/57804")

**Before addons:**
[IMG]http://www.sevoir.hu/uploads/ppaelott.png[/IMG]

**After added addons:**
[IMG]http://www.sevoir.hu/uploads/ppautan.png[/IMG]

Regards, Sevoir

---

