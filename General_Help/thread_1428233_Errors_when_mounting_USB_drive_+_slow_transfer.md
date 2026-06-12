---
title: "Errors when mounting USB drive + slow transfer"
date: 2010-03-12
forum: General Help
---

### Post by Elwro on 2010-03-12
Hello,

this afternoon I noticed my external USB HDD was working very slowly. Even listing a directory via nautilus takes a good few seconds! This is the output of dmesg | tail:
```
$ dmesg | tail
[ 3890.626170] sd 11:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 3890.626179] sd 11:0:0:0: [sdc] Add. Sense: Unrecovered read error
[ 3890.626189] end_request: I/O error, dev sdc, sector 6442360
[ 3890.626200] Buffer I/O error on device sdc1, logical block 805039
[ 3893.193152] sd 11:0:0:0: [sdc] Unhandled sense code
[ 3893.193162] sd 11:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3893.193170] sd 11:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 3893.193179] sd 11:0:0:0: [sdc] Add. Sense: Unrecovered read error
[ 3893.193188] end_request: I/O error, dev sdc, sector 6442360
[ 3893.193199] Buffer I/O error on device sdc1, logical block 805039

```

There are lots of these "Unrecovered read errors" and "Unhandled sense codes" in /var/log/syslog.

Could anyone suggest what the problem is and how to get to fixing it?

("lcdusb -v" says the "bcdUSB" is "2.0", so I guess the disk presumably does mount as USB 2.0 and not 1.1)

When the drive is mounted (manually or not), it takes a long while for its icon to appear on the desktop. This is puzzling, because (which I forgot to initially add) there is a small partition on the drive ("WD Smartware"; this is a WD 1 TB external HDD) which mounts without any problems and its icon appears immediately.

Still, "ls" works fast, while nautilus takes a looong time to display the folders. Strange. And how fast should my transfers really be? I'm not really sure not whether they are too slow. Maybe it's only some kind of nautilus blunder?

edit: the drive seems to be working fine under Windows XP. Its format is NTFS.

BUT System -> Administration -> Disk Utility shows it has "a few bad sectors". The self-test failed. I'll try to run chkdsk from Windows now.

edit2: I'm sorry, there's a hardware issue. Chkdsk is now (and will be for 10 hours) searching for bad sectors, but has already found problems elsewhere. Grrr, an almost new drive.

edit3: SORRY, MOVE ALONG, NOTHING (for you) TO WORRY ABOUT HERE. After chkdsk fixed the errors from the first 3 phases of checking (before it even got to scanning for bad sectors), I got some files back I didn't even know I had lost and the disk now works fine in Ubuntu.

---

