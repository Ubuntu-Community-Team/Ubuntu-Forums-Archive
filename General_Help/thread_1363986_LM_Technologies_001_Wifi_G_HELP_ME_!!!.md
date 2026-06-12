---
title: "LM Technologies 001 Wifi G HELP ME !!!"
date: 2009-12-25
forum: General Help
---

### Post by jman6495 on 2009-12-25
so ...
i really need wifi access , i got a LM TECHNOLOGIES USB WIFI G  (001)
for Christmas and it is not working!
this is the output of lsmod

isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
arc4                    1660  2 
ecb                     2524  2 
dm_crypt               12928  0 
```
zd1211rw               45408  0 
i think it's this but i'm not sure!
```
joydev                 10272  0 
pcmcia                 36808  0 
iptable_filter          3100  0 
mac80211              181076  1 zd1211rw
ip_tables              11692  1 iptable_filter
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
x_tables               16544  1 ip_tables
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
cfg80211               93052  2 zd1211rw,mac80211
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  1 sdhci
psmouse                56500  0 
serio_raw               5280  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  3 ttm,drm,intel_agp
ramzswap                8880  1 
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap

it doesn't show up in network manager ,
i am on ubuntu 9.10

i tried modprobe zd1211rw

it also comes with a driver in source code ,
i tried to compile it but there is an error ...

```
longhorn@jordan-laptop:~/Desktop/ZD1211LnxDrv_2_16_0_0$ sudo make
make both
make[1]: Entering directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
make clean
make[2]: Entering directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
/lib/modules/2.6.31-16-generic/build
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0
-I/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.h:49,
                 from /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:42:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zdcompat.h:69: error: conflicting types for ‘irqreturn_t’
include/linux/irqreturn.h:16: note: previous declaration of ‘irqreturn_t’ was here
In file included from /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.h:49,
                 from /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:42:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zdcompat.h:72:1: warning: "IRQ_RETVAL" redefined
In file included from include/linux/interrupt.h:10,
                 from include/linux/netdevice.h:1058,
                 from include/net/sock.h:50,
                 from include/linux/tcp.h:177,
                 from /home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:36:
include/linux/irqreturn.h:17:1: warning: this is the location of the previous definition
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: warning: initialization from incompatible pointer type
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‘...’ before ‘write’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‘...’ before ‘fd’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‘...’ before ‘buf’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‘...’ before ‘count’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: ‘dot11A_Channel’ undeclared here (not in a function)
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd_writel’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:791: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd_readl’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:831: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_enable_int’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:880: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_mgt_mon_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1282: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘HKeepingCB’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1574: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_rx_isr’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4218: error: ‘struct sk_buff’ has no member named ‘mac’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_open’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4414: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_get_stats’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4755: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_set_mac’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4799: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_close’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4893: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_xmit_frame’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5004: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5025: warning: ISO C90 forbids mixed declarations and code
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5026: warning: assignment from incompatible pointer type
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5029: warning: assignment from incompatible pointer type
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_set_multi’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5662: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_watchdog_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5847: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setiwencode’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6165: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_getiwencode’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6290: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setessid’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6334: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_getessid’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6374: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setfreq’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6409: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setrts’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6476: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setfrag’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6500: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_getfrag’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6541: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_getrate’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6564: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setpower’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6685: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_getpower’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6729: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl_setmode’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6759: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205wext_giwfreq’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6858: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205wext_giwmode’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6874: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205wext_giwrts’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6915: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205wext_siwscan’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7033: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_translate_scan’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7162: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7162: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7162: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘unsigned int’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7162: error: too few arguments to function ‘iwe_stream_add_event’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7172: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7172: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7172: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘U8 *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7172: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7183: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7183: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7183: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘unsigned int’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7183: error: too few arguments to function ‘iwe_stream_add_event’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7195: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7195: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7195: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘unsigned int’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7195: error: too few arguments to function ‘iwe_stream_add_event’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7224: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7224: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7224: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7224: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7242: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7242: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7242: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7242: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7255: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7255: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7255: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘U8 *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7255: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7272: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
include/net/iw_handler.h:569: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7272: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
include/net/iw_handler.h:569: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7272: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
include/net/iw_handler.h:569: note: expected ‘struct iw_event *’ but argument is of type ‘unsigned int’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7272: error: too few arguments to function ‘iwe_stream_add_value’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7280: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
include/net/iw_handler.h:569: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7280: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
include/net/iw_handler.h:569: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7280: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
include/net/iw_handler.h:569: note: expected ‘struct iw_event *’ but argument is of type ‘unsigned int’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7280: error: too few arguments to function ‘iwe_stream_add_value’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7296: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7296: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7296: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7296: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7314: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7314: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7314: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7314: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7327: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7327: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7327: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7327: error: too few arguments to function ‘iwe_stream_add_point’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205wext_giwscan’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7341: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_ioctl’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7568: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_init’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8476: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8708: error: implicit declaration of function ‘open’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8725: error: implicit declaration of function ‘read’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8729: error: implicit declaration of function ‘close’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8881: error: implicit declaration of function ‘write’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_setup_next_send’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9155: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_rx_ind’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9794: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9913: error: implicit declaration of function ‘eth_copy_and_sum’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_status_notify’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9949: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘chal_tout_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10050: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘scan_tout_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10060: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘asoc_tout_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10070: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘auth_tout_cb’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10080: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_start_timer’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10089: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_stop_timer’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10142: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_dis_intr’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10168: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_set_intr_mask’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10182: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_check_tcb_avail’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10209: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_delay_us’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10227: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_AcquireDoNotSleep’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10271: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zdcb_ReleaseDoNotSleep’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10277: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_set_zd_cbs’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10344: warning: assignment from incompatible pointer type
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘ChangeMacMode’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10886: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10887: error: ‘struct net_device’ has no member named ‘priv’
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‘zd1205_iw_getstats’:
/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10910: error: ‘struct net_device’ has no member named ‘priv’
make[4]: *** [/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/longhorn/Desktop/ZD1211LnxDrv_2_16_0_0'
make: *** [all] Error 2

```

i don't get it but i REALLY Need help!

PLEASE help
cause i REALLY don't want to have to use WINDOWS!!!


jman6495

---

### Post by jman6495 on 2009-12-26
fixed

---

### Post by jmlynn on 2009-12-26
Hi,
 
I had successfully installed Ubunto 9.10 on my Toshiba notebook, with the capability of display main desktop on the internal LCD and extended desktop on a second LCD monitor.

However, after I run System/Administration/Hardware Drivers and tried to install the "recommended" Nvidia accelerated graphics drivers (version 185), it failed during install, giving me the following error:
"System error: installArchives() failed"

When I reboot the machine and click System/preferences/display, I now get the following error:
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

If I select yes, I got the NVIDIA configure screen that I have no clues as to how to configure it.  

If I cleck No, I will get a low resolution display driver.   I am also unable to extend the desktop to the external screen.  

Any idea on how to restore to the Ubuntu distribution display driver without having to rinstall Unbunto? 

Appreciate any help!

Jeff

---

