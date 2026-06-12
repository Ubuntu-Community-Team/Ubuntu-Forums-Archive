---
title: "Output in Terminal SLOW in Desktop Mode!"
date: 2009-08-19
forum: General Help
---

### Post by snowmanZOMG on 2009-08-19
I have a C++ program and I've been developing on a Windows machine up until a few days ago.  There are no system specific calls so I just took the source files and copied them to my Ubuntu machine and started work right away.  In the program, I have a loop which simply runs some calculations on planetary bodies and updates positions based on time and then outputs the new positions to the screen.  However, this output process is EXCEEDINGLY slow in the terminal in the desktop mode.  If I switch to console mode (CTRL + ALT + F1), running the same program, it runs just fine.

This leads me to believe that this has something to do with my graphics.  I have an ATI/AMD HD3850 and I use ATI's fglrx driver, Catalyst 9.8 that was just released.  But to throw a wrench into things, this same behavior can be noticed while SSH'd into my machine from another machine (I've tried it via putty on a Windows machine).  The slowdown isn't as significant as on my Ubuntu machine itself in desktop mode, but it is still exceedingly slow.  Additionally, running my program under valgrind in desktop mode seems to run at the expected speed (aka, not exceedingly slow).

Running my code yields timings via time as follows:

In desktop mode:
```
$ /usr/bin/time ./solarsystem

0.82user 0.18system 0:26.25elapsed 3%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+541minor)pagefaults 0swaps

``````
$ /usr/bin/time ./solarsystem > output

0.70user 0.30system 0:01.05elapsed 95%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+13352outputs (0major+542minor)pagefaults 0swaps
``````

$ /usr/bin/time valgrind ./solarsystem

1.04user 0.02system 0:01.15elapsed 91%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+8outputs (0major+6126minor)pagefaults 0swaps
```In console mode:

```
$ /usr/bin/time ./solarsystem

0.07user 0.93system 0:01.02elapsed 98%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+546minor)pagefaults 0swaps

``````

$ /usr/bin/time ./solarsystem > output

0.74user 0.26system 0:01.01elapsed 98%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+12728outputs (0major+544minor)pagefaults 0swaps
``````
$ /usr/bin/time valgrind ./solarsystem

0.08user 0.92system 0:01.04elapsed 96%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+545minor)pagefaults 0swaps
```SSH via putty (connected locally on a wireless connection):
```
$ /usr/bin/time ./solarsystem

0.76user 0.24system 0:16.49elapsed 6%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+544minor)pagefaults 0swaps
``````
$ /usr/bin/time ./solarsystem > output

0.68user 0.32system 0:01.05elapsed 95%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+13200outputs (0major+544minor)pagefaults 0swaps
``````
$ /usr/bin/time valgrind ./solarsystem

1.04user 0.03system 0:01.08elapsed 98%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+8outputs (0major+6129minor)pagefaults 0swaps
```Obviously, the CPU utilization is funky, but I can't nail down the cause.

---

### Post by snowmanZOMG on 2009-08-21
Nobody?

---

