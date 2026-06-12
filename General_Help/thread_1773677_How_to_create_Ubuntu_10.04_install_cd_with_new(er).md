---
title: "How to create Ubuntu 10.04 install cd with new(er) kernel"
date: 2011-06-02
forum: General Help
---

### Post by acroix on 2011-06-02
Hello,

can someone guide me to a document or explain here how I can create an Ubuntu 10.04 base system with a newer, updated kernel?

Background: I need to run Ubuntu 10.04 LTS on a new mac mini that requires a kernel version that first was used in 10.10.

Thank you.

A.

---

### Post by mike555 on 2011-06-02
You need to ad the kernel PPA in terminal type;
"  sudo add-apt-repository ppa:kernel-ppa/ppa  " without the quotes, enter your password and enter.......   
  of course backup first in case things break.......update .. then restart ,then install remastersys , You must have ubiquity and ubiquity-frontend-gtk installed , then do a remaster , then burn the .iso to a DVD .........

---

### Post by acroix on 2011-06-02
Thank you mike555, is this process somewhere documented, preferable step by step?  I assume I do this all on a chrooted original cd image. A.

---

