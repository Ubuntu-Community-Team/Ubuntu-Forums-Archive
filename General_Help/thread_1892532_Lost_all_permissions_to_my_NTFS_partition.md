---
title: "Lost all permissions to my NTFS partition"
date: 2011-12-08
forum: General Help
---

### Post by anur.bhargav on 2011-12-08
I have lost "Write" permission for myself, and all other permissions for 'Others' and 'Group' on my important NTFS Partition(Contains all my Data).
Any amount of Chmod(ing) or using the GUI to set it right isn't working.

I get this error when doing it the GUI way.(No other details of why it couldn't set permissions is mentioned).

[IMG]http://ubuntuone.com/3HcmOHQsjG1BTuI0OG41ik[/IMG]


And this happens when doing it in CLI. This is quite an issue need help fast.

[IMG]http://ubuntuone.com/7BPgy0mRI2bZt4elvbtjqQ[/IMG]

Output of ```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=d615ecff-94d9-43e5-9fad-7a77886effca /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=50e23f68-b771-46f0-b028-12f037edc242 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=fb914df6-6962-43a6-adfa-269a0f2c8744 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=ce1ff294-0e83-445c-912d-d28c09de8844 none            swap    sw              0       0

```

---

### Post by WorMzy on 2011-12-08
You cannot chmod anything on an NTFS filesystem. Neither NTFS or FAT support UNIX file permissions.

How are you mounting the partition? Why are you showing us your fstab? If you'd like to have the partition automatically mounted, then see if this tutorial helps you: [HOWTO: Mount NTFS partitions with specific ownership/permissions]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by flemur13013 on 2011-12-08
Did you try "sudo chmod ... " ?

I don't see an NTFS partition in your fstab; FWIW, mine looks like this:

```
# Mount DATA NTFS partition:
/dev/sda5    /data      ntfs-3g    defaults    0 0
```

It ends up owned by root, but with all permissions for everyone.

---

### Post by anur.bhargav on 2011-12-08
> **WorMzy said:**
> You cannot chmod anything on an NTFS filesystem. Neither NTFS or FAT support UNIX file permissions.

How are you mounting the partition? Why are you showing us your fstab? If you'd like to have the partition automatically mounted, then see if this tutorial helps you: [HOWTO: Mount NTFS partitions with specific ownership/permissions]("http://ubuntuforums.org/showthread.php?t=1604251")

How am I mounting, that'd be manually. Why fstab, I thought it might be useful as I was asked for it for an old NTFS mounting/unmounting problem.

---

### Post by WorMzy on 2011-12-08
Manually how?

Are you using the mount command? udisks? Through a file manager?

---

### Post by anur.bhargav on 2011-12-08
> **WorMzy said:**
> Manually how?

Are you using the mount command? udisks? Through a file manager?

Through Nautilus File manager.. I just click on the partition. Then it'll Mounted at /media/Bunker (Device: /dev/sda5)

[IMG]http://ubuntuone.com/2m6qkMRN7FZvdELnTwLeFJ[/IMG]

---

### Post by WorMzy on 2011-12-08
I'm pretty sure that nautilus uses udisks, so unmount the partition, then run (in a terminal):

```
udisks --mount /dev/disk/by-label/Bunker
```

Do you get any errors?

---

### Post by anur.bhargav on 2011-12-08
> **WorMzy said:**
> I'm pretty sure that nautilus uses udisks, so unmount the partition, then run (in a terminal):

```
udisks --mount /dev/disk/by-label/Bunker
```

Do you get any errors?

Still no luck :confused:. The partition did get mounted but permissions remain same.

---

### Post by WorMzy on 2011-12-08
I assume that you just got the standard "Mounted /org/freedesktop/UDisks/devices/sd** at /media/Bunker" message?

To your knowledge, have you changed any udisk rules?

Does ```
dmesg | tail
```
list any error messages?

And what does ```
mount | grep -i Bunker
``` say?

---

### Post by anur.bhargav on 2011-12-08
> **WorMzy said:**
> I assume that you just got the standard "Mounted /org/freedesktop/UDisks/devices/sd** at /media/Bunker" message?

To your knowledge, have you changed any udisk rules?

Does ```
dmesg | tail
```
list any error messages?

And what does ```
mount | grep -i Bunker
``` say?

Sorry for the late reply. 
Output of ```
dmesg | tail
``` before mounting "Bunker"

> ```
[   21.516780] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   21.516784] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.516927] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.682220] init: plymouth-stop pre-start process (1429) terminated with status 1
[   22.368436] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   22.504805] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   24.499959] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  271.126821] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  271.208603] NTFS volume version 3.1.
[  400.297494] NTFS volume version 3.1.
```

After Mounting "Bunker"

> ```
[   21.516784] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.516927] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.682220] init: plymouth-stop pre-start process (1429) terminated with status 1
[   22.368436] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   22.504805] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   24.499959] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  271.126821] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  271.208603] NTFS volume version 3.1.
[  400.297494] NTFS volume version 3.1.
[  511.761708] NTFS volume version 3.1.
```

Output of ```
mount | grep -i Bunker
```

> ```
/dev/sda5 on /media/Bunker type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

```

---

### Post by WorMzy on 2011-12-08
Well, it appears that you're using the ntfs driver for some reason, rather than the ntfs-3g driver; that would explain why you don't have write access. Make sure that you have the ntfs-3g package installed. If you do, try re-installing it.

---

### Post by anur.bhargav on 2011-12-09
> **WorMzy said:**
> Well, it appears that you're using the ntfs driver for some reason, rather than the ntfs-3g driver; that would explain why you don't have write access. Make sure that you have the ntfs-3g package installed. If you do, try re-installing it.

OMG would be the word :popcorn:
You are awesome.. That did it. I think installing GParted caused the problem.
Can u educate me on how u were able to determine what package I was running in place of the default.

Now the output of ```
dmesg | tail
``` is, there's quite a lot of change

```
[   32.768265] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   32.824054] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   32.824370] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.216757] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   34.216763] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   34.216906] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.834081] audit_printk_skb: 12 callbacks suppressed
[   34.834084] type=1400 audit(1323430454.631:19): apparmor="DENIED" operation="open" parent=1655 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=1699 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   66.210594] NTFS driver 2.1.30 [Flags: R/O MODULE].
[   66.292666] NTFS volume version 3.1.
```

Output of ```
mount | grep -i Bunker
``` is
```
/dev/sda5 on /media/Bunker type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

In this output I could figure out rw=read/write which was ro=read_only previously.

---

### Post by WorMzy on 2011-12-09
> **anur.bhargav said:**
> Can u educate me on how u were able to determine what package I was running in place of the default.

This line in your dmesg: 
```
[  271.126821] NTFS driver 2.1.30 [Flags: R/O MODULE].
```

The "R/O MODULE" gives it away really. ;)

> In this output I could figure out rw=read/write which was ro=read_only previously. 

Exactly. :)

Glad you've got it working again.

---

### Post by anur.bhargav on 2011-12-09
> **WorMzy said:**
> 

Glad you've got it working again.

Thanks to you :)

---

