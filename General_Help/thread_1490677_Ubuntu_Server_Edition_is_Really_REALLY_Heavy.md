---
title: "Ubuntu Server Edition is Really REALLY Heavy"
date: 2010-05-22
forum: General Help
---

### Post by kevin11951 on 2010-05-22
Right now, my server (ubuntu server edition 10.04) is sitting idle, nothing is connected to it, and it has only been on for a few hours...

And its using 600MB of RAM!  not including cache and buffers...  and no gui or anything, just ssh and lamp (no one is connected to the lamp either).

Plus this is a dual core computer, and its load average is: 0.46, 0.38, 0.36
Thats a quarter of the computers total power...

to give you an idea, debian stable uses 44MB of ram, and sits at a perfect 0.00 when idle.

Here is a screenshot of htop:

---

### Post by Sporkman on 2010-05-22
My ubuntu server is running LAMP, ssh, and a java-based server for subsonic - its load average is:

load average: 0.00, 0.00, 0.00

---

### Post by kevin11951 on 2010-05-22
> **Sporkman said:**
> My ubuntu server is running LAMP, ssh, and a java-based server for subsonic - its load average is:

load average: 0.00, 0.00, 0.00

post your ram usage please :)

edit: what version is it?  mine is 10.04

---

### Post by Sporkman on 2010-05-22
> **kevin11951 said:**
> post your ram usage please :)

edit: what version is it?  mine is 10.04

> free
             total       used       free     shared    buffers     cached
Mem:       3758524    3677080      81444          0     388940    2173776
-/+ buffers/cache:    1114364    2644160
Swap:      7815520          4    7815516

Not sure what all that means - however, when I do "ps aux", the sum of the "%MEM" column is well under 10% (the machine has 4 gigs).

The version is 10.04, upgraded from 9.10.

---

### Post by kevin11951 on 2010-05-22
> **Sporkman said:**
> > free
             total       used       free     shared    buffers     cached
Mem:       3758524    3677080      81444          0     388940    2173776
-/+ buffers/cache:    1114364    2644160
Swap:      7815520          4    7815516

Not sure what all that means - however, when I do "ps aux", the sum of the "%MEM" column is well under 10% (the machine has 4 gigs).

The version is 10.04, upgraded from 9.10.

try "free -m" the "-m" makes it easier to read

---

### Post by Sporkman on 2010-05-22
> **kevin11951 said:**
> try "free -m" the "-m" makes it easier to read

> free -m
```
             total       used       free     shared    buffers     cached
Mem:          3670       3590         79          0        379       2124
-/+ buffers/cache:       1086       2583
Swap:         7632          0       7632
```

---

### Post by kevin11951 on 2010-05-22
> **Sporkman said:**
> > free -m
```
             total       used       free     shared    buffers     cached
Mem:          3670       3590         79          0        379       2124
-/+ buffers/cache:       1086       2583
Swap:         7632          0       7632
```

so yours is twice as heavy as mine... it is using about 1GB without cache or buffers

---

### Post by Sporkman on 2010-05-22
> **kevin11951 said:**
> so yours is twice as heavy as mine... it is using about 1GB without cache or buffers

...but the sum of the memory used by all processes is much lower..? (via ps aux)

---

### Post by bodhi.zazen on 2010-05-22
Linux is not windows and unused RAM is wasted RAM ...

Apache will scale ram use up and down, try starting with 512 Mb RAM (as you boot, at the grub screen, select edit, add mem=512M to the end of the kernel line.

Then try free- m ...

Other then that, one would wonder why your load is so high and what services you are running and how they are configured. You can optimize both apache and mysql to use less ram, but as you have free RAM you may wish to leave it.

---

### Post by kevin11951 on 2010-05-22
> **bodhi.zazen said:**
> Linux is not windows and unused RAM is wasted RAM ...

Apache will scale ram use up and down, try starting with 512 Mb RAM (as you boot, at the grub screen, select edit, add mem=512M to the end of the kernel line.

Then try free- m ...

Other then that, one would wonder why your load is so high and what services you are running and how they are configured. You can optimize both apache and mysql to use less ram, but as you have free RAM you may wish to leave it.

WOW!  thats interesting... i set it to 512, and now it says it using 107MB... thats... interesting.

---

### Post by tgalati4 on 2010-05-22
If this is a new install, you might have locate indexing going on.

---

### Post by FuturePilot on 2010-05-22
File server
```
]$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        475         21          0        103        264
-/+ buffers/cache:        107        389
Swap:         1105          0       1105

```

Web server
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        860        141          0        228        503
-/+ buffers/cache:        128        873
Swap:         1451          0       1451
```

---

### Post by bodhi.zazen on 2010-05-22
> **kevin11951 said:**
> WOW!  thats interesting... i set it to 512, and now it says it using 107MB... thats... interesting.

:twisted:

---

### Post by SabreWolfy on 2010-06-21
Similar thread [here]("http://guide.ubuntuforums.org/showthread.php?t=1494054"). I'm not convinced that where Karmic needed 8% (165MB) of the 2GB RAM, Lucid now needs 32% (650MB) on an idling Ubuntu server with dovecot, apache, mysql and postgresql.

---

### Post by rizzeh on 2010-06-21
43Mb with nothing running on it, only used as rtorrent, left 4 dead 2 and file server, plenty of memory :D

---

### Post by SabreWolfy on 2010-06-21
Yeah, that's what I'm trying to get back to. Karmic used around 160MB. Lucid is topping 650MB.

---

### Post by SabreWolfy on 2010-06-21
See [here]("http://guide.ubuntuforums.org/showpost.php?p=9491797&postcount=16").

---

