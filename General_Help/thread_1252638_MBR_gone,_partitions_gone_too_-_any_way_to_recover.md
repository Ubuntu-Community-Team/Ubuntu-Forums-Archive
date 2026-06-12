---
title: "MBR gone, partitions gone too - any way to recover?"
date: 2009-08-29
forum: General Help
---

### Post by moodog on 2009-08-29
I've been having some problems with my machine, and wanted to clear the MBR. I used this command from the livecd to clear the mbr:

```
sudo dd if=/home/ubuntu/fakembr80.txt of=/dev/sda bs=512 count=1
```

providing fakembr file, and then rebooted. I've now found that I've lost all partitions on that drive. Is there any way to recover the partitions? I don't have a copy of the original mbr.

When I start gparted from the livecd, it shows 

/dev/sda: unrecognised disk label

---

### Post by drs305 on 2009-08-29
Make sure you have the *universe* repository enabled.
From the LiveCD, download "testdisk": sudo apt-get install testdisk

Here are some links to testdisk usage. You can also search these forums for testdisk discussions:

[TestDisk Overview]("http://www.cgsecurity.org/wiki/TestDisk")

[TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

---

### Post by moodog on 2009-08-29
Thanks - gpart was able to solve the problem easily.

---

