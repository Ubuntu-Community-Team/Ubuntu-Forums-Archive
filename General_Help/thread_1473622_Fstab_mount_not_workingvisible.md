---
title: "Fstab mount not working/visible?"
date: 2010-05-05
forum: General Help
---

### Post by r0mmie on 2010-05-05
I have a problem with one of my partitions, that used to be automounted trough fstab, before my upgrade to Lucid.

The partitions is used for storing all things related to virtualization. It's purpose is not relevant to the error, I think.

The affected part of the fstab file looks as follows:

```

# backuppartition on sdb
UUID=b623c9a2-8d4a-4399-be07-b8b1c74d23fd /backup       ext4    defaults        1       3
# Virtualization Partition
UUID=a56a9445-d375-45b4-abb5-d3512da0a3e6 /home/***/virtual            ext4    defaults        1       3

```

I have included the 'backuppartition' part, to show that the settings are correct, because that partition mounts just fine. I checked the UUID's and they are both correct. 'backuppartition' is on /dev/sdb2 and 'virtualization partition' is on /dev/sdb1. sdb1 is the only one giving me troubles.

Now everything points to the fact that sdb1 is mounted properly, as the following dmesg messages and mount overview show:

dmesg | grep sdb

```

[    1.057607] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.057645] sd 3:0:0:0: [sdb] Write Protect is off
[    1.057647] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.057675] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.057775]  sdb: sdb1 sdb2
[    1.097227] sd 3:0:0:0: [sdb] Attached SCSI disk
[   15.624353] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   15.707232] EXT4-fs (sdb1): mounted filesystem with ordered data mode

```

sudo mount

```

/dev/sda2 on /home type ext4 (rw)
/dev/sdb2 on /backup type ext4 (rw)
/dev/sdb1 on /home/***/virtual type ext4 (rw)

```

The problem is, the partition is not mounted. If I look at the files in the directory virtual, it shows an empty directory.

After I manually mount the directory, using sudo mount /dev/sdb1 /home/***/virtual it magically works, and the 'mount' command shows a double entry for /dev/sdb1 as seen below:

```

/dev/sda2 on /home type ext4 (rw)
/dev/sdb2 on /backup type ext4 (rw)
/dev/sdb1 on /home/***/virtual type ext4 (rw)
/dev/sdb1 on /home/***/virtual type ext4 (rw)

```



Any ideas on how to get the partition to automount again (preferably trough fstab)?



P.S. I tried editing the fstab for the virtual parition, to

UUID=a56a9445-d375-45b4-abb5-d3512da0a3e6 /home/***/virtual            ext4    defaults,auto        1       3

Adding auto after defaults. This does not solve the problem though, as I expected.

---

### Post by dino99 on 2010-05-05
so it is inside virtualbox or something else

---

### Post by r0mmie on 2010-05-05
It's inside my main OS, not a virtual OS. I use the parition as a storage for qemu/kvm/virtualbox/vmware images. I don't think the purpose of the partition is in any way related to the problem, as the problem occurs before login.

---

### Post by r0mmie on 2010-05-08
*Bump* Anyone have similar problems? Any ideas?

---

