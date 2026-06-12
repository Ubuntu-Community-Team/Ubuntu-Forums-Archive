---
title: "Which package is &quot;ld&quot; in?"
date: 2010-05-15
forum: General Help
---

### Post by dodle on 2010-05-15
I messed up some system files on my computer when I was trying to manually compile MinGW.  Now, I think, I need to reinstall ld, but I cannot figure out which package it comes in.  I am unable to compile anything using g++ or gcc.  Here is the error:
```
/usr/bin/ld: cannot find -lstdc++
```
I have tried reinstalling packages [color=red]libstdc++6-4.4[/color] and [color=red]libstdc++6-4.4-dev[/color] to no avail.  So I think ld may have been replaced when I compiled and installed MinGW.  Unfortunately, I was unable to do a "sudo make uninstall", so I was unable to remove the MinGW files.  

I've already received help for one problem this has cuased: [http://ubuntuforums.org/showthread.php?t=1482684](http://ubuntuforums.org/showthread.php?t=1482684), but I am sure I will find even more errors in my system.

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
Might be faster to backup and re-install. You can remove the MinGW files manually. Not sure what ld is but google found [http://packages.ubuntu.com/dapper/ld.so.preload-manager](http://packages.ubuntu.com/dapper/ld.so.preload-manager)

---

### Post by warfacegod on 2010-05-15
I agree with sin. A new install seems like it would be far more simple. If you have your home folder on a separate HDD (like a sane human being:P), a backup wouldn't be strictly necessary.

---

### Post by Sin@Sin-Sacrifice on 2010-05-15
@warface - hahahahahahahahaaaa... quantum mechanics... but Einstein WAS wrong in that case.

---

### Post by demosthenese on 2010-05-15
Don't have an ubuntu system handy right now but entering 

```
apt-cache search linker
```

will give you some clues. On my debian system the most likely of the results is binutils.  Then running synaptic and selecting binutils, I can look at the installed files tab and see that /usr/bin/ld is indeed there.

Probably the same on ubuntu, but use apt-cache and synaptic to check.

Then try a reinstall of binutils.

Edit:
BTW got the linker keyword from doing a man ld.

---

### Post by gmargo on 2010-05-15
> **dodle said:**
> Now, I think, I need to reinstall ld, but I cannot figure out which package it comes in.

To figure out what package the **ld** program is in:
```

$ dpkg -S `which ld`
binutils: /usr/bin/ld

```

If the package is not installed, a good resource is [http://packages.ubuntu.com/](http://packages.ubuntu.com/) which allows you to search for a particular file.  Here is the search string for "ld": [http://packages.ubuntu.com/search?searchon=contents&keywords=ld&mode=exactfilename&suite=lucid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=ld&mode=exactfilename&suite=lucid&arch=any)

---

### Post by dodle on 2010-05-16
@ Sin and Warface:  I would do a reinstall, but I have to wait until I get a new cd drive as mine has given out, or try to figure out how to install from a USB drive, though I'm not sure my bios supports it.

I reinstalled binutils, but I still cannot compile my program.  I get the same error.  So I guess ld is not the problem :(.

---

### Post by dodle on 2010-05-16
Found my problem.  I created a link called libstdc++.so to libstdc++.so.6.  Apparently this link was missing and not being reinstalled with any of the packages that I tried.  Looking over this thread: [http://ubuntuforums.org/showthread.php?t=1482684](http://ubuntuforums.org/showthread.php?t=1482684), I probably deleted the file myself.

---

### Post by luigi_mb on 2010-05-16
> **dodle said:**
> I messed up some system files on my computer when I was trying to manually compile MinGW.  Now, I think, I need to reinstall ld, but I cannot figure out which package it comes in.  I am unable to compile anything using g++ or gcc.  Here is the error:
```
/usr/bin/ld: cannot find -lstdc++
```
I have tried reinstalling packages [color=red]libstdc++6-4.4[/color] and [color=red]libstdc++6-4.4-dev[/color] to no avail.  So I think ld may have been replaced when I compiled and installed MinGW.  Unfortunately, I was unable to do a "sudo make uninstall", so I was unable to remove the MinGW files.


It's not "ld" which is missing, but "stdc++". Try Synaptic and search for "std++", and see what you are missing.

/luigi

---

