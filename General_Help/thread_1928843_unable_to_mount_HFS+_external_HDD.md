---
title: "unable to mount HFS+ external HDD"
date: 2012-02-20
forum: General Help
---

### Post by txtzttm on 2012-02-20
I receive an error message when trying to mount my 3TB Hitatchi external HDD in Ubuntu 11.10. The drive is HFS+ formatted and I receive the same error with journaling enabled and disabled:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The drive shows up in my finder/explorer (sorry, new to Ubuntu) window, but when I click it I receive the above error. If I try to mount using terminal I get the same thing. The command I'm trying is:

sudo mount -t hfsplus -o force /dev/sdb1 /media/outerhaven

"/media/outerhaven" is a valid directory/mount point as far as I can tell.

Sorry if I've left any information out. Thanks in advance for any help.

---

