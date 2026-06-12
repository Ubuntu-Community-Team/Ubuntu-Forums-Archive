---
title: "LTS with newer repo's?"
date: 2011-11-28
forum: General Help
---

### Post by cyb3r_sn4k3 on 2011-11-28
I prefer to stick to LTS' as they tend to be more stable and I dont like upgrading alot. But a problem is that the repo's tend to be a little outdated for eg. The Arduino IDE is available in the 11.04 repo but not in the 10.04. Similarly, when I install Mono develop on 10.04 it only installs an old version and I have to manually install a newer version. Is there a work around for this? Maybe using newer repos?

---

### Post by mastablasta on 2011-11-28
using PPA's can keep you up to date with programmes while staying on LTS.

---

### Post by directhex on 2011-11-28
There are occasional third-party repos or PPAs for specific apps. e.g. I have a Mono repo on badgerports.org

---

### Post by BC59 on 2011-11-28
You could use the Ubuntu Backports for 10.04:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main universe multiverse restricted

You'll find here the Guide on how to:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by cyb3r_sn4k3 on 2011-11-28
> **BC59 said:**
> You could use the Ubuntu Backports for 10.04:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main universe multiverse restricted

You'll find here the Guide on how to:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


Looks like its what I need! Thanks!

---

