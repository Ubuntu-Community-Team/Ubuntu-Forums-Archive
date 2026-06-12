---
title: "DVD-ROM drive with read problems"
date: 2011-01-15
forum: General Help
---

### Post by motumboe on 2011-01-15
I have the same problem on two different PCs running ubuntu maverick.

When I try to copy the content of various DVD-ROMs, of different sources (recorded by me or by other people on different PCs), I get CRC errors. My /var/log/messages says, for example:

```
Jan 15 16:58:31 asrock kernel: [ 1431.888232] sr 1:0:0:0: [sr0] Unhandled sense code
Jan 15 16:58:31 asrock kernel: [ 1431.888241] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 15 16:58:31 asrock kernel: [ 1431.888250] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Jan 15 16:58:31 asrock kernel: [ 1431.888260] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Jan 15 16:58:31 asrock kernel: [ 1431.888271] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
Jan 15 16:58:39 asrock kernel: [ 1439.971042] sr 1:0:0:0: [sr0] Unhandled sense code
Jan 15 16:58:39 asrock kernel: [ 1439.971051] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 15 16:58:39 asrock kernel: [ 1439.971060] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Jan 15 16:58:39 asrock kernel: [ 1439.971070] sr 1:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
Jan 15 16:58:39 asrock kernel: [ 1439.971081] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00

```

Have you got any suggestions?

---

### Post by motumboe on 2011-01-22
a little bump
What could I search on Google?

---

### Post by Smart Viking on 2011-01-22
How to you try to copy them? With what program?

You could try with cdparanoia, all through i don't know if it works with DVDs:
```
sudo apt-get install cdparanoia
cdparanoia -B
```

---

### Post by motumboe on 2011-01-22
thank you! I'll try it now

---

