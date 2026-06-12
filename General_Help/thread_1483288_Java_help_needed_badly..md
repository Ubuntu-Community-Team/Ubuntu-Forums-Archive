---
title: "Java help needed badly."
date: 2010-05-14
forum: General Help
---

### Post by xSkittlez11x on 2010-05-14
Okay, so we just installed ubuntu to our computer and I wanna play Runscape. It requires Sun java SE 6. I have found the way to install plug ins, but, everytime I click 'install', it asks for a password. We do not have a password on our computer. What does this mean? Is there a password? Do I create one?

---

### Post by gmargo on 2010-05-14
What version of Ubuntu?  If 10.04 Lucid, then probably all you need to do is to install the **openjdk-6-jre** package.

---

### Post by ercula on 2010-05-14
well as far as i know you need to choose a password when you install. it is possible that you have selected an option so it boots without requiring you to enter a password. to reset or change the password i found this thread, 

[http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)

i realize that this is not exactly the "Ubuntu way" of doing things, but it doesn't seem too challenging. remember to be VERY CAREFUL when doing something of this nature, and read a bit about the commands so you know exactly what you are doing.

---

### Post by burton247 on 2010-05-14
As gmargo said I believe just install openjdk-6-jre should be good. But to install that you'll still need a password. You should have set up a password when you installed the system so see if ther person who installed it or set the account up knows. If now I'm assuming someone knows the root password. Log into root in the terminal and reset the password for that user

```
[user] passwd
```

---

### Post by 2hot6ft2 on 2010-05-14
Try the third post on this page if you've already enabled the partner repo., start at the first post if you haven't.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40](http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40)
:guitar:

---

