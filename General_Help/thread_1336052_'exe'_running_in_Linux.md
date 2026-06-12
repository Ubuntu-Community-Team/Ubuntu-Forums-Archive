---
title: "'exe' running in Linux?"
date: 2009-11-24
forum: General Help
---

### Post by chaopoch on 2009-11-24
I just notice that there is  'exe' running, but I can not find it with commands find and whereis, any comment? thanks.

[ATTACH]137421[/ATTACH]

---

### Post by markcaetano@gmail.com on 2009-11-24
Try going into terminal and tying 'top' without the quotes.

---

### Post by chaopoch on 2009-11-24
> **markcaetano@gmail.com said:**
> Try going into terminal and tying 'top' without the quotes.

Thanks, but I just wonder what application uses 'exe'?

---

### Post by niteshifter on 2009-11-24
Hi,

Just running top won't quite get it - OP will still just see "exe".
This is better:
```
top -c
```

Better still, install htop:
```
sudo apt-get install htop
```

Another handy tool is pstree:
```
sudo apt-get install pstree
```
It gives a "graphical" representation of processes, i.e. who invokes what. Do read the man page:
```
man pstree
```

---

### Post by chaopoch on 2009-11-24
command 'top -c' is enough for me to know what 'exe' is, thanks a lot.

---

