---
title: "installing gmt"
date: 2010-01-09
forum: General Help
---

### Post by thelastsamurai on 2010-01-09
hi...
I am sort of a newbie in ubuntu. i have installed GMT(Generic Mapping Tools) in ubuntu 9.04. I installed it using
"sudo apt-get install gmt" from the terminal but i cant find the installation directory.:-k
Can I install the whole package in a user defined directory, eg, in /usr/local/GMT?
Also how do I have to export the PATH in ~/.bashrc?
Thank u in advance...

---

### Post by Leppie on 2010-01-09
you can use the find command to look for files/folders:
```
sudo find / -name gmt
```
or if you're looking for an executable, use which:
```
which gmt  ##if gmt is the executable
```

---

### Post by OldGrantonian on 2010-01-09
> **thelastsamurai said:**
> hi...
i cant find the installation directory


I'm no techie, but have you tried:
 
 locate -r /gmt/

> 
Can I install the whole package in a user defined directory, eg, in /usr/local/GMT?
It's probably safer to allow synaptic to manage everything.

> 
Also how do I have to export the PATH in ~/.bashrc?
I'm sure that synaptic manages the PATH. I've installed lots of stuff, but I've never specified a path.
.

---

### Post by Leppie on 2010-01-09
using synaptic (or apt-get, aptitude, dpkg) gmt seems to install to /usr/share/gmt and /usr/lib/gmt.
i found a bunch of executables in /usr/lib/gmt/bin.

hope this helps.

---

### Post by thelastsamurai on 2010-01-19
Thank u to all of u.........now GMT is working properly(atleast for the time being):):):):):)

---

### Post by Leppie on 2010-01-19
glad it's working :)

---

### Post by relio10 on 2011-03-31
wondering if you can post how it is you solved the problem.  have found files using methods described, but at a bit of a loss past that point. 

thanks for any help.

---

