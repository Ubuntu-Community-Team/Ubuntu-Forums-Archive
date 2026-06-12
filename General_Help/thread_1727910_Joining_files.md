---
title: "Joining files"
date: 2011-04-13
forum: General Help
---

### Post by ki4jgt on 2011-04-13
I'm hacking my Zipit Z2 and putting this OS on it. The only problem is, it comes in parts. 1-5.

What are the Linux commands for joining files?

[http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/1gb-image/](http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/1gb-image/)

Thanks guys. All is appriciated!

---

### Post by timgood on 2011-04-13
```
cat partfile1 partfile2 > wholefile
```

```
man cat
``` is your friend. Or go [here]("http://www.computerhope.com/unix/ucat.htm").

Hope this helps.

---

