---
title: "please tell me what I'm doing wrong here"
date: 2009-11-04
forum: General Help
---

### Post by bradw on 2009-11-04
Ok, I tried to run make and make install to setup a wireless card with a ralink 2860 chipset. Im using the very latest file from ralink released a week ago or so.

Here is the output of make and make install and then a copy of my /etc/network/interfaces file. Also included iwconfig output. Now here is the really weird thing. If I boot my server (9.10) into the gnome gui wireless works fine. When I drop into a cli with the gui running everything is fine. However, if I drop to a cli and never log into the gui, wireless does not work. Can someone help me before I shoot my cat:)

make and make install output using sudo

bw@ubuntuserver:~$ cd /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0
bw@ubuntuserver:~/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0$ ./configure
bash: ./configure: No such file or directory
bw@ubuntuserver:~/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0$ sudo ./configure
[sudo] password for bw: 
sudo: ./configure: command not found
bw@ubuntuserver:~/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0$ make
make -C tools
make[1]: Entering directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools'
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-server/build SUBDIRS=/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-server'
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_aes.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_aes.c:1450: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_aes.c:1539: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.c:810: warning: cast from pointer to integer of different size
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/mlme.c:4562: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/action.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/spectrum.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/spectrum.c:1910: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_asic.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_asic.c: In function ‘AsicBBPAdjust’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_asic.c:701: warning: the frame size of 1872 bytes is larger than 1024 bytes
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c:1503: warning: the frame size of 1424 bytes is larger than 1024 bytes
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c:679: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c:958: warning: the frame size of 1392 bytes is larger than 1024 bytes
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sync.c:548: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/rtmp_data.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/rtmp_data.c:689: warning: unused variable ‘pRxD’
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/connect.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/connect.c: In function ‘InitChannelRelatedValue’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/connect.c:2840: warning: the frame size of 1056 bytes is larger than 1024 bytes
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/connect.c:310: warning: the frame size of 1632 bytes is larger than 1024 bytes
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.o
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:547: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-server/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:549: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-14-server/arch/x86/include/asm/string_64.h:58: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:673: warning: assignment makes integer from pointer without a cast
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:693: warning: assignment makes integer from pointer without a cast
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:935: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1689: error: ‘struct net_device’ has no member named ‘open’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1690: error: ‘struct net_device’ has no member named ‘stop’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1691: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1692: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1702: error: ‘struct net_device’ has no member named ‘get_stats’
/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.c:1736: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-server'
make: *** [LINUX] Error 2
bw@ubuntuserver:~/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0$ sudo make install
make -C /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.31-14-server/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.31-14-server/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
make: *** [install] Error 2
bw@ubuntuserver:~/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0$ 

Interfaces file output

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo
#iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
auto eth0
iface lo inet loopback
iface eth0 inet dhcp

# The wireless network interface
auto ra0
iface ra0 inet dhcp


iwconfig ouput

bw@ubuntuserver:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"LA County Sheriff"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:21:63:6A:70:DE   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-48 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bw@ubuntuserver:~$

---

### Post by bradw on 2009-11-04
OK now I shut server down for about an hour and no wireless period anymore. 
sudo /etc/init.d/networking restart does nothing. no dhcp offer received

---

### Post by vsperez on 2009-11-04
Hi.
You have a error when you install the module:

install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
make: *** [install] Error 2

Take a look at

[http://jomcode.com/fadhil/?p=59](http://jomcode.com/fadhil/?p=59)

or

[http://darkantos.wordpress.com/2009/02/07/driver-oficial-de-broadcom/](http://darkantos.wordpress.com/2009/02/07/driver-oficial-de-broadcom/)

In that page I found how to install my wireless card. 

Hope it helps

---

### Post by bradw on 2009-11-04
[QUOTE=vsperez;8245169]Hi.
You have a error when you install the module:

install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/bw/temp/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
make: *** [install] Error 2

Thanks for trying to help but one page you listed is not in english and the other is of no use to me. I dont know why I'm getting the errors and that is why I am asking for help. I'm really new to linux and would really like to get my wireless card working on my server. I could buy another card but I wont learn a thing if I do it that way. I want to learn and perhaps along the way get my wireless working. It is a ralink 2860 chipset and it cant be that hard for a seasoned linux person but for me I have tried everything I can find online and in the few ubuntu books I have and I have reached the bottom of my experience so I am asking for help. Inviting all guru's to help me if you get a moment.

---

### Post by bundle on 2009-11-05
Bradw, the problem is that this latest rt2860 driver from Ralink doesn't compile in kernel 2.6.31-14 (I think in no older kernels than 2.6.29, but I might be wrong). 

I don't know a lot about commands and can't do a lot of "experiments". Surely, there is a way to make the rt2860 to work properly (in my case, being able to see and connect to my wpa wifi network) in the Karmic version, but I don't know how to do it. I have been trying to find a solution or a workaround ever since I installed the 9.10 alpha 6, without success. Let's hope Ralink releases a new driver soon or someone produces a new rt2860 driver that really works ;-)

---

### Post by bundle on 2009-11-05
Hi, relating my post of this morning and if it is of any help, I have installed the rt3090 drivers (yes, its internal symbol RT2860STA) from this package: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.2.0.1-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.2.0.1-0ubuntu0~ppa1_all.deb),
as mentioned in [http://ubuntuforums.org/archive/index.php/t-1274886.html](http://ubuntuforums.org/archive/index.php/t-1274886.html).

After installing, I restarted the computer and after a few seconds I was connected to my WPA wifi network, without having to bother with any other tweak. So far, it's been working for a couple of hours, fast, stable and 100% signal strength. My netbook is an Asus Eeepc 1000HE with rt2860 chipset.

Hope this helps :-)

---

