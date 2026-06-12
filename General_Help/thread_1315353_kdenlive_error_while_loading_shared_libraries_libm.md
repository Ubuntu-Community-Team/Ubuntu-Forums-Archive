---
title: "kdenlive: error while loading shared libraries: libmlt++.so.2: cannot open shared..."
date: 2009-11-05
forum: General Help
---

### Post by Rytron on 2009-11-05
Hi.
I get this error when I run kdenlive via the terminal:
```

:~$ kdenlive
kdenlive: error while loading shared libraries: libmlt++.so.2: cannot open shared object file: No such file or directory
```

---

### Post by Rytron on 2009-11-05
I used Package Cleaner in Ubuntu-Tweak.

Then I did this:
```
sudo apt-get --purge remove kdenlive
sudo apt-get autoremove
sudo apt-get install kdenlive
```

All is fine now. Kdenlive works again.

;)

---

