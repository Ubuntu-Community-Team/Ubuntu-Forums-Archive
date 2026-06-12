---
title: "Multisync and W910i"
date: 2009-09-07
forum: General Help
---

### Post by sn0m on 2009-09-07
Hi guys, I'm trying to multisync my W910i (Sony Ericsson) with Evolution in my laptop via cable. I need to enter the right serial port (the default options /dev/ttySO and /dev/ttyS1 fail connection). Is there a way that I can find out where is the device mounted. It connects via a usb cable and I can see it on the desktop as sony ericsson mobile communication unit.
If it helps this is the output form /dev/ls
agpgart             psaux       tty11  tty53           usbdev4.1_ep81
audio               ptmx        tty12  tty54           usbdev5.1_ep00
block               pts         tty13  tty55           usbdev5.1_ep81
bus                 ram0        tty14  tty56           usbdev6.1_ep00
cdc-wdm0            ram1        tty15  tty57           usbdev6.1_ep81
cdrom               ram10       tty16  tty58           usbdev6.2_ep00
cdrw                ram11       tty17  tty59           usbdev6.2_ep81
char                ram12       tty18  tty6            usbdev7.1_ep00
console             ram13       tty19  tty60           usbdev7.1_ep81
core                ram14       tty2   tty61           usbdev8.1_ep00
cpu_dma_latency     ram15       tty20  tty62           usbdev8.1_ep81
disk                ram2        tty21  tty63           usbmon0
dri                 ram3        tty22  tty7            usbmon1
dsp                 ram4        tty23  tty8            usbmon2
dvd                 ram5        tty24  tty9            usbmon3
dvdrw               ram6        tty25  ttyACM0         usbmon4
ecryptfs            ram7        tty26  ttyACM1         usbmon5
fd                  ram8        tty27  ttyS0           usbmon6
full                ram9        tty28  ttyS1           usbmon7
fuse                random      tty29  ttyS2           usbmon8
hidraw0             rtc         tty3   ttyS3           vboxdrv
hpet                rtc0        tty30  urandom         vboxnetctl
initctl             scd0        tty31  usbdev1.1_ep00  vcs
input               sda         tty32  usbdev1.1_ep81  vcs1
kmem                sda1        tty33  usbdev2.1_ep00  vcs2
kmsg                sda2        tty34  usbdev2.1_ep81  vcs3
log                 sdb         tty35  usbdev2.3_ep00  vcs4
loop0               sdb1        tty36  usbdev2.3_ep01  vcs5
loop1               sequencer   tty37  usbdev2.3_ep82  vcs6
loop2               sequencer2  tty38  usbdev2.8_ep00  vcs7
loop3               serial      tty39  usbdev2.8_ep01  vcs8
loop4               sg0         tty4   usbdev2.8_ep03  vcsa
loop5               sg1         tty40  usbdev2.8_ep04  vcsa1
loop6               sg2         tty41  usbdev2.8_ep06  vcsa2
loop7               shm         tty42  usbdev2.8_ep81  vcsa3
mapper              snapshot    tty43  usbdev2.8_ep83  vcsa4
mem                 snd         tty44  usbdev2.8_ep84  vcsa5
mixer               sndstat     tty45  usbdev2.8_ep85  vcsa6
net                 sr0         tty46  usbdev2.8_ep86  vcsa7
network_latency     stderr      tty47  usbdev2.8_ep87  vcsa8
network_throughput  stdin       tty48  usbdev2.8_ep88  watchdog
null                stdout      tty49  usbdev2.8_ep89  xconsole
oldmem              tty         tty5   usbdev2.8_ep8a  zero
pktcdvd             tty0        tty50  usbdev3.1_ep00
port                tty1        tty51  usbdev3.1_ep81
ppp                 tty10       tty52  usbdev4.1_ep00
koli@koli-laptop:/$ 

Thanks in advance
Sokol

---

### Post by gready on 2009-09-25
I to am have problems getting multisync to connect to this phone 

I have however had success connecting and using Wammu 0.29 but this will not sync with evolution

I have tried using the same port in multisync ttyACM0 but this did not work either

---

