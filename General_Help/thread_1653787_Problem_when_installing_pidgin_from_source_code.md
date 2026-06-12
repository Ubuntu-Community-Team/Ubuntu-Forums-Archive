---
title: "Problem when installing pidgin from source code"
date: 2010-12-27
forum: General Help
---

### Post by soultrav on 2010-12-27
Hello,

I was trying to install pidgin from source code (because I wanted to modify some constants), but an error appears at 'make':
```

claudiu@elmer:~/Downloads/pidgin-2.7.9$ make
make  all-recursive
make[1]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9'
Making all in .
make[2]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9'
  GEN    package_revision_raw.txt
  GEN    package_revision.h
make[2]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9'
Making all in libpurple
make[2]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple'
make  all-recursive
make[3]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple'
Making all in gconf
make[4]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/gconf'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/gconf'
Making all in plugins
make[4]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/plugins'
Making all in perl
make[5]: Entering directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/plugins/perl'
  CC     perl.lo
../../../libtool: xrealloc: ../bash/subst.c:658: cannot allocate 67108864 bytes (805380096 bytes allocated)
make[5]: *** [perl.lo] Error 2
make[5]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/plugins/perl'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/claudiu/Downloads/pidgin-2.7.9'
make: *** [all] Error 2

```
I thought this happened because of those constants, so I changed them back to the original value, but the problem still persists.
./configure ran just fine. I am running Ubuntu version 10.10, and the pidgin I am trying to install is version 2.7.9. Any ideas?

---

