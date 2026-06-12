---
title: "Redcar installation on Ubuntu 9.04"
date: 2009-06-25
forum: General Help
---

### Post by mikeshn on 2009-06-25
I'm using these instructions to install redcar on Ubuntu 9.04 ([http://github.com/danlucraft/redcar/blob/eeebf739365d8bfd0e06ed001bd6b7960d76daa3/INSTALL.md](http://github.com/danlucraft/redcar/blob/eeebf739365d8bfd0e06ed001bd6b7960d76daa3/INSTALL.md)).

**However, it is failing in step #3  with following messages:**
root@mike:/home/mike# sudo cp rbgdkconversions.h /usr/lib/ruby/1.8/i486-linux/
cp: cannot create regular file `/usr/lib/ruby/1.8/i486-linux/': Is a directory
root@mike:/home/mike# sudo cp rbgtkconversions.h /usr/lib/ruby/1.8/i486-linux/
cp: cannot create regular file `/usr/lib/ruby/1.8/i486-linux/': Is a directory

Any suggestion would be appreciate.

Thanks

---

### Post by kwacka on 2009-06-27
First thought is to manually copy to the directory listed using full filename:```
sudo cp rbgdkconversions.h /usr/lib/ruby/1.8/i486-linux/rbgdkconversions.h
```

---

### Post by mikeshn on 2009-06-29
> **kwacka said:**
> First thought is to manually copy to the directory listed using full filename:```
sudo cp rbgdkconversions.h /usr/lib/ruby/1.8/i486-linux/rbgdkconversions.h
```

The directory doesn't exist...

---

### Post by theApokalypsis on 2009-08-07
> **mikeshn said:**
> The directory doesn't exist...

If still having some issues,

The directory (well Im using x86_64 linux) the directory was not i486 or whatever, it was usr/lib/ruby/1.8x86_64-linux/

I didnt really use any of the ./configure options.

---

