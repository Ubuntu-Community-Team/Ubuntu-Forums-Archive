---
title: "why does my ubuntu uses soooo much memory"
date: 2011-05-26
forum: General Help
---

### Post by baxy77bax on 2011-05-26
Hi, 

so i bought a new machine Dell i7, 8GB RAM, 0.5 TB disc ..... and i installed Ubuntu 10.4 on it and when i turned it on and start Geany , open few pdf , thunderbird and firefox, the system monitor reports some 900MB RAM used, but all window aplications cannot close or open normaly (they are very slow- minimazing the window executes in stages(small> smaller> smalest> minimized)). so i checked out what "top" says, and it seams that i'm using 400MB for opening a pdf in "Document Viewer", 700MB for Geany .... and so on up to 8GB and the swap kicks in and everything gets slow. I mean this is ........... on my previous computer I always had this problem but this was because I head 500MB of RAM but now i have 8GB and it still isn't enough .

any suggestions what i should do??? do i have some "memory use up all" mode turned on ??


cheers

---

### Post by mcduck on 2011-05-26
That sounds really high memory usage for Ubuntu, and the applications you mentioned.

Are you absolutely sure you are looking at correct memory values and not virtual memory, for example?

Next time you reach high memory usage, could you run "free -m" and post the output here?

---

### Post by baxy77bax on 2011-05-26
ok now i have firefox, geany and few file browsers turned on and when i run free -m i get

```

free -m
             total       used       free     shared    buffers     cached
Mem:          7964       5782       2182          0        122       3912
-/+ buffers/cache:       1746       6217
Swap:        23330        210      23120

```which is very high

when i turne off file browsers i get:
```

             total       used       free     shared    buffers     cached
Mem:          7964       5783       2180          0        122       3901
-/+ buffers/cache:       1759       6204
Swap:        23330        210      23120

```when i turne off geany i get:
```

             total       used       free     shared    buffers     cached
Mem:          7964       5666       2298          0        122       3901
-/+ buffers/cache:       1752       6211
Swap:        23330        200      23130

```when i turn of the firefox
```

             total       used       free     shared    buffers     cached
Mem:          7964       4877       3087          0        122       3853
-/+ buffers/cache:        938       7025
Swap:        23330        166      23164

```(by the way don't turn of the firefox when writing a post :) - not cool)

so this is when all things are turned off . 

ok, so i restart the comp rarely(maybe 3 times since i bought it) , but this is linux not windows and i don't think i have to restart it every day, several times a day to prevent crashing 

cheers

---

### Post by mcduck on 2011-05-26
1,7GB of used RAM is of course much, but not anything special considering the programs you have running. And you still have over 6GB of free memory.

The "+/- buffers/cache"-line is the one to read from "free" output, that's what tells you how much memory is used by programs, and how much is still available for them.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          7964       5782       2182          0        122       3912
-/+ buffers/cache:       1746       6217
Swap:        23330        210      23120
```
Here your OS and programs are using 1746MB of RAM, and still have 6217MB available if they need it.

There's 122MB of buffered data, for example something waiting to be written to hard drive. And 3912MB is used as cache, to store recently used data in memory in case you happen to use it again soon. As the cache is just a way of using otherwise unused memory to speed up your system, it still counts as free memory if the OS or any program needs more. (On a Linux system that has been running for a while the cache is supposed to fill most of the otherwise unused RAM.)

Your swap is mostly unused, there's 23GB of available swap space (quite much, actually), and 210MB is used at the moment. So little that it probably isn't because of actual swapping (especially when you have over 6GB of free RAM) but just because of the way how Linux kernel uses a swap as a way of testing if some data is still relevant enough to be kept in cache or if it should be dropped instead.

Anyway, your problems definitely aren't caused by memory usage, and really sound more like they'd be related to your graphics card or graphics drivers.

---

