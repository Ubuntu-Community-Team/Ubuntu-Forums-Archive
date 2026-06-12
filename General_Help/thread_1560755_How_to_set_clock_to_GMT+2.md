---
title: "How to set clock to GMT+2?"
date: 2010-08-25
forum: General Help
---

### Post by crazyfuturamanoob on 2010-08-25
I live in Helsinki. The time zone is GMT+2.

I tried to set the clock in BIOS but Ubuntu's clock is still 3 hours late. Why? And how to fix it?

PS. I want command-line solutions, not GUI.

---

### Post by LightningCrash on 2010-08-25
Command-line solutions here:
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)


```

$ echo "Australia/Adelaide" | sudo tee /etc/timezone
Australia/Adelaide
$ sudo dpkg-reconfigure --frontend noninteractive tzdata

Current default time zone: 'Australia/Adelaide'
Local time is now:      Sat May  8 21:19:24 CST 2010.
Universal Time is now:  Sat May  8 11:49:24 UTC 2010.

```

You should be able to echo "Etc/GMT+2" instead of the Australia

---

### Post by crazyfuturamanoob on 2010-08-25
Thanks, that did the trick. :D

---

