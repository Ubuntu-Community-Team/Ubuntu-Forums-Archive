---
title: "Chrome crashing randomly"
date: 2010-11-03
forum: General Help
---

### Post by antonvrg on 2010-11-03
i have upgraded to ubuntu 10.10 and it has been working fine. i opened up chrome and it loaded facebook, i tried opening lifehacker and it closed. it will open some sites but when you try others it just closes.

when opened in terminal got this:

```
made2shred@made2shred-desktop:~$ /usr/bin/chromium-browser %U
Attempting to load libmoonloaderxpi 
Attempting to load the system libmoon 
Segmentation fault
made2shred@made2shred-desktop:~$ 

```

how do i fix this?

Thanks, Anton.

SOLUTION: the moonlight plug-in had died, i reinstalled and works fine now, Thanks for all your help!

---

### Post by P4man on 2010-11-03
seems like a problem with the moonlight (silverlight) plugin.
If you really need it, try grabbing the latest version:
[http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)

---

### Post by antonvrg on 2010-11-05
> **P4man said:**
> seems like a problem with the moonlight (silverlight) plugin.
If you really need it, try grabbing the latest version:
[http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)


didn't work, same thing still

---

