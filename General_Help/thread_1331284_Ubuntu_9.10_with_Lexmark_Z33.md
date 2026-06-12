---
title: "Ubuntu 9.10 with Lexmark Z33"
date: 2009-11-19
forum: General Help
---

### Post by Butic on 2009-11-19
Lexmark Z33 doesn't work in Ubuntu 9.10.
I followed this [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+z33](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+z33) manual and everything goes ok until this step
```
/etc/rc2.d/S19cupsys restart
```nevertheless i figured out that i can use this instead
```
sudo /etc/rc2.d/S50cups restart
```anyway there was another problem
this command 
```
./z600
```shows error:

> ./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ok. i tried to install it doing like this:
```
sudo apt-get install libstdc++5
```it shows following lines:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidateok.... i tried to symlink libstdc++.so.6 to libstdc++.so.5 in /usr/lib/
but it doesnt help. just a bunch of new errors....

God, help me!

---

