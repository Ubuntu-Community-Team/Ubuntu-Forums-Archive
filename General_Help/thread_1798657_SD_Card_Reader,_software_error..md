---
title: "SD Card Reader, software error."
date: 2011-07-06
forum: General Help
---

### Post by AliBeaton on 2011-07-06
Hi all,

Happy (sometimes stressed!) user of Ubuntu and Kubuntu for the last 2 years, have come across the first issue that I couldn't solve via searching the forums. I hope somebody can help!

Use a dell mini with an inbuilt SD card reader. Yesterday the card reader stopped detecting SD cards. Narrowed this down to an Ubuntu software issue by booting Win XP on the same machine and transferring files to and from various SD cards. I have tried a couple of usb external card readers, but no luck there.

I use the card reader daily and have made no system changes, which is usually the culprit, and I am at a loss as to what has happened!

Can anybody suggest a workaround or a solution so that I can recover the functionality?

dmesg | tail after a card is inserted:

```
[ 1121.916198] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1121.916236] end_request: I/O error, dev sdb, sector 0
[ 1122.213927] sd 2:0:0:0: [sdb] Unhandled sense code
[ 1122.213944] sd 2:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1122.213962] sd 2:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[ 1122.213981] sd 2:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 1122.214000] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1122.214044] end_request: I/O error, dev sdb, sector 0
[ 1122.214057] quiet_error: 8 callbacks suppressed
[ 1122.214066] Buffer I/O error on device sdb, logical block 0

```Cheers,

Ali

---

