---
title: "Open Containing Folder in Firefox opens kid3-qt"
date: 2011-05-01
forum: General Help
---

### Post by master-m on 2011-05-01
Hi,

I'm running Kubuntu 10.10 with Firefox 4.0.1. from the firefox ppa.
If I want to open the folder of a downloaded file with the right-mouse-button menu, kid3-qt is opened and shows the folder.
I already tried the following:

[LIST=1]
[*]Removed kid3-qt -> Dolphin opens the folder, kid3-qt reinstalled leads to the same behaviour as before
[*]Reinstalled Firefox -> no change
[*]Removed the .mozilla dir to create a new profile -> no change
[*]mimeapps.list in ~/.local/share/applications looks like this:
[/LIST]
```
[Added Associations]
application/pdf=kde4-okular.desktop;
application/vnd.openxmlformats-officedocument.spreadsheetml.sheet=wine-Programs-Microsoft Office-Microsoft Office Excel 2007.desktop;
application/x-wine-extension-ini=kate-2.desktop;
application/x-wine-extension-mas=kate-2.desktop;
application/x-zerosize=kate-2.desktop;
audio/mpeg=kid3-qt.desktop;
inode/directory=kde4_dolphin.desktop;

[Added KDE Service Associations]
inode/directory=dolphinpart.desktop;

[Removed Associations]
application/x-wine-extension-mas=wine-extension-mas.desktop;

[Removed KDE Service Associations]
inode/directory=konsolepart.desktop;fsview_part.desktop;cervisiapart.desktop;konq_sidebartng.desktop;

```I also tried to bang my head against the desk, but to no avail.

Is there another location, which defines the applications for inode/directory?

Thanx,
Martin

---

### Post by ufleisch on 2011-05-02
You can either remove "inode/directory;" from the line starting with "MimeType=" in /usr/share/applications/kid3-qt.desktop (and then run update-desktop-database) or install version 1.6 of kid3-qt from [http://kid3.sourceforge.net](http://kid3.sourceforge.net).

Regards,
Urs

---

### Post by master-m on 2011-05-02
The first suggestion worked perfectly.

Yeah, thanks a lot! :)

---

