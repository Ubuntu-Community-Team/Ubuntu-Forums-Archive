---
title: "How do I remove apache2 from my ubuntu desktop system as if never installed?"
date: 2010-08-04
forum: General Help
---

### Post by compiz addict on 2010-08-04
I have apache2 on my system, and it stopped working since the router was messed with (not by me). I removed apache2 and deleted /etc/apache2, but if I install apache2 it doesn't bring the files back. How do I fix everything that I messed up so it's as if apache was never installed so I can install it again?

---

### Post by akester on 2010-08-04
```

sudo apt-get remove apache2
sudo apt-get autoremove

```
The second removes all the dependency packages installed alongside apache.
```

sudo apt-get install apache2

```

Hope this helps

---

### Post by compiz addict on 2010-08-04
Thanks. Found a website that said how to do it a little while ago already though. Now my only problem is PHP scripts wont work, they just get downloaded.

---

