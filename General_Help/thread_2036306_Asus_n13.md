---
title: "Asus n13"
date: 2012-08-01
forum: General Help
---

### Post by arturoman10101 on 2012-08-01
I recently got the ASUS N13 wifi adapter and I cannot get it to run.
I have searched the forums and just cant do it.
Help me?
I have tried to use the  "install.sh" that came with the disk but it always fails.
Here is the lsusb.
```
Bus 001 Device 006: ID 0b05:17ab ASUSTek Computer, Inc.
```

---

### Post by arturoman10101 on 2012-08-01
Ubuntu 12.04 kernel 3.2.0-27-generic-pae

---

### Post by steeldriver on 2012-08-01
hi can you also post the output of

```
lshw -C network
```

please

---

### Post by arturoman10101 on 2012-08-01
> **steeldriver said:**
> hi can you also post the output of

```
lshw -C network
```please
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:19:db:7d:38:3f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5788-v3.27 latency=64 mingnt=64 multicast=yes port=twisted pair
       resources: irq:11 memory:d2010000-d201ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:8
       logical name: wlan0
       serial: c8:60:00:d4:9b:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-27-generic-pae firmware=N/A multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


-Should I run this as super-user? How would I do that if i need to?

---

### Post by steeldriver on 2012-08-01
no that's fine - I just wanted to see what driver / firmware it reported

tbh I'm not an expert on these drivers - you can search the forum for '0b05:17ab' to see what's worked for other people - or hope that one of the wireless experts shows up

if you don't get any help then bump the thread and I will try to help - I have a feeling this is one of the cases that may need you to build an updated driver

in the meantime can you post the output of

```
lsmod | grep 8192
```

also posting the error message from the failed 'install.sh' attempt might help

---

### Post by arturoman10101 on 2012-08-01
```
lsmod | grep 8192
```
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95789  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi

I navigated to the cd with terminal and found the install.sh, i tried
 ```
chmod +x install.sh
```
but it didn't work. the file was 'write only'

