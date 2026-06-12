---
title: "Removing recovery mode option"
date: 2011-09-13
forum: General Help
---

### Post by jsvidyad on 2011-09-13
Hello,

  I use kubuntu 10.04 . It is set up as a dual boot system. When the system is started, I get a grub screen where I can choose which OS I want to boot. But, I also have a "recovery mode" option which gives root access to the computer without a password. Is there some way to remove the recovery mode option in the grub boot screen?

     It used to be easy in legacy grub where all I had to do was comment out the relevant lines in /boot/grub/menu.lst . But, grub2 seems to be different. I don't know what to do here.

Can someone please help me out??

---

### Post by sisco311 on 2011-09-13
You have to uncomment **#GRUB_DISABLE_RECOVERY="true"** in /etc/default/grub, then run:
```
sudo update-grub
```

For details, check out the community documentation: [uhelp]community/Grub2[/uhelp]

---

### Post by Quackers on 2011-09-13
Scroll down in the guide below to find what you're after

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jsvidyad on 2011-09-13
Thank you very much for your help.

---

### Post by sisco311 on 2011-09-13
You are welcome!

Please don't forget to mark this thread as [SOLVED]. Thanks.

---

### Post by jsvidyad on 2011-09-15
> **sisco311 said:**
> You are welcome!

Please don't forget to mark this thread as [SOLVED]. Thanks.

How do I do that?

---

### Post by sisco311 on 2011-09-15
At the top of the page click the "Thread Tools" Menu, then "Mark this thread as Solved".

For a screenshot see the link in my signature.

---

