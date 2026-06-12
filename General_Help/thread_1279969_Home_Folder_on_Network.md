---
title: "Home Folder on Network"
date: 2009-10-01
forum: General Help
---

### Post by measekite on 2009-10-01
Currently I have my home folder on a drive different from the rest of the operating system.

Is it also possible to have an external RAID device connected to a Gbit router with the Home folders there by creating an appropriate entry in FSTAB in the same way I am currently doing?

---

### Post by blueridgedog on 2009-10-01
If you can mount the remote drive into your file system, you can easily have a home directory on it.  Home directories on network devices are common in business.

---

### Post by measekite on 2009-10-02
> **blueridgedog said:**
> If you can mount the remote drive into your file system, you can easily have a home directory on it.  Home directories on network devices are common in business.

Yes but I plan on building a new desktop computer.  I am also thinking about an external RAID enclosure that connects via Gbit Ethernet.

How can I tell if this network attached device will mount into my filesystem before I spend the money to purchase it.  

If I am not able to then I will enable motherboard raid in my desktop.

---

### Post by Ocxic on 2009-10-02
just add the netowrk share, to your fstab and it will mount at boot, you'll not need you home directory till you login so you shouldn't have to worry about timing (if you can use NFS i would reccommend that)

---

### Post by blueridgedog on 2009-10-02
> **measekite said:**
> Yes but I plan on building a new desktop computer.  I am also thinking about an external RAID enclosure that connects via Gbit Ethernet.

How can I tell if this network attached device will mount into my filesystem before I spend the money to purchase it.  



Can you post the make and model of the enclosure?  Also, have you already verified that the Gbit Ethernet NIC on your motherboard is linux supported?

---

