---
title: "Cache /usr/lib for quick program loads?"
date: 2009-07-10
forum: General Help
---

### Post by 3rdalbum on 2009-07-10
I've got a theory that I'd like some input on.

I'd like to make programs load and work faster by caching all shared libraries in RAM. I've got enough of the stuff :-)  I've noticed that when I copy or read files, the system's cache seems to get much bigger; it seems like it's putting the file into cache and then not purging it afterwards.

Can I use this behaviour, by reading /usr/lib/* and directing the output to, say, /dev/null?  (so it doesn't actively occupy memory, just cache). When I load programs, will Linux see that the libraries it wants are already in the cache and use those copies rather than reading them again from disk?

I know, the obvious answer is "try it and you'll find out", but I sorta don't have time at the moment to run benchmarks. Has anyone else tried it and found any gotchas?

---

### Post by bear24rw on 2009-07-10
you can try the program preload

```
sudo aptitude install preload
```

and thats it, it will start recognizing which programs you use often and keep all the libraries for it in ram so that you programs load faster

---

