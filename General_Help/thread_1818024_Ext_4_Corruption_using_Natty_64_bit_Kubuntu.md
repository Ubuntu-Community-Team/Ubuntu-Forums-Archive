---
title: "Ext 4 Corruption using Natty 64 bit Kubuntu"
date: 2011-08-04
forum: General Help
---

### Post by imperial_oz on 2011-08-04
I'm having a problem that I've not seen before, in that I ma constantly getting corrupted Ext 4 filesystems on my / and /home partitions. I am having to boot using a cd rom and run fsck -y on at least one of these partitions almost daily (mainly / partition)

Looking at the system log, I'm seeing stuff like this:

04/08/11 04:28:37 PM	Valkyrie	kernel	[   28.090570] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098006] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098012] ata1.01: failed command: READ DMA EXT
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098018] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098020]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098023] ata1.01: status: { DRDY ERR }
04/08/11 04:36:54 PM	Valkyrie	kernel	[  524.098025] ata1.01: error: { UNC }
04/08/11 04:36:55 PM	Valkyrie	kernel	[  524.192019] ata1.00: configured for UDMA/133
04/08/11 04:36:55 PM	Valkyrie	kernel	[  524.211687] ata1.01: configured for UDMA/133
04/08/11 04:36:55 PM	Valkyrie	kernel	[  524.211709] ata1: EH complete
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917630] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917635] ata1.01: failed command: READ DMA EXT
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917642] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917644]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917647] ata1.01: status: { DRDY ERR }
04/08/11 04:36:56 PM	Valkyrie	kernel	[  525.917649] ata1.01: error: { UNC }
04/08/11 04:36:56 PM	Valkyrie	kernel	[  526.010963] ata1.00: configured for UDMA/133
04/08/11 04:36:56 PM	Valkyrie	kernel	[  526.026317] ata1.01: configured for UDMA/133
04/08/11 04:36:56 PM	Valkyrie	kernel	[  526.026340] ata1: EH complete
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729267] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729270] ata1.01: failed command: READ DMA EXT
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729274] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729274]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729276] ata1.01: status: { DRDY ERR }
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.729277] ata1.01: error: { UNC }
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.813336] ata1.00: configured for UDMA/133
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.831986] ata1.01: configured for UDMA/133
04/08/11 04:36:58 PM	Valkyrie	kernel	[  527.832009] ata1: EH complete
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531915] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531917] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531920] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531921]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531922] ata1.01: status: { DRDY ERR }
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.531923] ata1.01: error: { UNC }
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.615715] ata1.00: configured for UDMA/133
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.636638] ata1.01: configured for UDMA/133
04/08/11 04:37:00 PM	Valkyrie	kernel	[  529.636660] ata1: EH complete
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335603] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335609] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335616] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335617]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335620] ata1.01: status: { DRDY ERR }
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.335622] ata1.01: error: { UNC }
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.418090] ata1.00: configured for UDMA/133
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.431301] ata1.01: configured for UDMA/133
04/08/11 04:37:02 PM	Valkyrie	kernel	[  531.431322] ata1: EH complete
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130259] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130265] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130271] ata1.01: cmd 25/00:40:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 32768 in
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130273]          res 51/40:2f:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130276] ata1.01: status: { DRDY ERR }
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.130278] ata1.01: error: { UNC }
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.220469] ata1.00: configured for UDMA/133
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235959] ata1.01: configured for UDMA/133
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235984] sd 0:0:1:0: [sdb] Unhandled sense code
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235987] sd 0:0:1:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235990] sd 0:0:1:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235995] Descriptor sense data with sense descriptors (in hex):
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.235997]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.236014]         4f 6c 0d 85 
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.236019] sd 0:0:1:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.236026] sd 0:0:1:0: [sdb] CDB: Read(10): 28 00 4f 6c 0d 80 00 00 40 00
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.236039] end_request: I/O error, dev sdb, sector 1332481413
04/08/11 04:37:04 PM	Valkyrie	kernel	[  533.236062] ata1: EH complete
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747399] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747404] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747411] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747413]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747416] ata1.01: status: { DRDY ERR }
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.747418] ata1.01: error: { UNC }
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.828542] ata1.00: configured for UDMA/133
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.849206] ata1.01: configured for UDMA/133
04/08/11 04:37:06 PM	Valkyrie	kernel	[  535.849224] ata1: EH complete
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551077] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551081] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551087] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551088]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551090] ata1.01: status: { DRDY ERR }
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.551092] ata1.01: error: { UNC }
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.630934] ata1.00: configured for UDMA/133
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.643822] ata1.01: configured for UDMA/133
04/08/11 04:37:08 PM	Valkyrie	kernel	[  537.643840] ata1: EH complete
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345765] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345769] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345773] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345774]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345777] ata1.01: status: { DRDY ERR }
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.345778] ata1.01: error: { UNC }
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.424960] ata1.00: configured for UDMA/133
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.438464] ata1.01: configured for UDMA/133
04/08/11 04:37:10 PM	Valkyrie	kernel	[  539.438479] ata1: EH complete
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140399] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140404] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140411] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140412]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140415] ata1.01: status: { DRDY ERR }
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.140418] ata1.01: error: { UNC }
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.227419] ata1.00: configured for UDMA/133
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.243117] ata1.01: configured for UDMA/133
04/08/11 04:37:12 PM	Valkyrie	kernel	[  541.243131] ata1: EH complete
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944054] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944056] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944060] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944061]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944062] ata1.01: status: { DRDY ERR }
04/08/11 04:37:13 PM	Valkyrie	kernel	[  542.944063] ata1.01: error: { UNC }
04/08/11 04:37:13 PM	Valkyrie	kernel	[  543.029723] ata1.00: configured for UDMA/133
04/08/11 04:37:13 PM	Valkyrie	kernel	[  543.047771] ata1.01: configured for UDMA/133
04/08/11 04:37:13 PM	Valkyrie	kernel	[  543.047780] ata1: EH complete
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746718] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746723] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746730] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746732]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746735] ata1.01: status: { DRDY ERR }
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.746738] ata1.01: error: { UNC }
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.832092] ata1.00: configured for UDMA/133
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852442] ata1.01: configured for UDMA/133
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852459] sd 0:0:1:0: [sdb] Unhandled sense code
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852461] sd 0:0:1:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852465] sd 0:0:1:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852470] Descriptor sense data with sense descriptors (in hex):
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852472]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852487]         4f 6c 0d 85 
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852489] sd 0:0:1:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852492] sd 0:0:1:0: [sdb] CDB: Read(10): 28 00 4f 6c 0d 80 00 00 08 00
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852496] end_request: I/O error, dev sdb, sector 1332481413
04/08/11 04:37:15 PM	Valkyrie	kernel	[  544.852507] ata1: EH complete
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313840] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313845] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313852] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313853]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313856] ata1.01: status: { DRDY ERR }
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.313859] ata1.01: error: { UNC }
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.395499] ata1.00: configured for UDMA/133
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.408574] ata1.01: configured for UDMA/133
04/08/11 04:37:24 PM	Valkyrie	kernel	[  553.408585] ata1: EH complete
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109497] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109501] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109506] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109507]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109509] ata1.01: status: { DRDY ERR }
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.109510] ata1.01: error: { UNC }
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.189522] ata1.00: configured for UDMA/133
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.203244] ata1.01: configured for UDMA/133
04/08/11 04:37:26 PM	Valkyrie	kernel	[  555.203259] ata1: EH complete
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904253] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904258] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904263] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904264]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904267] ata1.01: status: { DRDY ERR }
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.904268] ata1.01: error: { UNC }
04/08/11 04:37:27 PM	Valkyrie	kernel	[  556.991984] ata1.00: configured for UDMA/133
04/08/11 04:37:27 PM	Valkyrie	kernel	[  557.007970] ata1.01: configured for UDMA/133
04/08/11 04:37:27 PM	Valkyrie	kernel	[  557.007985] ata1: EH complete
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706840] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706846] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706853] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706854]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706857] ata1.01: status: { DRDY ERR }
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.706859] ata1.01: error: { UNC }
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.794324] ata1.00: configured for UDMA/133
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.812555] ata1.01: configured for UDMA/133
04/08/11 04:37:29 PM	Valkyrie	kernel	[  558.812576] ata1: EH complete
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510491] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510494] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510499] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510500]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510502] ata1.01: status: { DRDY ERR }
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.510504] ata1.01: error: { UNC }
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.596661] ata1.00: configured for UDMA/133
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.608228] ata1.01: configured for UDMA/133
04/08/11 04:37:31 PM	Valkyrie	kernel	[  560.608251] ata1: EH complete
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313196] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313202] ata1.01: failed command: READ DMA EXT
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313209] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313210]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313213] ata1.01: status: { DRDY ERR }
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.313216] ata1.01: error: { UNC }
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.399068] ata1.00: configured for UDMA/133
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412935] ata1.01: configured for UDMA/133
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412962] sd 0:0:1:0: [sdb] Unhandled sense code
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412964] sd 0:0:1:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412968] sd 0:0:1:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412971] Descriptor sense data with sense descriptors (in hex):
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412973]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412980]         4f 6c 0d 85 
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412983] sd 0:0:1:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412987] sd 0:0:1:0: [sdb] CDB: Read(10): 28 00 4f 6c 0d 80 00 00 08 00
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.412994] end_request: I/O error, dev sdb, sector 1332481413
04/08/11 04:37:33 PM	Valkyrie	kernel	[  562.413010] ata1: EH complete
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698239] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698242] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698245] ata1.01: cmd 25/00:08:80:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698246]          res 51/40:00:85:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698247] ata1.01: status: { DRDY ERR }
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.698248] ata1.01: error: { UNC }
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.779106] ata1.00: configured for UDMA/133
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.789982] ata1.01: configured for UDMA/133
04/08/11 04:38:19 PM	Valkyrie	kernel	[  608.789999] ata1: EH complete
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517844] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517850] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517857] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517858]          res 51/40:00:9e:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517861] ata1.01: status: { DRDY ERR }
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.517863] ata1.01: error: { UNC }
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.606438] ata1.00: configured for UDMA/133
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.624577] ata1.01: configured for UDMA/133
04/08/11 04:38:21 PM	Valkyrie	kernel	[  610.624592] ata1: EH complete
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944316] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944321] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944328] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944330]          res 51/40:00:9f:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944333] ata1.01: status: { DRDY ERR }
04/08/11 04:38:24 PM	Valkyrie	kernel	[  612.944335] ata1.01: error: { UNC }
04/08/11 04:38:24 PM	Valkyrie	kernel	[  613.031781] ata1.00: configured for UDMA/133
04/08/11 04:38:24 PM	Valkyrie	kernel	[  613.048083] ata1.01: configured for UDMA/133
04/08/11 04:38:24 PM	Valkyrie	kernel	[  613.048099] ata1: EH complete
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747031] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747037] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747044] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747045]          res 51/40:00:9e:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747049] ata1.01: status: { DRDY ERR }
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.747051] ata1.01: error: { UNC }
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.834076] ata1.00: configured for UDMA/133
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.852687] ata1.01: configured for UDMA/133
04/08/11 04:38:25 PM	Valkyrie	kernel	[  614.852699] ata1: EH complete
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550697] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550702] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550709] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550710]          res 51/40:00:9e:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550713] ata1.01: status: { DRDY ERR }
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.550715] ata1.01: error: { UNC }
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.636451] ata1.00: configured for UDMA/133
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.647393] ata1.01: configured for UDMA/133
04/08/11 04:38:27 PM	Valkyrie	kernel	[  616.647408] ata1: EH complete
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351089] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351092] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351097] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351098]          res 51/40:00:9e:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351100] ata1.01: status: { DRDY ERR }
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.351101] ata1.01: error: { UNC }
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.430526] ata1.00: configured for UDMA/133
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.442101] ata1.01: configured for UDMA/133
04/08/11 04:38:29 PM	Valkyrie	kernel	[  618.442121] ata1: EH complete
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140019] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140024] ata1.01: failed command: READ DMA EXT
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140029] ata1.01: cmd 25/00:08:98:0d:6c/00:00:4f:00:00/f0 tag 0 dma 4096 in
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140030]          res 51/40:00:9e:0d:6c/40:00:4f:00:00/f0 Emask 0x9 (media error)
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140032] ata1.01: status: { DRDY ERR }
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.140034] ata1.01: error: { UNC }
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.224600] ata1.00: configured for UDMA/133
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237708] ata1.01: configured for UDMA/133
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237730] sd 0:0:1:0: [sdb] Unhandled sense code
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237733] sd 0:0:1:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237739] sd 0:0:1:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237746] Descriptor sense data with sense descriptors (in hex):
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237749]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237764]         4f 6c 0d 9e 
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237771] sd 0:0:1:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237778] sd 0:0:1:0: [sdb] CDB: Read(10): 28 00 4f 6c 0d 98 00 00 08 00
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237791] end_request: I/O error, dev sdb, sector 1332481438
04/08/11 04:38:31 PM	Valkyrie	kernel	[  620.237812] ata1: EH complete

