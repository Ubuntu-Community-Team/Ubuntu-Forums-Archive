---
title: "install driverethenet ?? acer 4745"
date: 2011-10-01
forum: General Help
---

### Post by ngubk on 2011-10-01
I install driver ethernet but unsuccessfully .:(



giang@giang-laptop:~/Desktop$ cd Ethernetdriver/AR81Family-linux-v1.0.1.13
  giang@giang-laptop:~/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13$ cd src
  giang@giang-laptop:~/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src$ makemake -C /lib/modules/2.6.32-34-generic/build SUBDIRS=/home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src modules
  make[1]: Entering directory `/usr/src/linux-headers-2.6.32-34-generic'
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/at_common_main.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e_main.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1c_main.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1c_hw.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e_hw.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e_param.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1c_param.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e_ethtool.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1c_ethtool.o
    CC [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/kcompat.o
    LD [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e.o
    Building modules, stage 2.
    MODPOST 1 modules
    CC      /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e.mod.o
    LD [M]  /home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src/atl1e.ko
  make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic'
  giang@giang-laptop:~/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src$ sudo make install
  make -C /lib/modules/2.6.32-34-generic/build SUBDIRS=/home/giang/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src modules
  make[1]: Entering directory `/usr/src/linux-headers-2.6.32-34-generic'
    Building modules, stage 2.
    MODPOST 1 modules
  make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic'
  gzip -c ../atl1e.7 > atl1e.7.gz
  # remove all old versions of the driver
  find /lib/modules/2.6.32-34-generic -name atl1e.ko -exec rm -f {} \; || true
  find /lib/modules/2.6.32-34-generic -name atl1e.ko.gz -exec rm -f {} \; || true
  install -D -m 644 atl1e.ko /lib/modules/2.6.32-34-generic/kernel/drivers/net/atl1e/atl1e.ko
  /sbin/depmod -a || true
  install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
  man -c -P'cat > /dev/null' atl1e || true
  atl1e.
  giang@giang-laptop:~/Desktop/Ethernetdriver/AR81Family-linux-v1.0.1.13/src$ t

---

