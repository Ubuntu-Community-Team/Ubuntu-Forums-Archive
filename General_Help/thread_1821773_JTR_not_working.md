---
title: "JTR not working"
date: 2011-08-09
forum: General Help
---

### Post by chidat on 2011-08-09
Hi,

I'm trying to work on the SmashTheStack wargame on Ubuntu, and I'm stuck at level 1 with using John the Ripper (JTR). I got the encrypted password and was able to run JTR on it using
```
sudo john -single pass.txt
```
but the output is
```
Loaded 1 password hash (FreeBSD MD5 [32/32])
guesses: 0  time: 0:00:00:00 100%  c/s: 3137  trying: user1900

```
I'm pretty sure that the 'trying:' part is supposed to be the attempted passwords, but this one doesn't work, and this is the only one that gets output. When I run
```
sudo john -show pass.txt
```
I get
```
0 password hashes cracked, 1 left
```
which I'm guessing means that nothing happened.. what am I doing wrong, and how can I get it to work? Thanks!

---

### Post by Basher101 on 2011-08-09
The hash is just the fingerprint of the password. You must do additional steps to actually get the password. I do not know these so google could help..

---

