---
title: "I can't update or install anything now!!"
date: 2009-06-29
forum: General Help
---

### Post by person9 on 2009-06-29
Hi, I was trying to install a bunch of packages in terminal, and suddenly i realized I didnt need to (it was going super slow anyway!) So i pushed Escape a couple times and then just closed terminal, thinking it would "kill" anything i was doing.

Well now nothing can "get an exclusive lock". I logged off and logged on again, in an effort to kill any processes that would cause that, but it's still not working. When I try to do this:

```
sudo apt-get autoclean
```

I get this:

```
rebecca@ubuntu:~$ sudo apt-get autoclean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

I pretty much can't do anything right now, and it's really annoying. Is there anything I did that I can fix now?

---

### Post by person9 on 2009-06-29
I ran 
```
 $ps -ax
```

I spotted 
```
12959 ?        S      0:01 apt-get install build-essential zip flex desktop-file

```

And then I killed it with 
```
rebecca@ubuntu:~$ sudo kill 12959

```

And then my computer's fan started going crazy so Im going to like restart and see if stuff works. Update in a second.

---

### Post by Blood//Stain//Child on 2009-06-29
Have you reset the machine and tried again?

---

### Post by Buzzez on 2009-06-29
> **person9 said:**
> I ran 
```
 $ps -ax
```I spotted 
```
12959 ?        S      0:01 apt-get install build-essential zip flex desktop-file

```And then I killed it with 
```
rebecca@ubuntu:~$ sudo kill 12959

```And then my computer's fan started going crazy so Im going to like restart and see if stuff works. Update in a second.
 
No need those stuffs, Just need close Add/Remove or Sypnatic windows or reboot machine. That's Ok

---

### Post by person9 on 2009-06-29
Thanks for your suggestion but I didn't have any of those things open. I had Terminal open, and then had closed it. I think it may be fine now, and I restarted my computer twice.

Ill post if theres an issue - Thanks!

---

