---
title: "ubuntu mount local windows  disk"
date: 2011-08-02
forum: General Help
---

### Post by whynot on 2011-08-02
Hi everyone
How is it possible to add a new hpfs disk with utf16 encoding files system? I would like to add my windows 7 device at the boot beginning automaticly? I could mount in gnome with nautilus with a one mouse click.




```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro	0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

```

/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       45940   368908288    7  HPFS/NTFS
/dev/sda3           45940       91201   363559936    7  HPFS/NTFS

```

Thanks.

---

### Post by dcstar on 2011-08-03
> **whynot said:**
> Hi everyone
How is it possible to add a new hpfs disk with utf16 encoding files system? I would like to add my windows 7 device at the boot beginning automaticly?
.

Install and use the **pysdm** package.

---

### Post by Mark Phelps on 2011-08-03
It's generally a BAD idea to automount a Win7 OS partition read-write in Ubuntu.  Any unclean shutdown or other disk problem runs the risk of leaving your Win7 OS partition in a "dirty" state -- which will then render it unbootable.

IF you're going to automount it, then make sure that it's done read-only.

---

### Post by Morbius1 on 2011-08-03
Couple of comments:

[1] "Mark Phelps" insists on giving that warning all over the place in this forum. There's 2 problems with it:

* He's absolutely right.
* He's always ignored.

[2] I really need to install Ubuntu once using Wubi but based on your fstab it appears that's how you installed Ubuntu. If true then your host partition is already mounted at /host.

Unfortunately it's mounts with permissions = 777 which violates "mark phelps" warning but sound like it's giving you what you want.
[COLOR=Blue][B]
EDIT[/B][/COLOR]: In fact there's even a bug report ( also ignored ) about the way Wubi auto mounts the host directory: [https://bugs.launchpad.net/wubi/+bug/630449](https://bugs.launchpad.net/wubi/+bug/630449)

---

