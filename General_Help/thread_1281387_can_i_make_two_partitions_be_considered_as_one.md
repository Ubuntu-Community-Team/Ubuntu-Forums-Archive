---
title: "can i make two partitions be considered as one?"
date: 2009-10-03
forum: General Help
---

### Post by chriskin on 2009-10-03
i used to have an ext4 for jaunty, now i have another for karmic
they are not next to each other but i would like karmic to get the extra 50gbs of jaunty now that i no longer go there, can i make my system think that the two partitions are one?

---

### Post by Bachstelze on 2009-10-03
No. Not without wiping everything, at least.

---

### Post by chriskin on 2009-10-03
> **Bachstelze said:**
> No. Not without wiping everything, at least.

if you mean wiping jaunty,i have no problem with that
if you mean wiping karmic,that's a problem :P

---

### Post by barthel on 2009-10-03
Personally, I'd just leave that partition alone as a backup. (I've still got hardy installed on one partition, which I'll use either for karmic or lucid.)

Your other best option is to back everything up, then move/consolidate your partitions. Parted might do it for you, but it might be simpler to just repartition and restore your backup.

---

### Post by CatKiller on 2009-10-03
Why not just mount the other partition?

---

### Post by orange-wedge on 2009-10-03
if your partition on karmic was lvm you could merge them.

[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by chriskin on 2009-10-03
> **CatKiller said:**
> Why not just mount the other partition?

i can mount it but then they would be separate ones, i would like them to be one 

> **barthel said:**
> Personally, I'd just leave that partition alone as a backup. (I've still got hardy installed on one partition, which I'll use either for karmic or lucid.)

Your other best option is to back everything up, then move/consolidate your partitions. Parted might do it for you, but it might be simpler to just repartition and restore your backup.

my hard drive is 160, not enough to spare partitions as backup

anyway, i'll find something to do :popcorn:

---

### Post by CatKiller on 2009-10-03
> **chriskin said:**
> i can mount it but then they would be separate ones, i would like them to be one 

Why?

Anyway, if they're on the same drive you could just nuke your Jaunty partition and shuffle the partitions in Gparted to expand your Karmic partition into the unallocated space. You'll need to check your GRUB configuration so that it doesn't still go looking for your Jaunty partition, but you'd need to do that anyway.

---

### Post by MaxIBoy on 2009-10-03
I can't believe no one has yet mentioned unionFS.

UnionFS lets you merge many filesystems or even just many folders together, but keep in mind:

[LIST]
[*]One filesystem has a higher "priority" than the other one, so if two have a file with the same name, the file from the higher priority one is shown.
[*]Also, the higher-priority one recieves all new files if you create them.
[/LIST]


So you could empty the unused Jaunty partition, and put it in UnionFS with higher priority than the Karmic partition, and all newly-created files go to the empty partition. 

****HOWEVER****
Do NOT put this over your root directory! Doing so will prevent some upgrades from working properly, because the UnionFS doesn't work when you haven't finished booting yet! So if a file which is important to the boot process gets added, it will go to a seperate partition and it will be missing during boot!

Do this to your home folder, which is where you've got all those huge, hard-disk-hungry videos etc. You can in fact mount an entire partition on top of a folder with UnionFS.




Honestly though, it's probably best to redo your partition table. And in the future, set up a dedicated home partition so you can share your documents and stuff accross multiple distros!

---

### Post by chriskin on 2009-10-03
> **MaxIBoy said:**
> I can't believe no one has yet mentioned unionFS.

UnionFS lets you merge many filesystems or even just many folders together, but keep in mind:

[LIST]
[*]One filesystem has a higher "priority" than the other one, so if two have a file with the same name, the file from the higher priority one is shown.
[*]Also, the higher-priority one recieves all new files if you create them.
[/LIST]


So you could empty the unused Jaunty partition, and put it in UnionFS with higher priority than the Karmic partition, and all newly-created files go to the empty partition. 

****HOWEVER****
Do NOT put this over your root directory! Doing so will prevent some upgrades from working properly, because the UnionFS doesn't work when you haven't finished booting yet! So if a file which is important to the boot process gets added, it will go to a seperate partition and it will be missing during boot!

Do this to your home folder, which is where you've got all those huge, hard-disk-hungry videos etc. You can in fact mount an entire partition on top of a folder with UnionFS.




Honestly though, it's probably best to redo your partition table. And in the future, set up a dedicated home partition so you can share your documents and stuff accross multiple distros!

thanks, that seems to be a worthy temporary solution, since that's what i'm searching for :)

---

### Post by barthel on 2009-10-04
> **MaxIBoy said:**
> I can't believe no one has yet mentioned unionFS.

I thought about mentinoning it, but given that the poster was referring to partitions by release name, I suspected that they were root partitions, and therefore not good candidates.

> Do this to your home folder, which is where you've got all those huge, hard-disk-hungry videos etc. You can in fact mount an entire partition on top of a folder with UnionFS.


If you're going to mount a partion on a folder, why not just set it up in fstab?

One habit I've kept from my Slackware days is the separate local partition, mounted as /usr/local. After a distribution install, I log in as root, and replace /home with a symlink to /usr/local/home.

---

