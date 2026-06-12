---
title: "Ubuntu boot loader and DNS?"
date: 2006-03-28
forum: General Help
---

### Post by phil2222 on 2006-03-28
hi people, Im very new on the forum, I have two questions, Im sorry if someones asked these before, Ive recently installed xp on my computer, then Ubuntu, however I heard you should get the option when you start the PC to choose which OS to boot, I dont get this and boots straight into Unix. Any ideas how I can boot into XP?

Also Ive added my DNS settings, however every few minutes Ubutu forgets them?


Any ideas? thanks

Phil

---

### Post by AndrewCaul on 2006-03-28
For the first question, what is the output of ```
sudo fdisk -l
```

And sorry, I'm not sure what's wrong with the second one. What program are you using to do it?

---

### Post by pacman^ on 2006-03-28
The DNS problem: 

sorry to ask but are you sure you run system -> administration -> networking as root? I just thought about you not having writing permissions to /etc...

---

### Post by AndrewCaul on 2006-03-28
[QUOTE=pacman^]The DNS problem: 

sorry to ask but are you sure you run system -> administration -> networking as root? I just thought about you not having writing permissions to /etc...[/QUOTE]
When I run it, I always have to type my password and access it as root, so Phil probably had to as well.

---

### Post by pacman^ on 2006-03-28
I just thought... Oh yes, I've edited my sudoers file so that I don't need to enter a password at all. ;) (maybe not very safe but better than typing root pw every single time you want to switch to daylight saving mode or something)

---

