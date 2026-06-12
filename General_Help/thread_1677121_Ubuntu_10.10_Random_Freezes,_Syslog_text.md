---
title: "Ubuntu 10.10 Random Freezes, Syslog text"
date: 2011-01-28
forum: General Help
---

### Post by mattym123 on 2011-01-28
Hi,

In the last month, I've had a lot of random freezes in ubuntu 10.10, I checked the syslog and found the following, This was repeated numerous times in the log, Can anyone make sense to this?

sr 6:0:0:0: [sr1] Unhandled sense code
sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 6:0:0:0: [sr1] Sense Key : Blank Check [current] 
sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
end_request: I/O error, dev sr1, sector 0

Buffer I/O error on device sr1, logical block 0
sr 6:0:0:0: [sr1] Unhandled sense code
sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 6:0:0:0: [sr1] Sense Key : Blank Check [current] 
sr 6:0:0:0: [sr1] Add. Sense: No additional sense information
sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
end_request: I/O error, dev sr1, sector 0

Thanks

Matt

---

