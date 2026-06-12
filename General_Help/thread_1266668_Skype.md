---
title: "Skype"
date: 2009-09-14
forum: General Help
---

### Post by boondocks on 2009-09-14
Just downloaded 32 and 64 bit versions of Skype:
[LIST]
[*]skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
[*]skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
[/LIST]
This Ubuntu 9.04 system is an
"Intel(R)  Core(TM)  Duo CPU   T2450  @ 2.00GHz stepping 0c"

Questions:
[LIST=1]
[*]How do I install this via the command line?  I have ONLY ssh access.
[*]Which deb file should I use?
[/LIST]

---

### Post by eldragon on 2009-09-14
> **boondocks said:**
> Just downloaded 32 and 64 bit versions of Skype:
[LIST]
[*]skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
[*]skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
[/LIST]
This Ubuntu 9.04 system is an
"Intel(R)  Core(TM)  Duo CPU   T2450  @ 2.00GHz stepping 0c"

Questions:
[LIST=1]
[*]How do I install this via the command line?  I have ONLY ssh access.
[*]Which deb file should I use?
[/LIST]

check the output of
```

uname -a

```

if it gives any indication of a 64bit system, then [*]skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
otherwise,the other one ;)

---

### Post by boondocks on 2009-09-14
uname -a 
> Linux ubsys  2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

So would this be the correct way to install it?```

 sudo  aptitude   install  skype-ubuntu-intrepid_2.1.0.47-1_i386.deb 
```

---

