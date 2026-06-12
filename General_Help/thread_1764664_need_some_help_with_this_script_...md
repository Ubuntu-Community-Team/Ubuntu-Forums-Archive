---
title: "need some help with this script .."
date: 2011-05-22
forum: General Help
---

### Post by neomaniac on 2011-05-22
hi  .. 
i want to boot symbian image rom on qemu  .. on ubuntu 11.4 
i modified this script to do so  : rom_boot.sh 

    #!/bin/sh
    #Script to boot a qemu/syborg text-shell rom.
    #You first need to have built your rom with syborg_builder.sh, and qemu with qemu_builder.sh 

export EPOCROOT=~/symbian/gcc/ export PYTHONPATH=${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/plugins 
cd ${EPOCROOT}sf/adaptation/qemu/symbian-qemu-0.9.1-12/qemu-symbian-svp/arm-softmmu ./qemu-system-arm -serial file:${EPOCROOT}syborg_serial.LOG \ -M ${EPOCROOT}sf/adaptation/qemu/baseport/syborg/syborg.dtb -kernel ${EPOCROOT}epoc32/rom/syborg_tshell_ARMV5_udeb.img
----------- 
but when i try to use it  .. nothing happens   ,, even the log file syborg_serial.log is still empty  ..  
any help ???????????????

---

