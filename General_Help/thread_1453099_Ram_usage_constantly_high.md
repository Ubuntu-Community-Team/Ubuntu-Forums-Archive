---
title: "Ram usage constantly high?"
date: 2010-04-12
forum: General Help
---

### Post by Doggins on 2010-04-12
Ubuntu 9.04 64-bit

I just checked my system monitor and it looks like my memory is at a constant 900 MB's out of 4 gigs of ram.

This seems high for only having firefox open. Any ideas?

---

### Post by prodigy_ on 2010-04-12
Emm. What exactly did you expect from a modern 64-bit OS with full-fledged GUI? Win7 x64 eats (at least) 2x more memory.

---

### Post by akakingess on 2010-04-12
Mine is at about 700MB without even FireFox running, of course it is the Server distro, so it has Samba and of course other stuff going on in the background, but that's about right.

---

### Post by darolu on 2010-04-12
You may have other processes in the background; and I find Firefox (at least in my systems) very demanding resources-wise, specially with memory; when playing flash video it goes really high.

Anyways, with today's standards 900MB is not THAT much.

---

### Post by Doggins on 2010-04-12
ahh ok, just wanted to check. thanks guys!

---

### Post by nixclusive on 2010-04-12
You are probably looking at the total memory usage including the buffers/cache. You can use the following command to see the actual memory usage:

```
free -m
```

On my computer, the above command has the output:

```

             total       used       free     shared    buffers     cached
Mem:          3952       1127       2824          0         30        409
**-/+ buffers/cache:        687       3264**
Swap:         3906          0       3906

```

Notice the highlighted line, that means only 687 MB is really being used. :)

---

