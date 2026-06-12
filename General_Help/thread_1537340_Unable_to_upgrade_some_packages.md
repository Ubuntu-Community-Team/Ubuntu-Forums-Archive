---
title: "Unable to upgrade some packages"
date: 2010-07-23
forum: General Help
---

### Post by jsvidyad on 2010-07-23
Hello,

   I ran sudo apt-get update and sudo apt-get dist-upgrade . It says that 3 packages are not upgraded. Thet are linux-generic, linux-image-generic and linux-headers generic. I have never had this problem when using sudo apt-get dist-upgrade since it is supposed to resolve all conflicts and other issues with upgrades. Can anyone tell me how I can upgrade those three packages?
:(

---

### Post by jimmyjones on 2010-07-23
Ditto,

glad it's not just me.

Must be broken on their end.

---

### Post by jsvidyad on 2010-07-23
Hello,

  I just wanted to add that the computer with this problem is running 32 bit ubuntu 10.04

---

### Post by mc4man on 2010-07-23
Wait awhile - when all the packages needed for the upgrade are available then the upgrade will proceed.

---

### Post by kiddykoff on 2010-07-23
I got the same problem, i'm running 64 bit Lucid.

---

### Post by Lucifer The Dark on 2010-07-23
mc4man is right, I had the same problem with some other packages last week because one needed update package wasn't ready at the time. It'll be fixed quickly enough, I had to wait 24 hours for mine.

---

### Post by vanquishedangel on 2010-07-24
I just updated to the Linux headers right off the site and then the updates installed and were no longer grayed out hope this works for the rest of ya

[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

---

### Post by vanquishedangel on 2010-07-24
> **vanquishedangel said:**
> I just updated to the Linux headers right off the site and then the updates installed and were no longer grayed out hope this works for the rest of ya

[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

 please ignore this post iy messed up my vidoe drivers and games wouldnt play, if you followed it and had issues, "sudo aptitude purge" the files and then run "sudo update-grub"

---

