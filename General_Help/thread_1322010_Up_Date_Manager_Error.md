---
title: "Up Date Manager Error"
date: 2009-11-10
forum: General Help
---

### Post by shadowfax1 on 2009-11-10
Hi there
Have this red triangle with an exclamation point in it on the top taskbar and when I click on it it starts the update manager only to inform me there has been errors...

Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


It keeps popping up..

---

### Post by JugglinPhil on 2009-11-10
It is trying to access the software provided on the Ubuntu live cd, so if you don't have the cd in your drive it's going to complain. To change that go to System => Administration => Software Sources and uncheck the Cd in the lower part of the window.

---

### Post by mikewhatever on 2009-11-10
Open 'Software Sources' under System->Admin and uncheck the cdrom box.

---

### Post by JugglinPhil on 2009-11-10
> **mikewhatever said:**
> Open 'Software Sources' under System->Admin and uncheck the cdrom box.
My words. :D

---

### Post by shadowfax1 on 2009-11-10
Thanxs...worked like a charm..not sure why...but thanxs

---

