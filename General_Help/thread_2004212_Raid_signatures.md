---
title: "Raid signatures"
date: 2012-06-15
forum: General Help
---

### Post by hop5uk on 2012-06-15
I am running 12.04 server edition.I have 2 x SSD disks which i set up during installation to run my operating System on Raid 1.I now want to add 3 x iTB disks for storage operating on Raid 5.I added them to the server and tried to use mdadm to set up the array.For some reason the array did not work properly and so i tried to start the procedure again by deleting the partition on each TB disk.
Unfortunately i am now in the position that the server will not boot with the storage disks connected.If i disconnect them it will boot fine but when they are connected ,the system gets to the Grub screen and then the screen goes blank.After alot5 of research i think that there is still a Raid signature left on the disks which is messing up the booting, but how can i get rid of it?I have tried removing one of the disks from the case and connecting it to the server after boot up via a USB caddie.I then tried to zero the superblock but it did not seem to be able to write to the disk.I am finally out of ideas and am left with 3 paperweights.Can anyone help?

---

### Post by steeldriver on 2012-06-15
mdadm --zero-superblock maybe? I think that basically overwrites the superblock with zeros - preventing it from identifying as a RAID device

```
mdadm --zero-superblock /dev/sdX
```You may need to stop the array and/or remove the device first if you haven't already done so

```
mdadm --stop /dev/mdN

mdadm --remove /dev/sdX
```or I guess if you don't want the data you could dd zeros over the whole partition - which would include any superblock(s) - but that may take a while

---

