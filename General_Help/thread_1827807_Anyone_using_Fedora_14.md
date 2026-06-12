---
title: "Anyone using Fedora 14"
date: 2011-08-18
forum: General Help
---

### Post by satish_j on 2011-08-18
I know this is not the place to ask Fedora related queries,but i am not getting good response on Fedoraforums,so i thought may be i should give a try here..
I need the output of a command, _from a working Fedora 14 system_, which will list permissions of all directories(recursively)under root folder.
So,can i expect help here?I will post the exact command to be used if i get a reply from someone using F14..
Thanks..

---

### Post by dino99 on 2011-08-18
if you have some programming skills then you have to write a script to do it.

better subforum for such request:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by lmarmisa on 2011-08-18
Try this command (run this command with root privileges):

```

find / -type d -exec ls -ld {} \;

```

---

### Post by yopnono on 2011-08-18
> **lmarmisa said:**
> Try this command (run this command with root privileges):

```

find / -type d -exec ls -ld {} \;

```

Will this not do the same?

```
ls -lsaR /
```

---

### Post by lmarmisa on 2011-08-18
> **yopnono said:**
> Will this not do the same?

```
ls -lsaR /
```

The command I proposed shows only directories. This is the main difference with yours.

---

### Post by yopnono on 2011-08-18
> **lmarmisa said:**
> The command I proposed shows only directories. This is the main difference with yours.

Right, your right :)

---

### Post by satish_j on 2011-08-18
well, i need not the command,but the output of the command from a working Fedora 14 system..

---

### Post by bodhi.zazen on 2011-08-18
Thread closed. Your question was asked and answered on the Fedora forums.

boot a F14 updated cd / iso using a usb of virtualbox and take a look for yourself ;)

---

