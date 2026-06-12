---
title: "Errors when booting"
date: 2011-06-18
forum: General Help
---

### Post by zer0 (00l on 2011-06-18
Hi Guys,
 
When booting ubuntu I keep getting the following errors but it is booting 

I am running a dual boot system with windows 7 also cp is failing with Input/Output error on some files when copying from the windows partition.
Do you think My HDD is screwed? if so How long can i run it this way 

6000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10258.096005] ata1.00: irq_stat 0x40000001
[10258.096010] ata1.00: failed command: READ DMA EXT
[10258.096019] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10258.096021]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10258.096026] ata1.00: status: { DRDY ERR }
[10258.096029] ata1.00: error: { UNC }
[10258.103162] ata1.00: configured for UDMA/33
[10258.103177] sd 0:0:0:0: [sda] Unhandled sense code
[10258.103181] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10258.103186] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[10258.103193] Descriptor sense data with sense descriptors (in hex):
[10258.103200]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[10258.103213]         1f 58 78 73 
[10258.103218] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[10258.103225] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 58 78 70 00 00 08 00
[10258.103237] end_request: I/O error, dev sda, sector 525891699
[10258.103243] Buffer I/O error on device sda3, logical block 62514958
[10258.103265] ata1: EH complete
[10259.912025] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10259.912031] ata1.00: irq_stat 0x40000001
[10259.912035] ata1.00: failed command: READ DMA EXT
[10259.912045] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10259.912047]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10259.912051] ata1.00: status: { DRDY ERR }
[10259.912054] ata1.00: error: { UNC }
[10259.919241] ata1.00: configured for UDMA/33
[10259.919251] ata1: EH complete
[10261.653907] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10261.653913] ata1.00: irq_stat 0x40000001
[10261.653917] ata1.00: failed command: READ DMA EXT
[10261.653927] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10261.653929]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10261.653933] ata1.00: status: { DRDY ERR }
[10261.653936] ata1.00: error: { UNC }
[10261.661160] ata1.00: configured for UDMA/33
[10261.661172] ata1: EH complete
[10263.395847] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10263.395851] ata1.00: irq_stat 0x40000001
[10263.395855] ata1.00: failed command: READ DMA EXT
[10263.395863] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10263.395864]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10263.395868] ata1.00: status: { DRDY ERR }
[10263.395870] ata1.00: error: { UNC }
[10263.403038] ata1.00: configured for UDMA/33
[10263.403048] ata1: EH complete
[10265.137700] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10265.137704] ata1.00: irq_stat 0x40000001
[10265.137708] ata1.00: failed command: READ DMA EXT
[10265.137716] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10265.137717]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10265.137721] ata1.00: status: { DRDY ERR }
[10265.137723] ata1.00: error: { UNC }
[10265.144897] ata1.00: configured for UDMA/33
[10265.144909] ata1: EH complete
[10266.879620] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10266.879624] ata1.00: irq_stat 0x40000001
[10266.879628] ata1.00: failed command: READ DMA EXT
[10266.879636] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10266.879637]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10266.879641] ata1.00: status: { DRDY ERR }
[10266.879643] ata1.00: error: { UNC }
[10266.886809] ata1.00: configured for UDMA/33
[10266.886819] ata1: EH complete
[10268.621507] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10268.621512] ata1.00: irq_stat 0x40000001
[10268.621516] ata1.00: failed command: READ DMA EXT
[10268.621523] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10268.621525]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10268.621529] ata1.00: status: { DRDY ERR }
[10268.621531] ata1.00: error: { UNC }
[10268.628785] ata1.00: configured for UDMA/33
[10268.628797] sd 0:0:0:0: [sda] Unhandled sense code
[10268.628800] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10268.628804] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[10268.628810] Descriptor sense data with sense descriptors (in hex):
[10268.628812]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[10268.628824]         1f 58 78 73 
[10268.628829] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[10268.628835] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 58 78 70 00 00 08 00
[10268.628846] end_request: I/O error, dev sda, sector 525891699
[10268.628850] Buffer I/O error on device sda3, logical block 62514958
[10268.628870] ata1: EH complete
[10270.363404] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10270.363409] ata1.00: irq_stat 0x40000001
[10270.363412] ata1.00: failed command: READ DMA EXT
[10270.363420] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10270.363422]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10270.363425] ata1.00: status: { DRDY ERR }
[10270.363428] ata1.00: error: { UNC }
[10270.370676] ata1.00: configured for UDMA/33
[10270.370688] ata1: EH complete
[10272.105323] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10272.105327] ata1.00: irq_stat 0x40000001
[10272.105331] ata1.00: failed command: READ DMA EXT
[10272.105339] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10272.105340]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10272.105344] ata1.00: status: { DRDY ERR }
[10272.105346] ata1.00: error: { UNC }
[10272.112454] ata1.00: configured for UDMA/33
[10272.112466] ata1: EH complete
[10273.846210] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10273.846216] ata1.00: irq_stat 0x40000001
[10273.846220] ata1.00: failed command: READ DMA EXT
[10273.846228] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10273.846230]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10273.846234] ata1.00: status: { DRDY ERR }
[10273.846236] ata1.00: error: { UNC }
[10273.853606] ata1.00: configured for UDMA/33
[10273.853622] ata1: EH complete
[10275.588079] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10275.588083] ata1.00: irq_stat 0x40000001
[10275.588087] ata1.00: failed command: READ DMA EXT
[10275.588095] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10275.588097]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10275.588100] ata1.00: status: { DRDY ERR }
[10275.588103] ata1.00: error: { UNC }
[10275.595283] ata1.00: configured for UDMA/33
[10275.595295] ata1: EH complete
[10277.330012] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10277.330017] ata1.00: irq_stat 0x40000001
[10277.330021] ata1.00: failed command: READ DMA EXT
[10277.330028] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10277.330030]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10277.330033] ata1.00: status: { DRDY ERR }
[10277.330036] ata1.00: error: { UNC }
[10277.337326] ata1.00: configured for UDMA/33
[10277.337338] ata1: EH complete
[10279.071877] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10279.071881] ata1.00: irq_stat 0x40000001
[10279.071885] ata1.00: failed command: READ DMA EXT
[10279.071893] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10279.071894]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10279.071898] ata1.00: status: { DRDY ERR }
[10279.071900] ata1.00: error: { UNC }
[10279.079170] ata1.00: configured for UDMA/33
[10279.079189] sd 0:0:0:0: [sda] Unhandled sense code
[10279.079193] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10279.079199] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[10279.079206] Descriptor sense data with sense descriptors (in hex):
[10279.079209]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[10279.079223]         1f 58 78 73 
[10279.079229] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[10279.079237] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 58 78 70 00 00 08 00
[10279.079250] end_request: I/O error, dev sda, sector 525891699
[10279.079256] Buffer I/O error on device sda3, logical block 62514958
[10279.079283] ata1: EH complete
[10280.830776] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10280.830783] ata1.00: irq_stat 0x40000001
[10280.830788] ata1.00: failed command: READ DMA EXT
[10280.830798] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10280.830800]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10280.830804] ata1.00: status: { DRDY ERR }
[10280.830807] ata1.00: error: { UNC }
[10280.837902] ata1.00: configured for UDMA/33
[10280.837914] ata1: EH complete
[10282.572676] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10282.572681] ata1.00: irq_stat 0x40000001
[10282.572686] ata1.00: failed command: READ DMA EXT
[10282.572695] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10282.572697]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10282.572702] ata1.00: status: { DRDY ERR }
[10282.572705] ata1.00: error: { UNC }
[10282.579611] ata1.00: configured for UDMA/33
[10282.579622] ata1: EH complete
[10284.313624] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10284.313628] ata1.00: irq_stat 0x40000001
[10284.313632] ata1.00: failed command: READ DMA EXT
[10284.313640] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10284.313641]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10284.313645] ata1.00: status: { DRDY ERR }
[10284.313647] ata1.00: error: { UNC }
[10284.320760] ata1.00: configured for UDMA/33
[10284.320769] ata1: EH complete
[10286.055501] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10286.055506] ata1.00: irq_stat 0x40000001
[10286.055509] ata1.00: failed command: READ DMA EXT
[10286.055517] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10286.055519]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10286.055522] ata1.00: status: { DRDY ERR }
[10286.055525] ata1.00: error: { UNC }
[10286.062775] ata1.00: configured for UDMA/33
[10286.062787] ata1: EH complete
[10287.797423] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10287.797428] ata1.00: irq_stat 0x40000001
[10287.797432] ata1.00: failed command: READ DMA EXT
[10287.797440] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10287.797441]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10287.797445] ata1.00: status: { DRDY ERR }
[10287.797447] ata1.00: error: { UNC }
[10287.804631] ata1.00: configured for UDMA/33
[10287.804641] ata1: EH complete
[10289.539310] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10289.539314] ata1.00: irq_stat 0x40000001
[10289.539318] ata1.00: failed command: READ DMA EXT
[10289.539326] ata1.00: cmd 25/00:08:70:78:58/00:00:1f:00:00/e0 tag 0 dma 4096 in
[10289.539327]          res 51/40:00:73:78:58/00:00:1f:00:00/e0 Emask 0x9 (media error)
[10289.539331] ata1.00: status: { DRDY ERR }
[10289.539333] ata1.00: error: { UNC }
[10289.546626] ata1.00: configured for UDMA/33
[10289.546642] sd 0:0:0:0: [sda] Unhandled sense code
[10289.546645] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10289.546651] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[10289.546658] Descriptor sense data with sense descriptors (in hex):
[10289.546661]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[10289.546675]         1f 58 78 73 
[10289.546681] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[10289.546689] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 58 78 70 00 00 08 00
[10289.546702] end_request: I/O error, dev sda, sector 525891699
[10289.546708] Buffer I/O error on device sda3, logical block 62514958
[10289.546734] ata1: EH complete
[10331.350798] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10331.350805] ata1.00: irq_stat 0x40000001
[10331.350811] ata1.00: failed command: READ DMA EXT
[10331.350821] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10331.350823]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10331.350827] ata1.00: status: { DRDY ERR }
[10331.350830] ata1.00: error: { UNC }
[10331.358071] ata1.00: configured for UDMA/33
[10331.358084] ata1: EH complete
[10332.800386] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10332.800393] ata1.00: irq_stat 0x40000001
[10332.800401] ata1.00: failed command: READ DMA EXT
[10332.800476] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10332.800479]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10332.800486] ata1.00: status: { DRDY ERR }
[10332.800489] ata1.00: error: { UNC }
[10332.807446] ata1.00: configured for UDMA/33
[10332.807460] ata1: EH complete
[10334.250021] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10334.250029] ata1.00: irq_stat 0x40000001
[10334.250035] ata1.00: failed command: READ DMA EXT
[10334.250044] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10334.250046]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10334.250051] ata1.00: status: { DRDY ERR }
[10334.250054] ata1.00: error: { UNC }
[10334.257335] ata1.00: configured for UDMA/33
[10334.257349] ata1: EH complete
[10335.700550] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10335.700557] ata1.00: irq_stat 0x40000001
[10335.700563] ata1.00: failed command: READ DMA EXT
[10335.700573] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10335.700574]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10335.700579] ata1.00: status: { DRDY ERR }
[10335.700582] ata1.00: error: { UNC }
[10335.707430] ata1.00: configured for UDMA/33
[10335.707447] ata1: EH complete
[10337.150135] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10337.150142] ata1.00: irq_stat 0x40000001
[10337.150148] ata1.00: failed command: READ DMA EXT
[10337.150158] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10337.150160]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10337.150165] ata1.00: status: { DRDY ERR }
[10337.150168] ata1.00: error: { UNC }
[10337.157194] ata1.00: configured for UDMA/33
[10337.157211] ata1: EH complete
[10338.600704] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10338.600712] ata1.00: irq_stat 0x40000001
[10338.600717] ata1.00: failed command: READ DMA EXT
[10338.600727] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10338.600729]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10338.600733] ata1.00: status: { DRDY ERR }
[10338.600736] ata1.00: error: { UNC }
[10338.607724] ata1.00: configured for UDMA/33
[10338.607746] sd 0:0:0:0: [sda] Unhandled sense code
[10338.607751] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10338.607759] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[10338.607769] Descriptor sense data with sense descriptors (in hex):
[10338.607773]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[10338.607794]         1e a9 21 24 
[10338.607803] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[10338.607817] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1e a9 21 20 00 00 08 00
[10338.607829] end_request: I/O error, dev sda, sector 514400548
[10338.607835] Buffer I/O error on device sda3, logical block 61078564
[10338.607857] ata1: EH complete
[10340.067282] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10340.067289] ata1.00: irq_stat 0x40000001
[10340.067294] ata1.00: failed command: READ DMA EXT
[10340.067304] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10340.067306]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10340.067310] ata1.00: status: { DRDY ERR }
[10340.067313] ata1.00: error: { UNC }
[10340.074414] ata1.00: configured for UDMA/33
[10340.074427] ata1: EH complete
[10341.517916] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[10341.517923] ata1.00: irq_stat 0x40000001
[10341.517928] ata1.00: failed command: READ DMA EXT
[10341.517938] ata1.00: cmd 25/00:08:20:21:a9/00:00:1e:00:00/e0 tag 0 dma 4096 in
[10341.517939]          res 51/40:00:24:21:a9/00:00:1e:00:00/e0 Emask 0x9 (media error)
[10341.517944] ata1.00: status: { DRDY ERR }
[10341.517947] ata1.00: error: { UNC }
[10341.524986] ata1.00: configured for UDMA/33
[10341.524998] ata1: EH complete


There are a lot more errors of the same kind.

---

