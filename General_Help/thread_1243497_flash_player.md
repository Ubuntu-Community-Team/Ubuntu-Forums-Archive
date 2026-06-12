---
title: "flash player"
date: 2009-08-18
forum: General Help
---

### Post by jojom271 on 2009-08-18
i tried to download adobe flash player 10 and install it. when installing it said i had a older version and would not let me install. what do i do? i also tried terminal it did not find it. maybe i am using wrong command

---

### Post by AmerNewbieInDE on 2009-08-18
This is funny, when i downloaded it, it would not install because it said i had a newer version..  But i dont

---

### Post by Dakiraun on 2009-08-18
Why not use the one(s) in the repositories?  The current multiverse repo for Jaunty has v10.0.32.

---

### Post by AmerNewbieInDE on 2009-08-18
because my flash doesnt work, am always getting a grey screen.

---

### Post by mhgsys on 2009-08-18
[http://ubuntuforums.org/showthread.php?t=1243506](http://ubuntuforums.org/showthread.php?t=1243506)

jojom271 > multiple threads are not handy

---

### Post by credobyte on 2009-08-18
```
sudo apt-get install flashplugin-nonfree

```

To check your current version ( only if installed via Aptitude ):
```
sudo aptitude show flashplugin-nonfree
```

---

### Post by bardictiger on 2009-08-23
I'm having multiple problems in installing Flash 10.  I download and install the DEB package from the Flash website.  The computer tells me that 10 is installed but I did the sudo aptitude show command it told me that 10 is not installed but that it's up to date.  When I go to websites which require Flash 10, I can't do anything.  HELP!

---

