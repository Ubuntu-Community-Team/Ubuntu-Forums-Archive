---
title: "Mount point screw up"
date: 2011-07-01
forum: General Help
---

### Post by jemmons on 2011-07-01
Hi I'm new with Ubuntu. I have worked with it off and on and have had fairly successful results with most of the times I have worked with it. But I'm stumped with this current problem. I built a new Ubuntu 11.04 machine a while back to be solely used for VM backups from Proxmox. I installed Ubuntu on a scsi raid 1 setup. It totaled 147 gb. I got that up and running after a few mistakes. Then I created Raid 0 with two 1 tb sata drives that would be used for the vm backups. It took a while but I got everything setup. I then mounted the Raid 0 array to /media/data. I then created a NFS share pointing to the data folder. The backups have been running for a while now and yesterday I logged in to double check some things and saw that I was out of disk space on raid 1 array. I started to check and saw that the mounted /media/data folder was taking up space on both the raid 1 and the raid 0. Is this normal? Sorry if I did a terrible job trying to describe my problem. I kind of forgot how I set this thing all up. I know I did something stupid and this is probably a easy fix but I can't seem to figure it out. If I had to I can completely break the RAID apart and start from scratch. Any help would be greatly appreciated. 

Thanks
Ubuntu newbie

---

