---
title: "RAID for stoarage, not installation"
date: 2010-09-08
forum: General Help
---

### Post by miststlkr on 2010-09-08
Every topic I can find when I search for this comes up with people wanting to install to a fakeRAID array, which is not what I am looking for.  I have a SSD with the OCS running on it just fine and want to add a raid array for storage.  I can get the array set up and running only until I reboot, at which point I have to load palimpsest and click to start the array, then mount it.   Is there a way to automate this process when I boot/login?

I am using an Asus M4A87TD-EVO motherboard which uses a jmicron controller chip, but the prefxes in /dev/mapper all start with pdc_ which would indicate a Promise controller, not sure if that is an issue or just extra useless information.  The OS is a 64-bit build of 10.04LTS 


Thanks for any help or links.

---

### Post by ronparent on 2010-09-09
You mention one thing I have noted with my own system. I had moved a raid 0 set from a MB with an nvidia chipset to one with an AMD (pdc) chipset. As I anticipated the partition tables were wiped. The nvidia designation in the meta data was retained!! So now although dmraid finds I have pdc and sil raids it also finds my nvidia raid array! I have had no problem retaining that id and partitioning and installing to it however - so the id remains.

I've personally had no problems with the raid 0 partitions not mounting however since they show in nautilus and mount readily if selected. In pre 9.04 I had the problem that the raids didn't show in nautilus unless I mounted them in fstab which would automatically mount them at boot. This behavior changed with 9.04 when fstab would no longer mount them at boot. There is a problem in 10.04, however, that gparted won't see the raids unless kparts is installed. But, now I'm beginning to ramble. With 10.10 there will be another change in fakeraid behavior that may fix your problem (or make it worse). From my stand point (being installed to a raid) it will be a great improvement. You should probably make a 4 or 5GB investment in a partition to investigate how it would affect your use.

---

