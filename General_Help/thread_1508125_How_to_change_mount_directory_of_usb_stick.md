---
title: "How to change mount directory of usb stick?"
date: 2010-06-12
forum: General Help
---

### Post by jasperyate on 2010-06-12
My usb stick continually automounts at /dev/sda10, and for a certain operation I'm trying to do I need it to be mounted at /dev/sda (or sdb, sdv, etc); is there any way to change it's mount directory?

As a bonus question, or rather the real question, what I'm really trying to do is format a bootstrap partition as shown here

```
Command (? for help): p
/dev/sda10
          #                    type name                length   base    ( size )  system
/dev/sda101     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/sda102         Apple_Bootstrap bootstrap             1600 @ 64      (800.0k)  NewWorld bootblock
/dev/sda103              Apple_Free Extra              7626392 @ 1664    (  3.6G)  Free space

Block size=512, Number of Blocks=7628056
DeviceType=0x0, DeviceId=0x0

Command (? for help): q
root@ubuntu:~# hformat -l bootstrap /dev/sda102
hformat: /dev/sda102: error opening medium (No such file or directory)

```but I don't know what to name the partition when the starting mount point is /dev/sda10. If it was originally /dev/sda, I know the second partition would be /dev/sda2, but I can't seem to figure out what directory I should perform the operation on.

any help on either question would be great. cheers.

---

### Post by dcstar on 2010-06-13
> **jasperyate said:**
> My usb stick continually automounts at /dev/sda10, and for a certain operation I'm trying to do I need it to be mounted at /dev/sda (or sdb, sdv, etc); is there any way to change it's mount directory?
.........

Label the partitions and they will be mounted under /media/label-name.

---

