---
title: "What is this... a Linux virus?"
date: 2009-11-18
forum: General Help
---

### Post by emigrant on 2009-11-18
hi all,
i have no idea from where the selected file has appeared in my pen drive:

[IMG]http://img109.imageshack.us/img109/787/screenshotqz.png[/IMG]

---

### Post by ibuclaw on 2009-11-18
If you don't know what it is, don't run it, delete it and never think about it again.

But, judging by the name (and the name only).

It is just a desktop file to run:
```
nautilus --no-desktop computer:
```
In other words, open up the "Computer" page in nautilus that displays all drives.


In Gnome (and other DE's), .desktop files need to have execute permissions in order to run them, else they come up with that prompt that you see.

Regards
Iain

---

### Post by aysiu on 2009-11-18
I would open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste in the command: ```
gedit /media/Pendrive/nautilus-computer.desktop
``` and then see what's actually in the file. If you can't make sense of it, paste the code here, and we'll let you know what it does.

---

### Post by emigrant on 2009-11-18
thanks for your inputs :)

this is the output for aysiu's command.

[php]#!/usr/bin/env xdg-open
[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
TryExec=nautilus
Exec=nautilus --no-desktop computer:
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
X-Ubuntu-Gettext-Domain=nautilus[/php]by the way i doubt this appeared after i created two mount points for the same pen drive (???)
because from the other mount point, i see the 'my coumputer' icon.

---

### Post by ibuclaw on 2009-11-18
> **emigrant said:**
> thanks for your inputs :)

this is the output for aysiu's command.

[php]#!/usr/bin/env xdg-open
[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
TryExec=nautilus
Exec=nautilus --no-desktop computer:
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
X-Ubuntu-Gettext-Domain=nautilus[/php]by the way i doubt this appeared after i created two mount points for the same pen drive (???)
because from the other mount point, i see the 'my coumputer' icon.

It's exactly what I said it was ...

Which means it is harmless, but probably not needed.

Regards
Iain

---

### Post by emigrant on 2009-11-18
Thank you :-)
But may i know why it emerge all of a suddon out of nowhere?

---

### Post by jocko on 2009-11-18
> **emigrant said:**
> Thank you :-)
But may i know why it emerge all of a suddon out of nowhere?
Because you accidentally dragged the icon from the gnome menu and dropped it in a nautilus window?
And the reason it's untrusted is because it's on your pendrive, which probably has the fat32 file system which can not store file permissions properly...

---

