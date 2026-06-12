---
title: "Access TTYs. Can't login."
date: 2012-05-04
forum: General Help
---

### Post by JustmeVSI on 2012-05-04
Hey guys.

I'm trying to loge in to my ttys to disable x-server so that I can install drivers for my video card. But when I press Ctrl + Alt + F1 - F6 and I enter my user name which a see in my upper right corner and my password for logging in it just tells me "Login incorrect". I have also tried using root as login and then my password but still no result.

What can I do about it?

I'm using Ubuntu 12.04

---

### Post by zero2xiii on 2012-05-04
Hay,

under the GUI, log in and in terminal type

```
whoami
```

Sometimes the username and the account name is not the same. The whoami result is the username you should use, if it is still not working. I have no idea why.

Btw, you must boot into recovery mode, then drop into a shell, and then run:
```
sudo tellinit 3
```
To install nvidia drivers manualy. It took me like 3 days worth of struggle to get it. Since you are already a level to high when u boot into a graphical login (I think that is telinit stage 4)... Even disabling xorg still leaves some other things that might cause issues (well it used to when i did this on ubuntu 10.04 trough 11.04)

Cherz

---

### Post by CharlesA on 2012-05-04
> **JustmeVSI said:**
> Hey guys.

I'm trying to loge in to my ttys to disable x-server so that I can install drivers for my video card. But when I press Ctrl + Alt + F1 - F6 and I enter my user name which a see in my upper right corner and my password for logging in it just tells me "Login incorrect". I have also tried using root as login and then my password but still no result.

What can I do about it?

I'm using Ubuntu 12.04

The username and password will be the same as the one you login to the GUI with. The password is not shown on the screen, so be careful not to make any mistakes.

---

### Post by JustmeVSI on 2012-05-04
Thanks mate. It worked out

---

