---
title: "Slow Boot From Flash Drive"
date: 2012-01-25
forum: General Help
---

### Post by bc110627 on 2012-01-25
Hi I am new to Ubuntu. I have created a bootable flash drive of 11.10 and 10.04 and have the same problem either way. When booting on a dell latitude d420 it takes forever. As much as 45 minutes to load. There is slew of error codes when it is loading. All look like they are regarding the hard drive. Saying 

failed command: Read DMA

or

udevd[95]: timeout: killing ' /sbin/blkid -o udev-p /dev/sda'

Once it is done with all these errors for five minutes the Ubuntu loading screen pops up and takes an extremely long time before It will load. I can boot onto my HP with no problem and takes 60 seconds at most to boot. Any and all help would be greatly appreciated.

 I am still learning so please take it easy on me if I'm a little slow.

BC

---

### Post by gennatolls on 2012-01-25
For me, booting into the live environment (as you are) has always been slower that once it is loaded onto my HDD.

---

### Post by bc110627 on 2012-01-25
On my HP it boots in less than a minute with no issues. I guess my main question is. If there is a problem with a hard drive can it cause a USB boot to be slower and if not what could be the reason it takes 30 minutes to boot from USB. 

BC

---

### Post by bc110627 on 2012-01-25
Below is the errors I'm getting. Once again any and all help is appreciated.


[  782.308782]          res 51/40:00:09:f8:50/00:00:00:00:00/e9 Emask 0x9 (media error) 
[  782.308788] ata1.00: status: { DRDY ERR } 
[  782.308793] ata1.00: error: { UNC } 
[  782.416776] ata1.00: configured for PIO0 
[  782.416802] sd 0:0:0:0: [sda] Unhandled sense code 
[  782.416807] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
[  782.416814] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor] 
[  782.416823] Descriptor sense data with sense descriptors (in hex): 
[  782.416827]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  782.416847]         09 50 f8 09 
[  782.416856] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed 
[  782.416867] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 09 50 f8 00 00 00 08 00 
[  782.416885] end_request: I/O error, dev sda, sector 156301312 
[  782.416893] Buffer I/O error on device sda, logical block 19537664 
[  782.416921] ata1: EH complete 
[  791.000513] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 
[  791.000524] ata1.00: failed command: READ MULTIPLE 
[  791.000537] ata1.00: cmd c4/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 pio 4096 in 
[  791.000539]          res 51/01:00:09:f8:50/00:00:00:00:00/e9 Emask 0x1 (device error) 
[  791.000545] ata1.00: status: { DRDY ERR } 
[  791.100824] ata1.00: configured for PIO0 
[  791.100840] ata1: EH complete 
[  799.635068] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 
[  799.635078] ata1.00: failed command: READ MULTIPLE 
[  799.635091] ata1.00: cmd c4/00:08:00:f8:50/00:00:00:00:00/e9 tag 0 pio 4096 in 
[  799.635094]          res 51/40:00:09:f8:50/00:00:00:00:00/e9 Emask 0x9 (media error) 
[  799.635100] ata1.00: status: { DRDY ERR } 
[  799.635104] ata1.00: error: { UNC } 
[  799.744829] ata1.00: configured for PIO0 
[  799.744847] ata1: EH complete 
[  808.312473] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0

---

### Post by C.S.Cameron on 2012-01-26
Try your flash drive in another computer to narrow down the possible source of the problem.

It should boot in less than a minute.

You can also check the MD5SUM of the iso, there could be a corruption with the download.

---

### Post by bc110627 on 2012-01-26
I have tried it numerous times on both my HP Pavilion and the Dell Latitude. On the Dell it takes close to 30 minutes with the above errors. On my HP there is no problems at all and it does take less than a minute. I know it is the laptop but I don't know what is the actual cause.

---

### Post by C.S.Cameron on 2012-01-27
Does your Dell have the necessary spec's required to run Ubuntu?
Perhaps give LUbuntu a try if not.

---

