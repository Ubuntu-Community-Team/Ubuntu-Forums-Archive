---
title: "fstab mount results in empty folder"
date: 2011-05-01
forum: General Help
---

### Post by ChaosIII on 2011-05-01
Hey!

I've recently installed Natty and now I've got a problem mounting two of my partitions via fstab. This is what my fstab file looks like:

```

proc                        /proc            proc    nodev,noexec,nosuid    0 0
UUID=2ea65813-a227-405f-90d2-69598120808e      /                          ext4    defaults,errors=remount-ro    0 1
UUID=6e4f2339-b796-484e-9473-804b4db1531e      /home                      ext4    defaults          0 2
UUID=FE60F02460EFE0FF                /home/michael/Windows    ntfs    defaults          0 0
UUID=e89dfcea-8b9d-46ff-928f-9ecd9e1bd8aa    /home/michael/Private    ext4    defaults          0 0
/dev/mapper/cryptswap1                none            swap    sw            0 0

```The problem are the second and third to last lines, mounting /home/michael/Windows and /home/michael/Private. After the system start, the two drives are being displayed on the desktop and in the unity launcher. They are, however, completely empty.

I CAN mount them by first executing *sudo umount -a *(which tells me that the two partitions in question cannot be unmounted, because they are not mounted) and then *sudo mount -a* (which correctly mounts the two partitions). The mount does not work, if I omit the umount command. I am lost. What's wrong?

Best,
ChaosIII

---

### Post by sdewittofm on 2011-05-11
I have the exact same problem, any ideas out there?

---

### Post by ChaosIII on 2011-05-13
I found something: It seems to be a problem with mounting under encrypted partitions. I tried mounting the drives under /media (and then created symlinks in the places where I actually would like to have mounted them) and it worked just fine. I also have no problem with mounting on my other box where I don't use an encrypted /home folder.

---

### Post by sdewittofm on 2011-05-13
Good catch, I hadn't thought about that.  I tried your suggestion and it seemed to fix the problem.  Thanks.

---

