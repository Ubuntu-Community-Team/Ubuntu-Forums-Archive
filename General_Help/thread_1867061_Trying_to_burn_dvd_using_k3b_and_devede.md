---
title: "Trying to burn dvd using k3b and devede"
date: 2011-10-22
forum: General Help
---

### Post by newellj79 on 2011-10-22
I'm using devede to convert .avi to .iso and then k3b to burn the .iso to a dvd.   Everything looked good and then it stopped.  This is the end of the log where it went wrong?  Can someone help?  Thanks...

 p, li { white-space: pre-wrap; }  [FONT=Monospace]rack 02: 3266 of 3268 MB written (fifo 100%) [buf  96%]   4.2x.[/FONT]
 [FONT=Monospace]Track 02: 3267 of 3268 MB written (fifo 100%) [buf  93%]   4.0x.[/FONT]
 [FONT=Monospace]Track 02: 3268 of 3268 MB written (fifo 100%) [buf  93%]   4.2x.[/FONT]
 [FONT=Monospace]Track 02: Total bytes read/written: 3427059712/3427059712 (1673369 sectors).[/FONT]
 [FONT=Monospace]Writing  time:  672.331s[/FONT]
 [FONT=Monospace]Average write speed   3.7x.[/FONT]
 [FONT=Monospace]Min drive buffer fill was 90%[/FONT]
 [FONT=Monospace]Fixating...[/FONT]
 [FONT=Monospace]Errno: 5 (Input/output error), flush cache scsi sendcmd: no error[/FONT]
 [FONT=Monospace]CDB:  35 00 00 00 00 00 00 00 00 00[/FONT]
 [FONT=Monospace]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=Monospace]Sense Bytes: 70 00 04 00 1C 88 99 0E 00 00 00 00 44 00 00 00[/FONT]
 [FONT=Monospace]Sense Key: 0x4 Hardware Error, Segment 0[/FONT]
 [FONT=Monospace]Sense Code: 0x44 Qual 0x00 (internal target failure) Fru 0x0[/FONT]
 [FONT=Monospace]Sense flags: Blk 1869977 (not valid) [/FONT]
 [FONT=Monospace]cmd finished after 7.466s timeout 200s[/FONT]
 [FONT=Monospace]/usr/bin/wodim: Cannot fixate disk.[/FONT]
 [FONT=Monospace]Trouble flushing the cache[/FONT]
 [FONT=Monospace]Fixating time:    7.466s[/FONT]
 [FONT=Monospace]/usr/bin/wodim: fifo had 53980 puts and 53980 gets.[/FONT]
 [FONT=Monospace]/usr/bin/wodim: fifo was 0 times empty and 30155 times full, min fill was 91%.[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]cdrecord command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1673369s -[/FONT]
 [FONT=Monospace][/FONT]

---

