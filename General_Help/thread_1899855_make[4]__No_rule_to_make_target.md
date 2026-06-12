---
title: "make[4]: *** No rule to make target"
date: 2011-12-24
forum: General Help
---

### Post by princebadshah on 2011-12-24
hello  Geeks, 
I am stuck with MAKE compile error ...
Any help please

root@ubuntu:/home/elysium/uclinux/nios2-linux/uClinux-dist# make vendor_hwselect SYSPTF=/home/elysium/temp/try1.ptf
make ARCH=nios2   -C vendors vendor_hwselect
make[1]: Entering directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors'
make -C /home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2/. dir_v=/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2/. -f /home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/vendors-common.mak vendor_hwselect
make[2]: Entering directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2'
make hwselect
make[3]: Entering directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2'
make[3]: *** No rule to make target `hwselect'.  Stop.
make[3]: Leaving directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2'
make[2]: *** [vendor_hwselect] Error 2
make[2]: Leaving directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors/Altera/nios2'
make[1]: *** [vendor_hwselect] Error 2
make[1]: Leaving directory `/home/elysium/uclinux/nios2-linux/uClinux-dist/vendors'
make: *** [vendor_hwselect] Error 2

---

### Post by WorMzy on 2011-12-24
That means that the Makefile doesn't have a set of commands for the target you're trying to build. Try running:

```
make help
```

and see if that gives you a list of known targets. Otherwise try running this:

```
grep "^[a-zA-Z]*:$" Makefile
```

to see what targets are defined.

---

### Post by princebadshah on 2011-12-24
ooh thanks for your reply but when I did this it became more complex for me here is which i get

root@ubuntu:/home/elysium/uclinux/nios2-linux/uClinux-dist# make help
Quick reference for various supported make commands.
----------------------------------------------------

