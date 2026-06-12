---
title: "Can't records CDs with 9.10"
date: 2010-01-05
forum: General Help
---

### Post by mart78 on 2010-01-05
Hello,

I just tried to record a CD (standard data cd) with Brasero first and then with GnomeBaker and it failed both times right as it started to write with following error:

```
Unable to mount mydisc
Error mounting: mount exited with exit code 1: helper failed with:
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
```

The errorlog from GnomeBaker says:

```
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 01 B2 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 888832 bytes
Writing  time:   17.440s
Average write speed 221.2x.
Fixating...
Fixating time:   19.148s
wodim: fifo had 206 puts and 15 gets.
wodim: fifo was 0 times empty and 5 times full, min fill was 97%.

```

I already tried without burnfree but that didn't help either. Anyone know what the problem might be. It might be that the cdwriter is defective as I never tried it before (pretty new Dell workstation) but somehow I don't think so.

Thx.

---

### Post by labinnsw on 2010-01-12
[http://ubuntuforums.org/showthread.php?t=1330191]("http://ubuntuforums.org/showthread.php?t=1330191")

This post deals with the same error caused by a hard disk.
In your case, looks like you need to make the directory "cdrom0"

So:

1. Change to command line view CTRL+ALT+F6 (or you could just open a terminal. If you use a terminal, just put "sudo" in front of the commands)
2. Login as root
3. Type:
```
mount /dev/sr0 /media/cdrom0
```

(You should get the same error as you did)

Create the folder manually

```
mkdir /media/cdrom0
```

and try again

```
mount /dev/sr0 /media/cdrom0
```

exit and return to the Gnome environment CTRL+ALT+F7

---

