---
title: "Karmic is slooooooooooow."
date: 2009-12-23
forum: General Help
---

### Post by Krovas on 2009-12-23
Just moved up to 9.10 from 8.04, but I'm not sure I can stay. The speed difference between the two is noticeable and occasionally painful, especially, for one example, running a Windows XP guest in VBox. XP in 8.04 was fairly snappy, but it just drags and drags in 9.10.

There seem to be rather more processes loaded by default: I don't remember loads of much over 210 simultaneous processes too often in 8.04, but Karmic runs ~255 or more all the time. 

My machine is not cutting edge my any means, and I realize that; dual-core Athlon 64 laptop with a gigger of ram, but really, Hardy ran so well, should there be such a quantum leap in hardware demands between two or three releases? Even bare-bones window managers (WindowMaker for instance), don't make much of a difference.

Anyway, before I fall back to Hardy...again...I'd like to take a crack at streamlining Karmic. Can anybody make some suggestions as to non-essential process to block? Optimization tutorials? I'll try just about anything.

---

### Post by taurus on 2009-12-23
Slow as in running slow (takes forever to open a window) or slow as in lag?

---

### Post by Krovas on 2009-12-23
> **taurus said:**
> Slow as in running slow (takes forever to open a window) or slow as in lag?

Both, at times. I suppose another gig of ram might make a difference, but I balk at throwing money at a problem unless I absolutely have to.

---

### Post by taurus on 2009-12-23
Did you install the x86 or the x86_64 version?  How much swap space did you create?  What is the graphic card on that laptop?

---

### Post by wojox on 2009-12-23
Suggestion = Fresh Install.

---

### Post by Krovas on 2009-12-23
> **taurus said:**
> Did you install the x86 or the x86_64 version?  How much swap space did you create?  What is the graphic card on that laptop?

x64, one gig, nVidia 6100 /w shared memory. Like I said, not the deadliest hardware, but Hardy didn't mind nearly as much.

---

### Post by Krovas on 2009-12-23
> **wojox said:**
> Suggestion = Fresh Install.


This is a fresh install, as of a couple of days ago.

---

### Post by taurus on 2009-12-23
Look into System -> Administration -> Hardware Drivers and install nvidia driver for your graphic card.  Also, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
free
```

---

### Post by BenAshton24 on 2009-12-23
Are your graphics card drivers installed /  up to date?

---

### Post by Krovas on 2009-12-23
> **taurus said:**
> Look into System -> Administration -> Hardware Drivers and install nvidia driver for your graphic card.  Also, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
free
```

nVidia accelerated graphics driver (version 185) is recommended and is currently in use.

```
krovas@thievesguild:~$ free
             total       used       free     shared    buffers     cached
Mem:        957408     776236     181172          0      15380     354124
-/+ buffers/cache:     406732     550676
Swap:       999416        272     999144

```

---

### Post by taurus on 2009-12-23
How about

```
top
```

---

### Post by Krovas on 2009-12-23
> **taurus said:**
> How about

```
top
```

```
top - 22:46:22 up  9:18,  2 users,  load average: 0.31, 0.30, 0.26
Tasks: 170 total,   1 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  3.4%sy,  0.0%ni, 92.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    957408k total,   789172k used,   168236k free,    15380k buffers
Swap:   999416k total,     1532k used,   997884k free,   349952k cached

```

---

