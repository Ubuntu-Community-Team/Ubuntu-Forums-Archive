---
title: "cannot read tar files from tape after 9.10  upgrade"
date: 2010-03-23
forum: General Help
---

### Post by PicselTech on 2010-03-23
After upgrading our backup tape server from 8.04LTS to 9.10 I can no longer read back data from the old tapes.

We use a home grown script which writes to the tape using the "tar" command

I have tracked the problem down to a change in the maximum block size that can be passed to the tar command.

previously we used the command:
[FONT=Courier New]tar -cb 2048 -f /dev/nst0 data-to-backup
[/FONT]
We came to the value of 2048 after various experiments as this gave us  the best throughput to the tape drive.[FONT=Courier New]
[/FONT]
[FONT=Verdana]Now when I try and read back the old tapes[/FONT] I get an error:
[FONT=Courier New]$ tar -xvb 2048 -f /dev/nst0
tar: /dev/nst0: Cannot read: Input/output error
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
[/FONT]

I have found that when writing a new tape, the maximum block size that I can use is 1024.

If I try and use a block size of 1024 to read the old tapes I get this error:
[FONT=Courier New]$ tar -xvb 2048 -f /dev/nst0
tar: /dev/nst0: Cannot read: Cannot allocate memory

[FONT=Verdana]I have tried searching on the internet, and trying different settings with mt.
Also tried using "dd" to read the tape with different block sizes, but all failed.

Does anyone know what I need to do to be able to read my old backup tapes ?
[/FONT]
----------------------
[FONT=Verdana]Server Hardware: Dell PE1950
[FONT=Courier New]$ uname -a
Linux backup-server 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux[/FONT]

Tape Hardware: Quantum SDLT600 with auto-loader
(from /proc/scsi/scsi)
[FONT=Courier New]Host: scsi4 Channel: 00 Id: 04 Lun: 00
  Vendor: QUANTUM  Model: SDLT600          Rev: 3333
  Type:   Sequential-Access                ANSI  SCSI revision: 04
Host: scsi4 Channel: 00 Id: 04 Lun: 01
  Vendor: QUANTUM  Model: UHDL             Rev: 0054
  Type:   Medium Changer                   ANSI  SCSI revision: 02
[/FONT]
[/FONT]($ mt -f /dev/nst0 status)
SCSI 2 tape drive:
File number=2, block number=2, partition=0.
Tape block size 0 bytes. Density code 0x4a (no translation).
Soft error count since last status=0
General status bits on (1010000):
 ONLINE IM_REP_EN

(ls -l /dev/nst0)
crw-rw---- 1 root tape 9, 128 2010-03-22 11:30 /dev/nst0

[FONT=Verdana](output from dmesg)[/FONT]
[   84.007408] st 4:0:4:0: Attached scsi tape st0
[   84.007412] st 4:0:4:0: st0: try direct i/o: yes (alignment 4 B)
[   84.012116] osst :I: Tape driver with OnStream support version 0.99.4
[   84.012118] osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
[ 1275.525046] st0: Block limits 4 - 16777212 bytes.

[FONT=Verdana]( messages in dmesg when read failed)[/FONT]
[93072.119145] st0: Failed to read 1048576 byte block with 524288 byte transfer.[/FONT][FONT=Courier New]
[/FONT]

---

### Post by cjhabs on 2010-03-23
What block size did you try with dd?
It should be 1048576

---

### Post by PicselTech on 2010-03-24
I have found that booting into an older kernel (2.6.27-17-server) which is still installed on the server, I can read the tape with a blocking factor of 2048 as before the upgrade.

I'm not a kernel guru, but I guess something has changed in there somewhere.

Does anyone know how I can find out what the magic variable is (from sysctl -a) which controls the block size and if I can change it by editing /etc/sysctl.conf or add something in /etc/sysctl.d/

---

### Post by PicselTech on 2010-03-25
The "st" driver is loaded into the kernel as a module, but none of the "param" options listed by modinfo seem to be appropriate :(
(the modinfo output from the 2.6.27 kernel has exactly the same "param"s)

# modinfo st
filename:       /lib/modules/2.6.31-20-generic-pae/kernel/drivers/scsi/st.ko
alias:          scsi:t-0x01*
alias:          char-major-9-*
license:        GPL
description:    SCSI tape (st) driver
author:         Kai Makisara
srcversion:     9511B91409CB23FB3BCD70B
depends:        
vermagic:       2.6.31-20-generic-pae SMP mod_unload modversions 586 
parm:           buffer_kbs:Default driver buffer size for fixed block mode (KB; 32) (int)
parm:           max_sg_segs:Maximum number of scatter/gather segments to use (256) (int)
parm:           try_direct_io:Try direct I/O between user buffer and tape drive (1) (int)
parm:           try_rdio:Try direct read i/o when possible (int)
parm:           try_wdio:Try direct write i/o when possible (int)

---

