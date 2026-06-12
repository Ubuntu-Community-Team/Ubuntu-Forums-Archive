---
title: "btrfs open_ctree failed after recent update"
date: 2012-02-18
forum: General Help
---

### Post by senojsitruc on 2012-02-18
I recently let the Update Manager run after ignoring it for a couple of weeks. It required a reboot. My USB btrfs volume didn't mount after reboot. dmesg revealed:

[  463.187097] btrfs: open_ctree failed
[  991.567090] device label StoreW devid 1 transid 37077 /dev/sdb
[ 1003.171989] device label StoreW devid 1 transid 37077 /dev/sdb
[ 1003.207990] parent transid verify failed on 79466496 wanted 33999 found 36704
[ 1003.208363] parent transid verify failed on 79466496 wanted 33999 found 36704
[ 1003.208857] parent transid verify failed on 79466496 wanted 33999 found 36704
[ 1003.208859] parent transid verify failed on 79466496 wanted 33999 found 36704
[ 1003.230889] btrfs: open_ctree failed

I've read dozens of pleas for "open_ctree" issues, but none of them had useful conclusions. Is there anything I can do?

Any help would be appreciated. Thank you.

Linux veriton 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by conradin on 2012-02-18
I dont use BtrFS just yet, but I remember from a conference that it keeps snapshots. Can you restore from a snapshot?
the man page seems to have a -r for recovery option. The kernel org webpage on the topic of snapshot recovery is also down..

---

### Post by senojsitruc on 2012-02-18
If btrfs takes and keeps automatic snapshots then I'm not sure how to find/access them.

btrfs-show plainly enough finds my volume:

$ sudo btrfs-show
Label: StoreW  uuid: e98e0ffd-3d0b-4b55-bacc-0d60797f0f29
	Total devices 1 FS bytes used 1.79TB
	devid    1 size 2.73TB used 1.90TB path /dev/sdb

Btrfs Btrfs v0.19

but everything else (like "btrfsctl -a") doesn't see it.

---

### Post by tomkk on 2013-05-02
Hi, I've got same problem as well - just upgraded my server box to 13.04  and it draged in a new kernel (3.8). Before I was running 3.7 (not btrfs related issue) and 3.5 (as compatibility backup) and both were running smooth.

With 3.8 I get this in kernel log:
[   13.517952] device fsid 9415cddb-e3b8-4977-804c-369553a7eda7 devid 4 transid 111130 /dev/sdh1
[   13.518535] btrfs: disk space caching is enabled
[   13.518773] btrfs: failed to read the system array on sdh1
[   13.523175] btrfs: open_ctree failed
[   13.598773] device fsid 9415cddb-e3b8-4977-804c-369553a7eda7 devid 4 transid 111130 /dev/sdh1
[   13.599277] btrfs: disk space caching is enabled
[   13.599507] btrfs: failed to read the system array on sdh1
[   13.619026] btrfs: open_ctree failed
[   13.620289] device fsid 9415cddb-e3b8-4977-804c-369553a7eda7 devid 4 transid 111130 /dev/sdh1
[   13.620785] btrfs: disk space caching is enabled
[   13.621014] btrfs: failed to read the system array on sdh1
[   13.626992] btrfs: open_ctree failed


Luckily for me since 3.7 was installed with external repository, during upgrade it wasn't removed like 3.5 - hence I'm able to run my box with 3.7 and be able to mount my file systems propperly.

---

### Post by oldos2er on 2013-05-02
Old thread closed.

---

