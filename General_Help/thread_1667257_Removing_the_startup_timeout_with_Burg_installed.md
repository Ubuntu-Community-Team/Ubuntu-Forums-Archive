---
title: "Removing the startup timeout with Burg installed"
date: 2011-01-14
forum: General Help
---

### Post by BKbroila on 2011-01-14
I have Burg installed and it's great!
But like what GRUB does, I don't like the timeout thing (having only 10 seconds to decide). I actually want to get rid of the 10 seconds and make it infinite seconds during startup, mainly because I usually turn on my laptop and turn away to do something else. 
 
So how do I get rid of the time? I haven't been able to find any related results in Google or here in the forums.

Thanks

---

### Post by BKbroila on 2011-01-18
Bump

---

### Post by RedRooster on 2011-09-13
Hi BKbroiler,

I know you poswed this question a few months back now, but I've just started playing with burg.
To change the BURG timeout (the time you have to choose which OS to load) Open up Terminal and type:

```
sudo gedit /boot/burg/burg.cfg
```

When the cfg file opens look for the line of text that says *set timeout=30*

I tried changing the timeout to =0 but all this did was removed the OS choices and booted straight in (luckily my default OS was Ubuntu) so I edited the burg.cfg file again and changed set timeout to =9999

That fixed it. Honestly I think the batterey in the laptop would run out of juice before I made my selection.

I hope that this has helped you. :)

---

### Post by drs305 on 2011-09-13
I would expect it to work the same as Grub 2. Set the timeout to -1

If you don't know the file, I would suspect /etc/default/burg, but you probably know more about BURG than I do.

---

