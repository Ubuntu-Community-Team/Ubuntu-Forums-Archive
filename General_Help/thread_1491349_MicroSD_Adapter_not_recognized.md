---
title: "MicroSD Adapter not recognized"
date: 2010-05-23
forum: General Help
---

### Post by JugglinPhil on 2010-05-23
It is a MicroSD to USB Adapter (with no "lock" switch); when plugged in it flashes for a while and then glows, but the computer can not access it.
It used to work fine under 9.10, is this anything that's known in 10.04?

---

### Post by sylvester_0 on 2010-05-23
Copy/paste the last few lines of output from "dmesg" (run that command at a terminal) so we can help you further.

---

### Post by JugglinPhil on 2010-05-23
[  414.032006] end_request: I/O error, dev sdc, sector 8
[  414.032015] Buffer I/O error on device sdc, logical block 1
[  414.570835] sd 7:0:0:0: [sdc] Unhandled sense code
[  414.570843] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  414.570851] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  414.570860] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  414.570870] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  414.570889] end_request: I/O error, dev sdc, sector 128
[  414.570898] Buffer I/O error on device sdc, logical block 16
[  415.109059] sd 7:0:0:0: [sdc] Unhandled sense code
[  415.109067] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  415.109074] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  415.109083] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  415.109093] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  415.109111] end_request: I/O error, dev sdc, sector 0
[  415.109120] Buffer I/O error on device sdc, logical block 0
[  415.647441] sd 7:0:0:0: [sdc] Unhandled sense code
[  415.647449] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  415.647456] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  415.647465] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  415.647474] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  415.647492] end_request: I/O error, dev sdc, sector 0
[  415.647502] Buffer I/O error on device sdc, logical block 0
[  416.186460] sd 7:0:0:0: [sdc] Unhandled sense code
[  416.186467] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  416.186474] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  416.186483] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  416.186492] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[  416.186511] end_request: I/O error, dev sdc, sector 4096
[  416.186521] Buffer I/O error on device sdc, logical block 512
[  416.735318] sd 7:0:0:0: [sdc] Unhandled sense code
[  416.735325] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  416.735333] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  416.735342] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  416.735351] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  416.735370] end_request: I/O error, dev sdc, sector 0
[  416.735379] Buffer I/O error on device sdc, logical block 0
[  417.273571] sd 7:0:0:0: [sdc] Unhandled sense code
[  417.273579] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  417.273587] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  417.273596] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  417.273606] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  417.273624] end_request: I/O error, dev sdc, sector 0
[  417.812209] sd 7:0:0:0: [sdc] Unhandled sense code
[  417.812216] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  417.812223] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  417.812232] sd 7:0:0:0: [sdc] Add. Sense: Data phase CRC error detected
[  417.812242] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  417.812260] end_request: I/O error, dev sdc, sector 0
[  417.812268] __ratelimit: 1 callbacks suppressed
[  417.812273] Buffer I/O error on device sdc, logical block 0

---

### Post by sylvester_0 on 2010-05-23
It looks like there's something seriously wrong with that medium. Are you able to read it in other devices? If losing the data on it is not a problem, I'd recommend repartitioning it (System -> Administration -> Disk Utility) then recreating the filesytem (vfat.) Perhaps the memory stick got to this state by improper removal?

---

### Post by adrianobrien87 on 2010-05-23
I too have the same issue,

When i do get it to work sometimes by deleting the part table, Ubuntu gives it some crazzy name with ASCII code in it?

At the moment i've tried re-deleting the partitioning table but now cant even get it to build a new one,

I've got to say i think this is due to Ubuntu 10 having issues with mircoSD (HC version) cards,

Mines a 8gb class 6

Thanks,
Adrian O'Brien

---

### Post by fragos on 2010-05-23
If your microSD is larger than 2GB it is SDHC and won't read in an SD reader, an SDHC reader is required. SDHC readers will also read SD cards. Your symptoms match what would occur when you tried to read an SDHC card in an SD reader.

---

### Post by adrianobrien87 on 2010-05-23
Thanks, but yea i am using a SDHC reader lol that would be very stupid, also considering we've both been using these cards and readers under Ubuntu 9, it would suggest more of a common issue with Ubuntu (or something were both missing) then our readers 

Thanks,
Adrian O'Brien

---

### Post by fragos on 2010-05-23
I only use full size SD cards but have no problems with my USB SDHC reader with any Ubuntu release including 10.04. I also have a Nokia N810 running Linux and I had to try a number of SDHC readers before I found one that worked with it. All the failed readers worked on my PC.

---

### Post by JugglinPhil on 2010-05-24
> **fragos said:**
> If your microSD is larger than 2GB it is SDHC and won't read in an SD reader, an SDHC reader is required. SDHC readers will also read SD cards. Your symptoms match what would occur when you tried to read an SDHC card in an SD reader.
It's a 2GB SD, not SDHC.
Is there a way to do it without deleting everything?

---

### Post by JugglinPhil on 2010-07-19
Alright I gave it up, by now I am willing to delete the Card's content. 
However, it does not even show up in the Disk Utility, same with GParted.

---

### Post by Richard Tangram on 2010-07-19
This gets more and more bizarre the more I look at it.  I am running Ubuntu 10.04 on a Dell Dimension 5150.  micro SD cards above 2GB will not run in an adapter (SD or SDHC) in the built in card reader (which Ubuntu recognises as a Samsung) but will work on any device I plug in to a USB port.  This includes my USB 2.0 card reader where the micro sdhc card is currently running in a micro sd adapter.  

Try getting a different slot to plug your sd adapter in?  Good Luck

---

### Post by fragos on 2010-07-19
The service manual didn't list an SD slot so it was probably an option. I'm not sure of the age of your PC but I'd bet the SD reader isn't SDHC and that's what's required. Even some internal card readers available today are only SD.

---

### Post by JugglinPhil on 2010-07-20
> **fragos said:**
> I'd bet the SD reader isn't SDHC and that's what's required.
Why would I need an SDHC reader for an SD card? 

My Laptop is about two years old, but I don't think that is the problem, as it used to work before 10.04.

---

### Post by fragos on 2010-07-20
the SD spec stops at 2GB, SDHC picks up from there. an SDHC reader reads SD as well

---

