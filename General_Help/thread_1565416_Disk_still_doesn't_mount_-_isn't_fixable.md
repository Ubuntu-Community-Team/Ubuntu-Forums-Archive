---
title: "Disk still doesn't mount - isn't fixable?"
date: 2010-08-31
forum: General Help
---

### Post by MacUsers on 2010-08-31
Hi guys,
I'm on 10.04 mini-installation. I thought my last drive was broken but the same thing is happening to another one as well. ***lshw -C disk*** outputs this:
```
 *-cdrom
       description: DVD writer
       product: CD/DVDW SH-W163A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS01
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```Which is perfectly alright, I think. But, whenever I put a disk in the drive I see this in the ***dmesg***:
```
[ 1168.015443] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1168.015449] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1168.015455] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 1168.015463] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[ 1168.015475] end_request: I/O error, dev sr0, sector 4096
[ 1168.015479] Buffer I/O error on device sr0, logical block 512
```Searching Google didn't get me any answer but a number of people appeared to be suffering from this. So, anyone out here seeing this too? I really appreciate some input/comment on this. Thanks in advance. Cheers!!

---

### Post by MacUsers on 2010-09-01
This thing is driving me crazy. I tried with another two drive, all with the very same result. Does every  Lucid (Ubuntu 10.04.1 LTS) owner experiencing the same or is it just me alone down the stream? Cheers!!

---

### Post by dino99 on 2010-09-01
install mountmanager to deal with partitions and devices: set the preferences into : system admin mountmanager (after installation indeed :))

---

### Post by MacUsers on 2010-09-01
> **dino99 said:**
> install mountmanager to deal with partitions and devices: set the preferences into : system admin mountmanager (after installation indeed :))I don't have any window manager installed, but mountmanager needs one to run, I assume. Is there any equivalent CLI thing for that? Cheers!!

---

### Post by shashikasaragodu on 2010-09-14
[SIZE="4"][/SIZE][FONT="Book Antiqua"][FONT="Arial"][FONT="System"][FONT="System"][SIZE="6"][SIZE="7"][FONT="Verdana"][FONT="System"][FONT="Arial Narrow"][FONT="Book Antiqua"][FONT="Arial"][FONT="Tahoma"][FONT="System"][SIZE="5"][SIZE="4"][FONT="Arial"][SIZE="4"][FONT="Arial"][SIZE="4"][FONT="Verdana"][SIZE="4"][SIZE="2"]dear fellow ubuntuers,
last week i wrote my over 40 gb data to dvd's. k3b had failure messages, leaving some hope, the disk might still be readable, i double checked before erasing the data from  my hard disk. i could open all the dvd's soon after burning. now i am not able to open any of the disks. i am on lucid in dell inspiron 1545, with TSSTcorp make Drive. Does this problem have anything to do with OS, Disk Drive, or my data are never going to be recovered?[/SIZE][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/SIZE][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/SIZE][/SIZE][/FONT][/FONT][/FONT][/FONT]
;)

---

