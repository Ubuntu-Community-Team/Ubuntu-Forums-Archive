---
title: "Removing a custom compiled kernel?"
date: 2012-06-05
forum: General Help
---

### Post by ojdon on 2012-06-05
Hi there, 

I have recently compiled custom kernels for Ubuntu, they all aren't perfect so I want to remove them off my system, when I run this command: 

```
dpkg -l | grep ^ii | grep 2.6.28-15 | awk -F' ' '{ print $2 }'
```

I get the following results:

```
3.3.6-030306
3.3.7core2duo
3.3.7-core2duo
3.3.7core2duo.old

```

I want to remove all the 3.3.7* ones and keep the 3.3.6 one. Unfortunately, the 3.3.7 ones don't seem to get removed when I run "sudo apt-get remove linux-image-3.3.7*" nor are they listed in Synaptic. Ubuntu-tweak didn't help either since it can't find them. Neither did the "one-liner" command to remove other kernels apart from the one listed when using "uname -r".

How do I go about removing this kernels manually? 

Regards

---

### Post by dino99 on 2012-06-05
you should find them inside /lib/modules/

there, sudo rm -rf 3.3.7*

---

### Post by ojdon on 2012-06-05
Thanks!

I have deleted the 3.3.7 related files in the /boot folder too. Ran "update-grub" and they are not in the menu entry. :) 

Is there anywhere else that I might have to delete 3.3.7 related folders & files?

---

