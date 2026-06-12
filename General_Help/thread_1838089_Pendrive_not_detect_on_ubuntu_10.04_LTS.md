---
title: "Pendrive not detect on ubuntu 10.04 LTS"
date: 2011-09-02
forum: General Help
---

### Post by Ikmal2129 on 2011-09-02
hye,,,,i have 1 questions.
why my usb pendrive not detect on my ubuntu 10.04 LTS??
but headset and broadband workking perfect.
what my proble?
sorg for my bad english.
i live on malaysia

---

### Post by Wim Sturkenboom on 2011-09-03
You need to be a bit more specific ;)

I assume you don't get an icon on the desktop. Does it show in the 'places' menu?

If not

After inserting the pendrive, run the commands *_lsusb_* and *_dmesg |tail -n15_* and post the resulting output here (between [noparse]```
 and 
```[/noparse])

---

### Post by mörgæs on 2011-09-03
> **isabellaswan said:**
> install or update usb drivers

This advice might be relevant in Windows, but not in Ubuntu. 

Please be very specific and exact when giving advice, else the result could be worse than nothing.

---

### Post by Ikmal2129 on 2011-09-03
[QUOTE]

ikmal@-Ikmal-:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0718:0433 Imation Corp. 
Bus 001 Device 006: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Ikmal2129 on 2011-09-03
ikmal@-Ikmal-:~$  dmesg |tail -n15
[   39.055195] PPP Deflate Compression module registered
[   53.002965] ISO 9660 Extensions: Microsoft Joliet Level 1
[   53.017717] ISOFS: changing to secondary root
[  401.491264] __ratelimit: 9 callbacks suppressed
[  401.491274] uget-gtk[2607]: segfault at 10 ip 080775fa sp b1d91270 error 4 in uget-gtk[8048000+36000]
[  541.489631] uget-gtk[2617]: segfault at 10 ip 080775fa sp b1ce5270 error 4 in uget-gtk[8048000+36000]
[ 1370.172635] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=209.85.175.101 DST=10.128.159.198 LEN=52 TOS=0x00 PREC=0x00 TTL=252 ID=16144 DF PROTO=TCP SPT=80 DPT=41029 WINDOW=6421 RES=0x00 ACK URGP=0 
[ 1371.424765] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=209.85.175.101 DST=10.128.159.198 LEN=52 TOS=0x00 PREC=0x00 TTL=252 ID=25926 DF PROTO=TCP SPT=80 DPT=41029 WINDOW=6421 RES=0x00 ACK URGP=0 
[ 2324.064883] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=91.189.90.217 DST=10.128.159.198 LEN=236 TOS=0x00 PREC=0x00 TTL=252 ID=30050 DF PROTO=TCP SPT=80 DPT=42966 WINDOW=6816 RES=0x00 ACK PSH URGP=0 
[ 2355.940649] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 2356.079750] usb 1-2: configuration #1 chosen from 1 choice
[ 2356.104110] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2356.112730] usb-storage: device found at 7
[ 2356.112738] usb-storage: waiting for device to settle before scanning
[ 2409.980635] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=91.189.90.217 DST=10.128.159.198 LEN=229 TOS=0x00 PREC=0x00 TTL=252 ID=27858 DF PROTO=TCP SPT=80 DPT=43030 WINDOW=6891 RES=0x00 ACK PSH URGP=0

---

### Post by Wim Sturkenboom on 2011-09-04
Only the lines starting with 2355 and 2356 are relevant. You should however get more after the last one

```

[91579.120027] usb 1-10: new high speed USB device using ehci_hcd and address 7
[91579.282732] usb 1-10: configuration #1 chosen from 1 choice
[91579.283148] scsi7 : SCSI emulation for USB Mass Storage devices
[91579.283302] usb-storage: device found at 7
[91579.283304] usb-storage: waiting for device to settle before scanning
[COLOR="Red"][91584.280311] usb-storage: device scan complete[/COLOR]
[91584.329030] scsi 7:0:0:0: Direct-Access     Verbatim STORE N GO       PMAP PQ: 0 ANSI: 0 CCS
[91584.331596] sd 7:0:0:0: Attached scsi generic sg3 type 0
[91585.020761] sd 7:0:0:0: [sdc] 8060928 512-byte logical blocks: (4.12 GB/3.84 GiB)
[91585.021500] sd 7:0:0:0: [sdc] Write Protect is off
[91585.021504] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[91585.021507] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[91585.026502] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[91585.026509]  sdc: sdc1
[91585.091536] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[91585.091544] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```
The red line is where 'you' don't get. Unfortunately I don't know how to solve that. Maybe others?

---

### Post by Ikmal2129 on 2011-09-07
who can help me????

---

### Post by pqwoerituytrueiwoq on 2011-09-07
have you tried other usb ports?

---

### Post by mörgæs on 2011-09-08
You need to give ALL the details you can possible think of, if we should be able to help:

[LIST]
[*]Complete hardware description
[*]Which software (does this also apply to newer Ubuntus?)
[*]Can't you read any USB sticks at all, or is this about one particular USB stick?
[*]Which make of USB stick are we talking of?
[*]Can the stick(s) be read from other computers?
[*]Test you have done to isolate the problem
[*]And so on
[*]And so on
[/LIST]

---

### Post by nipunshakya on 2011-09-08
> **Ikmal2129 said:**
> hye,,,,i have 1 questions.
why my usb pendrive not detect on my ubuntu 10.04 LTS??
but headset and broadband workking perfect.
what my proble?
sorg for my bad english.
i live on malaysia

Hello, i would like to give u a simple suggestion regarding pendrive......

when my pendrive didnt work on my fren's machine running ubuntu 10.10, i thought it was my pendrive's fault. when i tried to run it in my windows 7, it ran without errors...then i decided to backup its data and reformat it. While reformatting it, i changed my settings to format in default one(by clicking "Restore Device Defaults")...and then tried on ubuntu 10.10, it worked...my luck i guess....you can try that as well....goodluck

Regards,WinuxUser

---

### Post by Wim Sturkenboom on 2011-09-08
> **salemeni said:**
> Do
```
$sudo mount /dev/sdc1 /mnt 
```
Please note that OP does not get that far. Those were my results and there it works ;)

---

### Post by Ikmal2129 on 2011-09-08
> **mörgæs said:**
> You need to give ALL the details you can possible think of, if we should be able to help:

[LIST]
[*]Complete hardware description
[*]Which software (does this also apply to newer Ubuntus?)
[*]Can't you read any USB sticks at all, or is this about one particular USB stick?
[*]Which make of USB stick are we talking of?
[*]Can the stick(s) be read from other computers?
[*]Test you have done to isolate the problem
[*]And so on
[*]And so on
[/LIST]


1.I use hp mini 110-3012tu.
2.My broadand,bluetooth n headset work perfectly.
3.The pendrive not problem n can run on another computer.

---

