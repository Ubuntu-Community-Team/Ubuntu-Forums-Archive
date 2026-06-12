---
title: "USB pen drive unreadable"
date: 2010-05-29
forum: General Help
---

### Post by axelsvag on 2010-05-29
I try to use a usb pen drive. The usb pen drive show up under computer but not like a drive in geparted. When I look in the log file I find the drive ```
May 29 10:11:46 CQ60 kernel: [  112.942602] scsi 6:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2

```

I do not know what this mean but it looks like the drive show up like a scsi and not usb or?

I need a clue to get it work like a normal usb device

---

### Post by -humanaut- on 2010-05-29
Sounds like its locked to me. Have you had it on your or any other machine recently and didn't properly unmount it?

---

### Post by axelsvag on 2010-05-30
That is possible, Is there anything to do or does it have to go to the dustbin?

---

### Post by lmarmisa on 2010-05-30
Type this command with the pen drive disconnected:

> 
ls -l /media


---

### Post by axelsvag on 2010-06-11
OK, I will try it this weekend

---

