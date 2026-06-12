---
title: "mount usb drive from command line"
date: 2010-04-01
forum: General Help
---

### Post by bcrowell on 2010-04-01
I used to be able to mount usb media such as a digital camera like this:

mount -t vfat /dev/sdb1 /media/usbdisk

After upgrading to karmic, it no longer works. I get this error:

mount: special device /dev/sdb1 does not exist

Here's what I have in /dev:

```
adsp     cpu_dma_latency  hpet   loop6               null       pts    ram3    rtc0        shm       tty1   tty19  tty28  tty37  tty46  tty55  tty7     usbmon0  vcs7   vcsa8
audio    disk             input  loop7               nvidia0    ram0   ram4    scd0        snapshot  tty10  tty2   tty29  tty38  tty47  tty56  tty8     usbmon1  vcs8   zero
binder   dsp              kmsg   lp0                 nvidiactl  ram1   ram5    sda         snd       tty11  tty20  tty3   tty39  tty48  tty57  tty9     usbmon2  vcsa
block    dvd              log    mapper              oldmem     ram10  ram6    sda1        sndstat   tty12  tty21  tty30  tty4   tty49  tty58  ttyS0    vcs      vcsa1
bus      dvdrw            loop0  mcelog              parport0   ram11  ram7    sda2        sr0       tty13  tty22  tty31  tty40  tty5   tty59  ttyS1    vcs1     vcsa2
cdrom    ecryptfs         loop1  mem                 pktcdvd    ram12  ram8    sda5        stderr    tty14  tty23  tty32  tty41  tty50  tty6   ttyS2    vcs2     vcsa3
cdrw     fd               loop2  mixer               port       ram13  ram9    sequencer   stdin     tty15  tty24  tty33  tty42  tty51  tty60  ttyS3    vcs3     vcsa4
char     fd0              loop3  net                 ppp        ram14  random  sequencer2  stdout    tty16  tty25  tty34  tty43  tty52  tty61  urandom  vcs4     vcsa5
console  full             loop4  network_latency     psaux      ram15  rfkill  sg0         tty       tty17  tty26  tty35  tty44  tty53  tty62  usb      vcs5     vcsa6
core     fuse             loop5  network_throughput  ptmx       ram2   rtc     sg1         tty0      tty18  tty27  tty36  tty45  tty54  tty63  usblp0   vcs6     vcsa7
```

The sda devices are all partitions on my hard disk. No sdb devices appear. The camera's screen shows that it's hooked up to the computer via usb. I can log in to a gnome session, and it automatically displays an icon for the camera on my desktop and lets me access the files. However, I don't like gnome, and prefer to use fluxbox and mount things from the command line. Can anyone suggest how to do this?

Thanks in advance!

---

### Post by Chesamo on 2010-04-01
ED: Whoops, missed that last part.

ls the /dev directory before inserting the USB drive, then ls it after. The device that appears is the device ;-)

---

### Post by bcrowell on 2010-04-01
> **Chesamo said:**
> ED: Whoops, missed that last part.

ls the /dev directory before inserting the USB drive, then ls it after. The device that appears is the device ;-)

Ah, that's a very sensible suggestion, Chesamo, thanks!

Unfortunately it didn't help. 

$ ls /dev >b.b
[Connect camera. Wait a few minutes.]
$ ls /dev >c.c
$ diff b.b c.c

The result is that there is no difference between the /dev listing before and after connecting the camera.

---

### Post by moetunes on 2010-04-01
with camera unplugged type in terminal
demsg | tail
plug the camera in and run the command again. It should give a clue to the camera dev name.

---

### Post by bcrowell on 2010-04-01
> **moetunes said:**
> with camera unplugged type in terminal
demsg | tail
plug the camera in and run the command again. It should give a clue to the camera dev name.

Thanks for the suggestion, moetunes. Here is the only output I get from dmesg:

```

[  128.510068] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  128.663953] usb 1-3: configuration #1 chosen from 1 choice
```

I don't see anything that looks like a device name...?

---

### Post by bcrowell on 2010-04-01
Any other suggestions?

---

### Post by rbc on 2010-04-01
With the camera I have, if I want to access the photos on the camera directly (as opposed to using F-Spot or something), I find them in the ~/.gvfs directory. I doubt, however, that .gvfs is the true mount point. I know this doesn’t answer your question but maybe it will point you in the right direction

---

### Post by bcrowell on 2010-04-04
> **rbc said:**
> With the camera I have, if I want to access the photos on the camera directly (as opposed to using F-Spot or something), I find them in the ~/.gvfs directory. I doubt, however, that .gvfs is the true mount point. I know this doesn’t answer your question but maybe it will point you in the right direction

Hmm...thanks for the pointer, rbc. It looks like gvfs is how gnome handles this these days. However, I still need to figure out how to do it without using gnome.

---

### Post by bcrowell on 2010-04-05
Bump.

Still no suggestions from anybody? Gosh, this seems like such an absolutely straightforward thing to want to be able to do.

---

### Post by SnickerSnack on 2010-04-05
Have you tried reading off of the memory card directly?

Did you do these:

> mount -t vfat /dev/sdb1 /media/usbdisk

> $ ls /dev >b.b
[Connect camera. Wait a few minutes.]
$ ls /dev >c.c
$ diff b.b c.c

with the camera on?  If so, did you also try it with the camera off?

Have you tried

$ fdisk -l

with the camera on/off and with the card connected directly?

---

### Post by bcrowell on 2010-04-06
Hi, SnickerSnack -- Thanks for your suggestions!

> **SnickerSnack said:**
> Have you tried reading off of the memory card directly?
I don't have the optional removable memory card for this camera. I'm just using its built-in, nonremovable card.

> **SnickerSnack said:**
> Did you do these: [...]
with the camera on?  If so, did you also try it with the camera off?
Yes. No luck.

> **SnickerSnack said:**
> 
Have you tried

$ fdisk -l

with the camera on/off and with the card connected directly?
The fdisk command requires a device name as an argument, but I don't have any device name I can give it, since /dev/sdb1 isn't created.

One thing I've figured out today is that this problem is device-dependent. I have a USB thumb drive, and when I plug that in, the /dev/sdb1 device is created correctly by the OS. However, when I plug in this camera, the /dev/sdb1 device is not created. It doesn't matter whether the camera is powered up or not; either way, the OS fails to crate /dev/dsb1.

---

### Post by SnickerSnack on 2010-04-07
> **bcrowell said:**
> 
The fdisk command requires a device name as an argument, but I don't have any device name I can give it, since /dev/sdb1 isn't created.


I should have said to try:

```
sudo fdisk -l
```

it will list the disks that it sees, no specific device name needed.

This might not help you, but it's something to try.

However, I'm guessing that you're not going to be able to see that memory card.

---

