---
title: "Dual Core Support?"
date: 2006-02-14
forum: General Help
---

### Post by mempf on 2006-02-14
I have a AMD Athlon 64 X2 3800+ and i'm wondering does Ubuntu have native support for the dual core aspect of it?

Thanks

---

### Post by luckyaba on 2006-02-14
You need to upgrade to a SMP kernel

---

### Post by aeiah on 2006-02-14
i have that cpu, and you'll notice quite a difference once you get your kernel up to date. bear in mind that things such as wireless and graphics cards will probably need to be reinstalled after the kernal upgrade.

check: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

you want:  sudo apt-get install linux-k7-smp

---

### Post by mempf on 2006-02-14
I tried the k7-smp kernel but I can't get my nvidia drivers working properly. Can someone give me a howto? (I have a Geforce 7800GT)

Before with the standered 386 kernel I had used this guide to get my dirvers working before: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Thanks!

---

### Post by RAOF on 2006-02-14
Did you install the "linux-k7-smp" - it sounds like you don't have the -restricted-modules package for your kernel.

Failing that, the "Nvidia drivers" link in my sig should help.

---

### Post by aeiah on 2006-02-15
i also have a 7800GT and ive had no real problems installing the drivers. follow the guide that's [here]("http://www.ubuntuforums.org/showthread.php?t=75074"), as RAOF mentioned and follow method 2. it'll tell you where to grab the restricted modules, gcc-3.4 etc that you'll need.

---

