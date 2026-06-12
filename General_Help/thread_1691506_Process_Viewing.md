---
title: "Process Viewing"
date: 2011-02-20
forum: General Help
---

### Post by phanie on 2011-02-20
Is there any way to disable process viewing methods in Ubuntu such as ps aux?The point here is to hide my application which blocks flash drives running in the background. Can this be done? Or is there a way to hide them so that it cannot be seen in the system monitor?

---

### Post by asmoore82 on 2011-02-20
AppArmor or SELinux can do this. Of course Ubuntu leans more towards AppArmor
and RedHat/Fedora towards SELinux.

If your blocking app is important it should be running with sufficient privileges
where it can't be killed by normal users. If your app is killable and you are
instead trying to hide it &#8212; that is *security through obscurity* &#8212;
not a good thing.

I've always preferred good ol' Linux security where users can see everything
but can't break anything &#8212; hear you knocking but you can't come in.

---

### Post by phanie on 2011-02-20
Point taken. But, as of now, i am not yet able to do such things. Can you give me an example wherein my running file cannot be broken even though it can be seen? I am running an infinite loop file from start-up which checks if a flash drive is inserted and locks my PC. The problem is if it is ended through system monitor thats it. Thanks for the reply dude.

---

### Post by asmoore82 on 2011-02-20
Any process running as root or different user cannot be kill'd:
```
**ps -A | grep X**
29080 tty8     04:42:33 Xorg
**kill 29080**
bash: kill: (29080) - Operation not permitted
```

---

