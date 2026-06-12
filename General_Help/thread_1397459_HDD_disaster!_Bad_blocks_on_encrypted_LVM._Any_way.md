---
title: "HDD disaster! Bad blocks on encrypted LVM. Any way to rescue?"
date: 2010-02-03
forum: General Help
---

### Post by EyeScreaMan on 2010-02-03
Hi.

My hard disk had a failure. This is ubuntu 9.10 system encrypted at install with alternate CD (debian installer).

> 
ubuntu@ubuntu:/var/log$ sudo fdisk -l /dev/sda

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009e813

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48610   390459793+  83  Linux
/dev/sda2           48611       48641      249007+   5  Extended
/dev/sda5           48611       48641      248976   83  Linux


There are bad blocks on drive now :(

> 
 badblocks -v -s /dev/sda
Checking blocks 0 to 390711383
Checking for bad blocks (read-only test): 121600% done, 0:20 elapsed
124800% done, 3:28 elapsed
124900% done, 7:09 elapsed
125000% done, 10:34 elapsed
125100% done, 14:03 elapsed
125200% done, 18:46 elapsed
125300% done, 23:28 elapsed
125400% done, 27:24 elapsed
125500% done, 30:11 elapsed
1256
1257
1258
1259
1260
1261
1262
1263
1264
1265
1266
1267
1268
1269
1270
1271
1272
1273
1274
1275
1276
1277
1278
1279
1280
1281
1282
1283
1284
1285
1286
1287
1288
1289
1290
1291
1292
1293
1294
1295
1296
1297
1298
1299
1300
1301
1302
1303
1304
1305
1306
1307
1308
1309
1310
1311
1312
1313
1314
1315
1316
1317
1318
1319
1320
1321
1322
1323
1324
1325
1326
1327
1328
1329
1330
1331
1332
1333
1334
1335
1336
1337
1338
1339
1340
1341
1342
1343
1344
1345
1346
1347
29064696done, 36:56 elapsed
29064756done, 37:16 elapsed
29064757done, 37:36 elapsed
29064758done, 37:55 elapsed
29064759done, 38:15 elapsed
29064760done, 38:34 elapsed
29064761done, 38:54 elapsed
29064762done, 39:17 elapsed
29064763done, 39:37 elapsed
done
Pass completed, 110 bad blocks found.


> 



I boot up with Live CD and tried to mount this corrupted volume to rescue some data.


I can unlock it:

> 
root@pajonk:~# cryptsetup luksOpen /dev/sda1 crypt1
Enter LUKS passphrase:
key slot 0 unlocked.
Command successful.


and this creates "**/dev/mapper/pajonk-root**" device, but i cannot mount it due to read failures:

> 
ubuntu@ubuntu:~$ sudo mount /dev/mapper/pajonk-root /volume
mount: you must specify the filesystem type


> 
Feb  3 14:48:04 ubuntu kernel: [ 4617.229312] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Feb  3 14:48:04 ubuntu kernel: [ 4617.229317] ata1.01: BMDMA stat 0x65
Feb  3 14:48:04 ubuntu kernel: [ 4617.229324] ata1.01: cmd c8/00:08:c7:09:00/00:00:00:00:00/f0 tag 0 dma 4096 in
Feb  3 14:48:04 ubuntu kernel: [ 4617.229325]          res 51/40:08:c7:09:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Feb  3 14:48:04 ubuntu kernel: [ 4617.229329] ata1.01: status: { DRDY ERR }
Feb  3 14:48:04 ubuntu kernel: [ 4617.229331] ata1.01: error: { UNC }
Feb  3 14:48:04 ubuntu kernel: [ 4617.300200] ata1.00: configured for UDMA/100
Feb  3 14:48:05 ubuntu kernel: [ 4617.440304] ata1.01: configured for UDMA/133
Feb  3 14:48:05 ubuntu kernel: [ 4617.440316] sd 0:0:1:0: [sda] Unhandled sense code
Feb  3 14:48:05 ubuntu kernel: [ 4617.440319] sd 0:0:1:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb  3 14:48:05 ubuntu kernel: [ 4617.440323] sd 0:0:1:0: [sda] Sense Key : Medium Error [current] [descriptor]
Feb  3 14:48:05 ubuntu kernel: [ 4617.440328] Descriptor sense data with sense descriptors (in hex):
Feb  3 14:48:05 ubuntu kernel: [ 4617.440330]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Feb  3 14:48:05 ubuntu kernel: [ 4617.440341]         00 00 09 c7 
Feb  3 14:48:05 ubuntu kernel: [ 4617.440345] sd 0:0:1:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Feb  3 14:48:05 ubuntu kernel: [ 4617.440350] end_request: I/O error, dev sda, sector 2503
Feb  3 14:48:05 ubuntu kernel: [ 4617.440361] __ratelimit: 22 callbacks suppressed
Feb  3 14:48:05 ubuntu kernel: [ 4617.440364] Buffer I/O error on device dm-1, logical block 0
Feb  3 14:48:05 ubuntu kernel: [ 4617.440378] ata1: EH complete
Feb  3 14:48:36 ubuntu wpa_supplicant[1979]: CTRL-EVENT-SCAN-RESULTS 


> 
Feb  3 14:49:57 ubuntu kernel: [ 4730.280365] Buffer I/O error on device dm-1, logical block 0
Feb  3 14:49:57 ubuntu kernel: [ 4730.280373] Buffer I/O error on device dm-1, logical block 1
Feb  3 14:49:57 ubuntu kernel: [ 4730.280378] Buffer I/O error on device dm-1, logical block 2
Feb  3 14:49:57 ubuntu kernel: [ 4730.280384] Buffer I/O error on device dm-1, logical block 3
Feb  3 14:49:57 ubuntu kernel: [ 4730.280389] Buffer I/O error on device dm-1, logical block 4
Feb  3 14:49:57 ubuntu kernel: [ 4730.280394] Buffer I/O error on device dm-1, logical block 5
Feb  3 14:49:57 ubuntu kernel: [ 4730.280398] Buffer I/O error on device dm-1, logical block 6
Feb  3 14:49:57 ubuntu kernel: [ 4730.280403] Buffer I/O error on device dm-1, logical block 7
Feb  3 14:49:57 ubuntu kernel: [ 4730.280408] Buffer I/O error on device dm-1, logical block 8


also tried to check this drive:

> 
ubuntu@ubuntu:~$ sudo fsck -c /dev/mapper/pajonk-root
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/mapper/pajonk-root
Could this be a zero-length partition?


> 
ubuntu@ubuntu:~$ sudo fsck -c /dev/mapper/pajonk-root
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/mapper/pajonk-root
Could this be a zero-length partition?


Is there any chance to read data from this device. There are only 110 badblocks so most of my data should be fine.

Thanks in advance for any help.

---

### Post by Sentience on 2010-02-26
Has anyone figured out WHY this keeps happening? Its not a coincidence that it keeps happening right after upgrade.

---

