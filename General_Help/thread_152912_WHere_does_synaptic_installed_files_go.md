---
title: "WHere does synaptic installed files go?"
date: 2006-03-30
forum: General Help
---

### Post by kurakusan on 2006-03-30
TestDisk

I just used Synaptic package manager to install testdisk, a program to recover hard drives. After it was done I couldn't figure out where to find the program. Even using the search function nothing came up](*,)

---

### Post by az on 2006-03-30
[QUOTE=kurakusan]TestDisk

I just used Synaptic package manager to install testdisk, a program to recover hard drives. After it was done I couldn't figure out where to find the program. Even using the search function nothing came up](*,)[/QUOTE]

If you right-click on an installed package in synaptic and look in the properties, you get to see the installed files.

You can also run

dpkg -L testdisk

Not all packages which are not in main include menu entries.

---

### Post by kurakusan on 2006-03-30
I have no clue how to use testdisk
does anyone else know.
I can't find anything thats an executable. it keeps telling me I have to compile. but I thought I got the binary!!!!!!!!!

---

### Post by elamericano on 2006-03-31
That gets me too sometimes. I just installed it myself at your suggestion. It may come in useful. The executable was installed at /usr/sbin/testdisk. That is in your path (you can invoke it from anywhere). Just type this:
> sudo testdisk /list
That will show you your partitions. Then you can
> sudo testdisk
...to check everything, I guess. It just complained "TestDisk need[sic] 25 lines to work. Please enlarge the terminal and restart TestDisk." So I made my terminal full screen and repeated the command, and it worked. It's interactive from that point.

Generally you get help from linux commands with:
> testdisk --help
OR
> man testdisk

...once you know the name of the executable anyway. Applications usually go in /usr/bin or /usr/local or /usr/sbin. You can see /usr/sbin/testdisk in the properties of testdisk in Synaptic, as the previous poster said. Maybe you were expecting a .exe after it? :roll:

---

### Post by justleen on 2006-03-31
.. i find that which and whereis can be quite usefull aswell
```

$ whereis testdisk
$ which testdisk

```

---

### Post by elamericano on 2006-03-31
And for non-commands try 'locate' or the all-powerful 'find'.

---

