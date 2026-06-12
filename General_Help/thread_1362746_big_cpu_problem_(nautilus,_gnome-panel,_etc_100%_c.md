---
title: "big cpu problem (nautilus, gnome-panel, etc 100% cpu)"
date: 2009-12-23
forum: General Help
---

### Post by mjjna on 2009-12-23
hello,

since 2 days i've a big problem with my ubuntu (9.10)

My cpu is at 100%. if i do a top, i have dozen of gnome-panel processes, dozens of nautilus.

If i kill one of these process, it will execute again 1 second later.

my load average is of course very high, to 30.

I do not think I've done something on my ubuntu before the problem appears, only the standard updates, but I may be wrong.

Anyone as an idea?

---

### Post by chuina on 2009-12-23
Take a look here:
[http://ubuntuforums.org/showthread.php?t=1358573](http://ubuntuforums.org/showthread.php?t=1358573)
and here:
[http://ubuntuforums.org/showthread.php?t=1361875](http://ubuntuforums.org/showthread.php?t=1361875)

Thanks

---

### Post by mjjna on 2009-12-23
it is not a memory usage problem, I really have some processes that runs more than once at the same time.

 if i enter in a terminal

ps -ef | grep nautilus | wc -l

i get more than 40.

the same for gnome-panel, gnome-settings if i'm on gnome, kwin if o try with kde.

BTW, if i log in a gnome safe mode session, the problem does not happen.

---

### Post by chuina on 2009-12-23
You are correct.

My 
```
ps -ef | grep nautilus | wc -l
```result return with 2.

As i'm also a newbie so i'm out of resource.
Sorry..

---

### Post by mjjna on 2009-12-24
ok, I may have found the problem:

I remembered i've added vnc4server in the startup program list.

Removing it seems to fix the problem.

I will come back it editing the subject to solved in my next reboot (because i did not clean reboot, i came from a safe gnome session to a standard gnome session)

---

