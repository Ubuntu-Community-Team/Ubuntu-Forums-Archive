---
title: "Update manager error (nvidia + dvd-rom)"
date: 2010-02-07
forum: General Help
---

### Post by SilentPirate007 on 2010-02-07
I have recently stepped over to linux from windows (for obvious reasons) and everything works perfectly except for one thing. When I run an update, everything else updates, but I continuously get an error for nvidia and dvd-rom related updates (or so it seems):

[LEFT][B][COLOR=Blue]W: Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/Release.gpg)  Could not resolve 'nvidia.limitless.lupine.me.uk'

W: Failed to fetch [http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2](http://nvidia.limitless.lupine.me.uk/ubuntu/dists/edgy/stable/i18n/Translation-en_US.bz2)  Could not resolve 'nvidia.limitless.lupine.me.uk'

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz)  403  Forbidden

W: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]
[/B][/LEFT]

I don't **think** it's essential, as everything works just fine, but quite irritating.

Any solutions?

---

### Post by llawwehttam on 2010-02-07
Go to System>Administration>software sources and disable the cd and ofending repos.

Hope that works.

---

### Post by SilentPirate007 on 2010-02-07
Unfortunately not...

---