Then i copied all the files from the cd.
Navigated to the correct folder and did```
 chmod +x install.sh
``` then ```
./install.sh
```
i got this
```
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include: Cannot mkdir: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder: Cannot mkdir: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep: Cannot mkdir: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux: Cannot mkdir: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa: Cannot open: No such file or directory
rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp
tar: rtl8192_8188CU_linux_v3.0.2164.20110715: Cannot mkdir: Permission denied
tar: rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp: Cannot open: No such file or directory
tar: Exiting with failure status due to previous errors
USB-N13 Linux Driver Quick Start.txt
./install.sh: line 12: cd: USB-N13: No such file or directory
Authentication requested [root] for make driver:
Password: 
su: Authentication failure
Compile make driver error: 1, Please check error Mesg

```
:(

---

### Post by ahallubuntu on 2012-08-01
Use "sudo ./install.sh"

---

### Post by arturoman10101 on 2012-08-02
with 
sudo ./install.sh 
i get
```
        Auto install for 8192cu
        September, 1 2010 v 1.0.0
rtl8192_8188CU_linux_v3.0.2164.20110715/
rtl8192_8188CU_linux_v3.0.2164.20110715/autoconf_rtl8192c_usb_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/clean
rtl8192_8188CU_linux_v3.0.2164.20110715/core/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/
rtl8192_8188CU_linux_v3.0.2164.20110715/core/efuse/rtw_efuse.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_debug.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_eeprom.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ieee80211.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_io.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_query.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_rtl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_ioctl_set.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mlme_ext.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_mp_ioctl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_p2p.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_pwrctrl.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_rf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_security.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_sta_mgt.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_wlan_util.c
rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_cmd.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_dm.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/rtl8192c_sreset.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_halinit.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192_8188CU_linux_v3.0.2164.20110715/ifcfg-wlan0
rtl8192_8188CU_linux_v3.0.2164.20110715/include/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/autoconf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/basic_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/big_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/generic.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/little_endian.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swab.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/byteorder/swabb.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/circ_buf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/cmd_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_conf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ethernet.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/farray.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/h2clbk.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192CUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DEHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DETestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyCfg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DPhyReg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/Hal8192DUTestHWImg.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/hal_init.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ieee80211_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/if_ether.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/ip.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mlme_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/mp_custom_oid.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/nic_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_ce_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_intf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/pci_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/recv_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_sreset.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192c_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_dm.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_spec.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtl8192d_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_byteorder.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_cmd.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_debug.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_eeprom.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_efuse.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_event.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ht.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_io.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_query.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_rtl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_ioctl_set.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_led.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mlme_ext.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_ioctl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_mp_phy_regdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_p2p.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_pwrctrl.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_qos.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_rf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_security.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_version.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_xmit.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_ce.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_linux.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_ops_xp.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sdio_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/sta_info.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_hal.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_ops.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_osintf.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/usb_vendor_req.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wifi.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/wlan_bssdef.h
rtl8192_8188CU_linux_v3.0.2164.20110715/include/xmit_osdep.h
rtl8192_8188CU_linux_v3.0.2164.20110715/Kconfig
rtl8192_8188CU_linux_v3.0.2164.20110715/Makefile
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/ioctl_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/mlme_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/os_intfs.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/pci_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/recv_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/sdio_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/usb_intf.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/linux/xmit_linux.c
rtl8192_8188CU_linux_v3.0.2164.20110715/os_dep/osdep_service.c
rtl8192_8188CU_linux_v3.0.2164.20110715/runwpa
rtl8192_8188CU_linux_v3.0.2164.20110715/wlan0dhcp
rtl8192_8188CU_linux_v3.0.2164.20110715
USB-N13 Linux Driver Quick Start.txt
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-27-generic-pae/build M=/home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-27-generic-pae'
  CC [M]  /home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:0:
/home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/arturo/ASUS/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-27-generic-pae'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg

```

---

### Post by arturoman10101 on 2012-08-02
Would something like ndiswrapper work for this?:confused:

---

### Post by steeldriver on 2012-08-02
well fwiw I just downloaded a (presumably) newer version of the driver tarball

```
RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622
```[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

and it appeared to build / install OK on my 12.04 VM  - I didn't have a 8192 kernel module at all before, after I get

```
$ lsmod | grep 8192
8192cu         502394   0
```(note this is different from the default **rtl**8192cu)

Hope this helps

---

### Post by arturoman10101 on 2012-08-03
I ended up fixing it.
Just had to get a better connection.
I now feel like a  ](*,) #-o

---

### Post by arturoman10101 on 2012-08-03
It will only connect if i am very close to the wifi source.
It has full bars on the connection i am trying to connect to but it wont connect.
Am i doing something wrong?

---

### Post by Umkus on 2012-11-16
> **arturoman10101 said:**
> It will only connect if i am very close to the wifi source.
It has full bars on the connection i am trying to connect to but it wont connect.
Am i doing something wrong?

Same here! As soon as i drag my box&monitor all the way to another room, and put it next to the router, it works. Otherwise it ends up receiving the IP with dhcp, but fails even to ping router itself afterwards (destination host not reachable).

---

### Post by wbrb on 2013-01-22
> **steeldriver said:**
> well fwiw I just downloaded a (presumably) newer version of the driver tarball

```
RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622
```[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

and it appeared to build / install OK on my 12.04 VM  - I didn't have a 8192 kernel module at all before, after I get

```
$ lsmod | grep 8192
8192cu         502394   0
```(note this is different from the default **rtl**8192cu)

Hope this helps

Thank you for this post! My ASUS USB-N13 B1 (0b05:17ab) wouldn't work on 12.04. This is the post that finally fixed it for me. I was doing everything right except for failing to realize that there was room to scroll down on the Realtek website and select all the variants of this driver they've released.

It's amazing how well it worked when a newer (correct) version of the drivers is used. In my case the RTL8192CU.

I just grabbed the build-essential package and my linux-headers package, unzipped the drivers and then ran ```
sudo chmod u+x ./install.sh
sudo ./install.sh

```and the only error it threw was that the driver could not be installed because something was in use. So I disabled networking, ran ```
sudo modprobe -r rtl8192cu
``` and ran the ```
sudo ./install.sh
``` a second time. It succeeded so I started up networking again my desktop has wireless again for the first time in years. :KS

---

