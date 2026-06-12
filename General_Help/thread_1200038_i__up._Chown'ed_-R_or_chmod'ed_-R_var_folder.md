---
title: "i ****** up. Chown'ed -R or chmod'ed -R /var/ folder"
date: 2009-06-29
forum: General Help
---

### Post by niiklas on 2009-06-29
Hello i by misstake without knowing the concequences chmod'ed/chown'ed my /VAR/ folder. Im not sure which one it was i did it yesterday, and today i noticed i could no longer ssh to my system or use phpmyadmin. I get this error Wrong permissions on configuration file, should not be world writable!.

How can i reset it to its original state?, i still got access to a web based cron editor so i can probably execute code from there.

EDIT:
IT's a virtual private server so i got no physical access to the server..

---

### Post by liviubero on 2009-06-29
The defaults are by me:
```
> ls -ld /var/
drwxr-xr-x 15 root root 4096 2009-04-22 21:22 /var/
```

Hope this helps and this what you are looking for.

---

### Post by niiklas on 2009-06-29
cant get it to work looks like im screwed big time :s

---

### Post by liviubero on 2009-06-29
What do you mean by that?
Can you post the ouput of 
```
ls -ld /var/
```

---

