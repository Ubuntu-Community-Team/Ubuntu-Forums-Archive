---
title: "How to enable a USB wireless NIC in Lubuntu?"
date: 2010-11-10
forum: General Help
---

### Post by mr_luksom on 2010-11-10
I've just bought a usb wireless NIC with the intent of using the 802.11n capability, rather than the built-in 802.11g.

I've plugged it in, and realised I have absolutely no idea what to do next!

Any pointers would be much appreciated.

lsusb output
```
 glen@glen-kat:~$ lsusb
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:1010 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And the lsusb verbose for the wireless NIC (Realtek 8176?)
```
 Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8176 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

It isn't picked up as a network interface by iwconfig, eth1 is the on-board wireless card (not the USB I'm trying to configure).

```
 lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"Kaoticus II"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 94:44:52:4E:06:12   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-37 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:0   Missed beacon:4

irda0     no wireless extensions.

```

---

### Post by cavalier911 on 2010-11-10
From [www.pcidatabase.com](www.pcidatabase.com) :
```
Device ID:	0x8176
Chip Number:	REV_01
Chip Description:	Realtek RTL8188CE Wlan 802.11n
```

Go here: [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)  **thread #6**

---

### Post by mr_luksom on 2010-11-11
Thanks, that was perfect.

---

### Post by felipemendes on 2011-10-02
Just to make things easier for some people (me, for example!):

ID 0bda:8176 Realtek Semiconductor Corp.

may also mean that the correct chipset is **RTL8188CUS** (this was my case, and all other solutions I've found did not work).

This driver has an automated install script that didn't work for me. The downlodaded driver has another compressed file instead. So, if this is someone's right driver, one should extract the compressed file from within downloaded file.
Other steps are almost the same:

1.navigate to directory
2.sudo su
3.make
4.make install
5.reboot

---

### Post by Bikerbob on 2012-01-24
I cannot get the make to work.. I get the same error at the end.. I was having issues with kernel headers, but update manager loaded them in.

What do I need to do here to get this to work?? anyone?

James

root@dockside-Latitude-C800:/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.38-13-generic/build M=/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-13-generic'
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_cmd.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_security.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_debug.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_io.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_ioctl_query.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_ioctl_set.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/ieee80211.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_mlme.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_mlme_ext.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_wlan_util.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_pwrctrl.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_rf.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_recv.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_sta_mgt.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/rtw_xmit.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/efuse/rtl8712_efuse.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/core/led/rtl8192c_led.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/hal_init.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c_d_hal_init.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/hal/rtl8192c/usb/rtl8192c_cmd.o
  CC [M]  /home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/os_dep/osdep_service.o
/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/os_dep/osdep_service.c: In function ‘_rwlock_init’:
/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/os_dep/osdep_service.c:291:2: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/dockside/Documents/driver/rtl8192CU_linux_v2.0.974.20100803] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-13-generic'
make: *** [modules] Error 2

---

### Post by woody1 on 2012-08-02
Brilliant, thanks to cavalier911 and felipemendes, I had almost given up on this, but it is now working

---

