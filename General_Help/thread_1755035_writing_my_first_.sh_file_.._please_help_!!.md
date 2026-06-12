---
title: "writing my first *.sh file .. please help !!"
date: 2011-05-10
forum: General Help
---

### Post by neomaniac on 2011-05-10
i'm writing my first bash script .. , 
here's the script 

    #!/bin/sh
    #Script to build symbian QEMU
    #Pass `conf` if you need to ./configure first. Pass `clean` to clean. 

export EPOCROOT=~/symbian/gcc/ 
export SBS_HOME=${EPOCROOT}/home/m3ssaf/epocroot-pdk-3.0.i/oss+FCL+interim+sftools+linux_build.hg/sbsv2/raptor 
export SBS_GCCE441BIN=~/home/m3ssaf/symbian/gcc/epoc32/gcc/bin 
export PYTHONPATH=${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12/qemu-symbian-svp/plugins #cd ${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12/qemu-symbian-svp 

if [ "$1" == "conf" ]
then chmod +x configure ./configure --target-list=arm-softmmu --prefix=${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12 
fi
 
if [ "$1" == "clean" ]
then make clean else make && make install 
fi 

when i type $./qemu_builder.sh conf 
i get this error chmod: unrecognized option '--target-list' .. 
any ideas  ????????

---

### Post by TeoBigusGeekus on 2011-05-10
In both your "if" statements, you need to press enter to separate the commands that come after "then", rather than putting them all in the same line.

---

### Post by WorMzy on 2011-05-10
You're chaining together commands without closing the previous command. Put each command on a new line, or use a semi-colon to signify the end of one command before moving onto the next.

For example,

```
then chmod +x configure ./configure --target-list=arm-softmmu --prefix=${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12

```

should be

```
then chmod +x configure**;** ./configure --target-list=arm-softmmu --prefix=${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12

```

with a semi-colon after the "configure", or


```
then chmod +x configure
./configure --target-list=arm-softmmu --prefix=${EPOCROOT}/home/m3ssaf/symbian/gcc/sf/adapt/oss+FCL+sf+adapt+qemu.hg/hg/store/data/symbian-qemu-0.9.1-12

```

with a line-break after the "configure".

---

### Post by neomaniac on 2011-05-10
thanks guys  .. 
i think it's working now

---

