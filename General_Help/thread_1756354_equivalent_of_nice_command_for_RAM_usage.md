---
title: "equivalent of nice command for RAM usage"
date: 2011-05-12
forum: General Help
---

### Post by john1923 on 2011-05-12
I have a program with a memory leak.

Is there a way of limiting the amount of memory available to the program or dropping it's "memory priority" so that when the offending program demands all of my memory it doesn't affect the rest of my system.

This is how I run it at the moment, (it also occasionally demands lots of CPU)

nice /bin/sh "/opt/CLCDNAWorkbench5/clcdnawb5"

---

### Post by andrewc6l on 2011-05-12
You can set the maximum amount of RAM a program uses with the ulimit shell built-in command.

I'm not sure if Ubuntu honors ulimit -m, but you might want to try:

```
ulimit -m 256 
```

to give the program a maximum of 256k.

Alternately, you could try

```
ulimit -d 256
```

to limit the program's data segment to 256k.

You can also use

```
ulimit -e someNumber
```

to set the maximum scheduling priority (nice) (I'm not sure what that number would be, but it's probably something lower than the default.)

```
ulimit -a 
```

will list the current values. Use

```
man bash
```

and search for ulimit to see more details. Also, here's a link:
[http://wiki.linuxquestions.org/wiki/Ulimit](http://wiki.linuxquestions.org/wiki/Ulimit)

---

### Post by john1923 on 2011-05-13
Thanks, that helped a lot. But it doesn't entirely solve my problem

My ulimit -m limit is already at 1.5 GB per program, which is fine as I have 4GB of RAM.

However CLC instantly fills up the RAM, then steadily eats up all 11 GB of swap space.

This must mean that it is starting other memory demanding processes? or is something else going wrong.

Thank you

John

---

### Post by andrewc6l on 2011-05-17
It looks as if this is a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701141)

---

