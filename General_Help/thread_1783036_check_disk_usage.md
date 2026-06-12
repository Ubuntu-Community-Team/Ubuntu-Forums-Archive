---
title: "check disk usage"
date: 2011-06-15
forum: General Help
---

### Post by pacalici on 2011-06-15
hello,

i installed ubuntu via wubi. from windows, how can i check how much disk is ubuntu consuming?

thanks

---

### Post by lmarmisa on 2011-06-15
Open a terminal and type this command:

```

df -h

```

Wubi disk (Ubuntu root partition) is /dev/loop0. 

Windows partition is /dev/sda1.

---

### Post by Frogs Hair on 2011-06-15
From the Disk Utility under root disk or from the System Monitor uder file system. With Wubi you select up to 30Gb during installation.

---

### Post by pacalici on 2011-06-15
thanks, lmarmisa, this did the trick

> **lmarmisa said:**
> Open a terminal and type this command:

```

df -h

```

Wubi disk (Ubuntu root partition) is /dev/loop0. 

Windows partition is /dev/sda1.

---

### Post by pacalici on 2011-06-15
thanks

> **Frogs Hair said:**
> From the Disk Utility under root disk or from the System Monitor uder file system. With Wubi you select up to 30Gb during installation.

---

### Post by Rubi1200 on 2011-06-15
If your Wubi install is too small for your needs you have 2 options:

1. save personal and data files somewhere else such as an external drive so as to not use too much of the Wubi root.disk

2. add more space to the Wubi install
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

And welcome to the forums :-)

---

### Post by pacalici on 2011-06-22
> **Rubi1200 said:**
> If your Wubi install is too small for your needs you have 2 options:

1. save personal and data files somewhere else such as an external drive so as to not use too much of the Wubi root.disk

2. add more space to the Wubi install
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

And welcome to the forums :-)

thanks:)

---

### Post by Rubi1200 on 2011-06-22
Sure, no problem :-)

---

