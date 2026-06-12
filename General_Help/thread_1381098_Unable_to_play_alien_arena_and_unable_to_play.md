---
title: "Unable to play alien arena and unable to play"
date: 2010-01-14
forum: General Help
---

### Post by rasmus91 on 2010-01-14
Hey

I recently discovered how great a game Alien Arena is. and so i whished to update it, as i couldn't join any servers.

I ran in to a little trouble though, it wouldn't run the game giving me this:

```
~/.Games/alienarena7_33$ ./crx
./crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

```

I searched around a bit and found this solution: [http://ubuntuforums.org/showthread.php?t=956151]("http://ubuntuforums.org/showthread.php?t=956151") telling me that i need to compile the game my self, so thats what i tried, and i end up with this:
```
~/.Games/alienarena7_33/source$ make install
cp release/cr* ../
cp: cannot stat `release/cr*': No such file or directory
make: *** [install] Error 1
```
 but unable to find a solution.

any help would be appreciated.

---

