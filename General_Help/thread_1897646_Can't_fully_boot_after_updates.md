---
title: "Can't fully boot after updates"
date: 2011-12-19
forum: General Help
---

### Post by 00Vince00 on 2011-12-19
Hi,

About 2 days ago I took the plunge into 11.10 despite being skeptical about the new interface. I instantly started to like it and quickly had it installed (replacing linux mint which I found buggy). It is installed alongside Windows 7 with grub installed to a dedicated boot partition.

The problem is, now I've installed all the updates suggested by the update manager (around 260 updates) and after restarting the machine I can't get back into it. What happens is that after Ubuntu is selected a purple screen appears, then the orange dots and then a black screen where normally Ubuntu would log on but it just stays black. I don't even hear the logon chime. 

I was thinking that the cause might be a recently installed fglrx driver but I'm not  so sure.

Would anyone be able to point me into the right direction? Do I need to do something using the live cd?

My Specs:
HP G62-B20SA Laptop
Triple core AMD 
4GB RAM

Thanks

---

### Post by 00Vince00 on 2011-12-20
Bump

---

### Post by Perfect Storm on 2011-12-21
Boot into recovery mode, then type;
```
sudo aticonfig --initial
```

then reboot.

---

### Post by 00Vince00 on 2011-12-21
> **Artificial Intelligence said:**
> Boot into recovery mode, then type;
```
sudo aticonfig --initial
```then reboot.

Unfortunately that didn't work. Hmm looks like I'll have to do a reinstall.

---

### Post by Perfect Storm on 2011-12-21
There's known problem with restricted ATI driver and with Gnome Shell and Unity. Better to use Open driver for now, or you could chance it with: [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html)

---

### Post by kaldor on 2011-12-21
I had a similar issue with 11.04 when compiz was enabled. When you get the black screen, can you switch to a TTY (Ctrl Alt F1, Ctrl Alt F7) and then back to the desktop? Worked every time without fail when I had this problem.

---

