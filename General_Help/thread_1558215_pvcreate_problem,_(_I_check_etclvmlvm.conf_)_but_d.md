---
title: "pvcreate problem, ( I check /etc/lvm/lvm.conf ) but doesnot work"
date: 2010-08-21
forum: General Help
---

### Post by alperkayisi on 2010-08-21
Hi,

I created LVM volumes and then I tried to view it. I saw that LVM volumes was created successfully. but when I try to make sda5p1 a LVM physical volume with typing " sudo pvcreate /dev/sda5p1 " I got error that is 

Device /dev/sda5p1 not found (or ignored by filtering).

I check /etc/lvm/lvm.conf file for fix that problem. I mean I removed all filters sequentially. But I still got error. My filter was like that ;

   # By default we accept every block device:
    filter = [ "a/.*/" ]

    # Exclude the cdrom drive
    # filter = [ "r|/dev/cdrom|" ]

    # When testing I like to work with just loopback devices:
    # filter = [ "a/loop/", "r/.*/" ]

    # Or maybe all loops and ide drives except hdc:
    # filter =[ "a|loop|", "r|/dev/hdc|", "a|/dev/ide|", "r|.*|" ]

    # Use anchors if you want to be really specific
    # filter = [ "a|^/dev/hda8$|", "r/.*/" ]

Please help me out. I stuck with that for 3 days.

---

### Post by alperkayisi on 2010-08-21
still no reply

---

### Post by alperkayisi on 2010-08-22
still no reply :(

---

