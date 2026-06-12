---
title: "can't open sd card with photos"
date: 2012-01-18
forum: General Help
---

### Post by Friccy on 2012-01-18
Hi!
I have a problem for a while with Ubuntu and Mint.
They are not opening pictures from an SD CARD. If the SD CARD is opened, it shows juat about 10 pictures (out of about 100) and still can't wiev them.
The card reader is OK because if I boot from Windows, it's OK, pictures can be wieved and copied to the HD.
It doesen't work neither with picture wievers (Shotwell, DigiCam, etc.)
Any ideas how can it be fixed?

---

### Post by Scott Baker on 2012-01-18
I've run into this problem on occasion also. If anyone has a relatively simple solution, you now have 2 of us that would really appreciate the help. ](*,)

---

### Post by sudodus on 2012-01-18
It may help us help you, if you post the output of the following terminal commands (when the card and readers are attached via USB.
```
sudo fdisk -lu
```
```
df
```
And do you know what is the file system of the flash card? It should be shown by Windows (via Control Panel ...)

You can also try to find information about the card and reader hardware via the terminal command
```
gksudo lshw | less
``` or the GUI program ***hardinfo*** (maybe you need to install it via)
```
sudo apt-get install hardinfo
```

---

### Post by Friccy on 2012-01-18
The output for the 
gksudo lshw | less is

*-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:07:05.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64
             resources: irq:7 memory:b0100800-b01008ff
 It is just the part about the SD card controller.

---

### Post by sudodus on 2012-01-18
Good, the card reader is recognized. Now please post results from the other investigations too, to find out about the file system, partition size and if it is mounted. Maybe we could add another command (to look at the file /etc/mtab which show data about mounted devices.
```
cat /etc/mtab
```

---

### Post by Friccy on 2012-01-19
Hi Sudodus!

Here are the requested infos:
sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5d18b2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   112663844    56331891    7  HPFS/NTFS/exFAT
/dev/sda2       169983765   297379214    63697725    7  HPFS/NTFS/exFAT
/dev/sda3       297390080   312571903     7590912    7  HPFS/NTFS/exFAT
/dev/sda4       112663906   169983764    28659929+   f  W95 Ext'd (LBA)
/dev/sda5       112663908   139283549    13309821   83  Linux
/dev/sda6       139283613   165903254    13309821   83  Linux
/dev/sda7       165903318   169983764     2040223+  82  Linux swap / Solaris

friccy@friccy-HP ~ $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             13100844   6634556   5800800  54% /
udev                   1020116         4   1020112   1% /dev
tmpfs                   411212      1020    410192   1% /run
none                      5120         0      5120   0% /run/lock
none                   1028024       356   1027668   1% /run/shm
/dev/sda2             63697724  36234084  27463640  57% /media/IRATOK

It's really interesting that all other OS-es that are not based on Ubuntu can see, open the SD card that is in the built in reader.

---

### Post by sudodus on 2012-01-19
No, Ubuntu can see only the internal disk drive /dev/sda. I had hoped that is was seen by ***fdisk*** but not mounted. Can you find out what file system there is on the flash card? Ubuntu can mount FAT32 (which is common on such devices) but there are problems with exFAT (which is getting more common on such devices). exFAT is owned by Microsoft, which makes it hard to manage, but there are threads in the Ubuntu Forums, where people write that they can manage it with some special tools (downloaded from the internet).

But I have a feeling that the device should be shown anyway by fdisk (even if a partition with exFAT cannot be mounted), so I really have no more idea right now.

---

