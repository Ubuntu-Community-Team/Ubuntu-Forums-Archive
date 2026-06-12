---
title: "Some problems with Ubuntu"
date: 2006-05-27
forum: General Help
---

### Post by Zweih on 2006-05-27
When entering Synaptic, I get this error;

> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

And, when trying to upgrade to Dapper, I get this message;
> Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/dists/breezy/main/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/dists/breezy/restricted/binary-amd64/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Help is duelly appreciated.

EDIT: I think this is the wrong category. So, try to be forgiving when answering to my dilemma :P

---

### Post by johnc4510 on 2006-05-27
Open synaptic, click on settings on the toolbar, choose repositories. Now the first thing in the window should be the CD. Uncheck it, close the window and rerun synaptic. This should fix it. If not report back and we'll give you the command line fix.

---

### Post by Zweih on 2006-05-27
[QUOTE=johnc4510]Open synaptic, click on settings on the toolbar, choose repositories. Now the first thing in the window should be the CD. Uncheck it, close the window and rerun synaptic. This should fix it. If not report back and we'll give you the command line fix.[/QUOTE]
Ah thanks, I did that, and I'm updrading fine now. No box with problems or anything. Thanks for the quick support.

---

### Post by johnc4510 on 2006-05-27
My pleasure, glad I could help

---

### Post by Zweih on 2006-05-27
Argh, another problem arose while upgrading;

> **"COuld not install 'nvidia-glx'"]subprocess post-removal script returned error exit status 2[/quote]
:(

And, another just popped up said:**
> Could not install the upgrades

The upgrade aborts now. Your system can be in an unusable state. A recovery was run (dpkg --configure -a).; installArchives() failed

:(

---

