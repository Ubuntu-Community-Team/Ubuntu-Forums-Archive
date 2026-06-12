---
title: "Default OS For Boot Menu?"
date: 2010-10-07
forum: General Help
---

### Post by buzbuz on 2010-10-07
I'm a beginner and I just installed the latest version of Ubuntu on my wifes computer, I got everything running and all is good.  The only problem is that since it is my wifes computer, and she wants to use windows rather than linux, it is inconvenient for her to have to select Windows from the boot menu rather than me, on the occasion that I play with ubuntu, selected ubuntu.
Is there a way that I can set windows as the default rather than Ubuntu?  
Please let me know of any ideas/solutions.
Thanks!

---

### Post by sikander3786 on 2010-10-07
Install startup manager.

```
sudo apt-get install startupmanager
```

It will be under System > Administration > Startup Manager, select the default OS from there.

Alternatively you can edit /etc/default/grub and from "GRUB_DEFAULT=0" replace '0' with the Grub menu entry number of Windows, 5 in my case. After that, run,

```
sudo update-grub
```

---

### Post by drs305 on 2010-10-07
Edit:  ^^ sikander3786 has it covered.

StartUp-Manager. It's a nice GUI app that can set the default OS for you. Info in the "SUM" link in my signature line.

---

### Post by anglican on 2010-10-08
> **sikander3786 said:**
> Install startup manager.

```

Alternatively you can edit /etc/default/grub and from "GRUB_DEFAULT=0" replace '0' with the Grub menu entry number of Windows, 5 in my case. After that, run,
You can also set GRUB_DEFAULT to the name of the OS you want as default e.g.:
[CODE]
GRUB_DEFAULT="Microsoft Windows XP" then sudo update-grub
```That way if you install a new kernel, your default remains unchanged. It's one of the nice new features of grub2 :wink:

H

---

### Post by sikander3786 on 2010-10-08
> **anglican said:**
> You can also set GRUB_DEFAULT to the name of the OS you want as default e.g.:
```

GRUB_DEFAULT="Microsoft Windows XP" then sudo update-grub
```That way if you install a new kernel, your default remains unchanged. It's one of the nice new features of grub2 :wink:

H
Sounds good :-)

---

### Post by buzbuz on 2010-10-09
Thanks for all your quick help, everything works great now and the wife will be more happy with me

---

