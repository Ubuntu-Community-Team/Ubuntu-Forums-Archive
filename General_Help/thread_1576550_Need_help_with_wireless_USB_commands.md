---
title: "Need help with wireless USB commands???"
date: 2010-09-17
forum: General Help
---

### Post by dougalkerr on 2010-09-17
Hi folks

I have purchased a cheap and cheerful wireless USB device to use instead of hardwire to the router.
It is a Realtek or Ralink if you like model 2070.
I believe I have installed the software properly and it looks like I should be able to open a GUI to set the wireless up but, for the life of me I can't find the file that will open the GUI.
It seems to have been built using QT if I understand things correctly.
I no nothing about QT which probably doesn't help.

Any way in the Readme there is a whole host of information and examples to apply in Terminal by the looks of it. One example is as follows;

Config STA to Link with Ad-hoc and OPEN/NONE (Authentication/Encryption)
     1. iwconfig rausb0 mode ad-hoc
     2. iwconfig rausb0 key off
     3. iwconfig rausb0 essid "AP's SSID"

Now I think I realize the last line is setting the name of the wireless signal so no problem there but,  before I even get to that I can't get past 1. When I enter the code I get the message: 
Error for wireless request "Set Mode" (8B06)
     Set failed in device rausb0 ; No such device

So, I did lsusb and here is the line for the device;
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.

It seems the system sees the device but, I don't undestand how to get it working.
Please help guide me through things - anyone.

Thanks.

---

### Post by mikewhatever on 2010-09-17
Have you tried the built in Network Manager fo GUI? To get the device name, run **ifconfig -a**, which should show all available network devices. That said, you don't want to just copy/paste any command from the above list. The first one, for example, puts the device into adhoc mode - likely not what you want.

---

### Post by AlphaLexman on 2010-09-17
Is there an executable file that came with the hardware that starts the gui?
```
whereis rausb0
```
or,
```
whereis ralink
```
or look in: [ /usr/share/bin/ ] or [ /usr/local/bin/ ] for executables or related directories.

---

### Post by dougalkerr on 2010-09-17
mikewhatever - thanks for replying. I have ran the ifconfig -a but, the USB wireless device is not mentioned. I have been through the Network manager and set all settings for wireless that I can think of but, nothing activates it. That's wrong actually - the other day I did have it 'apparently' respond wirelessly when I had Auto eth0 set as the SSID instead of Tiscali but, of course it didn't come to anything. It just served to confuse me - easily done.

AlpaLexman - thanks for replying.
I made the commands you suggested but, both came back with the names followed by a colon. I presume this means they were not found?
I have looked in all locations possible but, can't see an executable file so maybe the installation is not finished.
Here is what I get when I try 'make';

make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/deke/RT25USB-SRC-V2.0.8.0 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic' 
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/deke/RT25USB-SRC-V2.0.8.0/Makefile". Fix it to use EXTRA_CFLAGS. Stop. 
make[1]: *** [_module_/home/deke/RT25USB-SRC-V2.0.8.0] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic' 
make: *** [all] Error 2 

Does any of this make sense to you guys?

---

### Post by AlphaLexman on 2010-09-17
It seems you are compiling from a source code...

Are you doing:
```
./configure
```before the 'make' command?
and,
```
make install
```after (a successful 'make')?

Also, are all dependencies met?

---

### Post by dougalkerr on 2010-09-19
AlphaLexman - I have now tried to follow the guide I have found on the cdrom that came with the device. I am pretty used to following guides to install software as I have to do it as part of my job and I have written a few scripts in my time (with that other operating system) but, this one takes the biscuit for not advizing on what to do when the various commands they ask you to carry out - dont' work.

I have always tried as hard as possible to remember all the likely problems that occur when I write a guide so that no-one has to come back and ask 'what the... it doesn't work when I type that'. So far it has never happened because I try very hard to write things in plain simple language that a child can follow.

However, we are talking about a multi-national company that obviously can't be bothered to pamper every single customer. What's a few bucks here and there if the majority of profit can be made easy from others that don't have a mind of their own... I digress, sorry.

Yes I have tried ./configure. I get the message - command not found.
I have tried make. I get the message - make: *** No targets specified and no makefile found. Stop.

I am stumped. Someone else has suggested a link to compat-wireless which I am going to look at.
I will let everyone know how I get on.

Thanks for the help so far.

---

### Post by dougalkerr on 2010-09-19
I went to the link for RutilT WLAN manager and basically discovered the related program within Synaptic. Why did no-one tell me about this? Oh well, live and learn.
I get an error message when the program runs - An error occured :
Can't get frequency/channel.
Code : 22

Any ideas folks?

It looks like my piece of kit may well be supported if I can get ubuntu to recognize it. It appears with lusub but, I can't get any software to work with it.
I have tried the Windows Wireless drivers and every one installs but, the program says no hardware detected.

......

---

### Post by mikewhatever on 2010-09-19
I think it's clear that the driver is not installed properly, if at all. If the ./configure command is not found, you must be running it from another directory, or there is another way of installing (installation script, for example). The output of make you posted earlier also exited with an error.
Perhaps this tread will help -> [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828).

---

### Post by dougalkerr on 2010-09-19
Mikewhatever - thanks very much for your help so far. It is amazing how much time we spend with one another trying to get perfection or simplicity...

I have been to this link before and this time I remembered seeing somewhere - mention of build-essential package. 
I went to synaptic - it wasn't installed, huh??? why the hell not. Never mind another slight slip by the developers.

I installed the package and here is the output of 'make' and 'make install'
deke@dell-desktop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ make
make -C tools
make[1]: Entering directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
/usr/bin/ld: cannot open output file bin2h: Permission denied
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
make: *** [build_tools] Error 2
deke@dell-desktop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ make
make -C tools
make[1]: Entering directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
/usr/bin/ld: cannot open output file bin2h: Permission denied
collect2: ld returned 1 exit status
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
make: *** [build_tools] Error 2
deke@dell-desktop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ sudo make
make -C tools
make[1]: Entering directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/action.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5687: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/spectrum.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/assoc.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:651: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:1429: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:929: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [LINUX] Error 2
deke@dell-desktop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ sudo make install
make -C /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/deke/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [install] Error 2
deke@dell-desktop:~/Downloads/2009_0525_RT3070_Linux_STA_v2.1.1.0$ 
 
I tried the RutilT WLAN program again, I didn't notice I hadn't plugged the device in but, the RutilT program did but, again here is the error message it gives;
error occured: Can't get frequency/channel. Code: 22.

Any ideas. I read from the developer of RutilT that the package is not supported any more so, I suppose no point in going there.
I have to go out for a while but, will look back later.
Thanks again.

---

### Post by mikewhatever on 2010-09-20
I am no expert in building from source, but it looks like you need to prefix both 'make' and 'make install' with sudo. Alternatively, use 'sudo su' as in the howto.

---

### Post by dougalkerr on 2010-09-21
mikewhatever

Yep, tried that... no joy.

I have had a reply from the manufacturer now and I will be trying to follow their advice again. It doesn't look straightforward so, will be a nice challenge.
I did leave a comment with them that they might consider producing a nice .deb file and have everything installed in it's rightful place ready to go. Haven't heard back from them today so my plea may have gone on deaf ears.

I'll keep everyone appraised of my progress or not.

---

