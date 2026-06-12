---
title: "Multiple Mplayers"
date: 2006-02-08
forum: General Help
---

### Post by OlineSixtyOne on 2006-02-08
I am currently using the repository MPlayer, but I want to compile and install my own alongside it. I have no trouble compiling it, the problem is I want to install it so that it can coexist with and not interfere with the repository MPlayer. This is partly because I want to optimize it more to my system, and because I want to compile Mencoder with x264 support which is not supported in the repositories. I either want to have two seperate, noninterfering MPlayer installations, or I want to only install Mencoder. 

I have found that just copying the mencoder binary to /usr/bin/ doesn't provide the complete functionality offered by a complete installation via sudo make install. However sudo make install isn't an option because it will overwrite my current MPlayer. I have scrutinized the makefile and browsed around the CVS release without finding any evidence of which libs I need to install to get full functionality.

Thanks for your help,
OlineSixtyOne

---

### Post by lamego on 2006-02-08
I don't know about MPlayer in particular, generally you can achieve this with most autoconf based configure with:
```
 ./configure --prefix=/opt/my_best_mplayer
```

---

### Post by OlineSixtyOne on 2006-02-08
Thank you, that works quite well.

---

