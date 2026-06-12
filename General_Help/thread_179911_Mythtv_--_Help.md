---
title: "Mythtv -- Help"
date: 2006-05-21
forum: General Help
---

### Post by basketcase on 2006-05-21
Let me start off by saying this is Ubuntu 5.10 (fresh installed today)
PRV-350 Card

[http://www.abarbaccia.com/](http://www.abarbaccia.com/)
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

I've followed the above instructions

I can load Mythtv, but when I try and specify Input, I get a segmentation Error.  

When I do a
sudo dmesg |grep ivtv


[4294699.221000] ivtv:  ==================== START INIT IVTV ====================
[4294699.221000] ivtv:  version 0.4.5 (tagged release) loading
[4294699.221000] ivtv:  Linux version: 2.6.12-10-386 386 gcc-3.4
[4294699.221000] ivtv:  In case of problems please include the debug info between
[4294699.221000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294699.221000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294699.225000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4294699.288000] tveeprom: ivtv version
[4294699.288000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294699.383000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294699.383000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294699.557000] saa7115 0-0021: ivtv driver
[4294699.557000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294699.663000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294699.729000] saa7127 0-0044: ivtv driver
[4294699.731000] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[4294699.732000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4294699.823000] msp3400 0-0040: ivtv driver
[4294699.827000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-B3, addr=40]
[4294699.893000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294699.893000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294701.332000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4294701.332000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294701.332000] ivtv0 warning: failed loading encoder firmware
[4294701.332000] ivtv0 warning: Error loading firmware -3!
[4294701.332000] ivtv0: Error -3 initializing firmware.
[4294701.405000] ivtv0: Error -12 on initialization
[4294701.405000] ivtv: probe of 0000:00:10.0 failed with error -12
[4294701.405000] ivtv:  ====================  END INIT IVTV  ====================

If I do this....

```
barry@umyth:/usr/lib/hotplug/firmware$ cd /usr/lib/hotplug/firmware
barry@umyth:/usr/lib/hotplug/firmware$ ls
ivtv-fw-dec.bin  ivtv-fw-enc.bin  v41-cx2341x-dec.fw  v41-cx2341x-enc.fw  v41-cx25840.fw  v4l-cx2341x-init.mpg

```

It shows me the files are there in the firmware directory.  

I'm stuck.  After almost 5 hours (2 installs of Ubuntu and 1 on Knoppmyth -- I'm getting frustrated).  

Thanks for any help/assistance you can offer.

---

### Post by Titus A Duxass on 2006-05-21
If you have the correct files (firmware) in the correct places try doing a cold reboot.

Switch of the PC and unplug it, wait for 30 seconds then start it up again.

---

### Post by Hendrik van den Boogaard on 2006-05-21
In my case (Dapper Drake), the firmware files must be placed in /lib/firmware/<kernelname>. It took me some time to figure that out though.

---

### Post by PBK on 2006-05-21
I have 5.10 with my 350 and 500 cards. My /usr/lib/hotplug/firmware/ directory looks like this:

-rw-r--r--  1 root root 262144 2006-03-25 09:11 ivtv-fw-dec.bin
-rw-r--r--  1 root root 262144 2006-03-25 09:11 ivtv-fw-enc.bin
lrwxrwxrwx  1 root root     41 2006-03-25 09:12 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-r--r--r--  1 root root 376836 2006-03-25 09:11 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-03-25 09:12 v4l-cx2341x-init.mpg
-r--r--r--  1 root root  14264 2006-03-25 09:11 v4l-cx25840.fw

  I used the HowTo from:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by basketcase on 2006-05-21
[QUOTE=PBK]I have 5.10 with my 350 and 500 cards. My /usr/lib/hotplug/firmware/ directory looks like this:

-rw-r--r--  1 root root 262144 2006-03-25 09:11 ivtv-fw-dec.bin
-rw-r--r--  1 root root 262144 2006-03-25 09:11 ivtv-fw-enc.bin
lrwxrwxrwx  1 root root     41 2006-03-25 09:12 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-r--r--r--  1 root root 376836 2006-03-25 09:11 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-03-25 09:12 v4l-cx2341x-init.mpg
-r--r--r--  1 root root  14264 2006-03-25 09:11 v4l-cx25840.fw

  I used the HowTo from:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)[/QUOTE]
-rwxrwxrwx  1 barry barry 155648 2005-12-29 06:06 v4l-cx2341x-init.mpg
drwxr-xr-x  3 root  root    4096 2006-05-20 19:05 ..
-rw-r--r--  1 root  root  262144 2006-05-20 22:39 ivtv-fw-enc.bin
-rw-r--r--  1 root  root  262144 2006-05-20 22:39 ivtv-fw-dec.bin
-r--r--r--  1 root  root   14264 2006-05-20 22:40 v41-cx25840.fw
-r--r--r--  1 root  root  376836 2006-05-20 22:41 v41-cx2341x-enc.fw
lrwxrwxrwx  1 root  root      41 2006-05-20 22:44 v41-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x  2 root  root    4096 2006-05-20 23:10 .

