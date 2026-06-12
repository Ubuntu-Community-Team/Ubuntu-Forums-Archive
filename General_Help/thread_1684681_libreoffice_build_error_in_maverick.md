---
title: "libreoffice build error in maverick"
date: 2011-02-09
forum: General Help
---

### Post by fremantle on 2011-02-09
im trying to build libreoffice 3 in my maverick machine, but after doing 'make' i got this build error
> Building module boost
=============
Entering /home/abr/libreoffice/libreoffice-build-3.3.0.4/build/libreoffice-3.3.0.4/boost

mkout -- version: 1.8
dmake:  Error: -- `./unxlngppc.pro/misc/f02578f5218f217a9f20e9c30e119c6a-boost_1_44_0.unpack' not found, and can't be made
Forcing regeneration of dependency info

nothing to do here...
dmake:  Error: -- `./unxlngppc.pro/misc/f02578f5218f217a9f20e9c30e119c6a-boost_1_44_0.unpack' not found, and can't be made
Retrying /home/abr/libreoffice/libreoffice-build-3.3.0.4/build/libreoffice-3.3.0.4/boost

dmake:  Error: -- `./unxlngppc.pro/misc/f02578f5218f217a9f20e9c30e119c6a-boost_1_44_0.unpack' not found, and can't be made

-----------------------------------------------------------------------
        Oh dear - something failed during the build - sorry !
  For more help with debugging build errors, please see the section in:
            [http://wiki.documentfoundation.org/Development](http://wiki.documentfoundation.org/Development)

 it seems that the error is inside 'boost', please re-run build
 inside this module to isolate the error and/or test your fix:
-----------------------------------------------------------------------

rm -Rf /home/abr/libreoffice/libreoffice-build-3.3.0.4/build/libreoffice-3.3.0.4/boost/unxlngppc.pro # optional module 'clean'
/bin/bash
cd /home/abr/libreoffice/libreoffice-build-3.3.0.4/build/libreoffice-3.3.0.4
source ./LinuxPPCEnv.Set.sh
cd boost
build

when the problem is isolated and fixed exit and re-run 'make' from the top-level
abr@abr-laptop:~/libreoffice/libreoffice-build-3.3.0.4/build/libreoffice-3.3.0.4/boost$

i cant figure it out here (kinda new at this), any helP?

---

### Post by davidmohammed on 2011-02-09
no idea - why are you trying to build it? - just install it from [the ppa]("http://www.omgubuntu.co.uk/2011/01/libreoffice-3-3-released/")

---

### Post by fremantle on 2011-02-09
ppa doesnt have a powerpc build

---

