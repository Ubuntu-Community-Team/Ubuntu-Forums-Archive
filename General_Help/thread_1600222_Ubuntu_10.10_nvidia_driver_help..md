---
title: "Ubuntu 10.10 nvidia driver help."
date: 2010-10-18
forum: General Help
---

### Post by yo2boy on 2010-10-18
Hello. I've got some help with people on some IRC but it still won't help solve my problem.

I recently installed Ubuntu 10.10 and to my surprise my graphics card driver wasn't available. So I installed it thru Synaptic and USC. I later Activated it and now I can't boot into my GUI. It's showing me some super scary tty1 screen and I almost flipped out of my chair.

For the past few days I've been always booting into RECOVERY MODE -> failsafeX

How do I go on resuming my normal boot and making use of my nvidia-96 driver???

For some extra information, I've linked up a paste when I run "glxinfo" in terminal.

[http://paste.ubuntu.com/515923/](http://paste.ubuntu.com/515923/)

---

### Post by godfromdfo on 2010-10-18
Hey! I think thats why mines not going to GUI any more too - because I updated my nvidia driver I think...

if anyone could help us we would be eternaly greatful

and @ OP: how did you loud into failsafe? 0_o

---

### Post by yo2boy on 2010-10-18
Well, when GRUB2 is showing the OS(es), go to Ubuntu Recovery Mode then a screen will show options. Choose the one that says "failsafeX" then the cursor will be active. When that happens click ok then choose the option, "Restart X"

Your Ubuntu Desktop should load.

This is the only option that works for me. I am very disappointed with 10.10 so far. Worst ubuntu experience yet.

---

### Post by yo2boy on 2010-10-18
Accidentally double posted.

---

### Post by Refalm on 2010-10-18
Have you tried reading this post in the sticky?

[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)

---

### Post by yo2boy on 2010-10-18
> **Refalm said:**
> Have you tried reading this post in the sticky?

[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)

Won't be compatible with my nvidia-96 driver.

---

### Post by godfromdfo on 2010-10-19
I read that link and I don't understand this part:

> If X is still not starting, add this to /etc/X11/xorg.conf

```
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```

how do I add it?

---

