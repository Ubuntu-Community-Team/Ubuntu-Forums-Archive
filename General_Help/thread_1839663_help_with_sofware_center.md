---
title: "help with sofware center"
date: 2011-09-06
forum: General Help
---

### Post by camilo23 on 2011-09-06
so my software center opens up and everything but when i wanna download a new program or uninstall one the list never shows up it just loads forever im not sure what the problem is or how to fix it
any help appreciated i have ubuntu 11.04

---

### Post by jfed on 2011-09-06
Try installing a dummy program with apt and see what happens

```
sudo apt-get install kautoclick
```

or any other light program with only a few dependencies, see if that works. You can always uninstall the program afterwards if you don't want it.

---

### Post by raja.genupula on 2011-09-06
give us ```

sudo apt-get update
```

output

---

### Post by camilo23 on 2011-09-07
> **raja.genupula said:**
> give us ```

sudo apt-get update
```

output

it shows this
  
"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read."
  no idea sorry im new to the whole ubuntu thing

---

### Post by camilo23 on 2011-09-07
> **jfed said:**
> Try installing a dummy program with apt and see what happens

```
sudo apt-get install kautoclick
```

or any other light program with only a few dependencies, see if that works. You can always uninstall the program afterwards if you don't want it.

is what its says im new to ubuntu so im not sure what it means
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "

---

### Post by raja.genupula on 2011-09-07
> **camilo23 said:**
> is what its says im new to ubuntu so im not sure what it means
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. "

Hey
then do this man , ubuntu never suggest the wrong  
```
sudo dpkg --configure -a
```
hope
its gonna solve your issue .

---

### Post by polki@mac.com on 2011-09-07
> **camilo23 said:**
> it shows this
  
"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read."
  no idea sorry im new to the whole ubuntu thing

The "playonlinux.list" might be malformed. It shouldn't start with "<!DOCTYPE".

Have a look in that file and see if you find strange things.

---

### Post by oldos2er on 2011-09-07
> **camilo23 said:**
> it shows this
  
"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read."
  no idea sorry im new to the whole ubuntu thing

Just remove that file that's corrupted: ```
sudo rm /etc/apt/sources.list.d/playonlinux.list

sudo apt-get update
```

---

### Post by camilo23 on 2011-09-07
that did it thanks so much     now i get this unhandlable error   and it says this   i would sure like to know what to do about it   "Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package."    thank you for your help and time  i really apologize for my inexperience

---

### Post by oldos2er on 2011-09-08
To install sun-java6-jre, you need to enable the partner repository. Run **software-properties-gtk**, Other Software tab, tick the boxes next to Canonical Partners. When you're done, run ```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

Not sure about the python2.7 error.

---

