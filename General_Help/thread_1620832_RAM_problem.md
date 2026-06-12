---
title: "RAM problem"
date: 2010-11-13
forum: General Help
---

### Post by pavankumarl73 on 2010-11-13
**I  recently noticed my RAM problem. When I start any application it  increases RAM usage but even after I close it RAM usage doesn't go down.  Instead when I restart that application RAM usage goes up again. I'm  little bit puzzled. Any idea? using ubuntu 10.10**

---

### Post by sohlinux on 2010-11-13
> **pavankumarl73 said:**
> **I  recently noticed my RAM problem. When I start any application it  increases RAM usage but even after I close it RAM usage doesn't go down.  Instead when I restart that application RAM usage goes up again. I'm  little bit puzzled. Any idea? using ubuntu 10.10**

which app is it? is it slowing you down a lot?

type in top at the terminal and paste it in here pls

---

### Post by efflandt on 2010-11-13
Are you looking at the correct number in **free**?  The important number is the one in the middle immediately following **-/+ buffers/cache** under **used**. Buffers and cache are freed up automatically if your system needs that RAM for programs.

```
             total       used       free     shared    buffers     cached
Mem:       8121512    2904304    5217208          0      90460    2169632
-/+ buffers/cache:     **644212**    7477300
Swap:            0          0          0
```

Why did you **bold** your entire post?

---

### Post by pavankumarl73 on 2010-11-13
Its not about which application is doing that. No matter whichever application I run and quit I experience the same problem. 

trans@trans-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        959800     875532      84268          0      54068     405480
-/+ buffers/cache:     415984     543816
Swap:       975868          0     975868


When I first start using 10.10 ram was ticking around 250mb while in idle state now I have installed few themes, screenlets,movida,banshee,vlc and nautilus-elementary. I don't think they are worth 200mb of ram while the system is in idle. Even now when I log in to my PC ram shows ~250 - 280mb but after I open mozilla or banshee and close it ram goes upto ~450MB even in idle state. I think ram is not being freed up after I close the application

OR DO U THINK MY UPGRADE MIGHT BE FAULTY?

---

### Post by dcstar on 2010-11-13
> **pavankumarl73 said:**
> 
........
OR DO U THINK MY UPGRADE MIGHT BE FAULTY?

No, you are wasting your time over this issue.

As others have stated, your system will free up cache as **it** requires it, not when **you** think it does.

---

### Post by sohlinux on 2010-11-14
I don't see a problem here, if your computer has not slowed down to an unbearable level then don't worry about it.

---

### Post by Verbeck on 2010-11-14
[URL="http://www.linuxatemyram.com/"]http://www.linuxatemyram.com/
[/URL]

---

