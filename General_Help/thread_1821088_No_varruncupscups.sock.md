---
title: "No /var/run/cups/cups.sock"
date: 2011-08-08
forum: General Help
---

### Post by lkjoel on 2011-08-08
As the title suggests, I don't have a file named /var/run/cups/cups.sock.
And, as a result, I can't print.

The error log of cups is attached below (extracted file is around 1.3MB)

Any help would be greatly appreciated

---

### Post by lkjoel on 2011-08-10
Anyone?

---

### Post by Habitual on 2011-08-10
try terminal >
```
sudo dpkg-reconfigure cups
```

---

### Post by lkjoel on 2011-08-10
I've tried that, but it takes forever to configure.
I've also tried:
```
apt-undo purge cups.*
apt-undo undo

```with the same results.

---

### Post by Habitual on 2011-08-15
Terminal > 
```
sudo find `pwd` / -name cups\.sock
```

output please.

---

