---
title: "libstdc++.so.6: version `GLIBCXX_3.4.11' not found"
date: 2010-05-13
forum: General Help
---

### Post by dodle on 2010-05-13
I have messed up something on my system.  If I try to run anything that uses apt I get the following error:
```
/usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found
```

I have tried manually installing the following packages from packages.ubuntu.com with dpkg:
[list][*]libstdc++6_4.4.1-4ubuntu9_i386.deb[*]libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb[*]gcc-4.4-base_4.4.1-4ubuntu9_i386.deb[*]gcc-4.4_4.4.1-4ubuntu9_i386.deb[*]g++-4.4_4.4.1-4ubuntu9_i386.deb[*]cpp-4.4_4.4.1-4ubuntu9_i386.deb[*]libc6_2.10.1-0ubuntu16_i386.deb[*]apt_0.7.23.1ubuntu2_i386.deb[*]apt-build_0.12.37_i386.deb[*]apt-utils_0.7.23.1ubuntu2_i386.deb[/list]

But none of them have fixed the problem.  Does anyone know which package I need to install, or how I fix this problem?  I am afraid to turn off my computer for fear that it will not restart.  I am using Ubuntu 9.10 Karmic.

---

### Post by gmargo on 2010-05-13
> **dodle said:**
> 
```
/usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found
```

Remove that file.  Where did it come from?  Did you compile it yourself?  It's not from a standard ubuntu package.

---

### Post by dodle on 2010-05-14
Okay, I think that explains it.  I've been trying to compile and install MinGW from source.  But I forgot to set the prefix and installed it to the wrong directory tree.  Then when I tried to uninstall it, I got:
```
$ sudo make uninstall
the uninstall target is not supported in this tree
```

So there are probably other unwanted files sitting around on my system, and I have no idea how to find and get rid of them.  

Thanks, deleting that file worked.

---

