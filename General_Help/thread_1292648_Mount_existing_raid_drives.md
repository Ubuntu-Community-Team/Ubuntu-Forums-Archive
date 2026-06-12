---
title: "Mount existing raid drives"
date: 2009-10-16
forum: General Help
---

### Post by acerunner on 2009-10-16
I have two drives that I believe were setup as raid0 on another linux machine. I think it was software raod. I want to move the raid setup to a different machine, but having a little trouble.

The drives show up in /dev as sda1 to 4, and sda1 to 4, instead of mda#. mdadm --query says they are not md arrays, while mdadm --examine shows Raid Level: raid1

If i mount by specifying ext3, I can see the folders, but some are not accessible. For example:
```
# ls
ls: cannot access PUBLIC: No such file or directory
lost+found PUBLIC
#cd PUBLIC
bash: cd: PUBLIC: No such file or directory
```


Please help, i need to access those files.

---

### Post by Crafty Kisses on 2009-10-16
Not sure if this would help any, but do you have the RAID modules loaded? Also can I see the output of the following:
```
sudo fdisk -l
```
From there I or somebody else can look at your table and get more information and help you further.

---

### Post by snek on 2009-10-16
I had a similar problem when moving a 2 drive raid1 array to another server recently. The commands which fixed it were:

 sudo mdadm –scan –assemble /dev/md2 /dev/sdc1 /dev/sdd1
sudo mkdir mount
sudo mount /dev/md2 mount/ 
 
[LIST]
[*] /dev/md2 is the new name of the raid array
[*]/dev/sdc1 is the name of the first drive which was part of the array
[*]/dev/sdd1 is the name of the 2nd drive
[*]you can discover the various drives connected to your system using “sudo blkid”
[/LIST]
Hope this helps you :)

---

### Post by acerunner on 2009-10-17
here's the result of fdisk
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007a00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4         369     2939895   fd  Linux raid autodetect
/dev/sda2             370         382      104422+  fd  Linux raid autodetect
/dev/sda3             383         505      987997+  fd  Linux raid autodetect
/dev/sda4             506      121601   972703620   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007a00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4         369     2939895   fd  Linux raid autodetect
/dev/sdb2             370         382      104422+  fd  Linux raid autodetect
/dev/sdb3             383         505      987997+  fd  Linux raid autodetect
/dev/sdb4             506      121601   972703620   fd  Linux raid autodetect

```

and this is what i get with blkid
```
/dev/sda1: UUID="4f021e55-b41a-d642-ec35-fac8933c140c" TYPE="mdraid" 
/dev/sda2: UUID="5a4c78e6-80c8-dc65-9094-45efacf3e30c" TYPE="mdraid" 
/dev/sda3: UUID="8ed43c58-2eac-221d-5fba-d0d444fab60d" TYPE="mdraid" 
/dev/sda4: UUID="927d99da-7c65-3380-41fe-235cb7cd2673" TYPE="mdraid" 
/dev/sdb1: UUID="4f021e55-b41a-d642-ec35-fac8933c140c" TYPE="mdraid" 
/dev/sdb2: UUID="5a4c78e6-80c8-dc65-9094-45efacf3e30c" TYPE="mdraid" 
/dev/sdb3: UUID="8ed43c58-2eac-221d-5fba-d0d444fab60d" TYPE="mdraid" 
/dev/sdb4: UUID="927d99da-7c65-3380-41fe-235cb7cd2673" TYPE="mdraid" 
/dev/loop0: TYPE="squashfs" 

```

i just wanna be sure im mounting it correctly before I actually do it. I don't want to overwrite or write anything as I am trying to recover deleted data, so i need to make sure there are no writes.

---

### Post by mvwrestler on 2010-06-11
Did you ever get the drives mounted and running correctly?

---

