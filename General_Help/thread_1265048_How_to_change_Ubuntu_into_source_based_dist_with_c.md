---
title: "How to change Ubuntu into source based dist with compile optimzations"
date: 2009-09-12
forum: General Help
---

### Post by Darvenkry on 2009-09-12
I've used Gentoo before, and i liked how it compiled all my packages from source with GCC optimizations flags. So all my files were optimized for my system (ie. put cflags like --msse3 --fastmath -O3 etc.). Is there a way to get synaptic to do this? And where can I add optimization cflags in ubuntu ( Gentoo had /etc/Make).

---

### Post by stderr on 2009-09-12
Ubuntu, based on Debian, doesn't compile as it goes. It downloads pre-compiled packages in [.deb format]("http://en.wikipedia.org/wiki/Deb_(file_format)"). This makes the whole operation quick and easy.

You can download source and compile from that yourself, but that's separate from the dependency handling and auto-updating of aptitude via the synaptic GUI.

I suppose I should say you can grab source via:

```
sudo apt-get source PACKAGE_NAME
```

edit: You may like to peruse [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine"):

> 
Explanation of the Repository Format 
[...]
deb: These repositories contain binaries or precompiled packages. These repositories are required for most users. 


and compare to your /etc/apt/sources.list file. You notice most lines will begin with "deb".

To get a better impression, how about browsing the http repos yourself? You get a better idea that way. Point your browser at [http://gb.archive.ubuntu.com/ubuntu/]("http://gb.archive.ubuntu.com/ubuntu/"), for example, and look under both the dists directory and pool directory. 

In terms of optimising your system, this probably isn't what you were hoping for, but these are different distros with different pluses and minuses. Personally I love Debian, but the Gentoo way certainly has lots of obvious benefits too.

---

