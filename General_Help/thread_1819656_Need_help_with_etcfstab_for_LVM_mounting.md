---
title: "Need help with /etc/fstab for LVM mounting"
date: 2011-08-06
forum: General Help
---

### Post by hakras on 2011-08-06
I configured a logical volume using 2x1TB USB drives.  Everything is working, but I'm worried that the system may lose its mind after a reboot and the logical volume will be lost.  My guess is that I should modify /etc/fstab to make sure the USB drives are detected as they currently are and that the logical volume is mounted.  Unfortunately, I'm not sure how to do this and don't want to make a mistake.

Here is the output of blkid:
```

/dev/sda: TYPE="nvidia_raid_member"
/dev/sdc1: UUID="588b2221-8196-460e-b5d2-a10520666078" TYPE="xfs"
/dev/sdb: TYPE="nvidia_raid_member"
/dev/sde1: LABEL="STORAGE3" UUID="e247f346-634b-435b-baa4-0a200acbf488" TYPE="xfs"
/dev/sdd1: UUID="XV5Rat-h0CZ-WhKt-aypc-EeAN-hXQS-h5KIyd" TYPE="LVM2_member"
/dev/sdf1: UUID="vPJIKp-EdCs-koit-sECK-HoTU-hikk-mp9Hsv" TYPE="LVM2_member"
/dev/mapper/nvidia_abgfdeeh1: UUID="f0299db3-b46c-4014-9ceb-dac0701f7c9e" TYPE="ext4"
/dev/mapper/nvidia_abgfdeeh2: UUID="d680efcd-a072-467c-86f3-6e4112a3d341" TYPE="ext4"
/dev/mapper/nvidia_abgfdeeh3: UUID="b5b749da-44c3-41b5-a4b1-87448b9c733e" TYPE="swap"
/dev/mapper/lvmgroup-lvmvolume: UUID="5b33294d-a38b-4542-b036-4ee894c82240" TYPE="xfs"

```

Here is my current /etc/fstab:
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_abgfdeeh1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_abgfdeeh2 /home           ext4    defaults        0       2
# /var was on /dev/sda1 during installation
UUID=588b2221-8196-460e-b5d2-a10520666078 /var            xfs     defaults        0       2
/dev/mapper/nvidia_abgfdeeh3 none            swap    sw              0       0

```

I have not made any modifications to /etc/fstab to this point.  What entries should I make in order to ensure the USB drives and the logical volume keep their current mount points?

---

### Post by hakras on 2011-08-06
I've been trolling the oracle (google) and can't come up with anything that matches what I'm looking for.  I currently have my logical volume mounted as /mnt/lvm, but need to add this to /etc/fstab along with the USB drives being properly assigned so the logical volumes are credible after a reboot.

For the logical volume, I'm thinking this will work:
```

UUID=5b33294d-a38b-4542-b036-4ee894c82240 /mnt/lvm            xfs     defaults        0       2

```

Does that look correct?  Does LVM have a way of knowing (already uses UUID) which drives belong in the group?  Maybe I'm driving myself nuts over nothing.  Anyone?

---

### Post by galvatron408 on 2011-08-06
hmm, I have never heard of what you're trying to accomplish with LVM.

When I work with LVM, it's just /dev/volume_group/logical_group soooo fstab would be...

/dev/volume_group/logical_group   /mnt/point

no matter how many drives you add, it's always going to be the same vg/lg.

---

### Post by hakras on 2011-08-06
I get what you're saying.  How about with USB drives being part of the LVM?  My 2 USB drives are /dev/sdd and /dev/sdf.  What if these USB drives somehow get unplugged and accidentally get plugged into different ports?  Will they still be /dev/sdd and /dev/sdf?  If not, will LVM know that they belong to the volume?

---

