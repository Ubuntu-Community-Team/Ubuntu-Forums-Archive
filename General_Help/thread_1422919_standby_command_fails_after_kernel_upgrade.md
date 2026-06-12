---
title: "standby command fails after kernel upgrade"
date: 2010-03-05
forum: General Help
---

### Post by petru.marginean on 2010-03-05
Hi,

After upgrading the kernel I cannot issue anymore the standby command for external hard drive Western Digital Element 1TB:

```
$> sudo hdparm -y /dev/sdd

/dev/sdd:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Invalid exchange
```The command above works fine in the 2.6.31-16-generic, but it fails in any of the newer versions:
- 2.6.31-17-generic
- 2.6.31-19-generic
- 2.6.31-20-generic

I've checked the /var/log/messages, but I cannot see any message while executing the command.

Please help,
Petru
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321"]
[/URL]

---

### Post by Intrepid Ibex on 2010-03-06
Maybe it (the external device) already is in that (standby) mode? Can you check out with: ```
sudo hdparm -C /dev/sdd
```

---

### Post by petru.marginean on 2010-03-07
Thanks for reply.
I've rebooted with the new kernel, and executed the command, and got strange results: it first the status was 
"active/idle", and after I've executed the command that fails, the status was... "unknown".

```
$> uname -r
2.6.31-20-generic

$> sudo hdparm -C /dev/sdd
/dev/sdd:
 drive state is:  active/idle

$> sudo hdparm -y /dev/sdd
/dev/sdd:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Invalid exchange

$> sudo hdparm -C /dev/sdd
/dev/sdd:
 drive state is:  unknown
```
Petru

---

### Post by petru.marginean on 2010-05-05
Any idea why this fails?

I'm stuck with the 2.6.31-16-generic version of the kernel; any newer version fails to put the external harddrive to sleep (the last one I've tried is 2.6.32.22).

```
$> sudo hdparm -y /dev/sdd

/dev/sdd:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Invalid exchange
```Regards,
Petru

---

### Post by petru.marginean on 2012-07-17
This still fails in 3.2.0 kernel (even the error message is slightly different):
```

$> sudo hdparm -y /dev/sdd

/dev/sdd:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Invalid argument

$> uname -a
Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 
UTC 2012 i686 i686 i386 GNU/Linux

```Regards,
PM

---

### Post by petru.marginean on 2012-07-17
The status of the drive is "unknown"

```
$> sudo hdparm -C /dev/sdd

/dev/sdd:
 drive state is:  unknown
```

Regards,
Petru

---

