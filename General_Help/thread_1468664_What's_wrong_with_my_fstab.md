---
title: "What's wrong with my fstab ?"
date: 2010-05-01
forum: General Help
---

### Post by MooPi on 2010-05-01
I have edited my fstab to auto mount two separate partitions. I've named the partitions BigBin and WindowsXP. BigBin auto mounts fine but my WindowsXP  will not and halts boot and causes plymouth to ask permission to skip the drive or manually correct. I skip and proceed with boot but PCmanFM doesn't mount the WindowsXP drive until I manually mount. Openbox system minimal install, pcmanfm.
```
*-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/disk
                version: 3.1
                serial: 58f54a47-c93e-714f-b3af-e1edd0f2aaa3
                size: 22GiB
                capacity: 22GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-04-29 06:34:39 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/BigBin
                version: 1.0
                serial: 819005e9-fd37-4f2a-91ef-162b7fe9e400
                size: 257GiB
                capacity: 257GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2010-04-29 03:17:17 filesystem=ext3 label=BigBin modified=2010-05-01 14:01:37 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,errors=continue,data=ordered mounted=2010-05-01 14:01:37 state=mounted
``````
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b3ce4e2a-f862-4f38-9402-00301e1f52a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b447b24-4a29-425c-87c5-4068e5ea50e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# BigBin /dev/sda3
UUID=819005e9-fd37-4f2a-91ef-162b7fe9e400 /media/BigBin   ext3     user,auto   0     0
# WindowsXP /dev/sda2
UUID=58f54a47-c93e-714f-b3af-e1edd0f2aaa3 /media/WindowsXP   ntfs   user,auto   0     0
```

---

### Post by DeMus on 2010-05-01
Do you have NTFS-3G running? You can install it through synaptic.

---

### Post by WorMzy on 2010-05-01
Does /media/WindowsXP exist? Is it empty?

Also, could you enter 'sudo blkid' into a terminal and post the output here?

Finally, is it really necessary to mount these partitions at boot? Could you not just mount them ad hoc?

---

### Post by coffeecat on 2010-05-01
> **DeMus said:**
> Do you have NTFS-3G running? You can install it through synaptic.

The ntfs-3g package comes in a default install. Since before Jaunty. Possibly even Hardy iirc.

> **MooPi said:**
> ```

# WindowsXP /dev/sda2
UUID=58f54a47-c93e-714f-b3af-e1edd0f2aaa3 /media/WindowsXP   ntfs   user,auto   0     0
```

I wonder if the options "user,auto" are your problem although, tbh, I don't know. I've been automounting NTFS partitions with fstab for a couple of years now, and a simple "defaults" or "defaults,nls=utf8" in field 4 works just fine for me. For example, this is a line from a Lucid fstab that I set up this morning:

```
# /media/DataA on /dev/sda2
UUID=FE201A50201A0FEF /media/DataA    ntfs    defaults,nls=utf8 0       0
```It's working just fine. By the way, you can have 'ntfs' or ntfs-3g' in the third field. It makes no difference. The ntfs-3g driver gets used either way.

---

### Post by MooPi on 2010-05-01
I have ntfs-3g installed and I can read and write to the WindowsXP folder after mount. Here is my output from blkid
```
/dev/sda1: UUID="b3ce4e2a-f862-4f38-9402-00301e1f52a1" TYPE="ext4" 
/dev/sda2: LABEL="WindowsXP" UUID="7EBC9389BC933A9B" TYPE="ntfs" 
/dev/sda3: LABEL="BigBin" UUID="819005e9-fd37-4f2a-91ef-162b7fe9e400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="9b447b24-4a29-425c-87c5-4068e5ea50e4" TYPE="swap" 
/dev/sdb1: LABEL="Sabrent" UUID="0D12-96B0" TYPE="vfat" 
/dev/sdb2: LABEL="Windows_BU" UUID="46d6fc5a-07cb-41ab-838b-80ae3523f196" TYPE="ext2" 
```



I just saw the glaring problem. My UUID for the WindowsXP partition was wrong and I have just corrected for a successful reboot and auto mount.

---

### Post by coffeecat on 2010-05-01
> **MooPi said:**
> 
```

# WindowsXP /dev/sda2
UUID=58f54a47-c93e-714f-b3af-e1edd0f2aaa3 /media/WindowsXP   ntfs   user,auto   0     0
```

> **MooPi said:**
> ```
 
/dev/sda2: LABEL="WindowsXP" UUID="7EBC9389BC933A9B" TYPE="ntfs" 
```

The UUID is wrong in your fstab.

---

### Post by WorMzy on 2010-05-01
There's the problem, the UUID that blkid reports is different to the UUID in fstab.

---

