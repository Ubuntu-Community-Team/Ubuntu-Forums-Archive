---
title: "Assertion error with dpkg"
date: 2006-06-08
forum: General Help
---

### Post by pianoboy3333 on 2006-06-08
Recently I tried to build a new linux kernel following [https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto) but I couldn't even get past the first step, do to an error with dpkg. I've noticed that this has been going on for about a day now it's very weird:
```

$ sudo apt-get install build-essential bin86 kernel-package
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
bin86 is already the newest version.
kernel-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I get this every time I use dpkg, a picture of what happens in synaptic can be found at [http://paste.ubuntu-nl.org/15355](http://paste.ubuntu-nl.org/15355)

Sometimes it says I have to use `dpkg --configure -a' but after I do that it gives me the same assertion error the next time.

---

