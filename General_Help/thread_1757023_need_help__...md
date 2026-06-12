---
title: "need help  .."
date: 2011-05-13
forum: General Help
---

### Post by neomaniac on 2011-05-13
i'm workin on QEMU for ARM on ubuntu 11.4  
and i needed to run this symbian-qemu-0.9.1-12-arm-none-symbianelf.sh script 
which is in this link
[http://www.duckload.com/download/5659095/symbian-qemu-0.9.1-12-arm-none-symbianelf.sh](http://www.duckload.com/download/5659095/symbian-qemu-0.9.1-12-arm-none-symbianelf.sh)

but i get this error .. 
mkdir: cannot create directory `/scratch': Permission denied

is there any way to work around it and be able to create folders outside the root folder ??

---

### Post by Lars Noodén on 2011-05-13
Can you show us the contents of the script around the lines that are producing the error?

---

### Post by neomaniac on 2011-05-13
well .. this is a portion of the script

pushenvvar CSL_SCRIPTDIR /scratch/paul/qemu/src/scripts-trunk
pushenvvar PATH /usr/local/tools/gcc-3.4.0/bin:/bin:/usr/bin
pushenvvar LD_LIBRARY_PATH /usr/local/tools/gcc-3.4.0/lib64:/usr/local/tools/gcc-3.4.0/lib
pushenvvar QMTEST_CLASS_PATH QMTEST_CLASS_PATH
pushenvvar MAKEINFO makeinfo
clean_environment
# task [001/090] /init/dirs
pushenv
pushenvvar CC_FOR_BUILD i686-pc-linux-gnu-gcc
mkdir -p /scratch/paul/qemu/obj
mkdir -p /scratch/paul/qemu/install
mkdir -p /scratch/paul/qemu/pkg
mkdir -p /scratch/paul/qemu/logs/data
mkdir -p /scratch/paul/qemu/install/share/doc/symbian-qemu-arm-none-symbianelf/html
mkdir -p /scratch/paul/qemu/install/share/doc/symbian-qemu-arm-none-symbianelf/pdf
popenv

---

### Post by Lars Noodén on 2011-05-13
If you make a directory **/scratch** as root and then make yourself the owner, the script should run.  Or you could rewrite parts of the script that refer to /scratch and point it to /home/neomaniac/scratch or something like that.

---

### Post by neomaniac on 2011-05-13
well .. i changed the permissions but still the same error ... 
is there anyother way around this other than rewriting these lines  ?? .. i mean it's almost 2400 line in there about 50% creating directories like this :D

---

### Post by Lars Noodén on 2011-05-13
> **neomaniac said:**
> well .. i changed the permissions but still the same error ... 
is there anyother way around this other than rewriting these lines  ?? .. i mean it's almost 2400 line in there about 50% creating directories like this :D

No.  The author hard-coded the paths instead of using a variable.  If you are careful you could do search and replace.

---

### Post by neomaniac on 2011-05-13
well .. that didn't work  .. 

the thing is i'm working on this other script 

1-    #!/bin/sh
2-    #Script to boot a qemu/syborg text-shell rom.
3-    #You first need to have built your rom with syborg_builder.sh, and qemu with qemu_builder.sh 
4-
5- export EPOCROOT=~/symbian/gcc/ 
6- export PYTHONPATH=${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/plugins 
7- cd ${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/bin ./qemu-system-arm -serial 
8- file:${EPOCROOT}syborg_serial.log \ -M ${EPOCROOT}sf/adaptation/qemu/baseport/syborg/syborg.dtb -kernel $/home/m3ssaf/epocroot-pdk-3.0.i/epoc32/rom/syborg_tshell_ARMV5_udeb.img

and i have 2 errors in it  ..  in lines 7 & 8 
the line 7 is basically because i don't have a bin folder with the script qemu-system-arm -serial in it  .. & the script i posted about should have provided me with the one i needed  .. 
but it didn't work out after all .. any help on how i can get what i'm missing ??

---

### Post by Lars Noodén on 2011-05-13
> **neomaniac said:**
> 
the line 7 is basically because i don't have a bin folder with the script qemu-system-arm -serial in it 

It sounds like you just have to go through each step manually.  
One thing that might or might not be useful is [test](http://manpages.ubuntu.com/manpages/natty/en/man1/test.1posix.html)

```

test -d /some/dir || mkdir -p /some/dir

```

---

### Post by neomaniac on 2011-05-13
i got the first error "line 7" working  .. it was just that i needed to rebuild the qemu but the script was in sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/arm-softmmu

now regarding the other error "line 8" what does file$ mean ??

---

### Post by Lars Noodén on 2011-05-14
> **neomaniac said:**
> 
now regarding the other error "line 8" what does file$ mean ??

[file](http://manpages.ubuntu.com/manpages/natty/en/man1/file.1posix.html) guesses the file type.  Are you sure the spacing is not off in the version of line 8 you have pasted here?

---

### Post by neomaniac on 2011-05-14
yea i think it's exactly as i posted it .. 
i got that script from this tutorial .. 
[http://www.symlab.org/wiki/index.php/How_to_build_and_run_a_Symbian_QEMU_ROM_with_GNU/Linux_tools](http://www.symlab.org/wiki/index.php/How_to_build_and_run_a_Symbian_QEMU_ROM_with_GNU/Linux_tools)

the thing is ..as i understood it  .. there should be a syborg_serial.log in this location .. 
but when i navigated to it it wasn't there  .. so ??
if it's just to write logs in it i can just create it  .. but it also doesn't recognize it and gives me the same error  ..

---

### Post by Lars Noodén on 2011-05-14
> **neomaniac said:**
> yea i think it's exactly as i posted it .. 
i got that script from this tutorial .. 
[http://www.symlab.org/wiki/index.php/How_to_build_and_run_a_Symbian_QEMU_ROM_with_GNU/Linux_tools](http://www.symlab.org/wiki/index.php/How_to_build_and_run_a_Symbian_QEMU_ROM_with_GNU/Linux_tools)

the thing is ..as i understood it  .. there should be a syborg_serial.log in this location .. 
but when i navigated to it it wasn't there  .. so ??
if it's just to write logs in it i can just create it  .. but it also doesn't recognize it and gives me the same error  ..

The spacing looks off.  Here is my guess:

```

export EPOCROOT=~/symbian/gcc/;

export PYTHONPATH=${EPOCROOT}sf/adapt/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/plugins;

cd ${EPOCROOT}sf/adapt/qemu/symbian-qemu-0.9.1-12/bin;

./qemu-system-arm -serial file:${EPOCROOT}syborg_serial.log \ 
-M ${EPOCROOT}sf/adapt/qemu/baseport/syborg/syborg.dtb -kernel \
${EPOCROOT}epoc32/rom/syborg_tshell_ARMV5_udeb.img 

```

---

### Post by neomaniac on 2011-05-14
well..
    #!/bin/sh
    #Script to boot a qemu/syborg text-shell rom.
    #You first need to have built your rom with syborg_builder.sh, and qemu with qemu_builder.sh

export EPOCROOT=~/symbian/gcc/
export PYTHONPATH=${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/plugins
cd ${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp ./qemu-system-arm -serial
file:${EPOCROOT}syborg_serial.log \ -M ${EPOCROOT}sf/adaptation/qemu/baseport/syborg/syborg.dtb -kernel $/home/m3ssaf/epocroot-pdk-3.0.i/epoc32/rom/syborg_tshell_ARMV5_udeb.img

it was looking for the qemu-system-arm script in the bin folder so that's not the end of the line .. but when i built the qemu the script was generated but in shown path up ... & that's how the other error got fixed ..

now ... 
file:${EPOCROOT}syborg_serial.log \ -M ${EPOCROOT}sf/adaptation/qemu/baseport/syborg/syborg.dtb -kernel $/home/m3ssaf/epocroot-pdk-3.0.i/epoc32/rom/syborg_tshell_ARMV5_udeb.img
is the whole line & can't be divided cause my guess is  .. the logs that should be written into that .log file is coming from syborg_tshell_ARMV5_udeb.img & syborg.dtb which i had 'em already in the pathes i passed in the script  .. 
the only thing remaining at this point is for it to see the syborg_serial.log or even create it

---

