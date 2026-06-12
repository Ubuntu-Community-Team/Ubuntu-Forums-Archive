---
title: "Can't mount USB pen!"
date: 2009-11-05
forum: General Help
---

### Post by JohnnyGo on 2009-11-05
First of all, HI! (My first post:p)

I'm not sure if this is the right place to ask, but i have a problem with a usb pen of mine, as the computer isn't able to mount the device. This happen like a week or so when i was trying to format my usb pen...

Can anyone help? I really needed this pen...

---

### Post by alphaniner on 2009-11-05
Does it work on other computers?

If not, it probably isn't formatted.  The easiest solution in this case is to install gparted, a graphical partitioning and formatting tool.

---

### Post by JohnnyGo on 2009-11-05
The problem is that i have tried with gparted, and the pen doesn't even appear there...

---

### Post by soni1770 on 2009-11-05
oh.
um,mm

---

### Post by alphaniner on 2009-11-05
> **JohnnyGo said:**
> The problem is that i have tried with gparted, and the pen doesn't even appear there...

Are you 100% sure?  There is a menu in the top right (I think, I don't use gParted) that allows you to select the device.

Otherwise, you're gonna have to dive into the terminal.  Please post the output of the following commands, **immediately after plugging in the pen**:

```
tail /var/log/syslog
sudo fdisk -l
```

---

### Post by JohnnyGo on 2009-11-05
It came out like this:

:~$tail /var/log/syslog
Nov  5 16:17:24 iesktop kernel: [ 5779.642634] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 492
Nov  5 16:17:56 iesktop kernel: [ 5812.193589] DeQueueRunning[0]= TRUE!
Nov  5 16:19:24 iesktop kernel: [ 5899.645222] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 412
Nov  5 16:20:01 iesktop /USR/SBIN/CRON[5757]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  5 16:20:52 iesktop kernel: [ 5988.435662] usb 1-1: USB disconnect, address 4
Nov  5 16:20:55 iesktop kernel: [ 5991.100037] usb 1-1: new high speed USB device using ehci_hcd and address 5
Nov  5 16:20:55 iesktop kernel: [ 5991.233372] usb 1-1: configuration #1 chosen from 1 choice
Nov  5 16:20:55 iesktop kernel: [ 5991.233706] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  5 16:20:55 iesktop kernel: [ 5991.233931] usb-storage: device found at 5
Nov  5 16:20:55 iesktop kernel: [ 5991.233935] usb-storage: waiting for device to settle before scanning
:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefb0efb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16924   135941998+   7  HPFS/NTFS
/dev/sda2           16925       19457    20346322+   f  W95 Ext'd (LBA)
/dev/sda5           17251       19457    17727696   83  Linux
/dev/sda6           16925       17250     2618532   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by kyuubi777 on 2009-11-05
when i was running x86 10.5.2 on my machine i ran into usb issues, but found that if i booted up with a flash drive in one of the ports it would always recognize it...
can't hurt to try it.

---

### Post by JohnnyGo on 2009-11-05
Ok, i'll try that...

It appears the same...

---

### Post by kyuubi777 on 2009-11-05
damn... oh well, here's a discussion on the subject. it seems they have a temp fix

[http://ohioloco.ubuntuforums.org/showthread.php?t=1307542&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=1307542&page=2)

waiting to hear what alphaniner says @ the moment based off your output

---

### Post by alphaniner on 2009-11-05
Things didn't finish configuring when you ran the commands.  That's my fault, I shouldn't have said to run them immediately.   What I meant to say was don't do anything else in between plugging in the pen and running the commands.

Good news is, there's enough info from the first command to show that the pen isn't completely borked or anything.

Please run the commands again, but this time about 10 seconds after plugging in the pen.

---

### Post by JohnnyGo on 2009-11-05
:~$ tail /var/log/syslog
Nov  5 16:39:35 iesktop kernel: [  766.961575] sd 5:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
Nov  5 16:39:35 iesktop kernel: [  766.961582] end_request: I/O error, dev sdb, sector 0
Nov  5 16:39:37 iesktop kernel: [  768.920477] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  5 16:39:37 iesktop kernel: [  768.920485] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current] 
Nov  5 16:39:37 iesktop kernel: [  768.920491] sd 5:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
Nov  5 16:39:37 iesktop kernel: [  768.920498] end_request: I/O error, dev sdb, sector 0
Nov  5 16:39:37 iesktop kernel: [  768.929604] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  5 16:39:37 iesktop kernel: [  768.929613] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current] 
Nov  5 16:39:37 iesktop kernel: [  768.929621] sd 5:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
Nov  5 16:39:37 iesktop kernel: [  768.929632] end_request: I/O error, dev sdb, sector 0

:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefb0efb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16924   135941998+   7  HPFS/NTFS
/dev/sda2           16925       19457    20346322+   f  W95 Ext'd (LBA)
/dev/sda5           17251       19457    17727696   83  Linux
/dev/sda6           16925       17250     2618532   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by alphaniner on 2009-11-05
Maybe I spoke too soon:

```
Nov 5 16:39:37 iesktop kernel: [ 768.929604] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 5 16:39:37 iesktop kernel: [ 768.929613] sd 5:0:0:0: [sdb] Sense Key : Medium Error [current]
Nov 5 16:39:37 iesktop kernel: [ 768.929621] sd 5:0:0:0: [sdb] Add. Sense: Cannot read medium - incompatible format
Nov 5 16:39:37 iesktop kernel: [ 768.929632] end_request: I/O error, dev sdb, sector 0
```

These errors, combined with the fact that **sudo fdisk -l** doesn't have an entry for the pen, suggest that there is something wrong with the pen itself.  It could also be the USB port or some other hardware issue, but it seems unlikely.  If you haven't already, try plugging it into another port or try another pen if you have one handy.  But I think the pen maybe toast.

One last thing to try, when the pen is plugged in (give it 10 seconds again) do
```

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
sudo fdisk -l
```

---

### Post by JohnnyGo on 2009-11-05
Ok, thanks for the help anyways!

Trying now...

It came out like this:

:~$ sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
dd: writing `/dev/sdb': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0101156 s, 0.0 kB/s
:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefb0efb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16924   135941998+   7  HPFS/NTFS
/dev/sda2           16925       19457    20346322+   f  W95 Ext'd (LBA)
/dev/sda5           17251       19457    17727696   83  Linux
/dev/sda6           16925       17250     2618532   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by alphaniner on 2009-11-05
Yeah, unless another known good pen malfunctions in the same way, I'd say that one is toast.

---

### Post by JohnnyGo on 2009-11-05
Ok, then i guess it really is toast...i've tried another one int he same usb port and it worked well...

Thanks for the help!

---

