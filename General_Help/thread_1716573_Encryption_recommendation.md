---
title: "Encryption recommendation"
date: 2011-03-28
forum: General Help
---

### Post by diamond_D on 2011-03-28
I just built my machine using a mixed partitioning scheme of primary, logical and LVM partitions. OS=Ubuntu 10.10 desktop
 
I have 3 sata HD's
 
HD1 - contains primary /boot and / root partitions
contains LVM volumegroup00 with the following mount points: /usr /usr/local /opt /tmp /var /swap /home
 
HD2 - contains a regular logical partition named /vbox1
- rest of space assigned to LVM volumegroup01
 
HD3 - contains a regular logical partition named /vbox2
- rest of space assigned to LVM volumegroup01
 
So as you can see my LVM has 2 volume groups. I want to create 3 logical volumes in volumegroup01 probably called /mediastore /appstore /docstore
 
I just realized that I'd love the ability to encrypt the 3 logical volumes. Is this possible to do post installation? The volumes contain no data as of yet because this was a fresh build. I've never worked with encryption before so I have no idea what to use. If necessary I could go back in with the alternate install CD and repartition the logical volumes.I can't encrypt the whole disk because I need my regular logical partitions. My plan is to also use rsynch to export the files from the logical volumes to an external drive. 
 
Can somebody recommend a solution that will allow me to do what I want above. I've read about LUKS, truecrypt and others but it is all a bit confusing. Looking for recommendations to save me time and frustration before I get my feet wet.
 
Thanks in advance.

---

