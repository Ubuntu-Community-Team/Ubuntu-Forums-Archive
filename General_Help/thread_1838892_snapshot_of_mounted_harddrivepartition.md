---
title: "snapshot of mounted harddrive/partition"
date: 2011-09-04
forum: General Help
---

### Post by flomow on 2011-09-04
Hi,
I am using Windows XP at the moment as a host to vmware server/virtualbox.
With our new server we want to switch to xubuntu as host operating system with virtualbox only.

At the moment we are using "Drive snapshot" to backup all data. This tool has the capability to make a snapshot of a partition freezing the actual situation and writing hdd changes to a buffer as long till snapshot is done. It is also possible to make differential backups from a hash file.

Practical this works like running a php-skript every night that does the following:

[LIST]
[*]Determing wich weekday it is (to choose betwenn full and incremental backuo)
[*]Suspending all vm guests
[*]Start the snapshot tool in the background
[*]resume all vm guests
[*]Wait until snapshot tool is finished
[/LIST]
This is much more comfortable than resuming the guest not until the snapshot/backup is done! (vm guests are oflline for only about 2 minutes!)

:confused: My question is now: Is there a linux toll that has the same functionality as "drive snapshot" ([http://www.drivesnapshot.de)?]("http://www.drivesnapshot.de%29?") the only tools i found do backups snapshots in UNmounted partitions...

Thanks in advance, flomow

---

### Post by flomow on 2011-09-09
Anyone?

---

### Post by Bodsda on 2011-09-09
> **flomow said:**
> Hi,
I am using Windows XP at the moment as a host to vmware server/virtualbox.
With our new server we want to switch to xubuntu as host operating system with virtualbox only.
 
At the moment we are using "Drive snapshot" to backup all data. This tool has the capability to make a snapshot of a partition freezing the actual situation and writing hdd changes to a buffer as long till snapshot is done. It is also possible to make differential backups from a hash file.
 
Practical this works like running a php-skript every night that does the following:

[LIST]
[*]Determing wich weekday it is (to choose betwenn full and incremental backuo)
[*]Suspending all vm guests
[*]Start the snapshot tool in the background
[*]resume all vm guests
[*]Wait until snapshot tool is finished
[/LIST]This is much more comfortable than resuming the guest not until the snapshot/backup is done! (vm guests are oflline for only about 2 minutes!)
 
:confused: My question is now: Is there a linux toll that has the same functionality as "drive snapshot" ([http://www.drivesnapshot.de)?]("http://www.drivesnapshot.de%29?") the only tools i found do backups snapshots in UNmounted partitions...
 
Thanks in advance, flomow
 
What are you actually trying to achieve?
 
Both vmware and virtualbox provide native snapshots which are a lot more powerful then the steps you detailed, and they don't take the machine offline
 
Bodsda

---

### Post by Cheesemill on 2011-09-09
You could take a look at setting up your drives/partitions using LVM. This way you can take a snapshot of the partition that hosts your VM files.

Check out [this page]("http://www.tuxradar.com/content/lvm-made-easy") or just google for LVM to get more info.

The Xubuntu installer can easily set up LVM partitions if you choose manual partitioning during setup.

---

### Post by flomow on 2011-09-11
> **Bodsda said:**
> What are you actually trying to achieve?
 
Both vmware and virtualbox provide native snapshots which are a lot more powerful then the steps you detailed, and they don't take the machine offline
 
Bodsda

Hey, 
AFAIK do vmwareserver and virtualbox not revert to a snapshot with the vm-guest running...
So the VMs are offline during merging the snapshot and the original "files" together.

> ou could take a look at setting up your drives/partitions using LVM.  This way you can take a snapshot of the partition that hosts your VM  files.

Check out [this page]("http://www.tuxradar.com/content/lvm-made-easy") or just google for LVM to get more info.

The Xubuntu installer can easily set up LVM partitions if you choose manual partitioning during setup.     Thanks, I will had a look at your link. Thats nearly what i need.

Did I understand it right that for creating a snapshot on LVM you need extra space on that LVM (to copy changed data)?
Thanks, flomow

---

