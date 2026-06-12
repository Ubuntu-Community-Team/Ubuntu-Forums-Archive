---
title: "Boot error"
date: 2010-10-24
forum: General Help
---

### Post by The Lost on 2010-10-24
Hey,
I was just looking for some help as my computer (not this one obviously) is having a bit of a meltdown. I was tinkering with the resolution settings, trying to get it back to the way it was (stupid stupid nvidia), and after finally succeeding turned my computer off. Now it refuses to boot up, not only will it not boot to ubuntu, but I can't even seem to boot from a flashdrive (which was the first thing i tried to do). TInstead it goes through pages and pages of something, I think some kind of test, and after about 15 minutes finally stops. After which I can do nothing. Here is a sample of the screen to see if anyone knows whats going on, I can always type up more if necessary it is simply a lot of typing.

[1849.432518] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[1849.557532] ata6.00: configured for UDMA/133
[1849.557781] sd 6:0:0:0: [sdc] Unhandled sense code
[1849.558094] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte= DRIVER_SENSE
[1849.558485] sd 6:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[1849.558881] Descriptor sense data with sense descriptors (in hex):
[1849.559274]     72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[1849.559677]     5b 8d 9a 7c
[1849.560081] sd 6:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[1849.560481] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 5b 8d 9a 7c 00 00 08 00
[1849.560894] end_request: I/O error, dev sdc, sector 1536006780
[1849.561301] Buffer I/O error on device sdc2, logical block 0
[1849.561706] Buffer I/O error on device sdc2, logical block 1
[1849.562110] Buffer I/O error on device sdc2, logical block 2
[1849.562514] Buffer I/O error on device sdc2, logical block 3
[1849.562896] Buffer I/O error on device sdc2, logical block 4
[1849.563280] Buffer I/O error on device sdc2, logical block 5
[1849.563661] Buffer I/O error on device sdc2, logical block 6
[1849.564039] Buffer I/O error on device sdc2, logical block 7
[1849.564415] ata6: EH complete 



(initramfs)


I can type after the initramfs bit, but I have absolutely no idea what is going one does anyone have any clue?

Thanks for your time

---

### Post by The Lost on 2010-10-28
nobody?

---

