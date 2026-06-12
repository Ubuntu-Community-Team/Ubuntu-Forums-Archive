---
title: "Ubuntu boot problem after upgrade from 10.04 to 10.10"
date: 2010-10-20
forum: General Help
---

### Post by sorinu26 on 2010-10-20
Hi, I'm new to Ubuntu and I've got a problem. :D

I installed Ubuntu 10.04 with Wubi. Everything was perfect till i updated Ubuntu to 10.10. It updated successfully, and after update it needed restart. I restarted and now it can't boot Ubuntu.

At dual-boot when i select Ubuntu it shows me this:

```
GNU GRUB

Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions anywhere else TAB lists possible device or file completions.

GRUB > _
```

Please help me solve this problem. :)

---

### Post by Quackers on 2010-10-20
Welcome to Ubuntu Forums :-)
Have a look at this thread and see if there's something to help you.
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by bcbc on 2010-10-20
Wubi problems on upgrade: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by sorinu26 on 2010-10-20
> **bcbc said:**
> Wubi problems on upgrade: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

I made what it said in that post and now its working perfect. I had to replace the file **'wubildr'** from **C:** partition with **'wubildr'** from **C:\ubuntu\winboot**. Thanks a lot! :)

---

