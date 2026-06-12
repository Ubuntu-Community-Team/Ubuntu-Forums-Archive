---
title: "synaptic package manager help"
date: 2010-10-06
forum: General Help
---

### Post by hawkerman on 2010-10-06
I'm brand new to Ubuntu, using 10.04, 32 bit.  I recently turned the computer on, the Synaptic package manager ran an update, but this message appeared. What do I do? and why did it happen? Thanks, so far this is the only hiccup, I have come across, otherwise loving Ubuntu.

Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cgroza on 2010-10-06
Its nothing, but you should disable the cd-rom as source from the Software Sources.
Do you have a CD in the CD-ROM?

---

### Post by hawkerman on 2010-10-06
That seems to have done the trick. I unchecked the CDrom box in the Software sources section, then ran the synaptic update, no errors. Whats odd is, I never checked that box before, why was it never a problem before? And no, I did not have a disc in the drive. 

Thanks a bunch, I'm still learning a lot about Ubuntu.

---

