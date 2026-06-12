---
title: "Update Error"
date: 2011-08-10
forum: General Help
---

### Post by Gargon0 on 2011-08-10
hi. i came back from college and found that the desktop that im currently on now needed to be updated. it was long overdue. but when i tried to update via the gui manager and terminal i got this error message (in photo). please help me correct this. thank you very much...btw am using Ubuntu 11.04

---

### Post by mmsmc on 2011-08-11
type this in terminal and please post results gksu gedit /etc/apt/sources.list

---

### Post by sikander3786 on 2011-08-11
There is a problem with your apt merge lists. You can simply go to a Terminal and run these commands:

```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

Now open Update Manager and everything should be fine.

Post # 2 here:

[http://ubuntuforums.org/showthread.php?t=1635115](http://ubuntuforums.org/showthread.php?t=1635115)

---

### Post by Gargon0 on 2011-08-11
thank you for the quick response guys. i got it working with the suggestion

---

