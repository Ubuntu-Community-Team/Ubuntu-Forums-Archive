---
title: "Cannot print with cups."
date: 2006-06-19
forum: General Help
---

### Post by zwastik on 2006-06-19
I am having some problems with my Canon LBP3200 printer, it doesn't print at all.

```
/var/log/cups/error_log
E [19/Jun/2006:10:21:27 -0400] PID 7102 (/usr/lib/cups/backend/ccp) stopped with status 1!
E [19/Jun/2006:10:21:27 -0400] [Job 7] Can't open FIFO: Permission denied
E [19/Jun/2006:10:22:10 -0400] Resume-Printer: Unauthorized
```

```
lpstat -t
connection type for LBP3200: ccp:/var/ccpd/fifo0
```

```
ls -l /usr/lib/cups/backend
total 60
-rwxr-xr-x 1 root root  7199 2006-04-11 19:39 beh
-rwxr-xr-x 1 root root 10300 2006-05-03 16:41 canon
-rwxr-xr-x 1 root root  5608 2006-02-13 21:13 ccp
-rwxr-xr-x 1 root root 10308 2006-05-03 16:41 epson
-rwxr-xr-x 1 root root 18416 2006-04-27 08:40 hp
lrwxrwxrwx 1 root root     3 2006-06-16 07:46 http -> ipp
lrwxrwxrwx 1 root root    24 2006-06-16 07:46 ipp -> ../backend-available/ipp
lrwxrwxrwx 1 root root    24 2006-06-16 07:46 lpd -> ../backend-available/lpd
lrwxrwxrwx 1 root root    29 2006-06-16 07:46 parallel -> ../backend-available/parallel
lrwxrwxrwx 1 root root    21 2006-06-16 07:46 smb -> ../../../bin/smbspool
lrwxrwxrwx 1 root root    27 2006-06-16 07:46 socket -> ../backend-available/socket
lrwxrwxrwx 1 root root    24 2006-06-16 07:46 usb -> ../backend-available/usb
```

```
sudo /usr/lib/cups/backend/ccp
direct ccp:/var/ccpd/fifo0 "Unknown" "Canon Priter Daemon Port#1"
direct ccp:/var/ccpd/fifo1 "Unknown" "Canon Priter Daemon Port#2"
direct ccp:/var/ccpd/fifo2 "Unknown" "Canon Priter Daemon Port#3"
direct ccp:/var/ccpd/fifo3 "Unknown" "Canon Priter Daemon Port#4"
direct ccp:/var/ccpd/fifo4 "Unknown" "Canon Priter Daemon Port#5"
direct ccp:/var/ccpd/fifo5 "Unknown" "Canon Priter Daemon Port#6"
direct ccp:/var/ccpd/fifo6 "Unknown" "Canon Priter Daemon Port#7"
direct ccp:/var/ccpd/fifo7 "Unknown" "Canon Priter Daemon Port#8"
```

```
sudo /usr/sbin/ccpdadmin
Usage:
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]

 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 39787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path   : Status
 ----------------------------------------------------------------------------
     [0]    : LBP3200   : ccp           : /var/ccpd/fifo0       : /dev/usblp0   :
```

```
lsusb
Bus 002 Device 002: ID 04a9:2636 Canon, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Printer drivers: (used alien -c)
> cndrvcups-capt-1.3x-x.i386.rpm : rpm file of the CAPT printer driver module
cndrvcups-common-1.3x-x.i386.rpm : rpm file of a common module for CUPS drivers



Thanks for reading, ubuntu rulz ;-)

---

### Post by ulefr01 on 2006-10-01
I have the same problem.
Have you a solutions for this problem ?
Thanks

---

### Post by PointSource on 2008-01-27
Try reinstalling the cupsys deb package:
```
sudo dpkg -i /var/cache/apt/archives/cupsys_{INSERT_VERSION_HERE}_i386.deb
```
Apart from that, open it up as an archive and copy the cupsd.conf file from ./etc/cups/ in the data.tar.gz file in it.
That's what worked for me.

---

