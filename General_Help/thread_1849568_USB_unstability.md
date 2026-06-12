---
title: "USB unstability"
date: 2011-09-24
forum: General Help
---

### Post by Pferra on 2011-09-24
Hi there:

I hope somebody can drive me to a good answer to this problem. I'm completly new to Ubuntu, coming from Windows, have read the forums looking for advice and noticed several threads talking about similar issues and complaining about the fact that it seems that there is not any kind of "official" solution.

I'm facing problems with USB massive storage devices (pen drives, smart phones, audio players). It does not happen with an external hard disk nor USB camera also attached to the system.

When copying from or to the device, which is mounted normally when plugged, the drive is suddenly unmounted, the transfer interrupted and an I/O error message shown.

Sometimes, the drive is automatically remounted after clicking "close" in the error message dialog box, without further user intervention. 

A .hal-mtab-lock file is left in the media folder.

This is a dmesg output, hope you can help me to understand it (sorry it is long, I don't know which is the relevant part):

```
[ 1362.676323] Buffer I/O error on device sdb1, logical block 119991
[ 1362.677521] sd 4:0:0:0: [sdb] Device not ready
[ 1362.677524] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.677528] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.677533] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.677537] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 0e ad b0 00 00 08 00
[ 1362.677548] end_request: I/O error, dev sdb, sector 961968
[ 1362.677552] Buffer I/O error on device sdb1, logical block 119990
[ 1362.678532] sd 4:0:0:0: [sdb] Device not ready
[ 1362.678538] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.678544] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.678552] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.678562] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.678579] end_request: I/O error, dev sdb, sector 2072
[ 1362.678587] Buffer I/O error on device sdb1, logical block 3
[ 1362.679540] sd 4:0:0:0: [sdb] Device not ready
[ 1362.679547] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.679552] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.679558] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.679565] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.679577] end_request: I/O error, dev sdb, sector 2072
[ 1362.679583] Buffer I/O error on device sdb1, logical block 3
[ 1362.681658] sd 4:0:0:0: [sdb] Device not ready
[ 1362.681663] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.681667] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.681673] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.681679] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.681692] end_request: I/O error, dev sdb, sector 2072
[ 1362.681698] Buffer I/O error on device sdb1, logical block 3
[ 1362.682646] sd 4:0:0:0: [sdb] Device not ready
[ 1362.682649] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.682653] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.682658] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.682663] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.682673] end_request: I/O error, dev sdb, sector 2072
[ 1362.682678] Buffer I/O error on device sdb1, logical block 3
[ 1362.683521] sd 4:0:0:0: [sdb] Device not ready
[ 1362.683524] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.683528] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.683532] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.683537] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.683548] end_request: I/O error, dev sdb, sector 2072
[ 1362.684522] sd 4:0:0:0: [sdb] Device not ready
[ 1362.684526] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.684530] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.684535] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.684541] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.684553] end_request: I/O error, dev sdb, sector 2168
[ 1362.686399] sd 4:0:0:0: [sdb] Device not ready
[ 1362.686403] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.686407] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.686413] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.686419] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.686430] end_request: I/O error, dev sdb, sector 2168
[ 1362.687395] sd 4:0:0:0: [sdb] Device not ready
[ 1362.687399] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.687402] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.687407] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.687412] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.687423] end_request: I/O error, dev sdb, sector 2168
[ 1362.688270] sd 4:0:0:0: [sdb] Device not ready
[ 1362.688274] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.688278] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.688283] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.688288] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.688299] end_request: I/O error, dev sdb, sector 2168
[ 1362.689146] sd 4:0:0:0: [sdb] Device not ready
[ 1362.689149] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.689153] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.689157] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.689162] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.689173] end_request: I/O error, dev sdb, sector 2072
[ 1362.690025] sd 4:0:0:0: [sdb] Device not ready
[ 1362.690028] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.690032] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.690037] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.690042] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 18 00 00 08 00
[ 1362.690053] end_request: I/O error, dev sdb, sector 2072
[ 1362.690909] sd 4:0:0:0: [sdb] Device not ready
[ 1362.690914] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.690920] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.690928] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.690937] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.690953] end_request: I/O error, dev sdb, sector 2168
[ 1362.691913] sd 4:0:0:0: [sdb] Device not ready
[ 1362.691920] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.691929] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.691938] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.691948] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 78 00 00 08 00
[ 1362.691968] end_request: I/O error, dev sdb, sector 2168
[ 1362.694150] sd 4:0:0:0: [sdb] Device not ready
[ 1362.694154] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.694158] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.694163] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.694169] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.694181] end_request: I/O error, dev sdb, sector 2064
[ 1362.695145] sd 4:0:0:0: [sdb] Device not ready
[ 1362.695149] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.695153] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.695157] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.695163] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.695174] end_request: I/O error, dev sdb, sector 2176
[ 1362.697900] sd 4:0:0:0: [sdb] Device not ready
[ 1362.697904] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.697908] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.697913] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.697919] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.697930] end_request: I/O error, dev sdb, sector 2176
[ 1362.700151] sd 4:0:0:0: [sdb] Device not ready
[ 1362.700157] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.700163] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.700171] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.700179] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.700195] end_request: I/O error, dev sdb, sector 2176
[ 1362.703060] sd 4:0:0:0: [sdb] Device not ready
[ 1362.703068] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.703075] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.703084] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.703094] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.703112] end_request: I/O error, dev sdb, sector 2064
[ 1362.704663] sd 4:0:0:0: [sdb] Device not ready
[ 1362.704669] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.704674] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.704680] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.704688] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.704699] end_request: I/O error, dev sdb, sector 2176
[ 1362.705646] sd 4:0:0:0: [sdb] Device not ready
[ 1362.705650] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.705653] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.705658] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.705664] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.705675] end_request: I/O error, dev sdb, sector 2112
[ 1362.707145] sd 4:0:0:0: [sdb] Device not ready
[ 1362.707149] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.707152] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.707157] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.707162] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.707173] end_request: I/O error, dev sdb, sector 2112
[ 1362.708646] sd 4:0:0:0: [sdb] Device not ready
[ 1362.708649] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.708653] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.708658] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.708663] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.708674] end_request: I/O error, dev sdb, sector 2112
[ 1362.709524] sd 4:0:0:0: [sdb] Device not ready
[ 1362.709530] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.709536] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.709542] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.709550] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.709566] end_request: I/O error, dev sdb, sector 2112
[ 1362.711406] sd 4:0:0:0: [sdb] Device not ready
[ 1362.711411] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.711415] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.711421] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.711427] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.711440] end_request: I/O error, dev sdb, sector 2112
[ 1362.713021] sd 4:0:0:0: [sdb] Device not ready
[ 1362.713024] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.713028] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.713032] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.713037] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.713048] end_request: I/O error, dev sdb, sector 2112
[ 1362.713895] sd 4:0:0:0: [sdb] Device not ready
[ 1362.713899] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.713902] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.713907] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.713914] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.713930] end_request: I/O error, dev sdb, sector 2112
[ 1362.714770] sd 4:0:0:0: [sdb] Device not ready
[ 1362.714774] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.714777] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.714782] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.714787] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.714798] end_request: I/O error, dev sdb, sector 2112
[ 1362.715797] sd 4:0:0:0: [sdb] Device not ready
[ 1362.715804] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.715811] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.715819] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.715826] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.715838] end_request: I/O error, dev sdb, sector 2112
[ 1362.717401] sd 4:0:0:0: [sdb] Device not ready
[ 1362.717406] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.717411] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.717416] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.717422] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 40 00 00 08 00
[ 1362.717434] end_request: I/O error, dev sdb, sector 2112
[ 1362.718397] sd 4:0:0:0: [sdb] Device not ready
[ 1362.718400] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.718404] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.718409] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.718414] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 00 00 00 08 00
[ 1362.718425] end_request: I/O error, dev sdb, sector 2304
[ 1362.719270] sd 4:0:0:0: [sdb] Device not ready
[ 1362.719274] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.719278] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.719282] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.719287] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 00 00 00 08 00
[ 1362.719298] end_request: I/O error, dev sdb, sector 2304
[ 1362.720147] sd 4:0:0:0: [sdb] Device not ready
[ 1362.720150] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.720154] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.720159] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.720165] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 08 00 00 08 00
[ 1362.720175] end_request: I/O error, dev sdb, sector 2312
[ 1362.721279] sd 4:0:0:0: [sdb] Device not ready
[ 1362.721286] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.721293] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.721301] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.721310] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 08 00 00 08 00
[ 1362.721328] end_request: I/O error, dev sdb, sector 2312
[ 1362.722776] sd 4:0:0:0: [sdb] Device not ready
[ 1362.722784] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.722791] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.722799] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.722808] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 10 00 00 08 00
[ 1362.722826] end_request: I/O error, dev sdb, sector 2320
[ 1362.723772] sd 4:0:0:0: [sdb] Device not ready
[ 1362.723776] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.723780] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.723785] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.723791] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 09 10 00 00 08 00
[ 1362.723803] end_request: I/O error, dev sdb, sector 2320
[ 1362.724646] sd 4:0:0:0: [sdb] Device not ready
[ 1362.724649] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.724654] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.724658] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.724664] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 00 00 00 08 00
[ 1362.724674] end_request: I/O error, dev sdb, sector 2816
[ 1362.725521] sd 4:0:0:0: [sdb] Device not ready
[ 1362.725524] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.725528] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.725533] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.725538] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 00 00 00 08 00
[ 1362.725548] end_request: I/O error, dev sdb, sector 2816
[ 1362.726397] sd 4:0:0:0: [sdb] Device not ready
[ 1362.726401] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.726405] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.726409] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.726415] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 08 00 00 08 00
[ 1362.726426] end_request: I/O error, dev sdb, sector 2824
[ 1362.727786] sd 4:0:0:0: [sdb] Device not ready
[ 1362.727793] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.727799] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.727807] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.727816] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 08 00 00 08 00
[ 1362.727832] end_request: I/O error, dev sdb, sector 2824
[ 1362.728779] sd 4:0:0:0: [sdb] Device not ready
[ 1362.728784] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.728789] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.728794] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.728800] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 10 00 00 08 00
[ 1362.728812] end_request: I/O error, dev sdb, sector 2832
[ 1362.729771] sd 4:0:0:0: [sdb] Device not ready
[ 1362.729774] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.729778] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.729783] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.729789] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0b 10 00 00 08 00
[ 1362.729800] end_request: I/O error, dev sdb, sector 2832
[ 1362.730653] sd 4:0:0:0: [sdb] Device not ready
[ 1362.730659] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.730668] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.730676] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.730684] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.730701] end_request: I/O error, dev sdb, sector 2064
[ 1362.732025] sd 4:0:0:0: [sdb] Device not ready
[ 1362.732032] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.732039] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.732047] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.732056] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.732073] end_request: I/O error, dev sdb, sector 2064
[ 1362.733149] sd 4:0:0:0: [sdb] Device not ready
[ 1362.733153] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.733157] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.733162] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.733167] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.733179] end_request: I/O error, dev sdb, sector 2064
[ 1362.734148] sd 4:0:0:0: [sdb] Device not ready
[ 1362.734152] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.734156] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.734161] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.734166] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.734177] end_request: I/O error, dev sdb, sector 2176
[ 1362.735020] sd 4:0:0:0: [sdb] Device not ready
[ 1362.735024] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.735028] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.735032] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.735037] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.735052] end_request: I/O error, dev sdb, sector 2176
[ 1362.736522] sd 4:0:0:0: [sdb] Device not ready
[ 1362.736526] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.736529] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.736534] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.736539] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.736550] end_request: I/O error, dev sdb, sector 2064
[ 1362.737397] sd 4:0:0:0: [sdb] Device not ready
[ 1362.737400] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.737404] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.737409] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.737414] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 10 00 00 08 00
[ 1362.737425] end_request: I/O error, dev sdb, sector 2064
[ 1362.738271] sd 4:0:0:0: [sdb] Device not ready
[ 1362.738274] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.738278] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.738283] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.738288] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 80 00 00 08 00
[ 1362.738299] end_request: I/O error, dev sdb, sector 2176
[ 1362.739286] sd 4:0:0:0: [sdb] Device not ready
[ 1362.739293] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1362.739300] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1362.739308] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1362.739316] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 18 00 00 00 08 00
[ 1362.739333] end_request: I/O error, dev sdb, sector 6144
[ 1362.766672] sdb: detected capacity change from 8064598016 to 0
[ 1380.016011] sd 4:0:0:0: [sdb] 15751168 512-byte logical blocks: (8.06 GB/7.51 GiB)
[ 1380.016839] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1380.020220] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1380.023746]  sdb: sdb1
[ 1383.060069] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 1383.256049] sd 4:0:0:0: [sdb] Device not ready
[ 1383.256055] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1383.256060] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1383.256066] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1383.256075] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 21 42 70 00 00 08 00
[ 1383.256087] end_request: I/O error, dev sdb, sector 2179696
[ 1383.256093] quiet_error: 46 callbacks suppressed
[ 1383.256097] Buffer I/O error on device sdb1, logical block 272206
[ 1383.259278] sd 4:0:0:0: [sdb] Device not ready
[ 1383.259283] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1383.259287] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1383.259292] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1383.259298] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 21 42 70 00 00 08 00
[ 1383.259309] end_request: I/O error, dev sdb, sector 2179696
[ 1383.259314] Buffer I/O error on device sdb1, logical block 272206
[ 1383.262437] sd 4:0:0:0: [sdb] Device not ready
[ 1383.262445] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1383.262453] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1383.262462] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1383.262471] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 21 42 70 00 00 08 00
[ 1383.262489] end_request: I/O error, dev sdb, sector 2179696
[ 1383.262499] Buffer I/O error on device sdb1, logical block 272206
[ 1383.280924] sdb: detected capacity change from 8064598016 to 0
[ 1399.006106] sd 4:0:0:0: [sdb] 15751168 512-byte logical blocks: (8.06 GB/7.51 GiB)
[ 1399.007797] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1399.009677] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1399.013272]  sdb: sdb1
[ 1685.010117] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 1685.350169] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 1685.670045] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 1685.990163] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[ 1686.197862] sd 4:0:0:0: [sdb] Device not ready
[ 1686.197869] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1686.197875] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1686.197883] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1686.197893] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 18 b6 ec 00 00 28 00
[ 1686.197910] end_request: I/O error, dev sdb, sector 1619692
[ 1686.201369] sd 4:0:0:0: [sdb] Device not ready
[ 1686.201376] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1686.201384] sd 4:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 1686.201392] sd 4:0:0:0: [sdb]  Add. Sense: Medium not present
[ 1686.201403] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 18 b6 ec 00 00 08 00
[ 1686.201422] end_request: I/O error, dev sdb, sector 1619692
[ 1687.016551] sdb: detected capacity change from 8064598016 to 0
[ 1699.006764] sd 4:0:0:0: [sdb] 15751168 512-byte logical blocks: (8.06 GB/7.51 GiB)
[ 1699.007267] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1699.008901] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1699.012362]  sdb: sdb1
[ 1714.102839] WARNING! power/level is deprecated; use power/control instead
[ 1714.200285] usb 1-7: USB disconnect, address 3
[ 2024.908524] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 6635.918702] [UFW BLOCK] IN=eth0 OUT= MAC=00:13:21:d4:18:8f:00:01:5c:22:d3:c1:08:00 SRC=74.86.67.66 DST=200.127.55.116 LEN=437 TOS=0x00 PREC=0x00 TTL=51 ID=0 DF PROTO=UDP SPT=5060 DPT=5060 LEN=417 
[12461.122668] [UFW BLOCK] IN=eth0 OUT= MAC=00:13:21:d4:18:8f:00:01:5c:22:d3:c1:08:00 SRC=219.148.1.91 DST=200.127.55.116 LEN=404 TOS=0x00 PREC=0x00 TTL=112 ID=50713 PROTO=UDP SPT=2733 DPT=1434 LEN=384 
[13843.100122] usb 1-5: new high speed USB device using ehci_hcd and address 4
[13843.254116] scsi5 : usb-storage 1-5:1.0
[13844.251144] scsi 5:0:0:0: Direct-Access     SAMSUNG  SV0643A          JW10 PQ: 0 ANSI: 0
[13844.252358] sd 5:0:0:0: Attached scsi generic sg2 type 0
[13844.254926] sd 5:0:0:0: [sdb] 12594960 512-byte logical blocks: (6.44 GB/6.00 GiB)
[13844.260405] sd 5:0:0:0: [sdb] Write Protect is off
[13844.260415] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[13844.260421] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[13844.262768] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[13844.273055]  sdb: sdb1
[13844.275746] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[13844.275758] sd 5:0:0:0: [sdb] Attached SCSI disk
[14249.730217] usb 1-5: USB disconnect, address 4
[14311.760050] usb 1-2: new high speed USB device using ehci_hcd and address 5
[14311.914080] scsi6 : usb-storage 1-2:1.0
[14312.912888] scsi 6:0:0:0: Direct-Access     Motorola MB525            0001 PQ: 0 ANSI: 2
[14312.914040] sd 6:0:0:0: Attached scsi generic sg2 type 0
[14312.922309] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[14828.942031] usb 1-2: USB disconnect, address 5
[14829.410065] usb 1-2: new high speed USB device using ehci_hcd and address 6
[14829.562231] scsi7 : usb-storage 1-2:1.0
[14830.560755] scsi 7:0:0:0: Direct-Access     Motorola MB525            0001 PQ: 0 ANSI: 2
[14830.561918] sd 7:0:0:0: Attached scsi generic sg2 type 0
[14830.568411] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[14840.005228] sd 7:0:0:0: [sdb] 15751168 512-byte logical blocks: (8.06 GB/7.51 GiB)
[14840.005888] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[14840.007369] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[14840.010677]  sdb: sdb1
[14975.260059] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14975.750087] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14976.280052] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14976.690058] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14977.031332] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14977.420054] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14977.570782] sd 7:0:0:0: [sdb] Unhandled error code
[14977.570788] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[14977.570794] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 45 19 e4 00 00 f0 00
[14977.570806] end_request: I/O error, dev sdb, sector 4528612
[14978.120088] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[14978.528916] sd 7:0:0:0: [sdb] Device not ready
[14978.528925] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[14978.528931] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[14978.528940] sd 7:0:0:0: [sdb]  Add. Sense: Medium not present
[14978.528950] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 45 1a d4 00 00 f0 00
[14978.528962] end_request: I/O error, dev sdb, sector 4528852
[14978.546795] sd 7:0:0:0: [sdb] Device not ready
[14978.546802] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[14978.546809] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[14978.546818] sd 7:0:0:0: [sdb]  Add. Sense: Medium not present
[14978.546842] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 45 1b c4 00 00 f0 00
[14978.546862] end_request: I/O error, dev sdb, sector 4529092
[14978.572911] sd 7:0:0:0: [sdb] Device not ready
[14978.572920] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[14978.572927] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[14978.572937] sd 7:0:0:0: [sdb]  Add. Sense: Medium not present
[14978.572949] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 45 1c b4 00 00 f0 00
[14978.572976] end_request: I/O error, dev sdb, sector 4529332
[14978.578655] FAT: unable to read inode block for updating (i_pos 10197315)
[14978.590646] FAT: FAT read failed (blocknr 4786)
[14978.592359] FAT: unable to read inode block for updating (i_pos 10197315)
[14978.599838] FAT: FAT read failed (blocknr 4737)
[14978.890189] FAT: bread failed in fat_clusters_flush
[14981.010499] sdb: detected capacity change from 8064598016 to 0
[15003.009327] sd 7:0:0:0: [sdb] 15751168 512-byte logical blocks: (8.06 GB/7.51 GiB)
[15003.009969] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15003.011548] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15003.013986]  sdb: sdb1

```

The same USB massive storage devices work perfectly well under windows.

The computer is a HP Compaq dc7100 SFF, 2Mb RAM, Ubuntu Natty. The devices presenting troubles are a Motorola Defy phone, a Kingston pen drive and an unbranded generic MP3 player.

Any help will be much appreciated, thanks in advance.

Pablo

---

### Post by Pferra on 2011-09-24
Sorry: forget to mention I'm talking about a Wubi install (a little detail ;-)

Regards...

Pablo

---

### Post by Pferra on 2011-10-04
No clues? No help for newbies? No solution? The question was wrongly presented? The answer is implied in the question and I didn't realize? Nobody actually using Ubuntu?........

---

### Post by Mr.Enigma on 2011-10-04
How old is the USB stick.  I'm no expert but this is what i think is happening either:
1. The usb stick is failing (drives do do that) (i said do do)
2. Kingston used to require special drivers that would install themselves using the auto-play feature on windows, it's possible those drivers got deleted or damaged.
3. The drive itself may have been corrupted, have you been around X-rays or magnets?

Try getting the files off of it using another computer if possible, and then re-format it and see if that helps.

---

### Post by Mr.Enigma on 2011-10-04
Also, try using a different USB port.  this really does look like a hardware error.

---

### Post by Pferra on 2011-10-05
Thank you Mr. Enigma.

The Kingston pen drive is less than a year old. The other failing devices are a new Motorola phone and a new generic unbranded MP3 player.

All of them work all right under, well, the other OS I have installed, and have not been exposed to magnetic fields nor other physical risks.

I've tried a Sony camera recently and the same happened: sudden unmounting in the middle of data transfer. I'm so unlucky that ALL my devices have been exposed to Gamma Rays?

I've seen lots of threads in the forums about USB problems, all of them slightly different and none with a conclusive answer. But, anycase, you have the overall feeling that there is a problem with Ubuntu's USB implementation and that nobody want to admit it, pointing to hardware issues or "propietary" (and therefore "evil") drivers.

It is very frustrating and disapointing that such a basic feature that should be transparent for the user was so problematic and that a formal and official help/fix/workaround is not provided or easy to find.

Thank you, Enigma, anyway, since you have been so kind to answer.

Pablo

---

### Post by Mr.Enigma on 2011-10-12
Okay so it's highly unlikely that there is a problem with the specific devices, since there a about 5 all doing the same thing.  So we have to look at the next layer, which is your computer. 

When you say other OS, is it installed to the same machine? Or is it on another machine?

If it's the same machine we can rule out hardware problems all together. 

In that case it's a problem with software.  Which can mean several things, I.E.

[LIST=1]
[*]bad controller for the USB bus
[*]Bad settings
[*]Device usage disabled
[*]etc.
[/LIST]
Check to make sure it's not disabled first.  I'm new to linux too and have no idea how to do that.  Try doing a search for disabling USB in ubuntu and reverse engineer it from there.  After that and it still doesn't work you'll want to look at how the software talks to the hardware and see if you can find problems there.

sorry i can't be of much more help to you, but like i said.  I'm new too.

---

### Post by Pferra on 2011-10-12
Thanks a lot Mr. Enigma for you help and concern.

Yes, the other OS is Windows and it is running in the same machine. As I stated in my first post, Ubuntu is installed alltogether with Windows, using Wubi.

All devices work well under Windows (XP, for further details).

Is there a way to force Ubuntu to use USB1? Now that I explain the setup to you, I realize that USB2 does not work under Windows an I had to "downgrade" to USB1 in order to have the stuff working properly. Could it be the same under Linux? I will surf the forums for posts about that.

Regarding settings, I have installed Wubi and touched nothing, so all the parameters are supossed to be set to defaults.

I will try your suggestion of studying activation/deactivation procedures.

Thanks again.

Pablo

---

### Post by dcstar on 2011-10-13
> **Pferra said:**
> Thanks a lot Mr. Enigma for you help and concern.

Yes, the other OS is Windows and it is running in the same machine. As I stated in my first post, Ubuntu is installed alltogether with Windows, using Wubi.

All devices work well under Windows (XP, for further details).

Is there a way to force Ubuntu to use USB1? Now that I explain the setup to you, **I realize that USB2 does not work under Windows an I had to "downgrade" to USB1 in order to have the stuff working properly.** Could it be the same under Linux? I will surf the forums for posts about that.
.......

Hang on, **you** have to change Windows to use your USB hardware and now you are wondering why Ubuntu is having issues?

---

### Post by Mark Phelps on 2011-10-13
Sorry to tell you this, but this USB-suddenly-dismounting problem is a persistant one for which there does not appear to be any real solution.

I use a bunch of different PCs (home and work), running several different Windows OSs and Linux distros, and the most stable of these is the Linux distros.

But even then, I will be copying files to/from USB stick (in ANY of the OSs) and suddenly, the copy will fail and complaing about not being able to find the device.

---

### Post by Pferra on 2011-10-15
Thank you Mark. I cannot oposse any argument against yours than my own experience of never having this trouble under Windows.

Any case, and to be loyal and honest, I upgraded to Ubuntu 11.10 and transfers to USB devices seem working as a charm. I'have just copied a 700Mb movie to my phone without any problem.

But perfect world is far from humans!!!! Unity sucks ;-)

Best regards.

Pablo

---

### Post by Pferra on 2011-10-15
Hahahaha.

Well, David, you are right, but under Windows at least I found a workaround (so long ago that I forgot it and remembered talking about the issue here).

Any case, as told in my response to Mark, the issue seems to be solved with Ubuntu Oneiric.

Thanks a lot to everybody.

Pablo

---

