---
title: "mdadm raid (level 1) nfs mysql access denied"
date: 2010-09-20
forum: General Help
---

### Post by Aurawin on 2010-09-20
I just built an AMD Phenom II Six Core with 4 Gigs Ram a 160Gib / and swap, and (2) Two Tb mirror for Raid (data storage)

I had been using DMRAID in the deprecated box but this box has MDADM v3.1.4 - 31st August 2010 from source (on MDADM wikipedia).

I have no permission problems with using the raid and dmraid is un-installed.  The raid is working perfectly and is mounted in my fstab with ext4 defaults 0 2 as my options.

I have two exports
/media/raid/Test 
/test 

Both show IP and subnet on the showmount -e for the server.
I can mount the test just fine on the server.
I cannot, however, mount the /media/raid/Test error:
mount.nfs: access denied by server while mounting hostname:/media/raid/Test

Using dmraid I am able to have the deprecated box export and mount nfs shares from the raid but using MDADM on the new computer, I cannot.  I get similar results with pointing MYSQL's data folder to a location on the "/media/raid/Database" (even with apparmor entries).

Anyone solve this problem for mysql or nfs?

---

### Post by Aurawin on 2010-09-20
Work A Round is forcing NFSV3 because NFSV4 is failing and not even logging any entries.

Quick fix : mount -t nfs -o vers=3 (...)

---

