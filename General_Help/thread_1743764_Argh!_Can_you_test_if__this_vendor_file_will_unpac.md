---
title: "Argh! Can you test if  this vendor file will unpack?"
date: 2011-04-29
forum: General Help
---

### Post by SilentSeven on 2011-04-29
Trying to get a STA driver from RAlink to unpack.  File has a .bz2 extension.

For some reason, I can't get the file to unpack.  Need an expert to confirm it's a problem with the file and not a problem with me (more likely)

Request:

[LIST]
[*]Can you try to unpack the file?
[*]If you can, what &%^T$ command are you using?
[/LIST]

File URL: 


[LIST]
[*][http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
[*]On that page, get file marked RT3572USB - they make ack this annoying license agreement but you can put in anything as it's not verified.
[/LIST]

Sorry to ask but I'm out of tricks.  Really need this file to setup my wireless on 11.04.

thx

---

### Post by howefield on 2011-04-29
Nothing wrong with the file.

No command needed, opens up in archive manager.

---

### Post by r-senior on 2011-04-29
Looks ok to me. You could use the GUI archive tool. If you want the command line, it's a bzip compressed tar archive, so:

```
tar -xjf <filename>
```

or, in two steps 

```
bunzip2 <filename>
tar -xf <tar_filename>
```

Either way will unpack the directory into your working directory.

---

### Post by cbowman57 on 2011-04-29
IIRC it extracts to a DPO file, which you need to extract again to create the directory.

I've had experience using that driver, give a holler if you need some help installing it.

---

### Post by jerome1232 on 2011-04-29
I'm using a default install of 11.04

Double Click, click extract.

the resulting file is actually a tar file you can also double click and then click extract.

Maybe your download is corrupt?

---

### Post by SilentSeven on 2011-04-30
Uh...right.  Thanks everyone.  My linux skills are pretty dull - I looked for the archive manager in the program list for like 10 minutes until I thought to right click on the file - presto!

For some reason, I couldn't get tar and bunzip2 to work.  Bunzip2 was telling me it wasn't valid file.  Oh well, archive manager worked great.

cbowman - there are conflicting instructions on how to enable the Linksys WUSB600N - any preference on which ones you like?  Still haven't archived success on that.  (11.04)

---

### Post by cbowman57 on 2011-04-30
> **SilentSeven said:**
> cbowman - there are conflicting instructions on how to enable the Linksys WUSB600N - any preference on which ones you like?  Still haven't archived success on that.  (11.04)

I'm attaching a text file that should walk you through it, hopefully without problems.

---

### Post by howefield on 2011-04-30
> **SilentSeven said:**
> I looked for the archive manager in the program list for like 10 minutes until I thought to right click on the file - presto!

Right clicking works fine, as should double clicking the file.

Just for info, you can add the menu entry for Archive Manager by going to System > Administration > Main Menu > click on Accessories in the left pane, and check Archive Manager in the right pane.

---

### Post by SilentSeven on 2011-04-30
Howefield - thanks for the simple menu mod!

Cbowman - thanks so much for the assist offer but no love on the procedure.  I may have omitted a key detail - my Linksys unit is a V2.  Here's a string of output to help debug.

Also, note in your instructions that I think you have a filename backwards - /include/os/linux_rt.h is actually rt_linux.h I think.

lsusb output
```

lsusb | grep 1737:0079
Bus 001 Device 005: ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2

```iwconfig output post procedure
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```Network manager shot post procedure - firmware not found error

[IMG]http://home.comcast.net/%7Ejsnord/pics/network.png[/IMG]

make output

```
make -C tools
make[1]: Entering directory `/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/action.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/dfs.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sync.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/connect.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/ags.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.o
In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess.h:571:0,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:211,
                 from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/include/os/rt_linux.h:51,
                 from /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/include/rtmp_os.h:53,
                 from /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/include/rtmp_comm.h:59,
                 from /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/include/rt_config.h:45,
                 from /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.c:40:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.c:1720:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.c:2209:28:
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52:2: warning: passing argument 4 of ‘usb_alloc_coherent’ from incompatible pointer type
include/linux/usb.h:1374:7: note: expected ‘dma_addr_t *’ but argument is of type ‘long long int *’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:235:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:242:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:280:11: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:509:12: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:568:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:598:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:612:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:630:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_io.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_data.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.o
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c: In function ‘RT30xx_ChipSwitchChannel’:
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:614:17: warning: unused variable ‘BbpR109’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:613:30: warning: unused variable ‘Tx1FinePowerCtrl’
/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:613:8: warning: unused variable ‘Tx0FinePowerCtrl’
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt28xx.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt35xx.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.mod.o
  LD [M]  /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'


```make install output

```
jeff@home-01-ubuntu:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO$ sudo make install
make -C /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-8-generic
make[1]: Leaving directory `/home/jeff/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'


```

---

### Post by cbowman57 on 2011-04-30
> **SilentSeven said:**
> Howefield - thanks for the simple menu mod!

Cbowman - thanks so much for the assist offer but no love on the procedure.  I may have omitted a key detail - my Linksys unit is a V2.  Here's a string of output to help debug.

Also, note in your instructions that I think you have a filename backwards - /include/os/linux_rt.h is actually rt_linux.h I think.



I accumulated that from a couple sources, and yes, there is a typo, never fixed it because it's obvious when you search the file.

Ok, the good news first, the driver did properly build & install from what I can see so that part is done.  Now you just need to find & install the particular firmware that it's lacking.

When it builds the driver warnings are fine, it's error messages that are the killer.

Good luck.

---

### Post by SilentSeven on 2011-04-30
OK.  I have the firmware from the ralinktech.com site - now i just need to search for the procedure to install.  Strangely that's not mentioned any other procedure.

Question:  Can you confirm that this driver works for the V2 hardware.  My understanding is that the V2 has a different chip (3572 vs. 2870).  The edits in the rtusb_dev_id.c file are in the 2870 section, not the 3572 section.  Don't know if this is important or not.

Really appreciate the personal assist!

---

### Post by cbowman57 on 2011-04-30
I've never used that particular device so I can't confirm it but I'm reaonably certain that it will.  I think you can pretty much ignore the references to 2870 vs 3572.  The guts of the 3572 driver seems to be 2870 code.  Wish I could help with the firmware problem but I used the Cisco AE1000 and it worked without a problem with just the driver installation.

---

### Post by cbowman57 on 2011-04-30
From what I can gather so far it looks like installing the firmware is simply a matter of extracting the .bin file & placing it in /lib/firmware 

Not positive though, let me know what you come up with.

---

### Post by SilentSeven on 2011-04-30
Just got it working (as proved by this post).  THANK YOU for your help. 

For a v2 card, you need modify your instructions as follows.  NO need to install any firmware.

When editing rtusb_dev_id.c, 
[LIST=1]
[*]_do not _update the RT2780 section.
[*]Do update the RT35xx section with the following
[/LIST]
```

{USB_DEVICE (0x1737,0x0079)}, /* WUSB600n */

```Blacklist all the rt28xxx modules in /etc/modprobe.d/blacklist.conf

```

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800pci
blacklist rt2x00pci

```

---

### Post by cbowman57 on 2011-04-30
Cool, now assemble those instructions & put them in a text file in case you need it for future reference.  There will likely be someone asking how to get theirs running in the forum soon. :)

---

