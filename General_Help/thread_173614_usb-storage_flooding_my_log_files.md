---
title: "usb-storage flooding my log files"
date: 2006-05-10
forum: General Help
---

### Post by kingcharles1666 on 2006-05-10
Hi,
Yesterday I was unable to start ubuntu because I had 0 disk space left. The system came back with a warning that the disk was full and that was it. I managed to get to the hard drive and found 6 gig log files (syslog, kern and debug) I deleted them and this allowed me to get back into my system. But right now I am watching them grow by the minute (about 0.1MB per 3 seconds).

all three logs are flooded by the same messages see below:

[PHP]May 10 08:07:15 localhost kernel: [ 1542.875174] usb-storage: *** thread awakened.
May 10 08:07:15 localhost kernel: [ 1542.875176] usb-storage: Command TEST_UNIT_READY (6 bytes)
May 10 08:07:15 localhost kernel: [ 1542.875178] usb-storage:  00 20 00 00 00 00
May 10 08:07:15 localhost kernel: [ 1542.875182] usb-storage: Bulk Command S 0x43425355 T 0x624b L 0 F 0 Trg 0 LUN 1 CL 6
May 10 08:07:15 localhost kernel: [ 1542.875185] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
May 10 08:07:15 localhost kernel: [ 1542.875713] usb-storage: Status code 0; transferred 31/31
May 10 08:07:15 localhost kernel: [ 1542.875715] usb-storage: -- transfer complete
May 10 08:07:15 localhost kernel: [ 1542.875717] usb-storage: Bulk command transfer result=0
May 10 08:07:15 localhost kernel: [ 1542.875719] usb-storage: Attempting to get CSW...
May 10 08:07:15 localhost kernel: [ 1542.875721] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
May 10 08:07:15 localhost kernel: [ 1542.875850] usb-storage: Status code 0; transferred 13/13
May 10 08:07:15 localhost kernel: [ 1542.875852] usb-storage: -- transfer complete
May 10 08:07:15 localhost kernel: [ 1542.875853] usb-storage: Bulk status result = 0
May 10 08:07:15 localhost kernel: [ 1542.875856] usb-storage: Bulk Status S 0x53425355 T 0x624b R 0 Stat 0x1
May 10 08:07:15 localhost kernel: [ 1542.875859] usb-storage: -- transport indicates command failure
May 10 08:07:15 localhost kernel: [ 1542.875861] usb-storage: Issuing auto-REQUEST_SENSE
May 10 08:07:15 localhost kernel: [ 1542.875864] usb-storage: Bulk Command S 0x43425355 T 0x624c L 18 F 128 Trg 0 LUN 1 CL 6
May 10 08:07:15 localhost kernel: [ 1542.875867] usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
May 10 08:07:15 localhost kernel: [ 1542.876266] usb-storage: Status code 0; transferred 31/31
May 10 08:07:15 localhost kernel: [ 1542.876268] usb-storage: -- transfer complete
May 10 08:07:15 localhost kernel: [ 1542.876270] usb-storage: Bulk command transfer result=0
May 10 08:07:15 localhost kernel: [ 1542.876272] usb-storage: usb_stor_bulk_transfer_buf: xfer 18 bytes
May 10 08:07:15 localhost kernel: [ 1542.876404] usb-storage: Status code 0; transferred 18/18
May 10 08:07:15 localhost kernel: [ 1542.876406] usb-storage: -- transfer complete
May 10 08:07:15 localhost kernel: [ 1542.876408] usb-storage: Bulk data transfer result 0x0
May 10 08:07:15 localhost kernel: [ 1542.876410] usb-storage: Attempting to get CSW...
May 10 08:07:15 localhost kernel: [ 1542.876412] usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
May 10 08:07:15 localhost kernel: [ 1542.876473] usb-storage: Status code 0; transferred 13/13
May 10 08:07:15 localhost kernel: [ 1542.876475] usb-storage: -- transfer complete
May 10 08:07:15 localhost kernel: [ 1542.876477] usb-storage: Bulk status result = 0
May 10 08:07:15 localhost kernel: [ 1542.876480] usb-storage: Bulk Status S 0x53425355 T 0x624c R 0 Stat 0x0
May 10 08:07:15 localhost kernel: [ 1542.876482] usb-storage: -- Result from auto-sense is 0
May 10 08:07:15 localhost kernel: [ 1542.876485] usb-storage: -- code: 0xf0, key: 0x2, ASC: 0x3a, ASCQ: 0x0
May 10 08:07:15 localhost kernel: [ 1542.876488] usb-storage: Not Ready: Medium not present
May 10 08:07:15 localhost kernel: [ 1542.876490] usb-storage: scsi cmd done, result=0x2
May 10 08:07:15 localhost kernel: [ 1542.876492] usb-storage: *** thread sleeping.
[/PHP]

The same message over and over.

I tried to kill the usb-storage process but it does not work. I tried to reinstall with synaptic but I cannot select the package.

Anybody got any ideas?

Many Thanks,

Charles (the linux NOOB)

---

### Post by kingcharles1666 on 2006-05-10
Anyone??

---

### Post by kingcharles1666 on 2006-05-13
bump

---

### Post by kingcharles1666 on 2006-05-18
another bump

---

### Post by kingcharles1666 on 2006-05-30
Hi, I am becoming a bit frustrated with this problem. I have tried everything but I cannot solve it. Is there really nobody out there that can shed some light on this problem?

---

### Post by dcstar on 2006-06-16
[QUOTE=kingcharles1666]Hi, I am becoming a bit frustrated with this problem. I have tried everything but I cannot solve it. Is there really nobody out there that can shed some light on this problem?[/QUOTE]
I believe the default Ubuntu Kernels are created with a "USB Mass Storage verbose debug" option set on.

I am just about to build a new kernel for myself with this switched off as I have the exact same problem, I'll try and let you know what the outcome is.

---

### Post by dcstar on 2006-06-16
[QUOTE=dcstar]I believe the default Ubuntu Kernels are created with a "**USB Mass Storage verbose debug**" option set on.

I am just about to build a new kernel for myself with this switched off as I have the exact same problem, I'll try and let you know what the outcome is.[/QUOTE]
Well guess what?

Now I **DO NOT** get my log files filled with usb-storage messages!!

I have just checked the latest official Dapper kernel, and it seems that it is switched off in that one - so I would recommend updating your kernel (or upgrading to Dapper).

---

### Post by kingcharles1666 on 2006-06-18
Thanks David, problem solved!

---

