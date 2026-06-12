---
title: "Free Magic is broken errors"
date: 2012-04-12
forum: General Help
---

### Post by wesaus35 on 2012-04-12
Hello, fairly new to linux but I'm learning. Sometimes when I boot up my laptop I get an error that reads like:

Free Magic is broken at: 0xffffffff: 0xe2c3f0 press any key to be aborted.

I press the key and normal start up continues. Within the past 48 hours I've received that code and free magic is broken at: 0x100010: 0xf0008770. After many google attempts, forum searches, and attempts at reviewing both official and community documentation I'm not having very good luck at learning what these error codes are referring to. So far I've learned that similar free magic codes refer to a memory issue. What should my next step be at this point? Another memtest...? Anyway I'm using Ubuntu 11.10, 32bit edition running on a Genuine Intel CPU T1400 @ 1.83 Ghz with standard Intel 945GM x86/MMX/SSE2 graphics (lol not a graphics card but a chipset). Any help or suggestions would be awesome. just in case this was posted in the wrong forums, sorry. :D

---

### Post by wesaus35 on 2012-04-13
so today just got a new code, Free magic is broken at 0x1c7b: 0x0
Any help with these would be awesome.

---

### Post by wesaus35 on 2012-04-14
lol well to keep bumping my own thread...after running memtest for over 8 hours, like 24 passes and 0 errors. Any idea of what my next step should be?

---

### Post by maureenc on 2012-06-26
I had one of those a few weeks ago and again today.... Am on trusty old Lucid which is now out of guarantee I think.... 

It booted as normal after a bit of key pressing... Will continue searching the web for suggestions...

Cheers
Mo

---

### Post by dino99 on 2012-06-26
its time to look at smart output and run fsck

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html](http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html)
[http://manpages.ubuntu.com/manpages/precise/en/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/fsck.8.html)

---

