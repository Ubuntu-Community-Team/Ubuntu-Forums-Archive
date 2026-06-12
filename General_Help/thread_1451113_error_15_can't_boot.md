---
title: "error 15 can't boot"
date: 2010-04-10
forum: General Help
---

### Post by mike596 on 2010-04-10
so last night i tried to boot my wubi and got error #15.  
im running 9.04 64 windows xp with a WD sata 80gb drive. 

here is the output of boot info script. im guessing my mbr is trashed


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


hdb: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hdb                                                iso9660    SLAX                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)


==================== hdb: Location of files loaded by Grub: ====================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

---

### Post by oldfred on 2010-04-10
Mike you have two threads on same issue:

Please see this:
[http://ubuntuforums.org/showthread.php?t=1450776](http://ubuntuforums.org/showthread.php?t=1450776)

---

