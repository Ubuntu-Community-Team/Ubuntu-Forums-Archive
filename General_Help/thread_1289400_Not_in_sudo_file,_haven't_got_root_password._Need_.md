---
title: "Not in sudo file, haven't got root password. Need help! :)"
date: 2009-10-12
forum: General Help
---

### Post by oxymoron on 2009-10-12
Hi,

I bought my first netbook this afternoon, got it home and wiped ubuntu 8.04 from it and installed the atom optimized version of 9.04. 

All went smoothly until I tried to use update manager. Apparently my username isn't on the sudoers file! This being ubuntu I also wasn't allowed to set a root password during installation. Basically I'm totally locked out.

How to fix?

Regards

---

### Post by sisco311 on 2009-10-12
Reboot in recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by jeremyswalker on 2009-10-12
You could try to boot into Recovery Mode. Once at the root console, type "passwd" (without quotes). This will prompt you to enter a new password, thus enabling root login.

EDIT: Actually, sisco311's solution is likely the better option. I forgot to mention adding yourself to the admin group.
```
adduser *username* admin
```

---

### Post by wojox on 2009-10-12
Here this should fix sudo: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Dam you all beat me to it!

---

### Post by oxymoron on 2009-10-12
Thanks for that link, it solved it!

---

