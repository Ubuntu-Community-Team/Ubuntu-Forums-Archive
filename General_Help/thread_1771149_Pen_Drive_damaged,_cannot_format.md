---
title: "Pen Drive damaged, cannot format"
date: 2011-05-30
forum: General Help
---

### Post by kyokusei on 2011-05-30
Hi, I've a Kingston Datatraveler 410 16GB pen drive that is damaged.
On windows it shows as "removable drive" and if I double click on it it say "insert a media", and obviously I cannot format.
On ubuntu gparted don't shows the device.
if I take "dmesg" it shows:

```

[ 2086.796089] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 2086.935169] scsi5 : usb-storage 1-1:1.0
[ 2087.936740] scsi 5:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 2
[ 2087.944900] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 2087.948811] sd 5:0:0:0: [sdb] READ CAPACITY failed
[ 2087.948820] sd 5:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2087.948830] sd 5:0:0:0: [sdb]  Sense Key : Illegal Request [current] 
[ 2087.948841] sd 5:0:0:0: [sdb]  Add. Sense: Invalid command operation code
[ 2087.949308] sd 5:0:0:0: [sdb] Write Protect is off
[ 2087.949316] sd 5:0:0:0: [sdb] Mode Sense: 16 1a 09 51
[ 2087.950181] sd 5:0:0:0: [sdb] No Caching mode page present
[ 2087.950189] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2087.955186] sd 5:0:0:0: [sdb] READ CAPACITY failed
[ 2087.955195] sd 5:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2087.955204] sd 5:0:0:0: [sdb]  Sense Key : Illegal Request [current] 
[ 2087.955214] sd 5:0:0:0: [sdb]  Add. Sense: Invalid command operation code
[ 2087.956565] sd 5:0:0:0: [sdb] No Caching mode page present
[ 2087.956573] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2087.956581] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```

There is a chance to format the pen drive?
Thanks

---

### Post by coldraven on 2011-05-30
It looks like it is broken :(
These things are just not designed to be kept in your pocket, they get bent!
I bought a rubberised "shockproof, waterproof" drive and it only lasted two weeks before it died.
It is maybe better to buy an SD card and adapter. the adapter will protect the card and if the adapter gets broken they only cost peanuts to replace.

---

### Post by satanselbow on 2011-05-30
> **coldraven said:**
> It looks like it is broken :(
These things are just not designed to be kept in your pocket, they get bent!
I bought a rubberised "shockproof, waterproof" drive and it only lasted two weeks before it died.
It is maybe better to buy an SD card and adapter. the adapter will protect the card and if the adapter gets broken they only cost peanuts to replace.


I learned the hard way that the best mileage (and least breakable) way to go is miniSD + USB adaptor ;) Sony Ericson do some nice cheap miniSD card readers that have a hinged case to protect the USB plug :D

It is usually the "USB plug" that receives the damage - whereas in reality the storage "chip" is intact but cannot be read or extracted from the enclosure.

---

