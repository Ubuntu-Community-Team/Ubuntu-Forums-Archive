---
title: "ctrl alt prt scr screwup?"
date: 2009-08-03
forum: General Help
---

### Post by jmerkin on 2009-08-03
Hi all

Unsure of the cause, but my install froze while running a basic command from terminal. I tried killing the program and firefox and it did nothing, so I tried a soft reset using Ctrl+Alt+PrtScr+R,E,I,U,B,S. It killed the GUI but didn't reboot so I thought I had them out of order and tried them in a different order, then I thought I had the wrong keys so I tried a few others. Then I gave up and gave it a hard boot.

Now it takes forever to boot up with my external usb attached it takes forever to get through POST (it stalls before RAM check). I unplugged it and it went through immediately. Concurrently, the external drive will now not be mounted. When I plug it in, it is recognized (in lsusb and dmesg) as an external HD. It does not show up in /dev. Only sda* show up. 

```
/dev$ ls  
adsp             loop3               ram3        tty    tty35  tty62           usbmon0
audio            loop4               ram4        tty0   tty36  tty63           usbmon1
block            loop5               ram5        tty1   tty37  tty7            usbmon2
bus              loop6               ram6        tty10  tty38  tty8            usbmon3
cdrom2           loop7               ram7        tty11  tty39  tty9            usbmon4
cdrw2            mapper              ram8        tty12  tty4   ttyS0           usbmon5
char             mem                 ram9        tty13  tty40  ttyS1           usbmon6
console          mixer               random      tty14  tty41  ttyS2           usbmon7
core             net                 rtc         tty15  tty42  ttyS3           vcs    
cpu_dma_latency  network_latency     rtc0        tty16  tty43  urandom         vcs1
disk             network_throughput  scd0        tty17  tty44  usbdev1.1_ep00  vcs2
dsp              null                sda         tty18  tty45  usbdev1.1_ep81  vcs3
dvd2             nvidia0             sda1        tty19  tty46  usbdev2.1_ep00  vcs4
dvdrw2           nvidiactl           sda2        tty2   tty47  usbdev2.1_ep81  vcs5
ecryptfs         oldmem              sda5        tty20  tty48  usbdev2.3_ep00  vcs6
fd               pktcdvd             sda6        tty21  tty49  usbdev2.3_ep02  vcs7
fd0              port                sda7        tty22  tty5   usbdev2.3_ep81  vcs8
full             ppp                 sda8        tty23  tty50  usbdev3.1_ep00  vcsa
fuse             psaux               sequencer   tty24  tty51  usbdev3.1_ep81  vcsa1
hidraw0          ptmx                sequencer2  tty25  tty52  usbdev4.1_ep00  vcsa2
hidraw1          pts                 sg0         tty26  tty53  usbdev4.1_ep81  vcsa3
hpet             ram0                sg1         tty27  tty54  usbdev5.1_ep00  vcsa4
initctl          ram1                shm         tty28  tty55  usbdev5.1_ep81  vcsa5
input            ram10               snapshot    tty29  tty56  usbdev6.1_ep00  vcsa6
kmem             ram11               snd         tty3   tty57  usbdev6.1_ep81  vcsa7
kmsg             ram12               sndstat     tty30  tty58  usbdev6.2_ep00  vcsa8
log              ram13               sr0         tty31  tty59  usbdev6.2_ep81  xconsole
loop0            ram14               stderr      tty32  tty6   usbdev6.2_ep82  zero
loop1            ram15               stdin       tty33  tty60  usbdev7.1_ep00
loop2            ram2                stdout      tty34  tty61  usbdev7.1_ep81

```

I'm not sure what I should do, if I should try to hit the same buttons with ctrl alt prtscr again, or if there's something I should change. Stupid move on my part. Anybody with ideas?

---

### Post by jmerkin on 2009-08-03
It might be of interest that a different usb device is recognized and mounted when plugged in. I'm running kubuntu 9.04. The external wasn't recognized on another computer as well. If it's possible I erased something on it (maybe the journal or something), then so be it and I'll reformat, though it'll hurt.

---

### Post by jmerkin on 2009-08-04
It's definitely something about the drive. While POSTing with it plugged in, it stalls. If I unlpug the drive mod-stall, it progresses. If I plug it in later, it'll stall again until I unplug it. 

And I got inpatient and tried some random keys with ctrl alt prtscr and nothing changed.

Could I have somehow changed it to boot from the drive?

---

### Post by jmerkin on 2009-08-04
Upon opening up gparted, after getting an error saying it can't read the partition tables on /dev/sda, a notification popped up recognizing an ext3 partition. It also says it is mounting the existing partition on the computer's hard drive as ext2fs during boot, which is also odd because it was ext3 when I installed and ext3 when I enter mount. Could I have mucked up the partition tables or deleted the journal?

I seem to be much more of a noob than I thought I was to do something seemingly this dumb...

---

