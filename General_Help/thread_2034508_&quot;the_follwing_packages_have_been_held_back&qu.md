---
title: "&quot;the follwing packages have been held back&quot;"
date: 2012-07-28
forum: General Help
---

### Post by TroyMW on 2012-07-28
Sometimes when I run 'apt-get upgrade' from the command line I get a message saying "the following packages have been held back".  This usually happens when there are updates to the linux-generic linux-headers-generic linux-image-generic packages?  Why does this happen?

---

### Post by cwsnyder on 2012-07-28
The proper usage is ```
sudo apt-get update
sudo apt-get dist-upgrade
``` to get all held back updates.  The updates are held back to prevent possible system regression (where your system breaks when it was working before the update).

---

### Post by annnomius on 2012-08-07
hmmm....

i have had a probelm for a while now related to this (mostly an annoyance, but i would like to know why it is occuring):
i have 2 packages that are always held back. even after the dist-upgrade they are held back:
```
>sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ibus-hangul nabi
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```any idea why this happens?

---

