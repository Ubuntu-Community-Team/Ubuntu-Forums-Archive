---
title: "john the ripper error"
date: 2011-06-16
forum: General Help
---

### Post by nethero on 2011-06-16
Hi there,

I have a md4 hash that I want to crack using john the ripper.  I downloaded the 1.7.7 jumbo version [from here]("http://www.openwall.com/john/").  I have my hash in a text file.  I typed...

```
john --format=raw-md4 /home/user/Desktop/hash.txt
```However, I get this error...

```
Loaded 1 password hash (Raw MD4 [32/32])
Crash recovery file is locked: ./john.rec
```What am I doing wrong?

EDIT:

Solved it.  In the hash file I had only entered my hash value.  I was supposed to enter something like  name:hash, name can be anything but there has to be a colon.  I reentered is as test:897634afd0982374....... and john the ripper worked.

---

