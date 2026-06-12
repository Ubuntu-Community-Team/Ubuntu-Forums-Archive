---
title: "ubuntu refusing to update and bugs"
date: 2010-02-27
forum: General Help
---

### Post by Cjtouhey on 2010-02-27
hey since my last notified update ive been having some problems, 1 being that it wont look for new updates it keeps giving me this error message 

Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

i tried the command in the error message that it advises but no luck
2 virtual box now refuses to work giving me a software source error
and 3 my screen saver wont show just goes black

can any one help me , thank you :)

---

### Post by 2hot6ft2 on 2010-02-27
I suspect that you have a cd in the drive and have it set to use the cd for sources since it keeps trying to get them from the cd. Go to
System > Administration > Software Sources
Uncheck the box in the bottom box so it wont look at the cd for packages.

---

### Post by Cjtouhey on 2010-02-27
cheers man virtual box still isnt letting me run still though it keeps giving me this error, 

 p, li { white-space: pre-wrap; }     Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  Machine
   Interface: 
  IMachine {540dcfda-3df2-49c6-88fa-033a28c2ff85}

 p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-source package.

could it have somthing to do with the last update?

---

