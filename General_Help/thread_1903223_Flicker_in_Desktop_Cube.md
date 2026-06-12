---
title: "Flicker in Desktop Cube"
date: 2012-01-02
forum: General Help
---

### Post by mclizardman on 2012-01-02
Hello, I am having a problem when I use the desktop cube. Whenever I turn the cube, there is a flicker of the previous image that appears in the current screen, and it lasts only a split second. This is really annoying, and was wondering if anyone else was having this problem, or knows how to fix it. Thanks!

---

### Post by mclizardman on 2012-01-03
Bump

---

### Post by bluexrider on 2012-01-03
> **mclizardman said:**
> Hello, I am having a problem when I use the desktop cube. Whenever I turn the cube, there is a flicker of the previous image that appears in the current screen, and it lasts only a split second. This is really annoying, and was wondering if anyone else was having this problem, or knows how to fix it. Thanks!
I have heard of this issue and experienced it once before. I think I reset compiz by using

```
gconftool-2 --recursive-unset /apps/compiz
```

then deleted the /.compiz folder and rebooting

---

### Post by collisionystm on 2012-01-03
> **mclizardman said:**
> Hello, I am having a problem when I use the desktop cube. Whenever I turn the cube, there is a flicker of the previous image that appears in the current screen, and it lasts only a split second. This is really annoying, and was wondering if anyone else was having this problem, or knows how to fix it. Thanks!

Yeah disable sync to vblank

open compiz config

click on OpenGL

set texture filter to fast and uncheck sync to vblank

log out and back in

---

### Post by mc4man on 2012-01-03
If none of the above help then you are one of many where rotate is currently unusable
bug report here, there possibly will be a fix in the future, don't hold your breath.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

---

### Post by mclizardman on 2012-01-04
Unfortunately, none of those suggestions worked. It's strange, it worked fine in Narwhal...

---

### Post by bluexrider on 2012-01-04
> **mclizardman said:**
> Unfortunately, none of those suggestions worked. It's strange, it worked fine in Narwhal...

It is a reported bug......I did find this might help:

                   This behavior annoyed me to the point where I finally pulled the oneiric versions of the debs and used --force-downgrade
which incidentally, while not ideal did result in a compiz that behaves  like it should.   As a workaround while waiting for a proper fix, it  seems to work better than the current packages.
   In the interest of disclosure, I'm not using unity so if you expect  unity to work this isn't the route to go.  Otherwise, dpkg -l | grep  compiz and replace anything with '0.9.6' in the version with it's  oneiric-era '0.9.4' equivalent.  There will be a couple extra '0.9.6'  packages without equivalents (probably due to some package  restructuring) that had to be removed outright (e.g. compiz-plugins-default, etc.).  Now make sure you also replace 'libdecoration0' (and 'libdecoration0-dev'  if appropriate) with their '0.9.4' oneiric equivalents as well.  Then  cross your fingers and reboot.  Pinning these packages until a proper  fix is available is left as an exercise for the reader.  No guarantees  of course, but it's working beautifully for me.


[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

---

