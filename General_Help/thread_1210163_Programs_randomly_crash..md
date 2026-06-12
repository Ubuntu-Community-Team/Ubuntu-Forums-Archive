---
title: "Programs randomly crash."
date: 2009-07-11
forum: General Help
---

### Post by dragos240 on 2009-07-11
I'm not sure why, but some of my programs have been crashing lately, I have no idea why....

I have run some of these programs in the terminal, and got a segfault.

---

### Post by ibuclaw on 2009-07-11
Any specific program?
What were you doing when the segfault occurred?
Have you tried the same application on a different workstation/OS?
If so, did something similar happen?

Regards
Iain

---

### Post by dragos240 on 2009-07-11
> **tinivole said:**
> Any specific program?
What were you doing when the segfault occurred?
Have you tried the same application on a different workstation/OS?
If so, did something similar happen?

Regards
Iain

I have one, computer at this house. I was originally playing toribash 3.5, and suddenly, it started crashing, also update-manager, any kde feature, and totem.

---

### Post by ibuclaw on 2009-07-11
mkay, could you post the following, if you have experienced a segmentation fault from several programs today:
```
dmesg | grep segfault
```

Regards
Iain

---

### Post by dragos240 on 2009-07-11
> **tinivole said:**
> mkay, could you post the following, if you have experienced a segmentation fault from several programs today:
```
dmesg | grep segfault
```Regards
Iain

I wonder why my other programs weren't working then.... 
```

~$ dmesg | grep segfault
[32751.472389] update-manager[8469]: segfault at 6c ip 0000006c sp bfe30c1c error 4 in python2.6[8048000+1dd000]
[32757.499392] update-manager[8473]: segfault at 6c ip 0000006c sp bffc0dac error 4 in python2.6[8048000+1dd000]
[32761.868393] update-manager[8477]: segfault at 6c ip 0000006c sp bfb7e96c error 4 in python2.6[8048000+1dd000]
[32871.054101] update-manager[8490]: segfault at 6c ip 0000006c sp bf86d65c error 4 in python2.6[8048000+1dd000]
[32897.298025] update-manager[8525]: segfault at 6c ip 0000006c sp bfcabd5c error 4 in python2.6[8048000+1dd000]

```

perhaps it's because I only opened update manager in a terminal.

---

### Post by ibuclaw on 2009-07-11
Hmm, dunno, but just incase, try running a full upgrade on your system.

```
sudo aptitude update && sudo aptitude full-upgrade
```

Regards
Iain

---