Sorry its so long but Im trying to be complete here. Its a new system so maybe that has something to do with it. I also have an XP partition on the same drive nut I'm have no problems with that

System:

Gigabyte Z68X-UD5-B3
Intel 2600 i7
8 Gb 1866 MHz RAM (Detuned to 1333 to see if that makes any difference -No)
Installed onto a WD 2TB Sata 2 drive
Kubuntu 11.04 64 bit (never saw this problem using 32 bit Natty on my old box)

Thoughts? Do you need more info?

thanks in advance

---

### Post by WhiteHorse on 2011-08-04
I think you have a failed read problem

---

### Post by Gyokuro on 2011-08-04
Check your sata cables and the drive (could be possible that you drive is faulty)

---

### Post by imperial_oz on 2011-08-04
I've done a clean re-install and I've turned off SMART monitoring at  the BIOS level. It appears that SMART can cause problems with some kernels...been a bug for a while it seems.

I'll see how that goes. Cables all seem ok and the XP installation on the same disk has no problems at all.

---

### Post by imperial_oz on 2011-08-04
Ok I can report that disabling SMART made no difference. Problem has reoccurred.

Now I'm all out of ideas

---

### Post by Gyokuro on 2011-08-04
Have you tried to replace the SATA cable or how have you test it - could you test your HD with HDAT2? ([http://www.hdat2.com/](http://www.hdat2.com/)) and what happens if you use Kubuntu 10.10?

---

### Post by mfraser on 2011-08-05
I'm getting the same in the logs of my daughter's computer which I upgraded today from Kubuntu 10.10 to 11.04:
)
Aug  5 14:58:12 Cartoonito kernel: [   17.531435] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug  5 14:58:12 Cartoonito kernel: [   17.534724] EXT4-fs (sda3): re-mounted. Opts: commit=0
Aug  5 14:58:15 Cartoonito kernel: [   20.458205] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug  5 14:58:15 Cartoonito kernel: [   20.640243] EXT4-fs (sda3): re-mounted. Opts: commit=0
Aug  5 14:59:04 Cartoonito kernel: [   70.283393] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:04 Cartoonito kernel: [   70.283396] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:04 Cartoonito kernel: [   70.283399] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:04 Cartoonito kernel: [   70.283417] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:04 Cartoonito kernel: [   70.283422] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 37 28 00 01 00 00
Aug  5 14:59:04 Cartoonito kernel: [   70.283430] end_request: I/O error, dev sda, sector 543111120
Aug  5 14:59:14 Cartoonito kernel: [   80.666613] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:14 Cartoonito kernel: [   80.666619] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:14 Cartoonito kernel: [   80.666628] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:14 Cartoonito kernel: [   80.666673] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:14 Cartoonito kernel: [   80.666685] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 90 00 00 a0 00
Aug  5 14:59:14 Cartoonito kernel: [   80.666704] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:22 Cartoonito kernel: [   88.035599] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:22 Cartoonito kernel: [   88.035604] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:22 Cartoonito kernel: [   88.035613] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:22 Cartoonito kernel: [   88.035657] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:22 Cartoonito kernel: [   88.035669] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:22 Cartoonito kernel: [   88.035688] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:29 Cartoonito kernel: [   95.537295] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:29 Cartoonito kernel: [   95.537301] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:29 Cartoonito kernel: [   95.537310] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:29 Cartoonito kernel: [   95.537360] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:29 Cartoonito kernel: [   95.537371] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:29 Cartoonito kernel: [   95.537390] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:36 Cartoonito kernel: [  102.641331] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:36 Cartoonito kernel: [  102.641337] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:36 Cartoonito kernel: [  102.641345] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:36 Cartoonito kernel: [  102.641389] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:36 Cartoonito kernel: [  102.641401] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:36 Cartoonito kernel: [  102.641419] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:43 Cartoonito kernel: [  109.753740] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:43 Cartoonito kernel: [  109.753743] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:43 Cartoonito kernel: [  109.753746] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:43 Cartoonito kernel: [  109.753765] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:43 Cartoonito kernel: [  109.753770] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:43 Cartoonito kernel: [  109.753778] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:50 Cartoonito kernel: [  116.841369] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:50 Cartoonito kernel: [  116.841372] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:50 Cartoonito kernel: [  116.841377] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:50 Cartoonito kernel: [  116.841402] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:50 Cartoonito kernel: [  116.841408] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:50 Cartoonito kernel: [  116.841418] end_request: I/O error, dev sda, sector 543129240
Aug  5 14:59:57 Cartoonito kernel: [  123.904162] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 14:59:57 Cartoonito kernel: [  123.904165] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 14:59:57 Cartoonito kernel: [  123.904170] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 14:59:57 Cartoonito kernel: [  123.904194] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 14:59:57 Cartoonito kernel: [  123.904201] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 14:59:57 Cartoonito kernel: [  123.904211] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:06 Cartoonito kernel: [  132.142793] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:06 Cartoonito kernel: [  132.142796] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:06 Cartoonito kernel: [  132.142799] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:06 Cartoonito kernel: [  132.142818] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:06 Cartoonito kernel: [  132.142823] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:06 Cartoonito kernel: [  132.142830] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:13 Cartoonito kernel: [  139.263408] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:13 Cartoonito kernel: [  139.263414] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:13 Cartoonito kernel: [  139.263423] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:13 Cartoonito kernel: [  139.263469] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:13 Cartoonito kernel: [  139.263481] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:13 Cartoonito kernel: [  139.263500] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:20 Cartoonito kernel: [  146.301268] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:20 Cartoonito kernel: [  146.301273] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:20 Cartoonito kernel: [  146.301282] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:20 Cartoonito kernel: [  146.301327] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:20 Cartoonito kernel: [  146.301339] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:20 Cartoonito kernel: [  146.301358] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:27 Cartoonito kernel: [  153.479957] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:27 Cartoonito kernel: [  153.479963] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:27 Cartoonito kernel: [  153.479972] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:27 Cartoonito kernel: [  153.480052] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:27 Cartoonito kernel: [  153.480071] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:27 Cartoonito kernel: [  153.480121] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:35 Cartoonito kernel: [  161.296245] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:35 Cartoonito kernel: [  161.296251] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:35 Cartoonito kernel: [  161.296260] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:35 Cartoonito kernel: [  161.296306] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:35 Cartoonito kernel: [  161.296317] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:35 Cartoonito kernel: [  161.296337] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:42 Cartoonito kernel: [  168.317618] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:42 Cartoonito kernel: [  168.317624] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:42 Cartoonito kernel: [  168.317633] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:42 Cartoonito kernel: [  168.317678] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:42 Cartoonito kernel: [  168.317690] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:42 Cartoonito kernel: [  168.317710] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:49 Cartoonito kernel: [  175.338949] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:49 Cartoonito kernel: [  175.338955] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:49 Cartoonito kernel: [  175.338964] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:49 Cartoonito kernel: [  175.339008] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:49 Cartoonito kernel: [  175.339019] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:49 Cartoonito kernel: [  175.339038] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:00:56 Cartoonito kernel: [  182.343711] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:00:56 Cartoonito kernel: [  182.343717] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:00:56 Cartoonito kernel: [  182.343726] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:00:56 Cartoonito kernel: [  182.343772] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:00:56 Cartoonito kernel: [  182.343784] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:00:56 Cartoonito kernel: [  182.343803] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:03 Cartoonito kernel: [  189.828695] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:03 Cartoonito kernel: [  189.828701] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:03 Cartoonito kernel: [  189.828710] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:03 Cartoonito kernel: [  189.828756] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:03 Cartoonito kernel: [  189.828768] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:03 Cartoonito kernel: [  189.828787] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:10 Cartoonito kernel: [  196.833485] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:10 Cartoonito kernel: [  196.833490] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:10 Cartoonito kernel: [  196.833499] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:10 Cartoonito kernel: [  196.833545] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:10 Cartoonito kernel: [  196.833556] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:10 Cartoonito kernel: [  196.833575] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:17 Cartoonito kernel: [  203.846609] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:17 Cartoonito kernel: [  203.846615] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:17 Cartoonito kernel: [  203.846624] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:17 Cartoonito kernel: [  203.846669] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:17 Cartoonito kernel: [  203.846680] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:17 Cartoonito kernel: [  203.846700] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:25 Cartoonito kernel: [  211.646306] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:25 Cartoonito kernel: [  211.646312] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:25 Cartoonito kernel: [  211.646321] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:25 Cartoonito kernel: [  211.646366] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:25 Cartoonito kernel: [  211.646378] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:25 Cartoonito kernel: [  211.646397] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:32 Cartoonito kernel: [  218.824907] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:32 Cartoonito kernel: [  218.824912] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:32 Cartoonito kernel: [  218.824921] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:32 Cartoonito kernel: [  218.824967] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:32 Cartoonito kernel: [  218.824979] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:32 Cartoonito kernel: [  218.824998] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:39 Cartoonito kernel: [  225.887758] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:39 Cartoonito kernel: [  225.887764] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:39 Cartoonito kernel: [  225.887773] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:39 Cartoonito kernel: [  225.887818] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:39 Cartoonito kernel: [  225.887829] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:39 Cartoonito kernel: [  225.887848] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:46 Cartoonito kernel: [  232.917295] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:46 Cartoonito kernel: [  232.917301] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:46 Cartoonito kernel: [  232.917309] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:46 Cartoonito kernel: [  232.917354] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:46 Cartoonito kernel: [  232.917366] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:46 Cartoonito kernel: [  232.917385] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:01:54 Cartoonito kernel: [  239.938707] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:01:54 Cartoonito kernel: [  239.938712] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:01:54 Cartoonito kernel: [  239.938721] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:01:54 Cartoonito kernel: [  239.938766] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:01:54 Cartoonito kernel: [  239.938778] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:01:54 Cartoonito kernel: [  239.938798] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:01 Cartoonito kernel: [  247.258188] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:01 Cartoonito kernel: [  247.258194] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:01 Cartoonito kernel: [  247.258204] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:01 Cartoonito kernel: [  247.258249] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:01 Cartoonito kernel: [  247.258260] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:01 Cartoonito kernel: [  247.258279] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:08 Cartoonito kernel: [  254.478191] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:08 Cartoonito kernel: [  254.478197] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:08 Cartoonito kernel: [  254.478206] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:08 Cartoonito kernel: [  254.478251] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:08 Cartoonito kernel: [  254.478264] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:08 Cartoonito kernel: [  254.478283] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:15 Cartoonito kernel: [  261.565833] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:15 Cartoonito kernel: [  261.565839] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:15 Cartoonito kernel: [  261.565848] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:15 Cartoonito kernel: [  261.565894] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:15 Cartoonito kernel: [  261.565906] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:15 Cartoonito kernel: [  261.565925] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:22 Cartoonito kernel: [  268.653420] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:22 Cartoonito kernel: [  268.653425] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:22 Cartoonito kernel: [  268.653434] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:22 Cartoonito kernel: [  268.653480] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:22 Cartoonito kernel: [  268.653492] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:22 Cartoonito kernel: [  268.653511] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:29 Cartoonito kernel: [  275.757609] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:29 Cartoonito kernel: [  275.757615] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:29 Cartoonito kernel: [  275.757624] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:29 Cartoonito kernel: [  275.757669] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:29 Cartoonito kernel: [  275.757681] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:29 Cartoonito kernel: [  275.757703] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:37 Cartoonito kernel: [  283.383321] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:37 Cartoonito kernel: [  283.383327] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:37 Cartoonito kernel: [  283.383335] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:37 Cartoonito kernel: [  283.383381] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:37 Cartoonito kernel: [  283.383393] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:37 Cartoonito kernel: [  283.383412] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:45 Cartoonito kernel: [  290.959463] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:45 Cartoonito kernel: [  290.959469] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:45 Cartoonito kernel: [  290.959477] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:45 Cartoonito kernel: [  290.959523] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:45 Cartoonito kernel: [  290.959534] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:45 Cartoonito kernel: [  290.959553] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:52 Cartoonito kernel: [  297.997370] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:52 Cartoonito kernel: [  297.997376] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:52 Cartoonito kernel: [  297.997384] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:52 Cartoonito kernel: [  297.997430] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:52 Cartoonito kernel: [  297.997442] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:52 Cartoonito kernel: [  297.997461] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:02:59 Cartoonito kernel: [  305.026985] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:02:59 Cartoonito kernel: [  305.026991] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:02:59 Cartoonito kernel: [  305.027000] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:02:59 Cartoonito kernel: [  305.027045] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:02:59 Cartoonito kernel: [  305.027057] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:02:59 Cartoonito kernel: [  305.027077] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:06 Cartoonito kernel: [  312.536866] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:06 Cartoonito kernel: [  312.536871] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:06 Cartoonito kernel: [  312.536880] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:06 Cartoonito kernel: [  312.536926] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:06 Cartoonito kernel: [  312.536938] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:06 Cartoonito kernel: [  312.536957] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:13 Cartoonito kernel: [  319.574787] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:13 Cartoonito kernel: [  319.574793] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:13 Cartoonito kernel: [  319.574802] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:13 Cartoonito kernel: [  319.574847] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:13 Cartoonito kernel: [  319.574859] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:13 Cartoonito kernel: [  319.574878] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:20 Cartoonito kernel: [  326.579556] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:20 Cartoonito kernel: [  326.579561] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:20 Cartoonito kernel: [  326.579570] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:20 Cartoonito kernel: [  326.579616] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:20 Cartoonito kernel: [  326.579628] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:20 Cartoonito kernel: [  326.579646] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:27 Cartoonito kernel: [  333.692048] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:27 Cartoonito kernel: [  333.692053] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:27 Cartoonito kernel: [  333.692062] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:27 Cartoonito kernel: [  333.692108] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:27 Cartoonito kernel: [  333.692119] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:27 Cartoonito kernel: [  333.692139] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:35 Cartoonito kernel: [  341.185327] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:35 Cartoonito kernel: [  341.185333] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:35 Cartoonito kernel: [  341.185342] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:35 Cartoonito kernel: [  341.185387] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:35 Cartoonito kernel: [  341.185398] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:35 Cartoonito kernel: [  341.185417] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:42 Cartoonito kernel: [  348.206677] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:42 Cartoonito kernel: [  348.206683] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:42 Cartoonito kernel: [  348.206692] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:42 Cartoonito kernel: [  348.206737] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:42 Cartoonito kernel: [  348.206749] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:42 Cartoonito kernel: [  348.206768] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:49 Cartoonito kernel: [  355.799361] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:49 Cartoonito kernel: [  355.799367] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:49 Cartoonito kernel: [  355.799375] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:49 Cartoonito kernel: [  355.799422] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:49 Cartoonito kernel: [  355.799434] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:49 Cartoonito kernel: [  355.799452] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:03:57 Cartoonito kernel: [  363.507956] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:03:57 Cartoonito kernel: [  363.507961] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:03:57 Cartoonito kernel: [  363.507970] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:03:57 Cartoonito kernel: [  363.508051] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:03:57 Cartoonito kernel: [  363.508068] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:03:57 Cartoonito kernel: [  363.508116] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:04 Cartoonito kernel: [  370.744540] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:04 Cartoonito kernel: [  370.744545] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:04 Cartoonito kernel: [  370.744554] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:04 Cartoonito kernel: [  370.744600] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:04 Cartoonito kernel: [  370.744612] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:04 Cartoonito kernel: [  370.744631] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:11 Cartoonito kernel: [  377.782473] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:11 Cartoonito kernel: [  377.782478] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:11 Cartoonito kernel: [  377.782487] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:11 Cartoonito kernel: [  377.782533] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:11 Cartoonito kernel: [  377.782545] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:11 Cartoonito kernel: [  377.782564] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:18 Cartoonito kernel: [  384.836927] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:18 Cartoonito kernel: [  384.836932] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:18 Cartoonito kernel: [  384.836941] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:18 Cartoonito kernel: [  384.836986] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:18 Cartoonito kernel: [  384.836998] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:18 Cartoonito kernel: [  384.837017] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:25 Cartoonito kernel: [  391.924572] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:25 Cartoonito kernel: [  391.924577] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:25 Cartoonito kernel: [  391.924586] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:25 Cartoonito kernel: [  391.924633] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:25 Cartoonito kernel: [  391.924645] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:25 Cartoonito kernel: [  391.924664] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:33 Cartoonito kernel: [  399.061878] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:33 Cartoonito kernel: [  399.061884] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:33 Cartoonito kernel: [  399.061892] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:33 Cartoonito kernel: [  399.061938] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:33 Cartoonito kernel: [  399.061950] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:33 Cartoonito kernel: [  399.061970] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:40 Cartoonito kernel: [  406.099723] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:40 Cartoonito kernel: [  406.099729] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:40 Cartoonito kernel: [  406.099738] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:40 Cartoonito kernel: [  406.099783] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:40 Cartoonito kernel: [  406.099795] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:40 Cartoonito kernel: [  406.099814] end_request: I/O error, dev sda, sector 543129240
Aug  5 15:04:47 Cartoonito kernel: [  413.352854] sd 2:0:0:0: [sda] Unhandled sense code
Aug  5 15:04:47 Cartoonito kernel: [  413.352857] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  5 15:04:47 Cartoonito kernel: [  413.352862] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Aug  5 15:04:47 Cartoonito kernel: [  413.352887] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Aug  5 15:04:47 Cartoonito kernel: [  413.352894] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00
Aug  5 15:04:47 Cartoonito kernel: [  413.352904] end_request: I/O error, dev sda, sector 543129240

Computer seems to be OK until I try to run Digikam and then it hangs. Going into tty1 I get the above errors.

---

### Post by Gyokuro on 2011-08-05
@mfraser + imperial_oz = you have both in your logs errors like:  CDB: Read(10): 28 00 20 5f 7e 98 00 00 08 00 and this indicates a HD defect - however I have seen smart reports which were ok but the drives was slowly dying. Which HD brand do you use and the size of drives will be interesting and maybe you should check the drive with tools of your drive manufacture (sometimes a firmware update of drive can help).

---

### Post by mfraser on 2011-08-05
This was a 500GB Samsung drive. Had done a FSCK on the drive and it came back ok, but running fsck.ext4 -c on the drive to check for bad blocks started showing read errors half way though.

I have now ordered another drive, hopefully this one will be OK.

---

### Post by imperial_oz on 2011-08-05
My drive is a fairly new 2T Western Digital Caviar (Black).

When I restart the machine I'll get the exact model and post it but I have to do some work just now :-(

I've put new sata cables on it but its not made any difference. I've also been running an XP install on another partition as well as an NTFS partition to allow me to swap files between Windows and Linux, on the same disk that have had no problems.

What I might try next is going back to 10.10 as this disk worked fine before with absolutely no problems. If the problems reoccur then it will look like a hardware problem. But I'm seeing similar issues being reported with Ext4 for some reason. I'd move to btfs but I'm not sure its really ready for full on use yet...or am I wrong about that?

Edit: Disk is a WDC WD2001FASS-00W2B0  (SATA 2) I have 2 of these plus a 2 Tb SATA 3 Western Digital drive. This drive is definitely on a SATA 2 port on the motherboard as I thought that the issues may be caused by being on a SATA 3 port.

---

### Post by imperial_oz on 2011-08-08
Latest update.

I booted to an install disk and ran 'fsck -c' over both Ext4 partitions.

I got a bunch of errors saying something like particular files seemed to point to multiple locations (apologies here, it was late and now my memory is a little loose) I said yes to forced corrections and rebooted when that process was finished. I didn't see any indications of bad sectors.

Since then, I copied the affected files off the disk and then copied them back and have seen no more 'disk read errors'.

I'm now thinking that having SMART enabled in the BIOS caused a bunch of corruptions that survived earlier fsck's and now things may have settled down. I will continue to monitor developments and report back after another week or so.

Thanks to all the suggestions.

---

