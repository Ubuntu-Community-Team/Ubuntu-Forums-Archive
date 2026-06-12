---
title: "cannot start Mondo"
date: 2011-04-24
forum: General Help
---

### Post by makoshark55 on 2011-04-24
I have installed mondoarchive from the Ubuntu software center on my Ubuntu 10.04 LTS but cannot seam to get it to start. I have tried From root terminal 'mondoarchive' and 'mondobackup'. I have tried sudo 'mondo' from terminal and have had no luck I get either error -1 terminal or not found in root terminal. Can someone tell me the secret to get it to work. I want to backup to dvd's
the terminal says```
root@james-desktop:/home/james# mondoarchive
Initializing...
Execution run ended; result=-1
Type 'less /var/log/mondoarchive.log' to see the output log
root@james-desktop:/home/james# 

```I have looked at the log file but I don't know what it means> [TH=19869] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=19869] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=19869] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.LYOb2G for Mondo.
    [TH=19869] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=19869] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=19916] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=19916] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=19916] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.1wf72V for Mondo.
    [TH=19916] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=19916] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=19954] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=19954] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=19954] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.720FN8 for Mondo.
    [TH=19954] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=19954] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=19976] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=19976] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=19976] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.QGhhWY for Mondo.
    [TH=19976] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=19976] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=20047] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=20047] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=20047] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.UtqjJA for Mondo.
    [TH=20047] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=20047] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=20141] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=20141] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=20141] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.dxTFBB for Mondo.
    [TH=20141] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=20141] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=24523] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=24523] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=24523] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.qE3E0p for Mondo.
    [TH=24523] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=24523] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=23466] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=23466] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
    [TH=23466] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /2%/mondo.tmp.csYzux for Mondo.
    [TH=23466] libmondo-files.c->register_pid#815: Unregistering PID
    [TH=23466] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256

---

### Post by David Beasley on 2011-08-07
Hi, wish I had found your post sooner, it would have saved me a whole day.. ended up with the same result as yourself..
I put it down to being new and just not knowing how stuff works..
Linux is very likable, but I am still a little blown away that some of the all time basic bits of that "other" operating system dont seem to be available for Linux users, either as freeware or commercially.
A simple disk image program that doesnt require a knowledge of command line inputs is a must for a new Linux user, so how come it is so hard to find??
If ever anyone is likely to screw things up it is when they dont really understand the op system.
Just wondering if you managed to find anything that has a GUI and actually works.. for me the search goes on..

Regards

DB

---

