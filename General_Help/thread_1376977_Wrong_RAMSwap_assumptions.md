---
title: "Wrong RAM/Swap assumptions"
date: 2010-01-09
forum: General Help
---

### Post by krisatm on 2010-01-09
I have a problem, and I hope it is just some misconfigration on my side, not a bug, so here goes:
I have 1GB ram and 2GB swap space. It seems that linux programs somehow are aware that there are 3GB ram avaialable and pretty fast uses more than 2.5GB. System becomes unresponsive because of excessive swapping. On the other hand if I disable swap, using the same programs (chrome, vlc, openoffice) I get only ~600MB use while watching videos and browsing net.

I know, that linux uses all available ram to enhance performance, but in my case, it really hurts the performance. I also cannot leave the swap off, because I sometimes want to do some 3d editing, and then the memory usage can exeed 1GB.

So basicly my question is, if it is possible to force swap usage only when really needed, and make it so, that swap is not considered free ram and filled up with useless junk. (For example, if swap is enabled VLC player just loads whole movie into swap! - which of course is useless, because movie is located on the same hard drive, but VLC is not the only offender)

---

### Post by NoaHall on 2010-01-09
Swap is not RAM. It is not considered to be free RAM. It is considered to be swap.

Do you have preload installed? If so, uninstall it.

---

### Post by happyhamster on 2010-01-09
> **krisatm said:**
>  On the other hand if I disable swap, using the same programs (chrome, vlc, openoffice) I get only ~600MB use while watching videos and browsing net.
That looks like a bug.

- As a workaround, you can set the "swappiness" of your system (default = 60). To check the current value:

cat /proc/sys/vm/swappiness

- To change it on the fly:

sudo sysctl -w vm.swappiness=20

0 = swap as little as possible (perhaps not safe), 100 = swap as much as possible.

- To make the change permanent, edit the file /etc/sysctl.conf:

gksudo gedit /etc/sysctl.conf

- and add:

vm.swappiness = 20

- Here's an interesting discussion on the matter:
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by lswb on 2010-01-09
The commands "swapon -a" and "swapoff -a" will enable/disable the use of swap but from you description, something appears to be misconfigured on your system. My system for example has 1GB memory and a 1GB swap partition, and I almost never see any swap being used. 

The tendency to swap can be influenced by changing the value of /proc/sys/vm/swappiness. FYI if you are not familiar with /proc, it is not a real directory of physical disk files, but a virtual filesystem that exposes various kernel values. Changes made in /proc are not permananent and will not persist upon a reboot, but there are often config files that can be used to make settings permanent. 

You can google up a better explanation of using /proc/sys/vm/swappiness than I can give here and find out how to make your changes persistent.

---

### Post by krisatm on 2010-01-09
Thank you happyhamster - the swappiness was the problem. And thanks for the extra literature on the subject - very enlightening. I have swapiness=10 now and it is working great.
Also thanks to lswb for clarification and extra useful information!

To conclude - it seems to me that workstations should have low swapiness and servers should have high swapiness.

---

### Post by dcstar on 2010-01-10
> **krisatm said:**
> Thank you happyhamster - the swappiness was the problem. And thanks for the extra literature on the subject - very enlightening. I have swapiness=10 now and it is working great.
Also thanks to lswb for clarification and extra useful information!

To conclude - it seems to me that workstations should have low swapiness and servers should have high swapiness.

You should report this as a bug, such behaviour isn't acceptable:

```
man ubuntu-bug
```

---

### Post by krisatm on 2010-01-10
> **dcstar said:**
> You should report this as a bug, such behaviour isn't acceptable:

```
man ubuntu-bug
```

Well, before I go and report it as a bug, I should determine which exactly is the buggy part.
As I understood from the swapiness article mentioned earlier, with high swapiness IO operations which need cache win, and some "less" used software, like browser or openoffice gets swapped out in favour of those operations - that makes those operations faster, but my user experience laggier. As I understand this is by design, no? (So critical IO operations would be as fast as possible on a server like machine, at the expense of background programs)

The thing I think is a bug, is that program data (like video files for player) are loaded into ram and/or swap, in their full size, at the same time crippling whole sistem (ram and swap maxed out, even switching to terminal tand typing in it takes looots of time). 
*** Next: rant based on my limited knowledge ***
Basically if it is reading/writing to hard drive, I want the data to really be there, not just stored in memory to write later, because that's when user expects some waiting - when he initates it by saving something etc., not when ever system "feels" its IO processes will be least affected by it. I think it is not only inconvenience, but also data safety issue - if I saved a file, and then power went out, I want to be sure file was saved not stored in ram.
*** Rant off ***

So what do you all think - which is the buggy part of behaviour, if any, and why as well as how it should be?

---

### Post by rnerwein on 2010-01-10
hi 
about RAM: there is absolutly no problem with huge RAM. you can run a 32 bit OS or a 64 bit OS.
i think your "problem" depends on caching. if cache is filled up very high and system begins flushing
the cache it seems to be hold for seconds.
there for if you change swapiness (never saw system swaping - just caching) you should have a look at 
dirty_ratio  ratio too (default is 40 --> change it to  15.
and there is another value that should be changed: vm.dirty_background_ratio ( in 9.10 it is already set to 10 - thats fits mostely).
you should "play" with your settings via "echo vlaue > xxxxxx" . because these vm-parameters depends on the usage of your system. 
and at least ---> it's no bug i think :;)
ciao
real programmers don't use mice

---

