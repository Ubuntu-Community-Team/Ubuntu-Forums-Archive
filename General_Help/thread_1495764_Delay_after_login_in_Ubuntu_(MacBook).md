---
title: "Delay after login in Ubuntu (MacBook)"
date: 2010-05-28
forum: General Help
---

### Post by alan4cult on 2010-05-28
Hi,

After I login on Ubuntu 10.04 there is a short delay (10 - 15 seconds)  before my desktop background loads and the icons are visible. After that  everything runs perfect. This has only started happening recently so  I'm not sure what the problems is?

---

### Post by dino99 on 2010-05-28
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by alan4cult on 2010-05-31
Thanks for the reply but that did not seem to work.
I have only started to have this problem recently. When I first installed 10.04 the desktop would load right away after login.

Any other suggestions?

---

### Post by alan4cult on 2010-06-02
bump

---

### Post by alan4cult on 2010-06-04
I downloaded an update from the update manager today and I think it decreaed the delay a bit. I'm pretty much a newbie so I'm not sure how to report this if it is a bug

---

