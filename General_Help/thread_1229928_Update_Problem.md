---
title: "Update Problem"
date: 2009-08-02
forum: General Help
---

### Post by twallace on 2009-08-02
New to Ubuntu and everything has been fine until this error message when trying to update: E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

HELP !

---

### Post by j.bell730 on 2009-08-02
Try:
```
sudo pkill apt
```

---

### Post by twallace on 2009-08-02
Tried that and now it's asking for a password???

---

### Post by michy99 on 2009-08-02
Give it your user password that you use to log on.

---

### Post by twallace on 2009-08-02
Tried that but it wouldn't let me enter anything, looks like it's updating now after I did a reboot...

---

### Post by j.bell730 on 2009-08-02
When it asks for a password like that, you won't see any feedback, not even stars or dots. All you need to do is type your password and press enter.

---

### Post by Soul-Sing on 2009-08-03
Close [COLOR="Red"]any[/COLOR] other package managers

if that doesn’t do anything:
```
rm /var/lib/dpkg/lock
```
```
rm /var/cache/apt/archives/lock
```

(please copy/paste commands)

---

### Post by twallace on 2009-08-23
1st idea seems to be working...

---

