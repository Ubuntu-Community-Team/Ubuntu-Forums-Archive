---
title: "Using a previous version of GCC"
date: 2009-11-23
forum: General Help
---

### Post by dgohn on 2009-11-23
I currently have GCC 4.2.4 installed.  A user on my server needs to use 4.2.3  How would he go about doing so?

---

### Post by dgohn on 2009-11-23
> **dgohn said:**
> I currently have GCC 4.2.4 installed.  A user on my server needs to use 4.2.3  How would he go about doing so?
 
bump

---

### Post by falconindy on 2009-11-23
Safest way would be to make a chroot and have the other GCC exist only in there.

---

### Post by dgohn on 2009-11-23
> **falconindy said:**
> Safest way would be to make a chroot and have the other GCC exist only in there.
Forgive my n00bness but how would I go about doing that?
 
Thanks in advance

---

### Post by falconindy on 2009-11-23
Hrmm... A proper chroot isn't all that easy to setup if you've never done so. Your other option is installing the older version of GCC manually to /usr/local/.

---

### Post by dgohn on 2009-11-24
Would installing it allow this user to use the older version while keeping the default for everyone else the newer?
 
Thanks

---

### Post by JBAlaska on 2009-11-24
> **dgohn said:**
> I currently have GCC 4.2.4 installed.  A user on my server needs to use 4.2.3  How would he go about doing so?

Easy answer: make them modify the source code to use 4.2.4.

You really let other users compile on your server?...wow

---

### Post by dgohn on 2009-11-24
I run a game hosting service so its better if I can accomodate each user if its possible.

---

### Post by JBAlaska on 2009-11-24
Well then, I may be wrong (and oft times R lol)but if you put 4.2.3 in their home path they should be ok..depending how you have their permissions setup.

---

### Post by dgohn on 2009-11-24
Ok thanks, i'll try

---

