---
title: "ubuntu not booting."
date: 2010-05-09
forum: General Help
---

### Post by stevedes on 2010-05-09
Ok i installed ubuntu Lucid via wubi and it worked perfectly until today. At a certain point, every application i launched would just show up as a empty window and whichever programs that were already open started complaining of a read-only filesystem.:confused:

so I ctrl+alt+F2 and Ctrl+alt+del and restarted my computer.
upon restarting, plymouth did not exit on its own, so I hit Esc. and saw the following error message on the terminal.

```
fsck from util-linux-ng 2.17.2
/dev/loop0 contains a file system with errors, check forced
/dev/loop0: Inodes that were a part of a corrupted orphan linked list found.

/dev/loop0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
           (i.e., without -a or -p options)
mountall: fsck / [667] terminated with status 4
mountall: File system has errors: /
```

---

### Post by nikefalcon on 2010-05-09
Boot off a Live CD and manually run fsck on the partition.But since you are using WUBI you'll have to find a way to acess the virtual disk form the live cd.....

try this:
> 
Boot the Ubuntu Desktop CD, or another LiveCD, then  mount the windows partition: 
```

sudo mkdir /win
sudo mount /dev/sda1 /win

```Replace sda1  with the appropriate device (a = disk, 1 = partition number), then mount  the virtual disk therein 
```

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

```Now the content of the virtual disk will be visible  under /vdisk. 7.04 users will have to install ntfs-3g first and specify  it as fstype to gain r/w access.  
To check the  filesystem you can use: 
```

sudo fsck /win/ubuntu/disks/root.disk[FONT=Verdana]
[/FONT]
```[FONT=Verdana]
[/FONT][FONT=Verdana]

  found this solution in the[ WubiGude ]("https://wiki.ubuntu.com/WubiGuide")on UbuntuWiki.
[/FONT]

---

### Post by stevedes on 2010-05-10
Thanks Nike, will try it when I get hold of a liveCD

---

### Post by stevedes on 2010-05-10
> **nikefalcon said:**
> Boot off a Live CD and manually run fsck on the partition.But since you are using WUBI you'll have to find a way to acess the virtual disk form the live cd.....

try this:
[FONT=Verdana]

  found this solution in the[ WubiGude ]("https://wiki.ubuntu.com/WubiGuide")on UbuntuWiki.
[/FONT]
Yes, I tried it and it works like a treat, Ubuntu has now booted perfectly.

---

