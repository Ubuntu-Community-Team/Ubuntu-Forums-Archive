---
title: "Getting a 32bit system to use 4gb of ram?"
date: 2010-09-23
forum: General Help
---

### Post by Black_Tanto on 2010-09-23
How is this accomplished? It only reads 3.4

---

### Post by cascade9 on 2010-09-23
You need the PAE kernel. Just searching for PAE in synaptic should find the kernel for you. 

Some info on PAE here- 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by migs73 on 2010-09-23
Check my post #5 first!!!


Try this code
```
cat /proc/cpuinfo | grep flags
```

And if 'nx' is reported then your CPU is able to use the PAE kernel.( if it reports back 'lm' as well then you could use the 64 bit version of Ubuntu but would require a fresh install)

Then see here;

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by migs73 on 2010-09-23
BTW if it does not report 'nx' check your BIOS settings to see if it is disabled, if so enable it and redo the code to see that it is there.
If none of this works them I am afraid that's as much RAM as you're going to get. This is not an Ubuntu/Linux problem but is for all OS's as it is limit on the Hardware addressing.

---

### Post by migs73 on 2010-09-23
I just re-read your OP. Do you already have PAE? Go to System > Administration > System Monitor and click on the System Tab. it'll tell you the kernel type near the top.
If you are not using the PAE kernel go to post #3.

If you already have the PAE kernel (It should load automatically when you put 10.04 on a machine with more than 3Gb RAM) then 3.4GiB reported (Note GiB not GB) is not bad. 4GB of RAM is about 3.8 GiB which is what is reported on my system. If you have reasonably high system overheads, this could eat into the amount of available RAM taking you to 3.4GiB.

---

