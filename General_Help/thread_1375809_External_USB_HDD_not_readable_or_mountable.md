---
title: "External USB HDD not readable or mountable"
date: 2010-01-08
forum: General Help
---

### Post by omaralqady on 2010-01-08
I have a 320GB My Passport Western Digital external HDD, which usually works fine in both Ubuntu and Vista except that when I connect it to Vista it gave a warning about something being wrong with it and an option to either do a disk check or continue and I usually dismissed the warning and continued until yesterday when Ubuntu warned me about bad sectors on the same disk, and I don't know how to repair bad sectors in FAT32 in Ubuntu so I used Vista's disk check and checked the "Scan for and attempt recovery of bad sectors", and "Automatically fix file system errors", and left it overnight and when I woke up it was still not done, so I cancelled it. After that Vista was not able to read the disk, and Ubuntu doesn't mount it and GParted doesn't read it, but the "Disk Utility" in Ubuntu reads as a non partitioned WD external HDD "2199 GB"! and when I tried fdisk -l it does not list it. Here is the output of "sudo lsusb":
```
omar@3omar:~$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 003: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a33 Unknown 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
And here is the output of "dmesg | tail":
```
omar@3omar:~$ dmesg | tail
[37152.574612] sd 9:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[37152.574617] sd 9:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[37152.574624] Info fld=0x0
[37152.574626] sd 9:0:0:0: [sdc] Add. Sense: Logical block address out of range
[37152.574634] end_request: I/O error, dev sdc, sector 2775038072
[37152.577645] sd 9:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[37152.577650] sd 9:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[37152.577655] Info fld=0x0
[37152.577657] sd 9:0:0:0: [sdc] Add. Sense: Logical block address out of range
[37152.577663] end_request: I/O error, dev sdc, sector 2775037984

```
I'm currently running "testdisk" on the disk but it is also reading it as a 2199 GB drive and it's counting up cylinders and the bottom line reads "Read error at x/2/1" and x is increasing one by one so it's taking a terribly long time and I'm not sure that this will even work so I thought I'd use this time to look up other possibilities.

Sorry for such a lengthy post :) but I would greatly appreciate all help and suggestions :)

---

### Post by mescobal on 2010-01-29
Same problem here. Any hint will be appreciated. I'll keep trying different recovery programs for WinXP. I'll post here if any success.
My WD 250 Gb USB external HD gives same size (2199 Gb) and makes a thin buzz sound 3 times when plugged, isn't recognized (Lin or Win) and different programs give the right name ("HD external.."). Apparently that means hardware damage but possibly some data could be recoverable.

---

### Post by efflandt on 2010-01-29
I have seen those Add Sense and Sense Key warnings when trying to connect a failing laptop drive in external usb enclosure.  One drive was beyond hope because I had dropped it a few feet flat onto a hard floor.  From the other I could not even copy the user's WinXP home directory or My Documents earlier, but weeks later it magically worked and I was able to recover data from it with some read errors.

This is an example of dmesg with a working Passport (ntfs partition, and bootable Ubuntu on ext3). It is sdf in this case due to usb multi-card reader.

```
[164051.090036] usb 1-1: new high speed USB device using ehci_hcd and address 5
[164051.241311] usb 1-1: configuration #1 chosen from 1 choice
[164051.242710] scsi4 : SCSI emulation for USB Mass Storage devices
[164051.242938] usb-storage: device found at 5
[164051.242943] usb-storage: waiting for device to settle before scanning
[164051.244641] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1/input/input7
[164051.244772] generic-usb 0003:1058:0705.0003: input,hidraw0: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:02.2-1/input1
[164056.240258] usb-storage: device scan complete
[164056.240844] scsi 4:0:0:0: Direct-Access     WD       5000BEV External 1.75 PQ: 0 ANSI: 4
[164056.241769] sd 4:0:0:0: Attached scsi generic sg7 type 0
[164056.254567] sd 4:0:0:0: [sdf] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[164056.256709] sd 4:0:0:0: [sdf] Write Protect is off
[164056.256718] sd 4:0:0:0: [sdf] Mode Sense: 23 00 00 00
[164056.256725] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[164056.264427] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[164056.264442]  sdf: sdf1 sdf2
[164056.312945] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[164056.312959] sd 4:0:0:0: [sdf] Attached SCSI disk
[164057.304835] kjournald starting.  Commit interval 5 seconds
[164057.305542] EXT3 FS on sdf2, internal journal
[164057.305548] EXT3-fs: mounted filesystem with writeback data mode.
```

---

### Post by no2498 on 2010-01-29
try unplugging it
and i hope you have something else to plug in like a camera that uses usb
restart the computer unmount what you had plugged  in
now plug in the hard drive
hope this helps you both 
its something to do with an old unmount

---

### Post by omaralqady on 2010-01-30
It's not a unmount thing, because I tried on Windows and Linux on more than one computer with the same result. I also removed the the case and the usb chip and tried connecting it directly through a SATA to USB cable to my laptop, it was still read as a 2199 GB drive, but Win Vista detected it with a different name, and that was the only difference, so it was in vain. 

I guess now the only hope I have is to have it magically work just for once like efflandt :)

If you guys have the data on your drives already backed up somewhere else or can live without it, go to WD's website and check if it's still in the warranty period, if it is and you haven't voided your warranty by opening the drive like I did :) they'll send you another one for free and then you're supposed to send them the old one.

That's it I guess, but if anyone has any ideas or tips, please share them with us :)

---

### Post by mescobal on 2010-02-07
Tried many WinXP recovery programs with no success. Tried freezing the HD (yes I did try this!) for 15 minutes and it didn't work.
I'm considering writing initial data of the disk "by hand" but I'm not sure which values I should use. Any news I'll posting here.

NEWS!!!!

In a mystical approach I hit the HD against the palm of my hand with and now it shows the right size and partition. I still can mount the drive but i'll keep trying and posting news here.

---

### Post by omaralqady on 2010-02-07
I tried various recovery programs as well, but of course none worked. I thought about freezing it, but I didn't go through with it :) and according to what you said, it wouldn't have mattered I guess.

-What you're suggesting might work, it's not 100% guaranteed, but it's probably our last bet, not considering commercial data recovery services of course which are too costly.

-I'm not sure about the values either, so I can't help you here. Perhaps someone who knows the FAT32 file system well and knows how to use dd for such a task can help.

---

### Post by oak3 on 2010-02-07
Hi,

I also have excact same problem, have no idea what i could do. I think i dont care anymore about data on disk, just want to make disk usable again :)

---

### Post by omaralqady on 2010-02-07
It's quite the opposite for me, I terribly need the data on it. I'll survive without it, but if I had to choose, I'd definitely choose the data. 

-In your case, if you hadn't opened the disk's case, and thus voided your warranty, you could go to this page: [http://websupport.wdc.com/warranty/serialinput.asp?aspsid=958005825&custtype=end&requesttype=warranty&lang=en]("http://websupport.wdc.com/warranty/serialinput.asp?aspsid=958005825&custtype=end&requesttype=warranty&lang=en") and check if your disk is still in the warranty period, if it is, go to this page: [http://websupport.wdc.com/warranty/rmainfo.asp?custtype=end&lang=en]("http://websupport.wdc.com/warranty/rmainfo.asp?custtype=end&lang=en") where you can get a replacement for it from WD. If it's out of the warranty period, then you're out of luck until perhaps we can find a solution here in this thread hopefully :)

---

### Post by omaralqady on 2010-02-07
@mescobal: That's good news I guess :D, maybe the next hit will get it to mount :D keep us posted please if anything comes up :)

---

