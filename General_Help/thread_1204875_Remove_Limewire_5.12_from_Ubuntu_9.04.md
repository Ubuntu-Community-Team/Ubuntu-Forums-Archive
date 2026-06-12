---
title: "Remove Limewire 5.12 from Ubuntu 9.04"
date: 2009-07-05
forum: General Help
---

### Post by james.brantley on 2009-07-05
[SIZE=3]Hello all, I have searched for this topic and I find it, but not an answer to my issue. I would like to remove Limewire 5.12 and apt-get remove is not helping. I did a search for the .deb file and could not find it. I know this has been discussed but as I say I could not find a resolution just discussion on the issue.

edit: Limewire is not showing up with "apt-cache search KEYWORD"
[/SIZE]

---

### Post by scouser73 on 2009-07-05
Hi James, did you enter this command: **apt-get --purge remove** appX [where appX would be the software you wish to delete].

---

### Post by james.brantley on 2009-07-05
> **scouser73 said:**
> Hi James, did you enter this command: **apt-get remove --purge** appX [where appX would be the software you wish to delete].

[SIZE=2]Just tried it and "couldn't find package limewire"[/SIZE]

---

### Post by james.brantley on 2009-07-05
I just tried this and it worked!

dpkg -r limewire-basic

---

### Post by aklilom on 2010-01-27
> **james.brantley said:**
> I just tried this and it worked!

dpkg -r limewire-basic

This worked for me too (on Ubuntu 9.10). Thanks.

---

