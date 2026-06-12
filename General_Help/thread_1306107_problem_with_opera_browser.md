---
title: "problem with opera browser"
date: 2009-10-30
forum: General Help
---

### Post by shaon3343 on 2009-10-30
[SIZE="2"][B]hi 
I've installed opera from a .deb package. after installation today i run the *"sudo apt-ger update"* in terminal. after updating list the terminal shows these line:[/B] [/SIZE]

[SIZE="3"]W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch[/SIZE]

**[SIZE="2"]So anybody can tell me what should i do??[/SIZE]**

---

### Post by pi4r0n on 2009-10-30
Try Solution No1 should be OK after that if not try No 2

**Solution No1** Type this in terminal

> gpg --keyserver keyserver.ubuntu.com --recv [last 8 characters of code]; gpg --export --armor [last 8 characters of code] | sudo apt-key add

**Solution No2** Do [this]("http://ubuntuforums.org/showthread.php?t=1261873")

Ta

pi4r0n

---

### Post by shaon3343 on 2009-10-30
please pardon me, what do you mean by "last 8 character of code" ?

---

### Post by sisco311 on 2009-10-30
this should work:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get update
```

---

### Post by shaon3343 on 2009-10-30
thaks all to help me , it really worked ( with the wget ... command) . thanksss. :D

---

