---
title: "Multiple Issues"
date: 2011-07-07
forum: General Help
---

### Post by Aaeru on 2011-07-07
Hello, I'm relatively new to linux and ubuntu both. I've done fine so far figuring things out for myself, but recently I came across a problem. And it is that I can't seem to run Synaptic Package Manager or the Update Manager without them giving me errors and closing. Also, if I try to use nautilus to navigate to any folder on my machine, nautilus simply self terminates and restarts, without me ever seeing the folder I tried to open. Also, when I try to add an icon or shortcut to my desktop, this happens as well.

So to start off I'm running:

Ubuntu 10.4 (lucid)
Kernel Linux 2.6.32-32 Generic
Gnome 2.30.2

3 Gb Ram
Intel Core 2 Duo 2.40 GHz

If any other system specifications are needed, please let me know.

Ok here goes.

When I run Synaptic Package Manager, I get this

```
~$ sudo synaptic
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 699, in <module>
    res = updateIndex(dbpath, addons, progress)
  File "/usr/sbin/update-apt-xapian-index", line 340, in updateIndex
    cache = apt.Cache(memonly=True,progress=aptprogress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 86, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 123, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.

```

And when I run the Update Manager, I get this:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'
```

Any and all help would be greatly appreciated.

---

### Post by _Narcisse_ on 2011-07-07
Hello,

A question similar to yours has been answered [here on Launchpad]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/66668"). Check out the commands in firsts comments, it seems they solve the issue. If you're somewhat familiar with the command line, you could try to execute them and see if it works. Be careful though, because some commands like 'rm' can be dangerous if typed incorrectly.

I can't really know for sure, because in years of Ubuntu this never happened to me. Had to happen to some people I guess :biggrin:

Also, check or post your /etc/apt/sources.list file

Good luck

---

### Post by Aaeru on 2011-07-08
Thank you very much. The problem was solved after I did all that and upgraded to 10.10 as well. I still have some broken dependencies, but I believe I can take care of those myself.

---

### Post by kanishkdudeja on 2011-07-08
Good fix..:)

---

