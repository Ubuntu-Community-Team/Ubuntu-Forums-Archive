---
title: "Ubuntu 8.04 LTs on X4250 Sun + Storagetek 2350"
date: 2010-03-23
forum: General Help
---

### Post by sevilla on 2010-03-23
Hi all..


I want increase my storage of my server with a StorageTek 2350.

Im using a PCI-EXT-SAS to connect my Storage. I installed CAM on a Windows XP to manage the storage. I upgrade the firmware on both controllers and created a virtual disk using 6x300GB. The results its a 800 GB Volumen using RAID 1+0. 

On ubuntu i can see my volume and created a partition using fdisk.

After, trying to create the Filesystem using mkfs.ext3 i got this error:

Mar 22 18:37:37 server kernel: [255905.850298]  sdc: sdc1
Mar 22 18:37:39 server kernel: [255908.123772]  sdc: sdc1
Mar 22 18:41:54 server kernel: [256162.892141] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892197] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892245] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892292] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892340] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892388] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892435] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892483] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892530] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892578] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892625] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892673] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892720] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892768] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892815] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892863] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892910] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.892958] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.893005] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.893053] aacraid: Host adapter abort request (7,0,0,0)
Mar 22 18:41:54 server kernel: [256162.902384] aacraid: Host adapter reset request. SCSI hang ?
Mar 22 18:42:54 server kernel: [256223.513141] aacraid: SCSI bus appears hung
Mar 22 18:43:39 server kernel: [256268.480523] IRQ 18/aacraid: IRQF_DISABLED is not guaranteed on shared IRQs

Mar 22 18:44:04 server kernel: [256293.022051] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022057] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022059] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022060] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022062] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022063] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022064] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022066] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022067] sd 7:0:0:0: Device offlined - not ready after error recovery
Mar 22 18:44:04 server kernel: [256293.022068] sd 7:0:0:0: Device offlined - not ready after error recovery
ar 22 18:44:04 server kernel: [256293.022344] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
Mar 22 18:44:04 server kernel: [256293.022347] sd 7:0:0:0: [sdc] CDB: Write(10): 2a 00 02 04 03 5f 00 01 04 00
Mar 22 18:44:04 server kernel: [256293.022353] end_request: I/O error, dev sdc, sector 33817439
Mar 22 18:44:04 server kernel: [256293.022408] Buffer I/O error on device sdc1, logical block 8454344
Mar 22 18:44:04 server kernel: [256293.022458] lost page write due to I/O error on sdc1
Mar 22 18:44:04 server kernel: [256293.022461] Buffer I/O error on device sdc1, logical block 8454345
Mar 22 18:44:04 server kernel: [256293.022990] sd 7:0:0:0: [sdc] Unhandled error code
Mar 22 18:44:04 server kernel: [256293.022992] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Mar 22 18:44:04 server kernel: [256293.022993] sd 7:0:0:0: [sdc] CDB: Write(10): 2a 00 02 04 04 63 00 00 04 00
Mar 22 18:44:04 server kernel: [256293.022998] end_request: I/O error, dev sdc, sector 33817699
Mar 22 18:44:04 server kernel: [256293.023059] sd 7:0:0:0: [sdc] Unhandled error code
Mar 22 18:44:04 server kernel: [256293.023060] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Mar 22 18:44:04 server kernel: [256293.023062] sd 7:0:0:0: [sdc] CDB: Write(10): 2a 00 02 04 04 67 00 01 04 00
Mar 22 18:44:04 server kernel: [256293.023067] end_request: I/O error, dev sdc, sector 33817703

Mar 22 18:44:04 server kernel: ectrejecting rererejrerejrejectrejectrejectirejerejectrejectingrejecrejectrejectrejectire
jectirejectrejectirejectingrejectinrejectrejectirejectirejectingrejectingrejectirejectrejectrejectirejecting I/rejectingre
jectirejectrejectirejecting rejectingrejectirejectirejectrejectrejectrejecting Irejectingrejecrejectrejectrejecting rejecr
ejecrejectrejectrejectrejectirejectirejecting rejecrejectrejectrejecrejectrejectingrejecrejectrejectrejecrejectirejectreje
ctrejectingrejectrejecrejectrejectinrejectrejectingrejectrejectrejectrejecrejectrejectirejectrejectingrejecrejecrejectreje
ctirejectrejectingrejecrejecrejectrejectirejectrejectirejectrejecting I/O rejectinrejectinrejectirejectirejectrejectrejecr
ejectrejectirejectrejectrejectrejectingrejectingrejectingrejectirejectrejectirejectirejectirejectrejectrejectrejectireject
rejecting rejectingrejectingrejectirejectrejectrejectrejectrejectirejectirejectirejectirejectirejectingrejectingrejectinre
jectirejectrejectrejectirejectirejectrejectrejectrej

I was using 2.6.24-23 but i compiled 2.6.33.1 and i have the same problems.


Anyone know how can i use my external storage directly using SAS cables?

---

### Post by dcstar on 2010-03-24
> **sevilla said:**
> 
I want increase my storage of my server with a StorageTek 2350.
.......

I do not see that the X2450 is actually Ubuntu/Debian compatible, the only thing the specs say is Red Hat & SUSE Linux:

[http://www.sun.com/servers/x64/x4250/specs.xml](http://www.sun.com/servers/x64/x4250/specs.xml)

There is no guarantee that anything more than basic operation of the SAS is actually supported if those kernel errors are anything to go by.

---

### Post by sevilla on 2010-03-24
I know ubuntu isnt fully compatible but i want know if someone had playing with this combination..

---

