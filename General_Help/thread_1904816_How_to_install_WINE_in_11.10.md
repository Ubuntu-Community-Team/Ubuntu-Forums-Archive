---
title: "How to install WINE in 11.10"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
hi, can I install WINE and use Windows applications in Ubuntu ? Photoscape image editor is very useful to me, will I be able to use it with WINE ?

[http://www.photoscape.org/ps/main/download.php](http://www.photoscape.org/ps/main/download.php)

---

### Post by oldos2er on 2012-01-05
```
sudo apt-get update && sudo apt-get install wine
```
Check Wine's app database to see if there's a chance of getting the app you want to work. [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by meetdilip on 2012-01-05
Thanks oldos2er. Is there any security risk involved in using WINE ?

---

### Post by cortman on 2012-01-05
I've heard there it could be possible to run malware through Wine, but I think that's only in theory. Practically, I don't think there's any at all.

---

### Post by oldos2er on 2012-01-05
> **meetdilip said:**
> Thanks oldos2er. Is there any security risk involved in using WINE ?

Good question. See [https://answers.launchpad.net/ubuntu/+source/wine/+question/59148](https://answers.launchpad.net/ubuntu/+source/wine/+question/59148) and [http://wiki.winehq.org/SecuringWine](http://wiki.winehq.org/SecuringWine)

---

### Post by bluexrider on 2012-01-05
> **meetdilip said:**
> Thanks oldos2er. Is there any security risk involved in using WINE ?
Yes. Because you would be able to run .exe files.

---

### Post by meetdilip on 2012-01-05
Thanks :)

---

### Post by bluexrider on 2012-01-06
Please mark this 
(SOLVED)

---

