---
title: "Could not download all repository indexe"
date: 2009-09-28
forum: General Help
---

### Post by BAMF1501 on 2009-09-28
ok i think i found the reason to why my cd drive aint working in 9.10 but not how to fix it says all this i think it means somthing..

```

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct
```


> Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by BAMF1501 on 2009-09-28
and says this in updater manager when updating for updated 

and im connected to internet

Failed to download repository information

Check your Internet connection


details


W:Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by BAMF1501 on 2009-09-28
bump

---

### Post by plucky on 2009-09-28
Are you running Jaunty or Karmic?

Open **System > Administration > Software Sources** And un-tick the boxes that have the CD-rom as a source.Reload and see if you still have the problem.

Good luck

---

