---
title: "Samsung ML-1665 drivers"
date: 2010-11-20
forum: General Help
---

### Post by beetleman64 on 2010-11-20
I've just bought a Samsung ML-1665 laser printer, and I cannot get it to work with Ubuntu 10.10. None of the drivers that Ubuntu suggests work and the driver from Samsung will not install for me. Thanks in advance.

---

### Post by AgenT on 2010-11-21
I may have found an answer for you:
[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

Read that page and follow the directions. It's a repository that will have your driver show up like any other program in Ubuntu Software Center for easy install.

---

### Post by beetleman64 on 2010-11-22
Thanks a lot, I'll give that a shot.

---

### Post by beetleman64 on 2010-11-22
Cheers for the tip, but I have managed to coax the driver from Samsung into working. For anyone else who's interested, you can run it by typing

```
 sudo sh [type directory here]
```

---

### Post by AgenT on 2010-11-25
Repository is a much better option because it's much cleaner. If you ever need to remove the drivers, you just remove them like any other program. Plus the author cleaned them up a bit (Samsung just made a big mess with the files).

Once you add the repository, just install the driver. Its the "program" called "samsungmfg-driver". Now all you have to do is plug the printer in. Ubuntu automatically sets it up for you.

---

### Post by shadow of the locust on 2011-01-12
> **AgenT said:**
> I may have found an answer for you:
[http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

Read that page and follow the directions. It's a repository that will have your driver show up like any other program in Ubuntu Software Center for easy install.

a google search brought me to this solution.

my ml1665 is working perfectly.  thank you :D

---

### Post by Johnny90 on 2011-12-27
Thx a lot, my Samsung ML-1550 is working fine now :)

---

