---
title: "Alt + F2 switches to TTY2 console"
date: 2011-06-20
forum: General Help
---

### Post by Anton K on 2011-06-20
Hi everyone,

I have the trouble described in the topic's name: when try to open KRunner (Alt + F2) I'm switched to console TTY2 (however, KRunner starts as well). Similarly Alt + F1 not only opens Kickoff menu, but switches me to TTY 1 as well.

My system is Kubuntu 11.04.

I cannot definitely say when did this trouble occur for the first time. But in absolutely clean system everything was fine.

Thanks.

---

### Post by Anton K on 2011-06-20
I've found the solution: bug was caused by installed package named:
```
console-cyrillic
```This bug is registered, details can be found there:

[https://bugs.launchpad.net/ubuntu/+source/console-cyrillic/+bug/520546](https://bugs.launchpad.net/ubuntu/+source/console-cyrillic/+bug/520546)

Solution was found in Russian Ubuntu forums (sorry, next links provides information in Russian. However, this bug is directly related to the Russian/Slavic auditory so I think it's okay):

[http://forum.ubuntu.ru/index.php?topic=133548.0](http://forum.ubuntu.ru/index.php?topic=133548.0)
[http://forum.ubuntu.ru/index.php?topic=119303.15](http://forum.ubuntu.ru/index.php?topic=119303.15)
[http://help.ubuntu.ru/wiki/%D1%80%D1%83%D1%81%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F_%D0%BA%D0%BE%D0%BD%D1%81%D0%BE%D0%BB%D0%B8](http://help.ubuntu.ru/wiki/%D1%80%D1%83%D1%81%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F_%D0%BA%D0%BE%D0%BD%D1%81%D0%BE%D0%BB%D0%B8)

Hope it can be useful for someone.

---

