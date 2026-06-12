---
title: "need to stop apt-get -f install"
date: 2010-10-14
forum: General Help
---

### Post by sonicb00m on 2010-10-14
I tried to upgrade deluge frm the  PPA on my ubuntu server lucid and it wanted to install loads of GTK packages which i didn't want.

I can't do anything with apt now except run 

apt-get -f install

I can't remove, or stop it from want to fix the problem and install loads of crap i don't want.

How do i fix it?

---

### Post by sonicb00m on 2010-10-14
I fixed it by purging the packages with aptitude.

---

