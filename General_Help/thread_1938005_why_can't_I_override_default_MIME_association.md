---
title: "why can't I override default MIME association"
date: 2012-03-08
forum: General Help
---

### Post by thenilly on 2012-03-08
fyi:

```

@panda:~$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

For tinkering purposes, I would like to open jpeg files with a custom program (which will write to a log and then open the file with the default app.)

I have my own .desktop file called anyware.desktop located in ~/.local/share/applications which looks like this
```

[Desktop Entry]
Name=Anyware Player
Comment=Testing anyware
Exec=/home/maria/anyware/proto/getexec.py %U
Icon=totem
Terminal=false
Type=Application
StartupNotify=true
MimeType=image/jpeg

```

I modified mimeapps.list, mimeinfo.cache, and defaults.list (all in the ~/.local/share/applications folder) to include the line
```

image/jpeg=anyware.desktop

```

I also ran update-desktop-database and logged out and back in.

And still if I double-click on my jpeg, it opens with ImageViewer.

Why am I not able to over-write the defaults??

---

