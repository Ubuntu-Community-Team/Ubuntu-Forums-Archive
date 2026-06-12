---
title: "fglrx compile with dpkg"
date: 2006-05-11
forum: General Help
---

### Post by flapane on 2006-05-11
flapane@a64:/usr/src/linux$ fakeroot make-kpkg --added_modules=fglrx-kernel 
modules_image
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.15-fla" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" 
KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package 
Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="x86_64"                  \
                             KDREV="10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  
\
                      echo "If you see messages that indicate that it is not"; 
\
                      echo "in fact being built as root, please file a bug ";  
\
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
echo "ROOT_CMD = "
ROOT_CMD =
/usr/bin/make -w -f debian/rules binary_modules
make[2]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
        ln -s Makefile.kbuild Makefile ; \
        cd .. ; \

#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
                
cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; 
\
        fi
dh_testdir
dh_testroot
PATCHLEVEL = 6
Kernel compiler version : 4.0.2
Detected compiler version : 4.0.3

You appear to be compiling the ATI kernel module with
a compiler different from the one that was used to compile
the running kernel. This may be perfectly alright and you
may be building this module for another kernel in which case
you may ignore this message.

The compiler that will be used to compile this module has been
determined from:
 1) the CC environment variable
 2) that specified in
    /usr/src/linux/include/linux/compile.h
 3) gcc
Using compiler gcc-4.0 version 4.0.3
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/gcc-check
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 
CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f 
Makefile SYSSRC=/usr/src/linux   KBUILD_PARAMS="-C /usr/src/linux 
SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[3]: Entering directory 
`/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory 
`/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue


I don't think the problem is the 4.0.2 against 4.0.3 of gcc, because here it says he can't find the Makefile!!

---

### Post by wzzrd on 2006-05-23
Did you ever find a sollution to this? I suffer the same problem!

---

### Post by flapane on 2006-05-23
i never solved, i gave up and started using radeon drivers, could ati programmers burn in the hell, i followed ALL their tips and put all the modules they suggest, without lucky.

---

### Post by wzzrd on 2006-05-23
I keep waking up in the middle of the night screaming 'nVidia!'. Ever experienced that? Funny stuff. Scares the shit out of my girlfriend though...

Wish I hadn't bought a Radeon. Damn' wish I hadn't...

---

### Post by flapane on 2006-05-23
yes...

---

### Post by wzzrd on 2006-05-23
Well, I finally did it. I'm not sure how though. After installing all the debs, I unpacked the fglrx-kernel-source tarball to /usr/src. 
And then I ran the modules-prepare build, install etc. command from within /usr/src. This procedure seems to have fixed the problem with the makefile errors in the building of the module. Still, I tinkered so friggin' much with this stuff, I'm not sure this did the trick. Might have been something else I did I forgot about ;)

However, after editing /etc/X11/xorg.conf and rebooting, I now have an accelerated desktop. At last.

---

### Post by flapane on 2006-05-23
but with your own compiled kernel or with an ubuntu kernel?
and if is compiled from you, could you post your .config file?

---

