---
title: "Extremely Slow Boot"
date: 2011-10-31
forum: General Help
---

### Post by FLCL on 2011-10-31
I have an Ubuntu installation 10.04 on the laptop my father uses. 
that takes 10+ minutes to boot up. Takes just as long in recovery mode. There is multiple (about 4) kernels on boot in the grub menu. Would this cause any problems? 

- Takes a minute or two for login prompt to appear after staring at login background.

- Upon login, it takes about 5 minutes to load. It just shows the Desktop background and a spinning wheel in the mean time

- Once everything does load, it is still extremely unresponsive for some time. Trying to close anything takes upwards of minutes  to get a reply. Opening anything, including home folder, takes a ridiculous amount of time.


- There is over 200GB of free space on the drive, so it's not even close to being full.

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-10-31
```
dmesg > ~/Desktop/dmesg.txt
```
that will put a file on your desktop post the content of that file or a copy of the file
also a boot chart would be useful
```
sudo apt-get install bootchart;sudo reboot
```
once it gets back on 
```
nautilus /var/log/bootchart
```
upload the picture there to [http://imgur.com/](http://imgur.com/) since it supports large images post a link to the image

---

### Post by Bucky Ball on 2011-10-31
How much RAM? What processor? Amount of kernels is not the problem.

---

### Post by FLCL on 2011-10-31
Working on it. It's taking a lot of effort just to get terminal going

Also, it has 4GB of RAM and Core2Duo 2.0ghz

Edit: Still waiting on Terminal, sorry. Finally got to the point where I could enter a command but it's taking forever.

Almost seems like the hard drive is about to completely die, but it was working fine a few days ago and hasn't taken any spills. No indicators of a failing drive either

---

### Post by FLCL on 2011-10-31
I'm seriously just considering a wipe. It's been a half hour and all i've been able to accomplish is a single command. I can't even open the file..I'll try to copy it to a flash drive but who knows how long it will take to even detect it..

**Edit:** It finally opened the file. While I wait for the browser to open,  I see this error repeated many times throughout the log ```
ata1.00: failed command: READ FPDMA QUEUED
```

---

### Post by FLCL on 2011-10-31
Took a long time but,**dmesg.txt file:**
```
1/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  648.954131] ata1.00: status: { DRDY ERR }
[  648.954135] ata1.00: error: { UNC }
[  648.957406] ata1.00: configured for UDMA/133
[  648.957422] ata1: EH complete
[  652.727111] ata1.00: exception Emask 0x0 SAct 0x1f SErr 0x0 action 0x0
[  652.727120] ata1.00: irq_stat 0x40000008
[  652.727127] ata1.00: failed command: READ FPDMA QUEUED
[  652.727140] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[  652.727142]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  652.727149] ata1.00: status: { DRDY ERR }
[  652.727153] ata1.00: error: { UNC }
[  652.730378] ata1.00: configured for UDMA/133
[  652.730399] ata1: EH complete
[  656.581092] ata1.00: exception Emask 0x0 SAct 0x2f SErr 0x0 action 0x0
[  656.581101] ata1.00: irq_stat 0x40000008
[  656.581108] ata1.00: failed command: READ FPDMA QUEUED
[  656.581121] ata1.00: cmd 60/08:18:10:6c:85/00:00:15:00:00/40 tag 3 ncq 4096 in
[  656.581124]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  656.581130] ata1.00: status: { DRDY ERR }
[  656.581134] ata1.00: error: { UNC }
[  656.584399] ata1.00: configured for UDMA/133
[  656.584420] ata1: EH complete
[  660.435069] ata1.00: exception Emask 0x0 SAct 0x1e SErr 0x0 action 0x0
[  660.435075] ata1.00: irq_stat 0x40000008
[  660.435081] ata1.00: failed command: READ FPDMA QUEUED
[  660.435094] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[  660.435096]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  660.435102] ata1.00: status: { DRDY ERR }
[  660.435106] ata1.00: error: { UNC }
[  660.438343] ata1.00: configured for UDMA/133
[  660.438361] ata1: EH complete
[  664.255727] ata1.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  664.255734] ata1.00: irq_stat 0x40000008
[  664.255741] ata1.00: failed command: READ FPDMA QUEUED
[  664.255754] ata1.00: cmd 60/08:18:10:6c:85/00:00:15:00:00/40 tag 3 ncq 4096 in
[  664.255756]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  664.255762] ata1.00: status: { DRDY ERR }
[  664.255766] ata1.00: error: { UNC }
[  664.259003] ata1.00: configured for UDMA/133
[  664.259023] ata1: EH complete
[  668.054185] ata1.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  668.054193] ata1.00: irq_stat 0x40000008
[  668.054200] ata1.00: failed command: READ FPDMA QUEUED
[  668.054212] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  668.054215]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  668.054221] ata1.00: status: { DRDY ERR }
[  668.054225] ata1.00: error: { UNC }
[  668.057455] ata1.00: configured for UDMA/133
[  668.057474] sd 0:0:0:0: [sda] Unhandled sense code
[  668.057478] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  668.057485] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  668.057493] Descriptor sense data with sense descriptors (in hex):
[  668.057498]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  668.057516]         15 85 6c 13 
[  668.057523] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  668.057534] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  668.057553] end_request: I/O error, dev sda, sector 361065491
[  668.057567] ata1: EH complete
[  672.089342] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  672.089351] ata1.00: irq_stat 0x40000008
[  672.089358] ata1.00: failed command: READ FPDMA QUEUED
[  672.089371] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  672.089374]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  672.089380] ata1.00: status: { DRDY ERR }
[  672.089384] ata1.00: error: { UNC }
[  672.092753] ata1.00: configured for UDMA/133
[  672.092769] ata1: EH complete
[  675.895431] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  675.895438] ata1.00: irq_stat 0x40000008
[  675.895444] ata1.00: failed command: READ FPDMA QUEUED
[  675.895457] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  675.895459]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  675.895465] ata1.00: status: { DRDY ERR }
[  675.895469] ata1.00: error: { UNC }
[  675.898936] ata1.00: configured for UDMA/133
[  675.898949] ata1: EH complete
[  679.705005] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  679.705013] ata1.00: irq_stat 0x40000008
[  679.705019] ata1.00: failed command: READ FPDMA QUEUED
[  679.705032] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  679.705035]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  679.705041] ata1.00: status: { DRDY ERR }
[  679.705045] ata1.00: error: { UNC }
[  679.708328] ata1.00: configured for UDMA/133
[  679.708343] ata1: EH complete
[  683.470119] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  683.470125] ata1.00: irq_stat 0x40000008
[  683.470131] ata1.00: failed command: READ FPDMA QUEUED
[  683.470144] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  683.470146]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  683.470152] ata1.00: status: { DRDY ERR }
[  683.470156] ata1.00: error: { UNC }
[  683.473503] ata1.00: configured for UDMA/133
[  683.473516] ata1: EH complete
[  687.257458] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  687.257465] ata1.00: irq_stat 0x40000008
[  687.257471] ata1.00: failed command: READ FPDMA QUEUED
[  687.257483] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  687.257486]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  687.257492] ata1.00: status: { DRDY ERR }
[  687.257496] ata1.00: error: { UNC }
[  687.260817] ata1.00: configured for UDMA/133
[  687.260830] ata1: EH complete
[  691.033695] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  691.033701] ata1.00: irq_stat 0x40000008
[  691.033707] ata1.00: failed command: READ FPDMA QUEUED
[  691.033720] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  691.033722]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  691.033728] ata1.00: status: { DRDY ERR }
[  691.033732] ata1.00: error: { UNC }
[  691.037080] ata1.00: configured for UDMA/133
[  691.037096] sd 0:0:0:0: [sda] Unhandled sense code
[  691.037101] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  691.037107] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  691.037120] Descriptor sense data with sense descriptors (in hex):
[  691.037124]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  691.037139]         15 85 6c 13 
[  691.037146] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  691.037156] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  691.037170] end_request: I/O error, dev sda, sector 361065491
[  691.037193] ata1: EH complete
[  695.209775] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  695.209784] ata1.00: irq_stat 0x40000008
[  695.209791] ata1.00: failed command: READ FPDMA QUEUED
[  695.209805] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  695.209808]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  695.209814] ata1.00: status: { DRDY ERR }
[  695.209818] ata1.00: error: { UNC }
[  695.213173] ata1.00: configured for UDMA/133
[  695.213188] ata1: EH complete
[  699.030442] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  699.030450] ata1.00: irq_stat 0x40000008
[  699.030457] ata1.00: failed command: READ FPDMA QUEUED
[  699.030470] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  699.030473]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  699.030479] ata1.00: status: { DRDY ERR }
[  699.030483] ata1.00: error: { UNC }
[  699.033749] ata1.00: configured for UDMA/133
[  699.033764] ata1: EH complete
[  702.817788] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  702.817795] ata1.00: irq_stat 0x40000008
[  702.817801] ata1.00: failed command: READ FPDMA QUEUED
[  702.817814] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  702.817816]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  702.817822] ata1.00: status: { DRDY ERR }
[  702.817827] ata1.00: error: { UNC }
[  702.821168] ata1.00: configured for UDMA/133
[  702.821182] ata1: EH complete
[  706.605130] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  706.605137] ata1.00: irq_stat 0x40000008
[  706.605143] ata1.00: failed command: READ FPDMA QUEUED
[  706.605156] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  706.605159]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  706.605165] ata1.00: status: { DRDY ERR }
[  706.605169] ata1.00: error: { UNC }
[  706.608423] ata1.00: configured for UDMA/133
[  706.608435] ata1: EH complete
[  710.392504] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  710.392511] ata1.00: irq_stat 0x40000008
[  710.392517] ata1.00: failed command: READ FPDMA QUEUED
[  710.392530] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  710.392532]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  710.392538] ata1.00: status: { DRDY ERR }
[  710.392542] ata1.00: error: { UNC }
[  710.395766] ata1.00: configured for UDMA/133
[  710.395780] ata1: EH complete
[  714.190944] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  714.190951] ata1.00: irq_stat 0x40000008
[  714.190958] ata1.00: failed command: READ FPDMA QUEUED
[  714.190971] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  714.190973]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  714.190979] ata1.00: status: { DRDY ERR }
[  714.190983] ata1.00: error: { UNC }
[  714.194182] ata1.00: configured for UDMA/133
[  714.194199] sd 0:0:0:0: [sda] Unhandled sense code
[  714.194203] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  714.194210] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  714.194222] Descriptor sense data with sense descriptors (in hex):
[  714.194226]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  714.194242]         15 85 6c 13 
[  714.194249] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  714.194258] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  714.194273] end_request: I/O error, dev sda, sector 361065491
[  714.194295] ata1: EH complete
[  718.192846] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  718.192855] ata1.00: irq_stat 0x40000008
[  718.192862] ata1.00: failed command: READ FPDMA QUEUED
[  718.192875] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  718.192878]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  718.192884] ata1.00: status: { DRDY ERR }
[  718.192888] ata1.00: error: { UNC }
[  718.196258] ata1.00: configured for UDMA/133
[  718.196273] ata1: EH complete
[  721.998849] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  721.998857] ata1.00: irq_stat 0x40000008
[  721.998865] ata1.00: failed command: READ FPDMA QUEUED
[  721.998878] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  721.998880]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  721.998886] ata1.00: status: { DRDY ERR }
[  721.998891] ata1.00: error: { UNC }
[  722.002421] ata1.00: configured for UDMA/133
[  722.002436] ata1: EH complete
[  725.786201] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  725.786209] ata1.00: irq_stat 0x40000008
[  725.786216] ata1.00: failed command: READ FPDMA QUEUED
[  725.786229] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  725.786232]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  725.786238] ata1.00: status: { DRDY ERR }
[  725.786242] ata1.00: error: { UNC }
[  725.789485] ata1.00: configured for UDMA/133
[  725.789500] ata1: EH complete
[  729.573536] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  729.573543] ata1.00: irq_stat 0x40000008
[  729.573549] ata1.00: failed command: READ FPDMA QUEUED
[  729.573562] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  729.573565]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  729.573571] ata1.00: status: { DRDY ERR }
[  729.573575] ata1.00: error: { UNC }
[  729.576661] ata1.00: configured for UDMA/133
[  729.576673] ata1: EH complete
[  733.371992] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  733.371999] ata1.00: irq_stat 0x40000008
[  733.372006] ata1.00: failed command: READ FPDMA QUEUED
[  733.372019] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  733.372021]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  733.372027] ata1.00: status: { DRDY ERR }
[  733.372031] ata1.00: error: { UNC }
[  733.375285] ata1.00: configured for UDMA/133
[  733.375298] ata1: EH complete
[  737.148235] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  737.148242] ata1.00: irq_stat 0x40000008
[  737.148249] ata1.00: failed command: READ FPDMA QUEUED
[  737.148262] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  737.148264]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  737.148270] ata1.00: status: { DRDY ERR }
[  737.148275] ata1.00: error: { UNC }
[  737.151445] ata1.00: configured for UDMA/133
[  737.151460] sd 0:0:0:0: [sda] Unhandled sense code
[  737.151464] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  737.151471] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  737.151479] Descriptor sense data with sense descriptors (in hex):
[  737.151484]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  737.151502]         15 85 6c 13 
[  737.151510] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  737.151516] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  737.151524] end_request: I/O error, dev sda, sector 361065491
[  737.151539] ata1: EH complete
[  741.057751] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  741.057760] ata1.00: irq_stat 0x40000008
[  741.057767] ata1.00: failed command: READ FPDMA QUEUED
[  741.057780] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  741.057783]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  741.057789] ata1.00: status: { DRDY ERR }
[  741.057793] ata1.00: error: { UNC }
[  741.061135] ata1.00: configured for UDMA/133
[  741.061150] ata1: EH complete
[  744.845097] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  744.845106] ata1.00: irq_stat 0x40000008
[  744.845113] ata1.00: failed command: READ FPDMA QUEUED
[  744.845126] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  744.845129]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  744.845135] ata1.00: status: { DRDY ERR }
[  744.845139] ata1.00: error: { UNC }
[  744.848488] ata1.00: configured for UDMA/133
[  744.848502] ata1: EH complete
[  748.621332] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  748.621339] ata1.00: irq_stat 0x40000008
[  748.621345] ata1.00: failed command: READ FPDMA QUEUED
[  748.621358] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  748.621361]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  748.621367] ata1.00: status: { DRDY ERR }
[  748.621371] ata1.00: error: { UNC }
[  748.624771] ata1.00: configured for UDMA/133
[  748.624785] ata1: EH complete
[  752.419789] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  752.419796] ata1.00: irq_stat 0x40000008
[  752.419802] ata1.00: failed command: READ FPDMA QUEUED
[  752.419815] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  752.419818]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  752.419824] ata1.00: status: { DRDY ERR }
[  752.419828] ata1.00: error: { UNC }
[  752.422955] ata1.00: configured for UDMA/133
[  752.422970] ata1: EH complete
[  756.173814] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  756.173821] ata1.00: irq_stat 0x40000008
[  756.173828] ata1.00: failed command: READ FPDMA QUEUED
[  756.173841] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  756.173843]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  756.173849] ata1.00: status: { DRDY ERR }
[  756.173853] ata1.00: error: { UNC }
[  756.176982] ata1.00: configured for UDMA/133
[  756.176993] ata1: EH complete
[  759.950041] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  759.950048] ata1.00: irq_stat 0x40000008
[  759.950054] ata1.00: failed command: READ FPDMA QUEUED
[  759.950067] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  759.950070]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  759.950076] ata1.00: status: { DRDY ERR }
[  759.950080] ata1.00: error: { UNC }
[  759.953398] ata1.00: configured for UDMA/133
[  759.953415] sd 0:0:0:0: [sda] Unhandled sense code
[  759.953420] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  759.953426] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  759.953435] Descriptor sense data with sense descriptors (in hex):
[  759.953439]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  759.953457]         15 85 6c 13 
[  759.953465] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  759.953475] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  759.953492] end_request: I/O error, dev sda, sector 361065491
[  759.953519] ata1: EH complete
[  764.118718] ata1.00: exception Emask 0x0 SAct 0x21 SErr 0x0 action 0x0
[  764.118727] ata1.00: irq_stat 0x40000008
[  764.118735] ata1.00: failed command: READ FPDMA QUEUED
[  764.118748] ata1.00: cmd 60/08:28:10:6c:85/00:00:15:00:00/40 tag 5 ncq 4096 in
[  764.118750]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  764.118756] ata1.00: status: { DRDY ERR }
[  764.118761] ata1.00: error: { UNC }
[  764.122006] ata1.00: configured for UDMA/133
[  764.122021] ata1: EH complete
[  767.946794] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  767.946802] ata1.00: irq_stat 0x40000008
[  767.946809] ata1.00: failed command: READ FPDMA QUEUED
[  767.946823] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  767.946825]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  767.946832] ata1.00: status: { DRDY ERR }
[  767.946836] ata1.00: error: { UNC }
[  767.950152] ata1.00: configured for UDMA/133
[  767.950169] ata1: EH complete
[  771.758909] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  771.758916] ata1.00: irq_stat 0x40000008
[  771.758923] ata1.00: failed command: READ FPDMA QUEUED
[  771.758936] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[  771.758938]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  771.758944] ata1.00: status: { DRDY ERR }
[  771.758948] ata1.00: error: { UNC }
[  771.762216] ata1.00: configured for UDMA/133
[  771.762230] ata1: EH complete
[  775.554806] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  775.554813] ata1.00: irq_stat 0x40000008
[  775.554820] ata1.00: failed command: READ FPDMA QUEUED
[  775.554832] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  775.554835]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  775.554841] ata1.00: status: { DRDY ERR }
[  775.554845] ata1.00: error: { UNC }
[  775.558230] ata1.00: configured for UDMA/133
[  775.558244] ata1: EH complete
[  779.375451] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  779.375458] ata1.00: irq_stat 0x40000008
[  779.375464] ata1.00: failed command: READ FPDMA QUEUED
[  779.375477] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  779.375479]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  779.375485] ata1.00: status: { DRDY ERR }
[  779.375489] ata1.00: error: { UNC }
[  779.378695] ata1.00: configured for UDMA/133
[  779.378708] ata1: EH complete
[  783.162814] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  783.162821] ata1.00: irq_stat 0x40000008
[  783.162828] ata1.00: failed command: READ FPDMA QUEUED
[  783.162841] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  783.162843]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  783.162849] ata1.00: status: { DRDY ERR }
[  783.162853] ata1.00: error: { UNC }
[  783.166235] ata1.00: configured for UDMA/133
[  783.166251] sd 0:0:0:0: [sda] Unhandled sense code
[  783.166255] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  783.166262] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  783.166271] Descriptor sense data with sense descriptors (in hex):
[  783.166275]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  783.166293]         15 85 6c 13 
[  783.166303] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  783.166310] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  783.166321] end_request: I/O error, dev sda, sector 361065491
[  783.166338] ata1: EH complete
[  787.231561] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  787.231569] ata1.00: irq_stat 0x40000008
[  787.231577] ata1.00: failed command: READ FPDMA QUEUED
[  787.231590] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  787.231593]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  787.231598] ata1.00: status: { DRDY ERR }
[  787.231603] ata1.00: error: { UNC }
[  787.234852] ata1.00: configured for UDMA/133
[  787.234867] ata1: EH complete
[  791.048494] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  791.048502] ata1.00: irq_stat 0x40000008
[  791.048509] ata1.00: failed command: READ FPDMA QUEUED
[  791.048523] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  791.048525]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  791.048531] ata1.00: status: { DRDY ERR }
[  791.048536] ata1.00: error: { UNC }
[  791.051808] ata1.00: configured for UDMA/133
[  791.051823] ata1: EH complete
[  794.835835] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  794.835844] ata1.00: irq_stat 0x40000008
[  794.835851] ata1.00: failed command: READ FPDMA QUEUED
[  794.835864] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  794.835867]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  794.835873] ata1.00: status: { DRDY ERR }
[  794.835877] ata1.00: error: { UNC }
[  794.839195] ata1.00: configured for UDMA/133
[  794.839209] ata1: EH complete
[  798.600938] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  798.600945] ata1.00: irq_stat 0x40000008
[  798.600951] ata1.00: failed command: READ FPDMA QUEUED
[  798.600964] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  798.600967]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  798.600973] ata1.00: status: { DRDY ERR }
[  798.600977] ata1.00: error: { UNC }
[  798.604181] ata1.00: configured for UDMA/133
[  798.604196] ata1: EH complete
[  802.366098] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  802.366106] ata1.00: irq_stat 0x40000008
[  802.366113] ata1.00: failed command: READ FPDMA QUEUED
[  802.366126] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  802.366128]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  802.366134] ata1.00: status: { DRDY ERR }
[  802.366138] ata1.00: error: { UNC }
[  802.369492] ata1.00: configured for UDMA/133
[  802.369500] ata1: EH complete
[  806.153430] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  806.153437] ata1.00: irq_stat 0x40000008
[  806.153444] ata1.00: failed command: READ FPDMA QUEUED
[  806.153457] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  806.153459]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  806.153465] ata1.00: status: { DRDY ERR }
[  806.153469] ata1.00: error: { UNC }
[  806.156735] ata1.00: configured for UDMA/133
[  806.156752] sd 0:0:0:0: [sda] Unhandled sense code
[  806.156756] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  806.156763] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  806.156772] Descriptor sense data with sense descriptors (in hex):
[  806.156779]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  806.156795]         15 85 6c 13 
[  806.156802] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  806.156812] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  806.156826] end_request: I/O error, dev sda, sector 361065491
[  806.156849] ata1: EH complete
[  810.085160] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  810.085169] ata1.00: irq_stat 0x40000008
[  810.085176] ata1.00: failed command: READ FPDMA QUEUED
[  810.085189] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  810.085192]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  810.085198] ata1.00: status: { DRDY ERR }
[  810.085202] ata1.00: error: { UNC }
[  810.088402] ata1.00: configured for UDMA/133
[  810.088416] ata1: EH complete
[  813.894727] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  813.894736] ata1.00: irq_stat 0x40000008
[  813.894744] ata1.00: failed command: READ FPDMA QUEUED
[  813.894757] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  813.894759]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  813.894765] ata1.00: status: { DRDY ERR }
[  813.894770] ata1.00: error: { UNC }
[  813.898135] ata1.00: configured for UDMA/133
[  813.898150] ata1: EH complete
[  817.670957] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  817.670964] ata1.00: irq_stat 0x40000008
[  817.670970] ata1.00: failed command: READ FPDMA QUEUED
[  817.670983] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  817.670986]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  817.670992] ata1.00: status: { DRDY ERR }
[  817.670996] ata1.00: error: { UNC }
[  817.674272] ata1.00: configured for UDMA/133
[  817.674285] ata1: EH complete
[  821.491626] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  821.491633] ata1.00: irq_stat 0x40000008
[  821.491639] ata1.00: failed command: READ FPDMA QUEUED
[  821.491652] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  821.491655]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  821.491661] ata1.00: status: { DRDY ERR }
[  821.491665] ata1.00: error: { UNC }
[  821.494906] ata1.00: configured for UDMA/133
[  821.494923] ata1: EH complete
[  825.278975] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  825.278982] ata1.00: irq_stat 0x40000008
[  825.278989] ata1.00: failed command: READ FPDMA QUEUED
[  825.279001] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  825.279004]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  825.279010] ata1.00: status: { DRDY ERR }
[  825.279014] ata1.00: error: { UNC }
[  825.282226] ata1.00: configured for UDMA/133
[  825.282240] ata1: EH complete
[  829.088527] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  829.088534] ata1.00: irq_stat 0x40000008
[  829.088540] ata1.00: failed command: READ FPDMA QUEUED
[  829.088553] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  829.088555]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  829.088561] ata1.00: status: { DRDY ERR }
[  829.088565] ata1.00: error: { UNC }
[  829.091770] ata1.00: configured for UDMA/133
[  829.091786] sd 0:0:0:0: [sda] Unhandled sense code
[  829.091791] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  829.091797] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  829.091806] Descriptor sense data with sense descriptors (in hex):
[  829.091814]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  829.091830]         15 85 6c 13 
[  829.091837] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  829.091846] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  829.091861] end_request: I/O error, dev sda, sector 361065491
[  829.091884] ata1: EH complete
[  833.164641] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  833.164650] ata1.00: irq_stat 0x40000008
[  833.164657] ata1.00: failed command: READ FPDMA QUEUED
[  833.164670] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  833.164673]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  833.164679] ata1.00: status: { DRDY ERR }
[  833.164683] ata1.00: error: { UNC }
[  833.167941] ata1.00: configured for UDMA/133
[  833.167958] ata1: EH complete
[  836.963092] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  836.963100] ata1.00: irq_stat 0x40000008
[  836.963108] ata1.00: failed command: READ FPDMA QUEUED
[  836.963121] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  836.963123]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  836.963129] ata1.00: status: { DRDY ERR }
[  836.963133] ata1.00: error: { UNC }
[  836.966393] ata1.00: configured for UDMA/133
[  836.966406] ata1: EH complete
[  840.761543] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  840.761550] ata1.00: irq_stat 0x40000008
[  840.761556] ata1.00: failed command: READ FPDMA QUEUED
[  840.761569] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  840.761572]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  840.761578] ata1.00: status: { DRDY ERR }
[  840.761582] ata1.00: error: { UNC }
[  840.764770] ata1.00: configured for UDMA/133
[  840.764782] ata1: EH complete
[  844.548910] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  844.548918] ata1.00: irq_stat 0x40000008
[  844.548924] ata1.00: failed command: READ FPDMA QUEUED
[  844.548938] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  844.548940]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  844.548946] ata1.00: status: { DRDY ERR }
[  844.548950] ata1.00: error: { UNC }
[  844.552237] ata1.00: configured for UDMA/133
[  844.552252] ata1: EH complete
[  848.358439] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  848.358447] ata1.00: irq_stat 0x40000008
[  848.358454] ata1.00: failed command: READ FPDMA QUEUED
[  848.358467] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  848.358469]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  848.358475] ata1.00: status: { DRDY ERR }
[  848.358479] ata1.00: error: { UNC }
[  848.361736] ata1.00: configured for UDMA/133
[  848.361751] ata1: EH complete
[  852.145775] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  852.145782] ata1.00: irq_stat 0x40000008
[  852.145789] ata1.00: failed command: READ FPDMA QUEUED
[  852.145801] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  852.145804]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  852.145810] ata1.00: status: { DRDY ERR }
[  852.145814] ata1.00: error: { UNC }
[  852.149137] ata1.00: configured for UDMA/133
[  852.149154] sd 0:0:0:0: [sda] Unhandled sense code
[  852.149158] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  852.149165] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  852.149177] Descriptor sense data with sense descriptors (in hex):
[  852.149181]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  852.149197]         15 85 6c 13 
[  852.149204] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  852.149213] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  852.149228] end_request: I/O error, dev sda, sector 361065491
[  852.149251] ata1: EH complete
[  856.088616] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  856.088625] ata1.00: irq_stat 0x40000008
[  856.088632] ata1.00: failed command: READ FPDMA QUEUED
[  856.088645] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  856.088648]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  856.088654] ata1.00: status: { DRDY ERR }
[  856.088658] ata1.00: error: { UNC }
[  856.091881] ata1.00: configured for UDMA/133
[  856.091893] ata1: EH complete
[  859.898174] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  859.898183] ata1.00: irq_stat 0x40000008
[  859.898190] ata1.00: failed command: READ FPDMA QUEUED
[  859.898204] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  859.898206]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  859.898212] ata1.00: status: { DRDY ERR }
[  859.898216] ata1.00: error: { UNC }
[  859.901559] ata1.00: configured for UDMA/133
[  859.901575] ata1: EH complete
[  863.674405] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  863.674412] ata1.00: irq_stat 0x40000008
[  863.674419] ata1.00: failed command: READ FPDMA QUEUED
[  863.674432] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  863.674434]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  863.674440] ata1.00: status: { DRDY ERR }
[  863.674445] ata1.00: error: { UNC }
[  863.677690] ata1.00: configured for UDMA/133
[  863.677704] ata1: EH complete
[  867.472855] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  867.472862] ata1.00: irq_stat 0x40000008
[  867.472868] ata1.00: failed command: READ FPDMA QUEUED
[  867.472881] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  867.472884]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  867.472890] ata1.00: status: { DRDY ERR }
[  867.472894] ata1.00: error: { UNC }
[  867.476215] ata1.00: configured for UDMA/133
[  867.476229] ata1: EH complete
[  871.282409] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  871.282416] ata1.00: irq_stat 0x40000008
[  871.282422] ata1.00: failed command: READ FPDMA QUEUED
[  871.282435] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  871.282438]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  871.282444] ata1.00: status: { DRDY ERR }
[  871.282448] ata1.00: error: { UNC }
[  871.285658] ata1.00: configured for UDMA/133
[  871.285672] ata1: EH complete
[  875.047546] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  875.047554] ata1.00: irq_stat 0x40000008
[  875.047561] ata1.00: failed command: READ FPDMA QUEUED
[  875.047575] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  875.047577]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  875.047583] ata1.00: status: { DRDY ERR }
[  875.047587] ata1.00: error: { UNC }
[  875.050825] ata1.00: configured for UDMA/133
[  875.050844] sd 0:0:0:0: [sda] Unhandled sense code
[  875.050848] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  875.050855] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  875.050864] Descriptor sense data with sense descriptors (in hex):
[  875.050868]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  875.050886]         15 85 6c 13 
[  875.050894] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  875.050904] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  875.050921] end_request: I/O error, dev sda, sector 361065491
[  875.050946] ata1: EH complete
[  879.116571] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  879.116579] ata1.00: irq_stat 0x40000008
[  879.116587] ata1.00: failed command: READ FPDMA QUEUED
[  879.116600] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[  879.116603]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  879.116609] ata1.00: status: { DRDY ERR }
[  879.116613] ata1.00: error: { UNC }
[  879.119858] ata1.00: configured for UDMA/133
[  879.119866] ata1: EH complete
[  882.955438] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  882.955447] ata1.00: irq_stat 0x40000008
[  882.955454] ata1.00: failed command: READ FPDMA QUEUED
[  882.955467] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  882.955470]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  882.955476] ata1.00: status: { DRDY ERR }
[  882.955480] ata1.00: error: { UNC }
[  882.958666] ata1.00: configured for UDMA/133
[  882.958680] ata1: EH complete
[  886.742778] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  886.742785] ata1.00: irq_stat 0x40000008
[  886.742792] ata1.00: failed command: READ FPDMA QUEUED
[  886.742805] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  886.742807]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  886.742813] ata1.00: status: { DRDY ERR }
[  886.742817] ata1.00: error: { UNC }
[  886.746224] ata1.00: configured for UDMA/133
[  886.746238] ata1: EH complete
[  890.530126] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  890.530133] ata1.00: irq_stat 0x40000008
[  890.530140] ata1.00: failed command: READ FPDMA QUEUED
[  890.530152] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  890.530155]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  890.530161] ata1.00: status: { DRDY ERR }
[  890.530165] ata1.00: error: { UNC }
[  890.533379] ata1.00: configured for UDMA/133
[  890.533392] ata1: EH complete
[  894.317472] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  894.317479] ata1.00: irq_stat 0x40000008
[  894.317486] ata1.00: failed command: READ FPDMA QUEUED
[  894.317498] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  894.317501]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  894.317507] ata1.00: status: { DRDY ERR }
[  894.317511] ata1.00: error: { UNC }
[  894.320768] ata1.00: configured for UDMA/133
[  894.320780] ata1: EH complete
[  898.115908] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  898.115914] ata1.00: irq_stat 0x40000008
[  898.115921] ata1.00: failed command: READ FPDMA QUEUED
[  898.115933] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  898.115936]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  898.115942] ata1.00: status: { DRDY ERR }
[  898.115946] ata1.00: error: { UNC }
[  898.119148] ata1.00: configured for UDMA/133
[  898.119164] sd 0:0:0:0: [sda] Unhandled sense code
[  898.119168] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  898.119175] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  898.119187] Descriptor sense data with sense descriptors (in hex):
[  898.119191]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  898.119207]         15 85 6c 13 
[  898.119214] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  898.119223] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  898.119238] end_request: I/O error, dev sda, sector 361065491
[  898.119261] ata1: EH complete
[  902.114296] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  902.114305] ata1.00: irq_stat 0x40000008
[  902.114312] ata1.00: failed command: READ FPDMA QUEUED
[  902.114325] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  902.114328]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  902.114334] ata1.00: status: { DRDY ERR }
[  902.114338] ata1.00: error: { UNC }
[  902.117828] ata1.00: configured for UDMA/133
[  902.117841] ata1: EH complete
[  905.890581] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  905.890590] ata1.00: irq_stat 0x40000008
[  905.890597] ata1.00: failed command: READ FPDMA QUEUED
[  905.890610] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  905.890613]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  905.890619] ata1.00: status: { DRDY ERR }
[  905.890623] ata1.00: error: { UNC }
[  905.893770] ata1.00: configured for UDMA/133
[  905.893786] ata1: EH complete
[  909.677896] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  909.677905] ata1.00: irq_stat 0x40000008
[  909.677912] ata1.00: failed command: READ FPDMA QUEUED
[  909.677925] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  909.677928]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  909.677934] ata1.00: status: { DRDY ERR }
[  909.677938] ata1.00: error: { UNC }
[  909.681165] ata1.00: configured for UDMA/133
[  909.681182] ata1: EH complete
[  913.476348] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  913.476355] ata1.00: irq_stat 0x40000008
[  913.476362] ata1.00: failed command: READ FPDMA QUEUED
[  913.476375] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  913.476378]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  913.476384] ata1.00: status: { DRDY ERR }
[  913.476388] ata1.00: error: { UNC }
[  913.479597] ata1.00: configured for UDMA/133
[  913.479610] ata1: EH complete
[  917.241488] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  917.241496] ata1.00: irq_stat 0x40000008
[  917.241503] ata1.00: failed command: READ FPDMA QUEUED
[  917.241517] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  917.241519]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  917.241525] ata1.00: status: { DRDY ERR }
[  917.241529] ata1.00: error: { UNC }
[  917.244743] ata1.00: configured for UDMA/133
[  917.244759] ata1: EH complete
[  921.051034] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  921.051041] ata1.00: irq_stat 0x40000008
[  921.051048] ata1.00: failed command: READ FPDMA QUEUED
[  921.051062] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  921.051064]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  921.051070] ata1.00: status: { DRDY ERR }
[  921.051074] ata1.00: error: { UNC }
[  921.054226] ata1.00: configured for UDMA/133
[  921.054245] sd 0:0:0:0: [sda] Unhandled sense code
[  921.054249] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  921.054256] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  921.054265] Descriptor sense data with sense descriptors (in hex):
[  921.054269]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  921.054287]         15 85 6c 13 
[  921.054295] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  921.054305] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  921.054322] end_request: I/O error, dev sda, sector 361065491
[  921.054337] ata1: EH complete
[  924.938335] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  924.938343] ata1.00: irq_stat 0x40000008
[  924.938351] ata1.00: failed command: READ FPDMA QUEUED
[  924.938364] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[  924.938366]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  924.938372] ata1.00: status: { DRDY ERR }
[  924.938376] ata1.00: error: { UNC }
[  924.941629] ata1.00: configured for UDMA/133
[  924.941643] ata1: EH complete
[  928.736777] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  928.736785] ata1.00: irq_stat 0x40000008
[  928.736793] ata1.00: failed command: READ FPDMA QUEUED
[  928.736806] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  928.736809]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  928.736815] ata1.00: status: { DRDY ERR }
[  928.736819] ata1.00: error: { UNC }
[  928.740171] ata1.00: configured for UDMA/133
[  928.740187] ata1: EH complete
[  932.535236] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  932.535244] ata1.00: irq_stat 0x40000008
[  932.535251] ata1.00: failed command: READ FPDMA QUEUED
[  932.535264] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  932.535267]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  932.535273] ata1.00: status: { DRDY ERR }
[  932.535277] ata1.00: error: { UNC }
[  932.538645] ata1.00: configured for UDMA/133
[  932.538660] ata1: EH complete
[  936.344792] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  936.344800] ata1.00: irq_stat 0x40000008
[  936.344807] ata1.00: failed command: READ FPDMA QUEUED
[  936.344820] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  936.344823]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  936.344829] ata1.00: status: { DRDY ERR }
[  936.344833] ata1.00: error: { UNC }
[  936.348153] ata1.00: configured for UDMA/133
[  936.348168] ata1: EH complete
[  940.132134] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  940.132142] ata1.00: irq_stat 0x40000008
[  940.132149] ata1.00: failed command: READ FPDMA QUEUED
[  940.132162] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  940.132164]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  940.132170] ata1.00: status: { DRDY ERR }
[  940.132174] ata1.00: error: { UNC }
[  940.135478] ata1.00: configured for UDMA/133
[  940.135491] ata1: EH complete
[  943.919486] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  943.919494] ata1.00: irq_stat 0x40000008
[  943.919500] ata1.00: failed command: READ FPDMA QUEUED
[  943.919513] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  943.919516]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  943.919522] ata1.00: status: { DRDY ERR }
[  943.919526] ata1.00: error: { UNC }
[  943.922743] ata1.00: configured for UDMA/133
[  943.922760] sd 0:0:0:0: [sda] Unhandled sense code
[  943.922765] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  943.922772] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  943.922784] Descriptor sense data with sense descriptors (in hex):
[  943.922788]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  943.922803]         15 85 6c 13 
[  943.922810] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  943.922820] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  943.922835] end_request: I/O error, dev sda, sector 361065491
[  943.922857] ata1: EH complete
[  948.073349] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  948.073358] ata1.00: irq_stat 0x40000008
[  948.073365] ata1.00: failed command: READ FPDMA QUEUED
[  948.073378] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  948.073381]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  948.073387] ata1.00: status: { DRDY ERR }
[  948.073391] ata1.00: error: { UNC }
[  948.076618] ata1.00: configured for UDMA/133
[  948.076633] ata1: EH complete
[  951.871827] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  951.871836] ata1.00: irq_stat 0x40000008
[  951.871843] ata1.00: failed command: READ FPDMA QUEUED
[  951.871856] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  951.871859]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  951.871865] ata1.00: status: { DRDY ERR }
[  951.871869] ata1.00: error: { UNC }
[  951.875211] ata1.00: configured for UDMA/133
[  951.875227] ata1: EH complete
[  955.648043] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  955.648050] ata1.00: irq_stat 0x40000008
[  955.648056] ata1.00: failed command: READ FPDMA QUEUED
[  955.648069] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  955.648072]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  955.648078] ata1.00: status: { DRDY ERR }
[  955.648082] ata1.00: error: { UNC }
[  955.651296] ata1.00: configured for UDMA/133
[  955.651314] ata1: EH complete
[  959.435386] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  959.435393] ata1.00: irq_stat 0x40000008
[  959.435400] ata1.00: failed command: READ FPDMA QUEUED
[  959.435413] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  959.435415]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  959.435421] ata1.00: status: { DRDY ERR }
[  959.435425] ata1.00: error: { UNC }
[  959.438628] ata1.00: configured for UDMA/133
[  959.438642] ata1: EH complete
[  963.244941] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  963.244948] ata1.00: irq_stat 0x40000008
[  963.244955] ata1.00: failed command: READ FPDMA QUEUED
[  963.244967] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  963.244970]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  963.244976] ata1.00: status: { DRDY ERR }
[  963.244980] ata1.00: error: { UNC }
[  963.248235] ata1.00: configured for UDMA/133
[  963.248249] ata1: EH complete
[  967.010072] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  967.010080] ata1.00: irq_stat 0x40000008
[  967.010088] ata1.00: failed command: READ FPDMA QUEUED
[  967.010100] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  967.010103]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  967.010109] ata1.00: status: { DRDY ERR }
[  967.010113] ata1.00: error: { UNC }
[  967.013325] ata1.00: configured for UDMA/133
[  967.013344] sd 0:0:0:0: [sda] Unhandled sense code
[  967.013348] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  967.013353] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  967.013361] Descriptor sense data with sense descriptors (in hex):
[  967.013363]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  967.013371]         15 85 6c 13 
[  967.013375] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  967.013380] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  967.013389] end_request: I/O error, dev sda, sector 361065491
[  967.013406] ata1: EH complete
[  971.081177] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  971.081186] ata1.00: irq_stat 0x40000008
[  971.081193] ata1.00: failed command: READ FPDMA QUEUED
[  971.081206] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  971.081209]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  971.081215] ata1.00: status: { DRDY ERR }
[  971.081219] ata1.00: error: { UNC }
[  971.084596] ata1.00: configured for UDMA/133
[  971.084611] ata1: EH complete
[  974.895752] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  974.895761] ata1.00: irq_stat 0x40000008
[  974.895768] ata1.00: failed command: READ FPDMA QUEUED
[  974.895781] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  974.895784]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  974.895790] ata1.00: status: { DRDY ERR }
[  974.895794] ata1.00: error: { UNC }
[  974.899110] ata1.00: configured for UDMA/133
[  974.899125] ata1: EH complete
[  978.694198] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  978.694205] ata1.00: irq_stat 0x40000008
[  978.694212] ata1.00: failed command: READ FPDMA QUEUED
[  978.694224] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  978.694227]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  978.694233] ata1.00: status: { DRDY ERR }
[  978.694237] ata1.00: error: { UNC }
[  978.697622] ata1.00: configured for UDMA/133
[  978.697636] ata1: EH complete
[  982.470432] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  982.470441] ata1.00: irq_stat 0x40000008
[  982.470448] ata1.00: failed command: READ FPDMA QUEUED
[  982.470461] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  982.470464]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  982.470470] ata1.00: status: { DRDY ERR }
[  982.470474] ata1.00: error: { UNC }
[  982.473726] ata1.00: configured for UDMA/133
[  982.473741] ata1: EH complete
[  986.257762] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  986.257769] ata1.00: irq_stat 0x40000008
[  986.257776] ata1.00: failed command: READ FPDMA QUEUED
[  986.257789] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  986.257792]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  986.257798] ata1.00: status: { DRDY ERR }
[  986.257802] ata1.00: error: { UNC }
[  986.261070] ata1.00: configured for UDMA/133
[  986.261083] ata1: EH complete
[  990.067320] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  990.067327] ata1.00: irq_stat 0x40000008
[  990.067334] ata1.00: failed command: READ FPDMA QUEUED
[  990.067346] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  990.067349]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  990.067354] ata1.00: status: { DRDY ERR }
[  990.067359] ata1.00: error: { UNC }
[  990.070756] ata1.00: configured for UDMA/133
[  990.070773] sd 0:0:0:0: [sda] Unhandled sense code
[  990.070777] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  990.070784] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  990.070793] Descriptor sense data with sense descriptors (in hex):
[  990.070797]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  990.070815]         15 85 6c 13 
[  990.070822] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  990.070833] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[  990.070850] end_request: I/O error, dev sda, sector 361065491
[  990.070874] ata1: EH complete
[  993.910202] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  993.910211] ata1.00: irq_stat 0x40000008
[  993.910218] ata1.00: failed command: READ FPDMA QUEUED
[  993.910231] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  993.910234]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  993.910240] ata1.00: status: { DRDY ERR }
[  993.910244] ata1.00: error: { UNC }
[  993.913587] ata1.00: configured for UDMA/133
[  993.913602] ata1: EH complete
[  997.697542] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  997.697550] ata1.00: irq_stat 0x40000008
[  997.697557] ata1.00: failed command: READ FPDMA QUEUED
[  997.697571] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[  997.697573]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[  997.697579] ata1.00: status: { DRDY ERR }
[  997.697583] ata1.00: error: { UNC }
[  997.700892] ata1.00: configured for UDMA/133
[  997.700905] ata1: EH complete
[ 1001.462662] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1001.462670] ata1.00: irq_stat 0x40000008
[ 1001.462676] ata1.00: failed command: READ FPDMA QUEUED
[ 1001.462711] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1001.462713]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1001.462720] ata1.00: status: { DRDY ERR }
[ 1001.462724] ata1.00: error: { UNC }
[ 1001.466079] ata1.00: configured for UDMA/133
[ 1001.466093] ata1: EH complete
[ 1005.250007] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1005.250014] ata1.00: irq_stat 0x40000008
[ 1005.250020] ata1.00: failed command: READ FPDMA QUEUED
[ 1005.250033] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1005.250036]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1005.250041] ata1.00: status: { DRDY ERR }
[ 1005.250045] ata1.00: error: { UNC }
[ 1005.253350] ata1.00: configured for UDMA/133
[ 1005.253363] ata1: EH complete
[ 1009.037351] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1009.037357] ata1.00: irq_stat 0x40000008
[ 1009.037364] ata1.00: failed command: READ FPDMA QUEUED
[ 1009.037377] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1009.037379]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1009.037385] ata1.00: status: { DRDY ERR }
[ 1009.037390] ata1.00: error: { UNC }
[ 1009.040635] ata1.00: configured for UDMA/133
[ 1009.040648] ata1: EH complete
[ 1012.813598] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1012.813606] ata1.00: irq_stat 0x40000008
[ 1012.813614] ata1.00: failed command: READ FPDMA QUEUED
[ 1012.813627] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1012.813630]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1012.813636] ata1.00: status: { DRDY ERR }
[ 1012.813640] ata1.00: error: { UNC }
[ 1012.816965] ata1.00: configured for UDMA/133
[ 1012.816978] sd 0:0:0:0: [sda] Unhandled sense code
[ 1012.816980] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1012.816984] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1012.816988] Descriptor sense data with sense descriptors (in hex):
[ 1012.816990]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1012.816999]         15 85 6c 13 
[ 1012.817003] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1012.817008] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1012.817016] end_request: I/O error, dev sda, sector 361065491
[ 1012.817032] ata1: EH complete
[ 1016.875720] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1016.875729] ata1.00: irq_stat 0x40000008
[ 1016.875736] ata1.00: failed command: READ FPDMA QUEUED
[ 1016.875749] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1016.875752]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1016.875758] ata1.00: status: { DRDY ERR }
[ 1016.875762] ata1.00: error: { UNC }
[ 1016.878966] ata1.00: configured for UDMA/133
[ 1016.878981] ata1: EH complete
[ 1020.677063] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1020.677071] ata1.00: irq_stat 0x40000008
[ 1020.677079] ata1.00: failed command: READ FPDMA QUEUED
[ 1020.677092] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1020.677094]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1020.677100] ata1.00: status: { DRDY ERR }
[ 1020.677104] ata1.00: error: { UNC }
[ 1020.680333] ata1.00: configured for UDMA/133
[ 1020.680345] ata1: EH complete
[ 1024.464395] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1024.464403] ata1.00: irq_stat 0x40000008
[ 1024.464410] ata1.00: failed command: READ FPDMA QUEUED
[ 1024.464423] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1024.464425]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1024.464431] ata1.00: status: { DRDY ERR }
[ 1024.464435] ata1.00: error: { UNC }
[ 1024.467713] ata1.00: configured for UDMA/133
[ 1024.467728] ata1: EH complete
[ 1028.251754] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1028.251762] ata1.00: irq_stat 0x40000008
[ 1028.251769] ata1.00: failed command: READ FPDMA QUEUED
[ 1028.251782] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1028.251785]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1028.251791] ata1.00: status: { DRDY ERR }
[ 1028.251795] ata1.00: error: { UNC }
[ 1028.255129] ata1.00: configured for UDMA/133
[ 1028.255144] ata1: EH complete
[ 1032.050208] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1032.050216] ata1.00: irq_stat 0x40000008
[ 1032.050222] ata1.00: failed command: READ FPDMA QUEUED
[ 1032.050235] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1032.050237]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1032.050243] ata1.00: status: { DRDY ERR }
[ 1032.050247] ata1.00: error: { UNC }
[ 1032.053616] ata1.00: configured for UDMA/133
[ 1032.053630] ata1: EH complete
[ 1035.837552] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1035.837559] ata1.00: irq_stat 0x40000008
[ 1035.837566] ata1.00: failed command: READ FPDMA QUEUED
[ 1035.837578] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1035.837581]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1035.837587] ata1.00: status: { DRDY ERR }
[ 1035.837591] ata1.00: error: { UNC }
[ 1035.841002] ata1.00: configured for UDMA/133
[ 1035.841020] sd 0:0:0:0: [sda] Unhandled sense code
[ 1035.841024] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1035.841031] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1035.841039] Descriptor sense data with sense descriptors (in hex):
[ 1035.841044]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1035.841062]         15 85 6c 13 
[ 1035.841071] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1035.841078] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1035.841089] end_request: I/O error, dev sda, sector 361065491
[ 1035.841108] ata1: EH complete
[ 1039.953173] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1039.953182] ata1.00: irq_stat 0x40000008
[ 1039.953189] ata1.00: failed command: READ FPDMA QUEUED
[ 1039.953203] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1039.953205]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1039.953211] ata1.00: status: { DRDY ERR }
[ 1039.953215] ata1.00: error: { UNC }
[ 1039.956722] ata1.00: configured for UDMA/133
[ 1039.956738] ata1: EH complete
[ 1043.767643] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1043.767652] ata1.00: irq_stat 0x40000008
[ 1043.767659] ata1.00: failed command: READ FPDMA QUEUED
[ 1043.767672] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1043.767675]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1043.767681] ata1.00: status: { DRDY ERR }
[ 1043.767685] ata1.00: error: { UNC }
[ 1043.771063] ata1.00: configured for UDMA/133
[ 1043.771078] ata1: EH complete
[ 1047.554998] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1047.555005] ata1.00: irq_stat 0x40000008
[ 1047.555011] ata1.00: failed command: READ FPDMA QUEUED
[ 1047.555024] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1047.555027]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1047.555033] ata1.00: status: { DRDY ERR }
[ 1047.555037] ata1.00: error: { UNC }
[ 1047.558331] ata1.00: configured for UDMA/133
[ 1047.558344] ata1: EH complete
[ 1051.342341] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1051.342348] ata1.00: irq_stat 0x40000008
[ 1051.342355] ata1.00: failed command: READ FPDMA QUEUED
[ 1051.342368] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1051.342370]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1051.342376] ata1.00: status: { DRDY ERR }
[ 1051.342380] ata1.00: error: { UNC }
[ 1051.345595] ata1.00: configured for UDMA/133
[ 1051.345609] ata1: EH complete
[ 1055.140797] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1055.140805] ata1.00: irq_stat 0x40000008
[ 1055.140812] ata1.00: failed command: READ FPDMA QUEUED
[ 1055.140825] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1055.140828]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1055.140834] ata1.00: status: { DRDY ERR }
[ 1055.140838] ata1.00: error: { UNC }
[ 1055.144289] ata1.00: configured for UDMA/133
[ 1055.144306] ata1: EH complete
[ 1058.917063] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1058.917072] ata1.00: irq_stat 0x40000008
[ 1058.917079] ata1.00: failed command: READ FPDMA QUEUED
[ 1058.917093] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1058.917095]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1058.917102] ata1.00: status: { DRDY ERR }
[ 1058.917106] ata1.00: error: { UNC }
[ 1058.920401] ata1.00: configured for UDMA/133
[ 1058.920424] sd 0:0:0:0: [sda] Unhandled sense code
[ 1058.920429] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1058.920436] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1058.920444] Descriptor sense data with sense descriptors (in hex):
[ 1058.920449]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1058.920467]         15 85 6c 13 
[ 1058.920477] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1058.920482] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1058.920490] end_request: I/O error, dev sda, sector 361065491
[ 1058.920510] ata1: EH complete
[ 1062.879249] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1062.879258] ata1.00: irq_stat 0x40000008
[ 1062.879265] ata1.00: failed command: READ FPDMA QUEUED
[ 1062.879278] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1062.879281]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1062.879287] ata1.00: status: { DRDY ERR }
[ 1062.879291] ata1.00: error: { UNC }
[ 1062.882565] ata1.00: configured for UDMA/133
[ 1062.882581] ata1: EH complete
[ 1066.691653] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1066.691662] ata1.00: irq_stat 0x40000008
[ 1066.691669] ata1.00: failed command: READ FPDMA QUEUED
[ 1066.691682] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1066.691685]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1066.691691] ata1.00: status: { DRDY ERR }
[ 1066.691695] ata1.00: error: { UNC }
[ 1066.695111] ata1.00: configured for UDMA/133
[ 1066.695125] ata1: EH complete
[ 1070.478981] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1070.478988] ata1.00: irq_stat 0x40000008
[ 1070.478995] ata1.00: failed command: READ FPDMA QUEUED
[ 1070.479007] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1070.479010]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1070.479016] ata1.00: status: { DRDY ERR }
[ 1070.479020] ata1.00: error: { UNC }
[ 1070.482234] ata1.00: configured for UDMA/133
[ 1070.482246] ata1: EH complete
[ 1074.288545] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1074.288553] ata1.00: irq_stat 0x40000008
[ 1074.288560] ata1.00: failed command: READ FPDMA QUEUED
[ 1074.288573] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1074.288576]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1074.288582] ata1.00: status: { DRDY ERR }
[ 1074.288586] ata1.00: error: { UNC }
[ 1074.291885] ata1.00: configured for UDMA/133
[ 1074.291900] ata1: EH complete
[ 1078.086978] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1078.086985] ata1.00: irq_stat 0x40000008
[ 1078.086992] ata1.00: failed command: READ FPDMA QUEUED
[ 1078.087005] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1078.087007]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1078.087013] ata1.00: status: { DRDY ERR }
[ 1078.087017] ata1.00: error: { UNC }
[ 1078.090474] ata1.00: configured for UDMA/133
[ 1078.090488] ata1: EH complete
[ 1081.896553] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1081.896560] ata1.00: irq_stat 0x40000008
[ 1081.896567] ata1.00: failed command: READ FPDMA QUEUED
[ 1081.896579] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1081.896582]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1081.896587] ata1.00: status: { DRDY ERR }
[ 1081.896592] ata1.00: error: { UNC }
[ 1081.900069] ata1.00: configured for UDMA/133
[ 1081.900085] sd 0:0:0:0: [sda] Unhandled sense code
[ 1081.900091] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1081.900095] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1081.900100] Descriptor sense data with sense descriptors (in hex):
[ 1081.900102]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1081.900110]         15 85 6c 13 
[ 1081.900114] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1081.900119] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1081.900127] end_request: I/O error, dev sda, sector 361065491
[ 1081.900143] ata1: EH complete
[ 1085.899539] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1085.899548] ata1.00: irq_stat 0x40000008
[ 1085.899555] ata1.00: failed command: READ FPDMA QUEUED
[ 1085.899568] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1085.899571]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1085.899577] ata1.00: status: { DRDY ERR }
[ 1085.899581] ata1.00: error: { UNC }
[ 1085.902864] ata1.00: configured for UDMA/133
[ 1085.902883] ata1: EH complete
[ 1089.693411] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1089.693420] ata1.00: irq_stat 0x40000008
[ 1089.693428] ata1.00: failed command: READ FPDMA QUEUED
[ 1089.693441] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1089.693443]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1089.693449] ata1.00: status: { DRDY ERR }
[ 1089.693453] ata1.00: error: { UNC }
[ 1089.696736] ata1.00: configured for UDMA/133
[ 1089.696754] ata1: EH complete
[ 1093.480715] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1093.480722] ata1.00: irq_stat 0x40000008
[ 1093.480729] ata1.00: failed command: READ FPDMA QUEUED
[ 1093.480741] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1093.480744]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1093.480750] ata1.00: status: { DRDY ERR }
[ 1093.480754] ata1.00: error: { UNC }
[ 1093.484025] ata1.00: configured for UDMA/133
[ 1093.484041] ata1: EH complete
[ 1097.279167] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1097.279176] ata1.00: irq_stat 0x40000008
[ 1097.279183] ata1.00: failed command: READ FPDMA QUEUED
[ 1097.279196] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1097.279199]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1097.279205] ata1.00: status: { DRDY ERR }
[ 1097.279209] ata1.00: error: { UNC }
[ 1097.282548] ata1.00: configured for UDMA/133
[ 1097.282565] ata1: EH complete
[ 1101.077618] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1101.077626] ata1.00: irq_stat 0x40000008
[ 1101.077633] ata1.00: failed command: READ FPDMA QUEUED
[ 1101.077646] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1101.077649]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1101.077655] ata1.00: status: { DRDY ERR }
[ 1101.077659] ata1.00: error: { UNC }
[ 1101.080905] ata1.00: configured for UDMA/133
[ 1101.080918] ata1: EH complete
[ 1104.864962] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1104.864969] ata1.00: irq_stat 0x40000008
[ 1104.864976] ata1.00: failed command: READ FPDMA QUEUED
[ 1104.864989] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1104.864991]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1104.864997] ata1.00: status: { DRDY ERR }
[ 1104.865002] ata1.00: error: { UNC }
[ 1104.868221] ata1.00: configured for UDMA/133
[ 1104.868243] sd 0:0:0:0: [sda] Unhandled sense code
[ 1104.868248] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1104.868259] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1104.868267] Descriptor sense data with sense descriptors (in hex):
[ 1104.868271]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1104.868287]         15 85 6c 13 
[ 1104.868293] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1104.868303] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1104.868317] end_request: I/O error, dev sda, sector 361065491
[ 1104.868338] ata1: EH complete
[ 1108.823615] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1108.823623] ata1.00: irq_stat 0x40000008
[ 1108.823630] ata1.00: failed command: READ FPDMA QUEUED
[ 1108.823644] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1108.823646]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1108.823652] ata1.00: status: { DRDY ERR }
[ 1108.823656] ata1.00: error: { UNC }
[ 1108.826923] ata1.00: configured for UDMA/133
[ 1108.826943] ata1: EH complete
[ 1112.639578] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1112.639586] ata1.00: irq_stat 0x40000008
[ 1112.639594] ata1.00: failed command: READ FPDMA QUEUED
[ 1112.639607] ata1.00: cmd 60/08:10:10:6c:85/00:00:15:00:00/40 tag 2 ncq 4096 in
[ 1112.639610]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1112.639616] ata1.00: status: { DRDY ERR }
[ 1112.639620] ata1.00: error: { UNC }
[ 1112.642961] ata1.00: configured for UDMA/133
[ 1112.642980] ata1: EH complete
[ 1116.415796] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1116.415803] ata1.00: irq_stat 0x40000008
[ 1116.415810] ata1.00: failed command: READ FPDMA QUEUED
[ 1116.415823] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1116.415825]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1116.415831] ata1.00: status: { DRDY ERR }
[ 1116.415835] ata1.00: error: { UNC }
[ 1116.419221] ata1.00: configured for UDMA/133
[ 1116.419239] ata1: EH complete
[ 1120.236472] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1120.236482] ata1.00: irq_stat 0x40000008
[ 1120.236489] ata1.00: failed command: READ FPDMA QUEUED
[ 1120.236503] ata1.00: cmd 60/08:10:10:6c:85/00:00:15:00:00/40 tag 2 ncq 4096 in
[ 1120.236505]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1120.236511] ata1.00: status: { DRDY ERR }
[ 1120.236515] ata1.00: error: { UNC }
[ 1120.239882] ata1.00: configured for UDMA/133
[ 1120.239900] ata1: EH complete
[ 1124.034925] ata1.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[ 1124.034931] ata1.00: irq_stat 0x40000008
[ 1124.034938] ata1.00: failed command: READ FPDMA QUEUED
[ 1124.034951] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1124.034954]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1124.034960] ata1.00: status: { DRDY ERR }
[ 1124.034964] ata1.00: error: { UNC }
[ 1124.038306] ata1.00: configured for UDMA/133
[ 1124.038324] ata1: EH complete
[ 1127.871168] ata1.00: exception Emask 0x0 SAct 0x9 SErr 0x0 action 0x0
[ 1127.871175] ata1.00: irq_stat 0x40000008
[ 1127.871182] ata1.00: failed command: READ FPDMA QUEUED
[ 1127.871195] ata1.00: cmd 60/08:18:10:6c:85/00:00:15:00:00/40 tag 3 ncq 4096 in
[ 1127.871198]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1127.871204] ata1.00: status: { DRDY ERR }
[ 1127.871208] ata1.00: error: { UNC }
[ 1127.874434] ata1.00: configured for UDMA/133
[ 1127.874454] sd 0:0:0:0: [sda] Unhandled sense code
[ 1127.874459] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1127.874465] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1127.874474] Descriptor sense data with sense descriptors (in hex):
[ 1127.874478]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1127.874496]         15 85 6c 13 
[ 1127.874504] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1127.874515] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1127.874531] end_request: I/O error, dev sda, sector 361065491
[ 1127.874552] ata1: EH complete
[ 1131.900916] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[ 1131.900924] ata1.00: irq_stat 0x40000008
[ 1131.900932] ata1.00: failed command: READ FPDMA QUEUED
[ 1131.900945] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1131.900947]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1131.900953] ata1.00: status: { DRDY ERR }
[ 1131.900957] ata1.00: error: { UNC }
[ 1131.904324] ata1.00: configured for UDMA/133
[ 1131.904342] ata1: EH complete
[ 1135.719051] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1135.719060] ata1.00: irq_stat 0x40000008
[ 1135.719067] ata1.00: failed command: READ FPDMA QUEUED
[ 1135.719080] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1135.719083]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1135.719089] ata1.00: status: { DRDY ERR }
[ 1135.719093] ata1.00: error: { UNC }
[ 1135.722305] ata1.00: configured for UDMA/133
[ 1135.722320] ata1: EH complete
[ 1139.517518] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1139.517526] ata1.00: irq_stat 0x40000008
[ 1139.517533] ata1.00: failed command: READ FPDMA QUEUED
[ 1139.517547] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1139.517549]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1139.517555] ata1.00: status: { DRDY ERR }
[ 1139.517559] ata1.00: error: { UNC }
[ 1139.520721] ata1.00: configured for UDMA/133
[ 1139.520736] ata1: EH complete
[ 1143.304852] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1143.304860] ata1.00: irq_stat 0x40000008
[ 1143.304866] ata1.00: failed command: READ FPDMA QUEUED
[ 1143.304879] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1143.304882]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1143.304888] ata1.00: status: { DRDY ERR }
[ 1143.304892] ata1.00: error: { UNC }
[ 1143.308072] ata1.00: configured for UDMA/133
[ 1143.308087] ata1: EH complete
[ 1147.103304] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1147.103313] ata1.00: irq_stat 0x40000008
[ 1147.103320] ata1.00: failed command: READ FPDMA QUEUED
[ 1147.103333] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1147.103335]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1147.103341] ata1.00: status: { DRDY ERR }
[ 1147.103345] ata1.00: error: { UNC }
[ 1147.106537] ata1.00: configured for UDMA/133
[ 1147.106553] ata1: EH complete
[ 1150.879541] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1150.879548] ata1.00: irq_stat 0x40000008
[ 1150.879554] ata1.00: failed command: READ FPDMA QUEUED
[ 1150.879567] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1150.879570]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1150.879576] ata1.00: status: { DRDY ERR }
[ 1150.879580] ata1.00: error: { UNC }
[ 1150.882704] ata1.00: configured for UDMA/133
[ 1150.882720] sd 0:0:0:0: [sda] Unhandled sense code
[ 1150.882724] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1150.882730] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1150.882739] Descriptor sense data with sense descriptors (in hex):
[ 1150.882743]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1150.882761]         15 85 6c 13 
[ 1150.882769] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1150.882780] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1150.882796] end_request: I/O error, dev sda, sector 361065491
[ 1150.882819] ata1: EH complete
[ 1154.830644] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1154.830652] ata1.00: irq_stat 0x40000008
[ 1154.830660] ata1.00: failed command: READ FPDMA QUEUED
[ 1154.830673] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1154.830676]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1154.830682] ata1.00: status: { DRDY ERR }
[ 1154.830686] ata1.00: error: { UNC }
[ 1154.833971] ata1.00: configured for UDMA/133
[ 1154.833986] ata1: EH complete
[ 1158.643036] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1158.643045] ata1.00: irq_stat 0x40000008
[ 1158.643052] ata1.00: failed command: READ FPDMA QUEUED
[ 1158.643065] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1158.643068]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1158.643074] ata1.00: status: { DRDY ERR }
[ 1158.643078] ata1.00: error: { UNC }
[ 1158.646490] ata1.00: configured for UDMA/133
[ 1158.646497] ata1: EH complete
[ 1162.441488] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1162.441495] ata1.00: irq_stat 0x40000008
[ 1162.441502] ata1.00: failed command: READ FPDMA QUEUED
[ 1162.441515] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1162.441518]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1162.441524] ata1.00: status: { DRDY ERR }
[ 1162.441528] ata1.00: error: { UNC }
[ 1162.444870] ata1.00: configured for UDMA/133
[ 1162.444879] ata1: EH complete
[ 1166.228834] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1166.228841] ata1.00: irq_stat 0x40000008
[ 1166.228848] ata1.00: failed command: READ FPDMA QUEUED
[ 1166.228861] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1166.228863]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1166.228869] ata1.00: status: { DRDY ERR }
[ 1166.228873] ata1.00: error: { UNC }
[ 1166.232087] ata1.00: configured for UDMA/133
[ 1166.232101] ata1: EH complete
[ 1170.016180] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1170.016188] ata1.00: irq_stat 0x40000008
[ 1170.016195] ata1.00: failed command: READ FPDMA QUEUED
[ 1170.016208] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1170.016211]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1170.016217] ata1.00: status: { DRDY ERR }
[ 1170.016221] ata1.00: error: { UNC }
[ 1170.019588] ata1.00: configured for UDMA/133
[ 1170.019603] ata1: EH complete
[ 1173.803525] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1173.803532] ata1.00: irq_stat 0x40000008
[ 1173.803539] ata1.00: failed command: READ FPDMA QUEUED
[ 1173.803551] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1173.803554]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1173.803560] ata1.00: status: { DRDY ERR }
[ 1173.803564] ata1.00: error: { UNC }
[ 1173.806960] ata1.00: configured for UDMA/133
[ 1173.806974] sd 0:0:0:0: [sda] Unhandled sense code
[ 1173.806978] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1173.806984] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1173.806991] Descriptor sense data with sense descriptors (in hex):
[ 1173.806994]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1173.807008]         15 85 6c 13 
[ 1173.807014] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1173.807022] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1173.807036] end_request: I/O error, dev sda, sector 361065491
[ 1173.807055] ata1: EH complete
[ 1178.101772] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1178.101780] ata1.00: irq_stat 0x40000008
[ 1178.101788] ata1.00: failed command: READ FPDMA QUEUED
[ 1178.101801] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1178.101803]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1178.101810] ata1.00: status: { DRDY ERR }
[ 1178.101814] ata1.00: error: { UNC }
[ 1178.105112] ata1.00: configured for UDMA/133
[ 1178.105127] ata1: EH complete
[ 1181.878009] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1181.878018] ata1.00: irq_stat 0x40000008
[ 1181.878026] ata1.00: failed command: READ FPDMA QUEUED
[ 1181.878039] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1181.878041]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1181.878047] ata1.00: status: { DRDY ERR }
[ 1181.878051] ata1.00: error: { UNC }
[ 1181.881369] ata1.00: configured for UDMA/133
[ 1181.881384] ata1: EH complete
[ 1185.665373] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1185.665381] ata1.00: irq_stat 0x40000008
[ 1185.665389] ata1.00: failed command: READ FPDMA QUEUED
[ 1185.665402] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1185.665404]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1185.665410] ata1.00: status: { DRDY ERR }
[ 1185.665415] ata1.00: error: { UNC }
[ 1185.668629] ata1.00: configured for UDMA/133
[ 1185.668640] ata1: EH complete
[ 1189.430478] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1189.430486] ata1.00: irq_stat 0x40000008
[ 1189.430492] ata1.00: failed command: READ FPDMA QUEUED
[ 1189.430505] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1189.430507]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1189.430513] ata1.00: status: { DRDY ERR }
[ 1189.430517] ata1.00: error: { UNC }
[ 1189.433795] ata1.00: configured for UDMA/133
[ 1189.433812] ata1: EH complete
[ 1193.217822] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1193.217829] ata1.00: irq_stat 0x40000008
[ 1193.217836] ata1.00: failed command: READ FPDMA QUEUED
[ 1193.217848] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1193.217851]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1193.217857] ata1.00: status: { DRDY ERR }
[ 1193.217861] ata1.00: error: { UNC }
[ 1193.221058] ata1.00: configured for UDMA/133
[ 1193.221072] ata1: EH complete
[ 1197.005166] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1197.005173] ata1.00: irq_stat 0x40000008
[ 1197.005180] ata1.00: failed command: READ FPDMA QUEUED
[ 1197.005192] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1197.005195]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1197.005201] ata1.00: status: { DRDY ERR }
[ 1197.005205] ata1.00: error: { UNC }
[ 1197.008749] ata1.00: configured for UDMA/133
[ 1197.008767] sd 0:0:0:0: [sda] Unhandled sense code
[ 1197.008771] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1197.008778] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1197.008790] Descriptor sense data with sense descriptors (in hex):
[ 1197.008794]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1197.008810]         15 85 6c 13 
[ 1197.008816] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1197.008826] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1197.008840] end_request: I/O error, dev sda, sector 361065491
[ 1197.008865] ata1: EH complete
[ 1200.948004] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1200.948013] ata1.00: irq_stat 0x40000008
[ 1200.948021] ata1.00: failed command: READ FPDMA QUEUED
[ 1200.948034] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1200.948037]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1200.948043] ata1.00: status: { DRDY ERR }
[ 1200.948047] ata1.00: error: { UNC }
[ 1200.951346] ata1.00: configured for UDMA/133
[ 1200.951361] ata1: EH complete
[ 1204.724233] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1204.724241] ata1.00: irq_stat 0x40000008
[ 1204.724249] ata1.00: failed command: READ FPDMA QUEUED
[ 1204.724262] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1204.724264]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1204.724271] ata1.00: status: { DRDY ERR }
[ 1204.724275] ata1.00: error: { UNC }
[ 1204.727525] ata1.00: configured for UDMA/133
[ 1204.727540] ata1: EH complete
[ 1208.522693] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1208.522701] ata1.00: irq_stat 0x40000008
[ 1208.522708] ata1.00: failed command: READ FPDMA QUEUED
[ 1208.522721] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1208.522723]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1208.522729] ata1.00: status: { DRDY ERR }
[ 1208.522733] ata1.00: error: { UNC }
[ 1208.526352] ata1.00: configured for UDMA/133
[ 1208.526367] ata1: EH complete
[ 1212.332246] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1212.332253] ata1.00: irq_stat 0x40000008
[ 1212.332259] ata1.00: failed command: READ FPDMA QUEUED
[ 1212.332272] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1212.332274]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1212.332280] ata1.00: status: { DRDY ERR }
[ 1212.332284] ata1.00: error: { UNC }
[ 1212.335685] ata1.00: configured for UDMA/133
[ 1212.335698] ata1: EH complete
[ 1216.108487] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1216.108495] ata1.00: irq_stat 0x40000008
[ 1216.108502] ata1.00: failed command: READ FPDMA QUEUED
[ 1216.108516] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1216.108518]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1216.108524] ata1.00: status: { DRDY ERR }
[ 1216.108528] ata1.00: error: { UNC }
[ 1216.111764] ata1.00: configured for UDMA/133
[ 1216.111779] ata1: EH complete
[ 1219.918040] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1219.918047] ata1.00: irq_stat 0x40000008
[ 1219.918054] ata1.00: failed command: READ FPDMA QUEUED
[ 1219.918067] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1219.918070]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1219.918076] ata1.00: status: { DRDY ERR }
[ 1219.918080] ata1.00: error: { UNC }
[ 1219.921245] ata1.00: configured for UDMA/133
[ 1219.921260] sd 0:0:0:0: [sda] Unhandled sense code
[ 1219.921264] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1219.921271] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1219.921280] Descriptor sense data with sense descriptors (in hex):
[ 1219.921284]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1219.921300]         15 85 6c 13 
[ 1219.921305] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1219.921312] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1219.921323] end_request: I/O error, dev sda, sector 361065491
[ 1219.921339] ata1: EH complete
[ 1224.150606] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1224.150615] ata1.00: irq_stat 0x40000008
[ 1224.150622] ata1.00: failed command: READ FPDMA QUEUED
[ 1224.150635] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1224.150638]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1224.150644] ata1.00: status: { DRDY ERR }
[ 1224.150648] ata1.00: error: { UNC }
[ 1224.154092] ata1.00: configured for UDMA/133
[ 1224.154107] ata1: EH complete
[ 1227.948103] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1227.948112] ata1.00: irq_stat 0x40000008
[ 1227.948119] ata1.00: failed command: READ FPDMA QUEUED
[ 1227.948132] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1227.948135]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1227.948141] ata1.00: status: { DRDY ERR }
[ 1227.948145] ata1.00: error: { UNC }
[ 1227.951474] ata1.00: configured for UDMA/133
[ 1227.951488] ata1: EH complete
[ 1231.735445] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1231.735452] ata1.00: irq_stat 0x40000008
[ 1231.735459] ata1.00: failed command: READ FPDMA QUEUED
[ 1231.735471] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1231.735474]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1231.735480] ata1.00: status: { DRDY ERR }
[ 1231.735484] ata1.00: error: { UNC }
[ 1231.738837] ata1.00: configured for UDMA/133
[ 1231.738851] ata1: EH complete
[ 1235.544999] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1235.545007] ata1.00: irq_stat 0x40000008
[ 1235.545013] ata1.00: failed command: READ FPDMA QUEUED
[ 1235.545026] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1235.545029]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1235.545035] ata1.00: status: { DRDY ERR }
[ 1235.545039] ata1.00: error: { UNC }
[ 1235.548352] ata1.00: configured for UDMA/133
[ 1235.548366] ata1: EH complete
[ 1239.332351] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1239.332359] ata1.00: irq_stat 0x40000008
[ 1239.332365] ata1.00: failed command: READ FPDMA QUEUED
[ 1239.332378] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1239.332381]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1239.332387] ata1.00: status: { DRDY ERR }
[ 1239.332391] ata1.00: error: { UNC }
[ 1239.335782] ata1.00: configured for UDMA/133
[ 1239.335795] ata1: EH complete
[ 1243.153013] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1243.153020] ata1.00: irq_stat 0x40000008
[ 1243.153026] ata1.00: failed command: READ FPDMA QUEUED
[ 1243.153039] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1243.153041]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1243.153047] ata1.00: status: { DRDY ERR }
[ 1243.153051] ata1.00: error: { UNC }
[ 1243.156420] ata1.00: configured for UDMA/133
[ 1243.156438] sd 0:0:0:0: [sda] Unhandled sense code
[ 1243.156443] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1243.156449] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1243.156461] Descriptor sense data with sense descriptors (in hex):
[ 1243.156465]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1243.156481]         15 85 6c 13 
[ 1243.156488] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1243.156497] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1243.156512] end_request: I/O error, dev sda, sector 361065491
[ 1243.156535] ata1: EH complete
[ 1247.100882] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1247.100891] ata1.00: irq_stat 0x40000008
[ 1247.100898] ata1.00: failed command: READ FPDMA QUEUED
[ 1247.100911] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1247.100913]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1247.100919] ata1.00: status: { DRDY ERR }
[ 1247.100923] ata1.00: error: { UNC }
[ 1247.104237] ata1.00: configured for UDMA/133
[ 1247.104253] ata1: EH complete
[ 1250.894301] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1250.894310] ata1.00: irq_stat 0x40000008
[ 1250.894318] ata1.00: failed command: READ FPDMA QUEUED
[ 1250.894331] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1250.894333]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1250.894339] ata1.00: status: { DRDY ERR }
[ 1250.894344] ata1.00: error: { UNC }
[ 1250.897607] ata1.00: configured for UDMA/133
[ 1250.897622] ata1: EH complete
[ 1254.703853] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1254.703860] ata1.00: irq_stat 0x40000008
[ 1254.703866] ata1.00: failed command: READ FPDMA QUEUED
[ 1254.703879] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1254.703881]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1254.703887] ata1.00: status: { DRDY ERR }
[ 1254.703891] ata1.00: error: { UNC }
[ 1254.707286] ata1.00: configured for UDMA/133
[ 1254.707300] ata1: EH complete
[ 1258.524516] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1258.524523] ata1.00: irq_stat 0x40000008
[ 1258.524530] ata1.00: failed command: READ FPDMA QUEUED
[ 1258.524542] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1258.524545]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1258.524551] ata1.00: status: { DRDY ERR }
[ 1258.524555] ata1.00: error: { UNC }
[ 1258.527858] ata1.00: configured for UDMA/133
[ 1258.527873] ata1: EH complete
[ 1262.322953] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1262.322960] ata1.00: irq_stat 0x40000008
[ 1262.322967] ata1.00: failed command: READ FPDMA QUEUED
[ 1262.322980] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1262.322982]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1262.322988] ata1.00: status: { DRDY ERR }
[ 1262.322992] ata1.00: error: { UNC }
[ 1262.326353] ata1.00: configured for UDMA/133
[ 1262.326367] ata1: EH complete
[ 1266.088090] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1266.088098] ata1.00: irq_stat 0x40000008
[ 1266.088105] ata1.00: failed command: READ FPDMA QUEUED
[ 1266.088118] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1266.088121]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1266.088127] ata1.00: status: { DRDY ERR }
[ 1266.088131] ata1.00: error: { UNC }
[ 1266.091412] ata1.00: configured for UDMA/133
[ 1266.091431] sd 0:0:0:0: [sda] Unhandled sense code
[ 1266.091435] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1266.091442] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1266.091454] Descriptor sense data with sense descriptors (in hex):
[ 1266.091458]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1266.091474]         15 85 6c 13 
[ 1266.091481] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1266.091490] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1266.091505] end_request: I/O error, dev sda, sector 361065491
[ 1266.091528] ata1: EH complete
[ 1270.071041] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1270.071049] ata1.00: irq_stat 0x40000008
[ 1270.071057] ata1.00: failed command: READ FPDMA QUEUED
[ 1270.071070] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1270.071073]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1270.071079] ata1.00: status: { DRDY ERR }
[ 1270.071083] ata1.00: error: { UNC }
[ 1270.074445] ata1.00: configured for UDMA/133
[ 1270.074460] ata1: EH complete
[ 1273.873808] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1273.873817] ata1.00: irq_stat 0x40000008
[ 1273.873825] ata1.00: failed command: READ FPDMA QUEUED
[ 1273.873838] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1273.873841]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1273.873847] ata1.00: status: { DRDY ERR }
[ 1273.873851] ata1.00: error: { UNC }
[ 1273.877358] ata1.00: configured for UDMA/133
[ 1273.877372] ata1: EH complete
[ 1277.661168] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1277.661177] ata1.00: irq_stat 0x40000008
[ 1277.661184] ata1.00: failed command: READ FPDMA QUEUED
[ 1277.661197] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1277.661200]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1277.661206] ata1.00: status: { DRDY ERR }
[ 1277.661210] ata1.00: error: { UNC }
[ 1277.664550] ata1.00: configured for UDMA/133
[ 1277.664566] ata1: EH complete
[ 1281.448502] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1281.448510] ata1.00: irq_stat 0x40000008
[ 1281.448516] ata1.00: failed command: READ FPDMA QUEUED
[ 1281.448529] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1281.448532]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1281.448538] ata1.00: status: { DRDY ERR }
[ 1281.448542] ata1.00: error: { UNC }
[ 1281.451909] ata1.00: configured for UDMA/133
[ 1281.451923] ata1: EH complete
[ 1285.235873] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1285.235881] ata1.00: irq_stat 0x40000008
[ 1285.235888] ata1.00: failed command: READ FPDMA QUEUED
[ 1285.235901] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1285.235903]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1285.235909] ata1.00: status: { DRDY ERR }
[ 1285.235913] ata1.00: error: { UNC }
[ 1285.239163] ata1.00: configured for UDMA/133
[ 1285.239179] ata1: EH complete
[ 1289.023188] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1289.023195] ata1.00: irq_stat 0x40000008
[ 1289.023203] ata1.00: failed command: READ FPDMA QUEUED
[ 1289.023216] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1289.023219]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1289.023225] ata1.00: status: { DRDY ERR }
[ 1289.023229] ata1.00: error: { UNC }
[ 1289.026714] ata1.00: configured for UDMA/133
[ 1289.026733] sd 0:0:0:0: [sda] Unhandled sense code
[ 1289.026738] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1289.026744] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1289.026753] Descriptor sense data with sense descriptors (in hex):
[ 1289.026757]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1289.026775]         15 85 6c 13 
[ 1289.026783] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1289.026794] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1289.026810] end_request: I/O error, dev sda, sector 361065491
[ 1289.026836] ata1: EH complete
[ 1292.939573] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1292.939581] ata1.00: irq_stat 0x40000008
[ 1292.939588] ata1.00: failed command: READ FPDMA QUEUED
[ 1292.939601] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1292.939604]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1292.939610] ata1.00: status: { DRDY ERR }
[ 1292.939614] ata1.00: error: { UNC }
[ 1292.942960] ata1.00: configured for UDMA/133
[ 1292.942980] ata1: EH complete
[ 1296.742277] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1296.742285] ata1.00: irq_stat 0x40000008
[ 1296.742292] ata1.00: failed command: READ FPDMA QUEUED
[ 1296.742306] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1296.742308]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1296.742314] ata1.00: status: { DRDY ERR }
[ 1296.742319] ata1.00: error: { UNC }
[ 1296.745577] ata1.00: configured for UDMA/133
[ 1296.745593] ata1: EH complete
[ 1300.529605] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1300.529612] ata1.00: irq_stat 0x40000008
[ 1300.529619] ata1.00: failed command: READ FPDMA QUEUED
[ 1300.529632] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1300.529635]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1300.529640] ata1.00: status: { DRDY ERR }
[ 1300.529645] ata1.00: error: { UNC }
[ 1300.532944] ata1.00: configured for UDMA/133
[ 1300.532958] ata1: EH complete
[ 1304.339159] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1304.339166] ata1.00: irq_stat 0x40000008
[ 1304.339173] ata1.00: failed command: READ FPDMA QUEUED
[ 1304.339186] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1304.339189]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1304.339195] ata1.00: status: { DRDY ERR }
[ 1304.339199] ata1.00: error: { UNC }
[ 1304.342481] ata1.00: configured for UDMA/133
[ 1304.342496] ata1: EH complete
[ 1308.148742] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1308.148751] ata1.00: irq_stat 0x40000008
[ 1308.148758] ata1.00: failed command: READ FPDMA QUEUED
[ 1308.148771] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1308.148774]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1308.148780] ata1.00: status: { DRDY ERR }
[ 1308.148784] ata1.00: error: { UNC }
[ 1308.152202] ata1.00: configured for UDMA/133
[ 1308.152216] ata1: EH complete
[ 1311.969377] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1311.969386] ata1.00: irq_stat 0x40000008
[ 1311.969393] ata1.00: failed command: READ FPDMA QUEUED
[ 1311.969406] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1311.969409]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1311.969415] ata1.00: status: { DRDY ERR }
[ 1311.969419] ata1.00: error: { UNC }
[ 1311.972614] ata1.00: configured for UDMA/133
[ 1311.972632] sd 0:0:0:0: [sda] Unhandled sense code
[ 1311.972635] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1311.972641] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1311.972648] Descriptor sense data with sense descriptors (in hex):
[ 1311.972651]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1311.972665]         15 85 6c 13 
[ 1311.972671] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1311.972679] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1311.972693] end_request: I/O error, dev sda, sector 361065491
[ 1311.972715] ata1: EH complete
[ 1315.874727] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1315.874736] ata1.00: irq_stat 0x40000008
[ 1315.874744] ata1.00: failed command: READ FPDMA QUEUED
[ 1315.874757] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1315.874759]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1315.874765] ata1.00: status: { DRDY ERR }
[ 1315.874770] ata1.00: error: { UNC }
[ 1315.878104] ata1.00: configured for UDMA/133
[ 1315.878119] ata1: EH complete
[ 1319.655163] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1319.655172] ata1.00: irq_stat 0x40000008
[ 1319.655179] ata1.00: failed command: READ FPDMA QUEUED
[ 1319.655192] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1319.655195]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1319.655201] ata1.00: status: { DRDY ERR }
[ 1319.655205] ata1.00: error: { UNC }
[ 1319.658659] ata1.00: configured for UDMA/133
[ 1319.658674] ata1: EH complete
[ 1323.453584] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1323.453593] ata1.00: irq_stat 0x40000008
[ 1323.453601] ata1.00: failed command: READ FPDMA QUEUED
[ 1323.453614] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1323.453617]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1323.453623] ata1.00: status: { DRDY ERR }
[ 1323.453627] ata1.00: error: { UNC }
[ 1323.456920] ata1.00: configured for UDMA/133
[ 1323.456937] ata1: EH complete
[ 1327.240928] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1327.240935] ata1.00: irq_stat 0x40000008
[ 1327.240943] ata1.00: failed command: READ FPDMA QUEUED
[ 1327.240955] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1327.240958]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1327.240964] ata1.00: status: { DRDY ERR }
[ 1327.240968] ata1.00: error: { UNC }
[ 1327.244278] ata1.00: configured for UDMA/133
[ 1327.244292] ata1: EH complete
[ 1331.028296] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1331.028303] ata1.00: irq_stat 0x40000008
[ 1331.028309] ata1.00: failed command: READ FPDMA QUEUED
[ 1331.028321] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1331.028323]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1331.028329] ata1.00: status: { DRDY ERR }
[ 1331.028333] ata1.00: error: { UNC }
[ 1331.031709] ata1.00: configured for UDMA/133
[ 1331.031721] ata1: EH complete
[ 1334.793399] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1334.793405] ata1.00: irq_stat 0x40000008
[ 1334.793411] ata1.00: failed command: READ FPDMA QUEUED
[ 1334.793423] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1334.793426]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1334.793432] ata1.00: status: { DRDY ERR }
[ 1334.793436] ata1.00: error: { UNC }
[ 1334.797002] ata1.00: configured for UDMA/133
[ 1334.797012] sd 0:0:0:0: [sda] Unhandled sense code
[ 1334.797014] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1334.797018] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1334.797023] Descriptor sense data with sense descriptors (in hex):
[ 1334.797025]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1334.797033]         15 85 6c 13 
[ 1334.797037] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1334.797042] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1334.797050] end_request: I/O error, dev sda, sector 361065491
[ 1334.797064] ata1: EH complete
[ 1338.625170] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1338.625180] ata1.00: irq_stat 0x40000008
[ 1338.625187] ata1.00: failed command: READ FPDMA QUEUED
[ 1338.625200] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1338.625202]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1338.625208] ata1.00: status: { DRDY ERR }
[ 1338.625212] ata1.00: error: { UNC }
[ 1338.628480] ata1.00: configured for UDMA/133
[ 1338.628494] ata1: EH complete
[ 1342.434723] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1342.434732] ata1.00: irq_stat 0x40000008
[ 1342.434739] ata1.00: failed command: READ FPDMA QUEUED
[ 1342.434752] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1342.434755]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1342.434761] ata1.00: status: { DRDY ERR }
[ 1342.434765] ata1.00: error: { UNC }
[ 1342.438023] ata1.00: configured for UDMA/133
[ 1342.438038] ata1: EH complete
[ 1346.222070] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1346.222076] ata1.00: irq_stat 0x40000008
[ 1346.222083] ata1.00: failed command: READ FPDMA QUEUED
[ 1346.222095] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1346.222098]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1346.222104] ata1.00: status: { DRDY ERR }
[ 1346.222108] ata1.00: error: { UNC }
[ 1346.225478] ata1.00: configured for UDMA/133
[ 1346.225491] ata1: EH complete
[ 1350.009392] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1350.009398] ata1.00: irq_stat 0x40000008
[ 1350.009404] ata1.00: failed command: READ FPDMA QUEUED
[ 1350.009416] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1350.009418]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1350.009424] ata1.00: status: { DRDY ERR }
[ 1350.009428] ata1.00: error: { UNC }
[ 1350.012841] ata1.00: configured for UDMA/133
[ 1350.012852] ata1: EH complete
[ 1353.807842] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1353.807849] ata1.00: irq_stat 0x40000008
[ 1353.807855] ata1.00: failed command: READ FPDMA QUEUED
[ 1353.807867] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1353.807869]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1353.807875] ata1.00: status: { DRDY ERR }
[ 1353.807879] ata1.00: error: { UNC }
[ 1353.811155] ata1.00: configured for UDMA/133
[ 1353.811168] ata1: EH complete
[ 1357.584092] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1357.584098] ata1.00: irq_stat 0x40000008
[ 1357.584104] ata1.00: failed command: READ FPDMA QUEUED
[ 1357.584117] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1357.584119]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1357.584125] ata1.00: status: { DRDY ERR }
[ 1357.584129] ata1.00: error: { UNC }
[ 1357.587495] ata1.00: configured for UDMA/133
[ 1357.587512] sd 0:0:0:0: [sda] Unhandled sense code
[ 1357.587516] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1357.587523] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1357.587532] Descriptor sense data with sense descriptors (in hex):
[ 1357.587536]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1357.587554]         15 85 6c 13 
[ 1357.587562] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1357.587572] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1357.587589] end_request: I/O error, dev sda, sector 361065491
[ 1357.587603] ata1: EH complete
[ 1361.589527] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1361.589536] ata1.00: irq_stat 0x40000008
[ 1361.589543] ata1.00: failed command: READ FPDMA QUEUED
[ 1361.589556] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1361.589558]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1361.589564] ata1.00: status: { DRDY ERR }
[ 1361.589568] ata1.00: error: { UNC }
[ 1361.592908] ata1.00: configured for UDMA/133
[ 1361.592922] ata1: EH complete
[ 1365.392027] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1365.392036] ata1.00: irq_stat 0x40000008
[ 1365.392043] ata1.00: failed command: READ FPDMA QUEUED
[ 1365.392056] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1365.392059]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1365.392065] ata1.00: status: { DRDY ERR }
[ 1365.392069] ata1.00: error: { UNC }
[ 1365.395434] ata1.00: configured for UDMA/133
[ 1365.395448] ata1: EH complete
[ 1369.179379] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1369.179385] ata1.00: irq_stat 0x40000008
[ 1369.179391] ata1.00: failed command: READ FPDMA QUEUED
[ 1369.179403] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1369.179406]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1369.179412] ata1.00: status: { DRDY ERR }
[ 1369.179416] ata1.00: error: { UNC }
[ 1369.182846] ata1.00: configured for UDMA/133
[ 1369.182860] ata1: EH complete
[ 1372.988938] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1372.988946] ata1.00: irq_stat 0x40000008
[ 1372.988953] ata1.00: failed command: READ FPDMA QUEUED
[ 1372.988966] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1372.988968]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1372.988975] ata1.00: status: { DRDY ERR }
[ 1372.988979] ata1.00: error: { UNC }
[ 1372.992322] ata1.00: configured for UDMA/133
[ 1372.992341] ata1: EH complete
[ 1376.765158] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1376.765164] ata1.00: irq_stat 0x40000008
[ 1376.765170] ata1.00: failed command: READ FPDMA QUEUED
[ 1376.765182] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1376.765185]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1376.765191] ata1.00: status: { DRDY ERR }
[ 1376.765195] ata1.00: error: { UNC }
[ 1376.768646] ata1.00: configured for UDMA/133
[ 1376.768660] ata1: EH complete
[ 1380.563645] ata1.00: exception Emask 0x0 SAct 0x7ff SErr 0x0 action 0x0
[ 1380.563653] ata1.00: irq_stat 0x40000008
[ 1380.563660] ata1.00: failed command: READ FPDMA QUEUED
[ 1380.563673] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1380.563676]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1380.563682] ata1.00: status: { DRDY ERR }
[ 1380.563686] ata1.00: error: { UNC }
[ 1380.567034] ata1.00: configured for UDMA/133
[ 1380.567056] sd 0:0:0:0: [sda] Unhandled sense code
[ 1380.567060] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1380.567067] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1380.567076] Descriptor sense data with sense descriptors (in hex):
[ 1380.567080]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1380.567098]         15 85 6c 13 
[ 1380.567106] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1380.567116] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1380.567132] end_request: I/O error, dev sda, sector 361065491
[ 1380.567167] ata1: EH complete
[ 1384.550889] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1384.550897] ata1.00: irq_stat 0x40000008
[ 1384.550904] ata1.00: failed command: READ FPDMA QUEUED
[ 1384.550917] ata1.00: cmd 60/08:08:10:6c:85/00:00:15:00:00/40 tag 1 ncq 4096 in
[ 1384.550920]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1384.550926] ata1.00: status: { DRDY ERR }
[ 1384.550930] ata1.00: error: { UNC }
[ 1384.554201] ata1.00: configured for UDMA/133
[ 1384.554215] ata1: EH complete
[ 1388.338242] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1388.338251] ata1.00: irq_stat 0x40000008
[ 1388.338258] ata1.00: failed command: READ FPDMA QUEUED
[ 1388.338271] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1388.338274]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1388.338280] ata1.00: status: { DRDY ERR }
[ 1388.338284] ata1.00: error: { UNC }
[ 1388.341599] ata1.00: configured for UDMA/133
[ 1388.341614] ata1: EH complete
[ 1392.092270] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1392.092278] ata1.00: irq_stat 0x40000008
[ 1392.092284] ata1.00: failed command: READ FPDMA QUEUED
[ 1392.092297] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1392.092300]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1392.092306] ata1.00: status: { DRDY ERR }
[ 1392.092310] ata1.00: error: { UNC }
[ 1392.095796] ata1.00: configured for UDMA/133
[ 1392.095812] ata1: EH complete
[ 1395.890709] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1395.890716] ata1.00: irq_stat 0x40000008
[ 1395.890723] ata1.00: failed command: READ FPDMA QUEUED
[ 1395.890736] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1395.890738]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1395.890744] ata1.00: status: { DRDY ERR }
[ 1395.890748] ata1.00: error: { UNC }
[ 1395.894218] ata1.00: configured for UDMA/133
[ 1395.894232] ata1: EH complete
[ 1399.700295] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1399.700303] ata1.00: irq_stat 0x40000008
[ 1399.700310] ata1.00: failed command: READ FPDMA QUEUED
[ 1399.700323] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1399.700326]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1399.700332] ata1.00: status: { DRDY ERR }
[ 1399.700336] ata1.00: error: { UNC }
[ 1399.703585] ata1.00: configured for UDMA/133
[ 1399.703603] ata1: EH complete
[ 1403.454306] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1403.454314] ata1.00: irq_stat 0x40000008
[ 1403.454321] ata1.00: failed command: READ FPDMA QUEUED
[ 1403.454334] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1403.454337]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1403.454343] ata1.00: status: { DRDY ERR }
[ 1403.454347] ata1.00: error: { UNC }
[ 1403.457605] ata1.00: configured for UDMA/133
[ 1403.457626] sd 0:0:0:0: [sda] Unhandled sense code
[ 1403.457630] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1403.457637] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1403.457649] Descriptor sense data with sense descriptors (in hex):
[ 1403.457653]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1403.457668]         15 85 6c 13 
[ 1403.457675] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1403.457684] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 15 85 6c 10 00 00 08 00
[ 1403.457699] end_request: I/O error, dev sda, sector 361065491
[ 1403.457723] ata1: EH complete
[ 1407.386061] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1407.386070] ata1.00: irq_stat 0x40000008
[ 1407.386077] ata1.00: failed command: READ FPDMA QUEUED
[ 1407.386090] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1407.386093]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1407.386099] ata1.00: status: { DRDY ERR }
[ 1407.386103] ata1.00: error: { UNC }
[ 1407.389200] ata1.00: configured for UDMA/133
[ 1407.389220] ata1: EH complete
[ 1411.228914] ata1.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[ 1411.228923] ata1.00: irq_stat 0x40000008
[ 1411.228930] ata1.00: failed command: READ FPDMA QUEUED
[ 1411.228943] ata1.00: cmd 60/08:10:10:6c:85/00:00:15:00:00/40 tag 2 ncq 4096 in
[ 1411.228946]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1411.228952] ata1.00: status: { DRDY ERR }
[ 1411.228956] ata1.00: error: { UNC }
[ 1411.232184] ata1.00: configured for UDMA/133
[ 1411.232200] ata1: EH complete
[ 1415.016251] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[ 1415.016259] ata1.00: irq_stat 0x40000008
[ 1415.016265] ata1.00: failed command: READ FPDMA QUEUED
[ 1415.016278] ata1.00: cmd 60/08:00:10:6c:85/00:00:15:00:00/40 tag 0 ncq 4096 in
[ 1415.016281]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1415.016287] ata1.00: status: { DRDY ERR }
[ 1415.016291] ata1.00: error: { UNC }
[ 1415.019551] ata1.00: configured for UDMA/133
[ 1415.019569] ata1: EH complete
[ 1418.836912] ata1.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[ 1418.836919] ata1.00: irq_stat 0x40000008
[ 1418.836927] ata1.00: failed command: READ FPDMA QUEUED
[ 1418.836940] ata1.00: cmd 60/08:10:10:6c:85/00:00:15:00:00/40 tag 2 ncq 4096 in
[ 1418.836942]          res 51/40:08:13:6c:85/00:00:15:00:00/40 Emask 0x409 (media error) <F>
[ 1418.836948] ata1.00: status: { DRDY ERR }
[ 1418.836952] ata1.00: error: { UNC }
[ 1418.840064] ata1.00: configured for UDMA/133
[ 1418.840080] ata1: EH complete
```

---

### Post by pqwoerituytrueiwoq on 2011-11-01
have you ever altered any of the partitions after the install?
personally i would fire up a live usb and copy all my important stuff and reload the os
the 1st line in dmesg should be start with [0.0
was there a flash drive plunged in during the boot?

---

### Post by FLCL on 2011-11-03
None of the partitions have been touched since install, I'll probably follow suit with you're idea and backup everything important before a new install.
Nothing was plugged in when I booted it up, but when I was handed the laptop it had a DVD in the drive and a memory card inserted.

---

