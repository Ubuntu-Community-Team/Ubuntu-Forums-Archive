---
title: "A whole bunch of /dev/sr0 errors on startup. How bad could it be?"
date: 2010-06-23
forum: General Help
---

### Post by fadey on 2010-06-23
Hi, everyone

On system startup I get a whole bunch of this:

```


[   10.218885] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   10.218891] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   10.218896] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   10.218901] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   10.218911] end_request: I/O error, dev sr0, sector 0
[   10.218979] Buffer I/O error on device sr0, logical block 0

```

I can see it in dmesg output after. Just was wondering if this was a dangerous error.

---

### Post by happyhamster on 2010-06-23
It likely means that your dvd-drive won't work correctly. It's a common bug on Lucid for dvd-drives with a sata connection (several Samsung models for example). See:
[https://bugs.launchpad.net/ubuntu/lucid/+source/udev/+bug/554433](https://bugs.launchpad.net/ubuntu/lucid/+source/udev/+bug/554433)

---

### Post by mc4man on 2010-06-23
If you are booting up with media in the drive then those messages are quite normal.

(generally are anyway - 
from inserting audio cd or blank media

> doug@doug-laptop:~$ dmesg |tail
[ 2197.583035] Info fld=0x0
[ 2197.583043] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 2197.583059] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 2197.583094] end_request: I/O error, dev sr0, sector 0
[ 2197.587249] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2197.587255] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2197.587260] Info fld=0x0
[ 2197.587262] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 2197.587268] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 2197.587281] end_request: I/O error, dev sr0, sector 0

from inserting dvd (movie
> doug@doug-laptop:~$ dmesg |tail
[ 2197.583059] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 2197.583094] end_request: I/O error, dev sr0, sector 0
[ 2197.587249] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2197.587255] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2197.587260] Info fld=0x0
[ 2197.587262] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 2197.587268] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 2197.587281] end_request: I/O error, dev sr0, sector 0
[ 2317.377029] UDF-fs: Partition marked readonly; forcing readonly mount
[ 2317.416337] UDF-fs INFO UDF: Mounting volume 'RATATOUILLE', timestamp 2007/08/31 02:08 (1f10)

---

### Post by fadey on 2010-06-24
Ooops. I'm booting without CD inside. And that's actualy true. My cdrom does not work.

---

### Post by skaramanger on 2010-06-25
I get the same error messages.  I boot with no media in the drive and it is an IDE unit.

---