make xconfig               Configure the target etc
make config                "
make menuconfig            "
make qconfig               "
make gconfig               "
make dep                   2.4 and earlier kernels need this step
make                       build the entire tree and final images
make clean                 clean out compiled files, but not config
make distclean             clean out all non-distributed files
make oldconfig             re-run the config without interaction
make linux                 compile the selected kernel only
make romfs                 install all files to romfs directory
make image                 combine romfs and kernel into final image
make modules               build all modules
make modules_install       install modules into romfs
make DIR_only              build just the directory DIR
make DIR_romfs             install files from directory DIR to romfs
make DIR_clean             clean just the directory DIR
make single                non-parallelised build
make single[make-target]   non-parallelised build of "make-target"
make V/P_default           full default build for V=Vendor/P=Product
/bin/sh: -c: line 0: unexpected EOF while looking for matching `"'
/bin/sh: -c: line 1: syntax error: unexpected end of file
make: *** [help] Error 1
root@ubuntu:/home/elysium/uclinux/nios2-linux/uClinux-dist# grep "^[a-zA-Z]*:$" Makefile
remoteconfig:
modules:
image:
release:
sparse:
sparseall:
dep:
relink:
bugreport:
help:

---

### Post by WorMzy on 2011-12-24
That grep command was a little too hastily thrown together, don't worry that it doesn't match up to the help output.

I don't like that make help ends with an error, although that could just be a sh quirk. Try switching to bash

```
bash
```

then running it again

```
make help
```

In any case, from the output it looks like you're trying to build a kernel, although it doesn't look like the standard Linux kernel.

Can you tell us what you're trying to do, and what instructions you've been following (if any).

---

### Post by princebadshah on 2011-12-24
There is MAKEALL file in this current directory whose contents are following ,,,


#!/bin/sh

if [ "$1" = "-p" ] ; then
    pretend=true
    shift
else
    pretend=false
fi

MAKE=${MAKE:-make}
LOG_DIR="LOG"

arches="$@"
if [ -z "$arches" ] ; then
    all_arches=$(
        cd vendors/config
        echo */config.arch | sed 's:/config.arch::g'
    )
    arches=""
    for arch in ${all_arches} ; do
        CROSS_COMPILE=$(
            var="CROSS_COMPILE"
            makefile="vendors/config/${arch}/config.arch"
            export ROOTDIR=$PWD
            echo -e "e:\\n\\t@echo \$(${var})\\ninclude ${makefile}" | \
                ${MAKE} --no-print-directory -s -f - 2>/dev/null
        )
        if [ -n "$CROSS_COMPILE" ] ; then
            if ${CROSS_COMPILE}gcc -v 2>/dev/null 1>&2 ; then
                arches="${arch} ${arches}"
                echo "Adding ${arch} to build list"
            else
                echo "Skipping ${arch}: unable to find '${CROSS_COMPILE}gcc'"
            fi
        elif [ "${arch}" != "host" -a "${arch}" != "common" ] ; then
            echo "Skipping ${arch}: does not define CROSS_COMPILE"
        fi
    done
    echo
fi

mkdir -p "${LOG_DIR}"
PASS=""
FAIL=""
for arch in ${arches} ; do
    list=$(
        cd vendors
        grep -l ${arch}/config.arch */*/config.arch | sed 's:/config.arch::g'
    )
    echo "Building boards:"
    echo " `echo ${list} | sed 's: :\n :g'`"
    echo

    for board in ${list} ; do
        sanitized=$(echo "${board}" | sed s:/:_:g)
        log="${LOG_DIR}/${sanitized}.log"
        imgs="${LOG_DIR}/${sanitized}"
        rm -rf "${log}"{,.FAIL} "${imgs}" images
        printf "#### BUILDING BOARD: ${board}: "
        if ${pretend} || ${MAKE} ${board}_default > "${log}" 2>&1 ; then
            echo PASS
            PASS="${PASS} ${board}"
            if ! ${pretend} ; then
                rsync -a --delete images/ "${imgs}"
            fi
        else
            echo FAIL
            FAIL="${FAIL} ${board}"
            printf "\n\nSingle target ...\n\n" >> "${log}"
            ${MAKE} single >> "${log}" 2>&1
            ${MAKE} single > "${log}".FAIL 2>&1
        fi
        ${pretend} || svn st > "${log}".svn
    done
done

cat <<EOF

These boards passed:
 `echo ${PASS:-no passes here} | sed 's: :\n :g'`

These boards failed:
 `echo ${FAIL:-no failures here} | sed 's: :\n :g'`

EOF

[ -n "${FAIL}" ] && exit 1 || exit 0

---

### Post by princebadshah on 2011-12-24
> **WorMzy said:**
> That grep command was a little too hastily thrown together, don't worry that it doesn't match up to the help output.

I don't like that make help ends with an error, although that could just be a sh quirk. Try switching to bash

```
bash
```then running it again

```
make help
```In any case, from the output it looks like you're trying to build a kernel, although it doesn't look like the standard Linux kernel.

Can you tell us what you're trying to do, and what instructions you've been following (if any).


oot@ubuntu:/home/elysium/uclinux/nios2-linux/uClinux-dist# bash
root@ubuntu:/home/elysium/uclinux/nios2-linux/uClinux-dist# make help
Quick reference for various supported make commands.
----------------------------------------------------

make xconfig               Configure the target etc
make config                "
make menuconfig            "
make qconfig               "
make gconfig               "
make dep                   2.4 and earlier kernels need this step
make                       build the entire tree and final images
make clean                 clean out compiled files, but not config
make distclean             clean out all non-distributed files
make oldconfig             re-run the config without interaction
make linux                 compile the selected kernel only
make romfs                 install all files to romfs directory
make image                 combine romfs and kernel into final image
make modules               build all modules
make modules_install       install modules into romfs
make DIR_only              build just the directory DIR
make DIR_romfs             install files from directory DIR to romfs
make DIR_clean             clean just the directory DIR
make single                non-parallelised build
make single[make-target]   non-parallelised build of "make-target"
make V/P_default           full default build for V=Vendor/P=Product
/bin/sh: -c: line 0: unexpected EOF while looking for matching `"'
/bin/sh: -c: line 1: syntax error: unexpected end of file
make: *** [help] Error 1


I am MS student compiing uClinux kernel for Altera DE2 board and following

[http://www.alterawiki.com/wiki/Install_Nios_II_Linux#Nios2_Linux_Tarball](http://www.alterawiki.com/wiki/Install_Nios_II_Linux#Nios2_Linux_Tarball)

Thanks alot for your help  ...

I dont know whether it is a prob regarding ubuntu or uclinux

---

### Post by WorMzy on 2011-12-25
Hm, I get the feeling that that project is very out of date. GCC 4.2 hasn't been in the Ubuntu repositories since Hardy (8.04).


Anyway, I just realised that you posted the MAKEALL file, and it has sh in the shebang. Have you followed the earlier instructions on that tutorial about changing the /bin/sh symlink so that it points to bash, rather than dash (which is the default on Ubuntu)?

---

### Post by princebadshah on 2011-12-25
Yes, I changes to bash... and  everything went fine untill this
 make vendor_hwselect SYSPTF=/home/elysium/temp/try1.ptf
I posted MAKEALL to verify that there would e an error in that file  as main error is 
&quot;No rule to make target `hwselect'.  Stop.&quot;.

---

### Post by WorMzy on 2011-12-25
Sorry for the lateness of this reply, busy day and all that. :)

I've tried following the tutorial, and I'm stumbling at the same point, albeit with a different error (possibly due to my not having an ptf file or a 2.6 kernel config handy). I'm afraid that you'll have to wait for some assistance from someone with more expertise in this area, or else see if you can find more direct help from someone associated with Nios II (you might want to check here: [http://www.alteraforum.com/]("http://www.alteraforum.com/")).

Sorry I can't be of more help.

---

