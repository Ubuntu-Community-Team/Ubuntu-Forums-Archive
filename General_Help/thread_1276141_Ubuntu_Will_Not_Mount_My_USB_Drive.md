---
title: "Ubuntu Will Not Mount My USB Drive"
date: 2009-09-26
forum: General Help
---

### Post by poolcue2002 on 2009-09-26
I'm running the newest version of Ubuntu and it will not let me mount my usb drive. I get the message "Invalid Mount Option When Attempting To Mount The Volume".


someone told me to go to terminal and type in dmesg | tail     and when i do i got this...

[ 4493.844547] hdc: drive not ready for command
[ 4493.844588] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 4493.844594] ide: failed opcode was: unknown
[ 4493.844599] hdc: drive not ready for command
[ 4493.844660] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 4493.844666] ide: failed opcode was: unknown
[ 4493.844671] hdc: drive not ready for command
[ 4493.844724] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 4493.844730] ide: failed opcode was: unknown
[ 4493.844734] hdc: drive not ready for command


If anyone has any advice or can tell me what to do i would be more than grateful.. Thanks!

---

### Post by wojox on 2009-09-26
Newest version being Karmic Alpha or Jaunty? How are you mounting it? What does this produce:

```
lsusb
```

---

### Post by bodyharvester on 2009-09-26
if its karmic it may be a bug to report, jaunty however there will be a way known here

heres some more code to try:

code
```
sudo fdisk -l
```

does it still give details of your usb?

---

### Post by scouser73 on 2009-09-26
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