---

### Post by PBK on 2006-05-21
I don't know if this is typo, a font thing or what, but I see my file names starting with "v4" have the (lower case) _letter_ "L" after it and your's has what looks like the _number_ "1" ....?

  If that is the problem, I wonder how that happened...


[QUOTE=basketcase]

Originally Posted by PBK
I have 5.10 with my 350 and 500 cards. My /usr/lib/hotplug/firmware/ directory looks like this:

-rw-r--r-- 1 root root 262144 2006-03-25 09:11 ivtv-fw-dec.bin
-rw-r--r-- 1 root root 262144 2006-03-25 09:11 ivtv-fw-enc.bin
lrwxrwxrwx 1 root root 41 2006-03-25 09:12 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-r--r--r-- 1 root root 376836 2006-03-25 09:11 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2006-03-25 09:12 v4l-cx2341x-init.mpg
-r--r--r-- 1 root root 14264 2006-03-25 09:11 v4l-cx25840.fw

I used the HowTo from:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
-rwxrwxrwx 1 barry barry 155648 2005-12-29 06:06 v4l-cx2341x-init.mpg
drwxr-xr-x 3 root root 4096 2006-05-20 19:05 ..
-rw-r--r-- 1 root root 262144 2006-05-20 22:39 ivtv-fw-enc.bin
-rw-r--r-- 1 root root 262144 2006-05-20 22:39 ivtv-fw-dec.bin
-r--r--r-- 1 root root 14264 2006-05-20 22:40 v41-cx25840.fw
-r--r--r-- 1 root root 376836 2006-05-20 22:41 v41-cx2341x-enc.fw
lrwxrwxrwx 1 root root 41 2006-05-20 22:44 v41-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x 2 root root 4096 2006-05-20 23:10 .
 .[/QUOTE]

---

### Post by basketcase on 2006-05-21
[QUOTE=PBK]I don't know if this is typo, a font thing or what, but I see my file names starting with "v4" have the (lower case) _letter_ "L" after it and your's has what looks like the _number_ "1" ....?

  If that is the problem, I wonder how that happened...[/QUOTE]
I thought it was 41
I'll change everything to 4l (Lowercase L)

Thanks!

---

### Post by basketcase on 2006-05-21
Renamed everything....
Shut the computer down, unplugged it, fired it back up and here we are!!

Man Myth is a PITA to install! 

Thanks for everyone's help. 

[4294699.419000] ivtv:  ==================== START INIT IVTV ===================                                                                             =
[4294699.419000] ivtv:  version 0.4.5 (tagged release) loading
[4294699.419000] ivtv:  Linux version: 2.6.12-10-386 386 gcc-3.4
[4294699.419000] ivtv:  In case of problems please include the debug info betwee                                                                             n
[4294699.419000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294699.419000] ivtv:  any module options, when mailing the ivtv-users mailingl                                                                             ist.
[4294699.431000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4294699.492000] tveeprom: ivtv version
[4294699.492000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294699.562000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #                                                                             0
[4294699.562000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294699.739000] saa7115 0-0021: ivtv driver
[4294699.739000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294699.846000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294699.953000] saa7127 0-0044: ivtv driver
[4294699.955000] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[4294699.957000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4294700.005000] msp3400 0-0040: ivtv driver
[4294700.009000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-B3, addr=40]
[4294700.075000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294700.075000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294701.640000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294701.866000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[4294702.096000] ivtv0: Encoder revision: 0x02050032
[4294702.106000] ivtv0: Decoder revision: 0x02020023
[4294702.108000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4                                                                             096KB total)
[4294702.111000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20                                                                             48KB total)
[4294702.114000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20                                                                             48KB total)
[4294702.117000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer                                                                             s (2048KB total)
[4294702.121000] ivtv0: Create encoder radio stream
[4294702.124000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (10                                                                             24KB total)
[4294702.126000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (102                                                                             4KB total)
[4294702.130000] ivtv0: Create decoder VOUT stream
[4294702.130000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (102                                                                             4KB total)
[4294702.289000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[4294702.399000] tuner: type set to 47 (LG NTSC (TAPE series)) by ivtv i2c drive                                                                             r #0
[4294702.612000] ivtv0: Initialized WinTV PVR 350, card #0
[4294702.612000] ivtv:  ====================  END INIT IVTV  ===================

---

### Post by scifan on 2006-06-13
btw, with my PVR 500, I had to down-grade ivtv from 0.4.5 to 0.4.4 because ivtv would freeze when I'd change channel's...  (the IVTV driver would freak and then system wouldn't respond as expected...)

---

