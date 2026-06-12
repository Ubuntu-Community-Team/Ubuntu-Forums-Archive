---
title: "Cannot find boost_system-mt"
date: 2010-01-27
forum: General Help
---

### Post by M_Mungo on 2010-01-27
Hello.

I'm running Ubuntu Jaunty 9.04

I recently tried to install 0 A.D. (rts game).  I receive the following errors:

[I]Linking AtlasUI
/usr/bin/ld: cannot find -lboost_system-mt
collect2: ld returned 1 exit status
make[1]: *** [../../../binaries/system/libAtlasUI_dbg.so] Error 1
make: *** [AtlasUI] Error 2
make: *** Waiting for unfinished jobs....
/usr/bin/ld: cannot find -lboost_system-mt
collect2: ld returned 1 exit status
make[1]: *** [../../../binaries/system/pyrogenesis_dbg] Error 1
make: *** [pyrogenesis] Error 2
Linking test
/usr/bin/ld: cannot find -lboost_system-mt
collect2: ld returned 1 exit status
make[1]: *** [../../../binaries/system/test_dbg] Error 1
make: *** [test] Error 2
michael@michael-desktop:~/trunk/build/workspaces/gcc$ [/I]

I tried using synaptic package manager to update boost but, the compiling for the game stops much sooner in the overall process.

Any ideas out there?

---

### Post by raktarok on 2010-01-28
Hi,

I would suggest you to install some packages, if they are not already installed.

```
sudo apt-get install libboost-system-dev 
```

If this doesn't solve it, then try this too.

```
sudo apt-get install libboost*
```

Also, have a look at auto-apt - I find it very useful when I am compiling programs. 
[https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt)

---

