---
title: "Problem! Wifi Card! (usb)"
date: 2011-07-26
forum: General Help
---

### Post by JzJad on 2011-07-26
I have a Realtek Wifi Card (usb Plug-In) and since the Disk is for windows, iv looked and found tutz but there all old or just stupidly complicated xD so if there is a way to use the installation files from the disk and use them with like wine" or something or if there is a source for the software that i havnt found? Thx!!! :o



also if any one knows of a really good IRC server for ubuntu it would be well appreciated if you could tell me, iv tried Unreal but it wont install right for some reason xD so any thing else would be appreciated :popcorn:atm trying Ubuntu's Irc :)


**Software/USB info**
REALTEK 11n Wireless LAN Utility---- ty

---

### Post by wildmanne39 on 2011-07-27
Hi, run these commands in a terminal please
```
lsusb
```
```
sudo lshw -C network
```
```
iwconfig
```
```
lsmod
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by JzJad on 2011-07-27
```

Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:2504 Hewlett-Packard DeskJet F4200 series
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
frostbyte@frostbyte-EN996AA-ABA-s7310n:~$ sudo lshw -C network
[sudo] password for frostbyte: 
  *-network                     
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:17:31:05:7f:c0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.10 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:cfffe000-cfffefff ioport:e400(size=64)
frostbyte@frostbyte-EN996AA-ABA-s7310n:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



```  :popcorn:

---

### Post by wildmanne39 on 2011-07-27
Hi, here is link to install your driver
[http://ubuntuforums.org/showthread.php?p=11086418#post11086418](http://ubuntuforums.org/showthread.php?p=11086418#post11086418)
You do not need to worry about removing ndiswrapper unless you installed it.
Thank you

---

### Post by JzJad on 2011-07-29
Thanks alot! :) I'll try it as soon as I get home

---

### Post by wildmanne39 on 2011-07-29
Hi, your welcome! keep us updated with your progress.

---

### Post by JzJad on 2011-07-29
unfortunately the read me makes no sense so i cant get it to install :(

if u can help like even if u need to VNC that would be fine xD
-----------------------------------------------------------------

i run auto install (bash install.sh)
 and get at the end i need a password my admin password dont work so wth?
> Auto install for 8192cu
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
autoconf_rtl8192c_usb_linux.h
clean
core
hal
ifcfg-wlan0
include
Kconfig
Makefile
os_dep
rtl8192_8188CU_linux_v3.0.2164.20110715
runwpa
wlan0dhcp
install.sh: line 12: cd: autoconf_rtl8192c_usb_linux.h: Not a directory
Authentication requested [root] for make driver:
Password: 
su: Authentication failure
Compile make driver error: 1, Please check error Mesg



Ohhh i Forgot to Sudo xD

---

### Post by wildmanne39 on 2011-07-30
Hi, yes you need to change in to the directory you extracted the file to the run.
```
sudo su
    make
    make install
```
You also must have linux-headers and build essentials installed.

---

