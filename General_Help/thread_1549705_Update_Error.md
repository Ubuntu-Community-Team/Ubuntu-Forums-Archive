---
title: "Update Error???"
date: 2010-08-10
forum: General Help
---

### Post by AmeliaCorwin on 2010-08-10
Hey everyone, I have this red caution icon on my toolbar, and when I click on it, the update manager starts and then I get this message:

Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Please help! :confused:

---

### Post by Peter09 on 2010-08-10
It looks like the CDRom is still enabled in Sources.
 
I believe that System->Administration->Sources (from memory) should allow you to remove it from the list of sources. Make sure the internet repositories are enabled.

---

### Post by AmeliaCorwin on 2010-08-10
Oh thanks so much! I feel stupid now a little but glad it's fixed now! 
:D

---

