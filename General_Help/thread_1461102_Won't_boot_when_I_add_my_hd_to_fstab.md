---
title: "Won't boot when I add my hd to fstab"
date: 2010-04-23
forum: General Help
---

### Post by flammenwurfer on 2010-04-23
I have an external hdd that I have added to the fstab so it will mount when I boot.  But every time I add the line to fstab and reboot, it hangs during the boot process and says something about ureadahead-other status 4.

here is my line in fstab..

/dev/sdc1  /NAS  ext3  defaults  0 0

Is there anything wrong with that? 

I couldn't remember what fs I chose when I formatted it so I did "sudo parted /dev/sdc print" and it said it was ext3.

---

### Post by flammenwurfer on 2010-04-23
Oops, was trying to edit my title and accidentally submitted twice.  Sorry.

---

### Post by louieb on 2010-04-23
Whatever your problem is it not ureadahead-other. The status 4 msg is just spam - it means there is nothing on the disk that needs to be preloaded.

                                                                                         [All about  ureadahead]("http://ubuntuforums.org/showthread.php?t=1434502&highlight=ureadahead-other") 

Your fstab entry looks fine - assuming you have a /NAS directory and /dev/sdc1 is the right device. Might use the partitions UUID instead of /dev/sdc1 - maybe it getting confused.
to find the UUID 
```
sudo blkid -c /dev/null 
```fstab looks like 
UUID=<whatever> ext3 defaults 0 0

BTW: is this a USB drive? Are you running Lucid?

---

