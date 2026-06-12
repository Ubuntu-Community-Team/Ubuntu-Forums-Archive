---
title: "Making use of 4 Gb memory Ubuntu 32bit system"
date: 2010-01-30
forum: General Help
---

### Post by ww711 on 2010-01-30
Currently running a 32bit Ubuntu system on a Compaq nx6325 with 4Gb of physical RAM.

I've enabled the PAE kernel
uname -a gives me

```
Linux 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

```

also free -m-t gives me
```

             total       used       free     shared    buffers     cached
Mem:          2897       2612        285          0         59       2220
-/+ buffers/cache:        331       2566
Swap:         3153        116       3036
Total:        6051       2728       3322


```

also cat /proc/meminfo | grep MemTotal

```

MemTotal:        2967436 kB

```

it seems that 1 gig is not used somewhere or not doing anything? I'm trying to optimise my laptop...

---

### Post by Psycho.mario on 2010-01-30
32Bit OS' can only use about 3Gb. You would need to re-install a 64Bit OS to use all your RAM

---

### Post by howefield on 2010-01-30
> **Psycho.mario said:**
> 32Bit OS' can only use about 3Gb. You would need to re-install a 64Bit OS to use all your RAM

He has the PAE kernel enabled, which can address more memory than you quote. 64 bit is a fine version, but not required simply to address 4 gig of memory.

---

### Post by howefield on 2010-01-30
> **ww711 said:**
> Currently running a 32bit Ubuntu system on a Compaq nx6325 with 4Gb of physical RAM.

What's the output from 

```
sudo dmidecode -t17 |grep Size
```

Might be a BIOS issue

---

### Post by ww711 on 2010-01-30
> **howefield said:**
> What's the output from 

```
sudo dmidecode -t17 |grep Size
```

output

```

	Size: 2048 MB
	Size: 2048 MB

```

---

### Post by howefield on 2010-01-30
> **ww711 said:**
> ```

	Size: 2048 MB
	Size: 2048 MB

```

I'm sure I read about this some time ago, a limitation of the hardware, do a search for - model number 4 gig memory - or something similar, you 'll turn up lots of stuff like the following

[http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1264883349302+28353475&threadId=1187020](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1264883349302+28353475&threadId=1187020)

---

### Post by ww711 on 2010-01-30
Disappointing outcome...robbed of memory.

---

### Post by JSeymour on 2010-01-30
Hmmm... Suspect perhaps it's your BIOS.  I have 4GB in this Dell PowerEdge 1600SC, running 32-bit 9.10, and I get:```

$ grep MemTotal /proc/meminfo
MemTotal:        3549756 kB
$ sudo dmidecode -t17 |grep Size
[sudo] password for jseymour: 
    Size: 1024 MB
    Size: 1024 MB
    Size: 1024 MB
    Size: 1024 MB

```So about 3.5GB is seen.  I know 256MB went to the graphics card.  Dunno where the other 256MB went.  *shug* I figure if I can't do it with 3.5GB, I'm in trouble ;)

Jim

---

