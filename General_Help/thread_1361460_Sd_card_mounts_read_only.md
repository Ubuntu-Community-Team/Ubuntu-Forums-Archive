---
title: "Sd card mounts read only"
date: 2009-12-22
forum: General Help
---

### Post by MrGreen on 2009-12-22
Hi,

I have 9,10 loaded on my desktop, tried to load some files to an SD card [2gb] and got error read-only. Thing is it works fine on my laptop [9.04]

Cannot find a way to change permissions so I can use it on my desktop

Any ideas?

MrG

---

### Post by HereInOz on 2009-12-22
Can you copy files to it using sudo?

---

### Post by stew721 on 2009-12-22
I had this same problem when inserting a particular microSD, while other microSD cards mounted without issue.  I found the issue to be errors and ran fsck on it, fixing errors found.  It's mounted with full read/write permissions since.

---

### Post by MrGreen on 2009-12-22
Just loaded up card to check and have got full permissions.... very weird...thanks for your help :confused:

---

### Post by Andry22 on 2009-12-22
Yeah, I had the same case when try to load data to my phone with 1gb sd card on it, maybe it was a silly solution;) but you can try it,
I type sudo nautilus on terminal and opened my sd card from it,
but you have to be careful using this way, because you're opening nautilus in root mode, so do not delete any file on filesystem forlder or related on it..

---

