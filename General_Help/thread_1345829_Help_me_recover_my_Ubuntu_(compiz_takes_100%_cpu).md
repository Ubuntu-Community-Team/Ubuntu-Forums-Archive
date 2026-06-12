---
title: "Help me recover my Ubuntu (compiz takes 100% cpu)"
date: 2009-12-04
forum: General Help
---

### Post by Lockheed on 2009-12-04
It's not as bad as it sounds but worse than I would expect form a linux.

Yesterday, my comp started to act up and I had no choice but to cut power and restart it. after I did, ubuntu lost a lot of settings (emule, nicottine, a lot of Appearances) but that's not the worst.
The worst thing is, that since then every time I start computer process called compiz.real takes 100% of cpu and everything works extremely slow.

I tried reinstalling Compiz Fusion, I did checkdisk - nothing worked. I need it but to write this post I had to kill it and now I am missing all the useful functions, not mentioning the fact that now cairo docs is not transparent and takes 30% of the screen (OpenGL issues from killing compiz.real).

Help, anyone?

---

### Post by OllyDBG on 2009-12-04
try to give it a low priority by running top as a root

```
sudo top
```then type

```
r
```and then type your Process ID for compiz ofc (you will find the process ID 

under PID column)

then you will be asked to put a renice which is     19 for lowest priority and -20 for highest

type 19 and see, hope this helps :)

---

### Post by OpSecShellshock on 2009-12-04
Sounds kind of like a video card failure. Do you have an after-market video card in addition to the on-board card? There may have been a problem with it, which then caused the system to fall back to it on restart.

---

### Post by Frogging101 on 2009-12-04
There is something seriously wrong with that system. I would say a video card problem, though. Try taking a look at the drivers.

---

### Post by OllyDBG on 2009-12-04
you can also try 

```
metacity --replace
```

---

### Post by Lockheed on 2009-12-05
No hardware issue at all but pure Ubuntuness. Problem disappeared after 17 restarts. If it reoccurs after another one, it remains to be seen. In some aspects, linux is more unpredictable than failing windows.

---

### Post by Lockheed on 2010-01-28
Ok, now I am getting this after every restart of the system. I need to kill compiz.real and then start it again to be able to use computer.
Sometimes, I am even unable to kill it because it is too slow to start a terminal or process manager.

Why? Why? Why?

---

