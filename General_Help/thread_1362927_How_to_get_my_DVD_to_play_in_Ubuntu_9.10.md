---
title: "How to get my DVD to play in Ubuntu 9.10?"
date: 2009-12-23
forum: General Help
---

### Post by losthighway on 2009-12-23
Hey everyone. I installed Ubuntu 9.10 and seem to be having an issue playing DVDs. Movie Player won't play it, and I tried VLC and Dragon Player and they both had the same result. Is there something I need to install or download? Thanks.

---

### Post by oakgrove on 2009-12-23
In a terminal:
```
$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
```

$ sudo apt-get install libdvdcss2
```
Should fix you right up

---

### Post by headflux on 2010-01-06
Thanks... I had this same problem and your fix worked a treat.

---

