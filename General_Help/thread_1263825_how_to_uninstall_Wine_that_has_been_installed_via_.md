---
title: "how to uninstall Wine that has been installed via terminal?"
date: 2009-09-11
forum: General Help
---

### Post by mac666 on 2009-09-11
Hey
I installed Wine beta via terminal, but now i cant remove it...
I dont know which direction to head?
Thanks...

---

### Post by Efwis on 2009-09-11
open terminal and enter

```
sudo apt-get remove wine
```

---

### Post by P4man on 2009-09-11
that won't work. He compiled wine from source, despite our warnings and telling him to wait for repository to come online again, instead of compiling from source. To quote myself a few hours ago:

> Just wait a bit until its up, otherwise you're gonna get in to trouble trying to** uninstall** or upgrade wine with the next release.

> well, I predict another "urgent please help" post in short order when you're gonna try to update wine 

Anyway, perhaps there is an uninstall script in the folder where you compiled wine. Try

> sudo ./uninstall

there.

---

### Post by mac666 on 2009-09-11
> **P4man said:**
> that won't work. He compiled wine from source, despite our warnings and telling him to wait for repository to come online again, instead of compiling from source. To quote myself a few hours ago:




Anyway, perhaps there is an uninstall script in the folder where you compiled wine. Try



there.
Sorry about that but ive been waiting for a new drive 2 weeks, and when i got it i really wanted to try out the new games ive bought, without having to install stupid windows

There is no uninstall script, so i cant remove it?
I have the feeling that a new ubuntu installation is comming up!

---

### Post by P4man on 2009-09-11
1 more try, go to the folder where you compiled wine and try this:

```
sudo make uninstall
```

---

### Post by mac666 on 2009-09-11
> **P4man said:**
> 1 more try, go to the folder where you compiled wine and try this:

```
sudo make uninstall
```
thanks seems promising, lots of text flowing around now

Will i need to this 1 times for each time i made" make" before? :D

---

### Post by P4man on 2009-09-11
No, but you're gonna have to do 50 sit-ups and 100 hail Ubuntu's :)

---

