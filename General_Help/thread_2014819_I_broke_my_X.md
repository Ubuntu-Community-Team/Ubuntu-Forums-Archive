---
title: "I broke my X"
date: 2012-07-02
forum: General Help
---

### Post by Carborundum on 2012-07-02
Some background: Sometimes when I boot, LightDM fails to start properly, so I instead end up in tty1. This isn't a huge problem, as all I have to do to fix it is 'sudo restart lightdm'.

This morning, I had the bright idea to try 'sudo startx' instead, just to see what would happen. X started OK, but Compiz didn't. Even worse, I couldn't switch back to tty1 (or any other tty). I did manage to shut down the system normally however, by pressing the power button on my computer, which brought up the "Do you wish to shut down" window.

Since then, I can't login through LightDM at all. When I give it my password, it seems to accept it, but a moment later I end up right back at the login screen. I can still login through tty without problem.

Any ideas on what might have happened, and how to fix it?

---

### Post by stderr on 2012-07-02
File permissions perhaps? Try ```
ls -al | grep root
``` on your home dir and see what that turns up.

---

### Post by QIII on 2012-07-02
You might try starting lightdm as a service

```
sudo service lightdm start
```

---

### Post by matt_symes on 2012-07-02
Hi

Also, as well as the above good suggestions, take a look in the log files. 

As you are having problems logging in with lightdm, i would start looking in

```
/var/log/lightdm/lightdm.log
```

After that take a look in

```
/var/log/Xorg.0.log
```

Post back any errors here.

Kind regards

---

### Post by steeldriver on 2012-07-02
I agree with stderr - 'sudo startx' from your user account is a perfect recipe for ending up with a root-owned ~/.Xauthority

---

### Post by Carborundum on 2012-07-08
Thank you all for your replies! Unfortunately I can't test any of this, as I lost patience a few hours after I posted this and simply reinstalled everything from scratch. :P

I'll mark this as solved, and thanks again for replying. Sorry for wasting your time.

---

### Post by WorMzy on 2012-07-08
To elaborate on what stderr and steeldriver are saying, you shouldn't run "sudo startx". "startx" should be run as *you*, not root. By sudo-ing it, you probably messed up the ownership of your .Xauthority file, causing it to be owned by root, and unreadable by your standard user account.

---

### Post by Carborundum on 2012-07-09
> **WorMzy said:**
> To elaborate on what stderr and steeldriver are saying, you shouldn't run "sudo startx". "startx" should be run as *you*, not root. By sudo-ing it, you probably messed up the ownership of your .Xauthority file, causing it to be owned by root, and unreadable by your standard user account.
Noted. I won't be doing that again. :D

---

