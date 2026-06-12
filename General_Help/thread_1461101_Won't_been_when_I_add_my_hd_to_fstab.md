---
title: "Won't been when I add my hd to fstab"
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

### Post by geirha on 2010-04-23
Test it before you reboot. «sudo mount -a» will mount all automatic entries in /etc/fstab that isn't already mounted. «sudo mount /NAS» will mount just that entry. And if it fails, post the error message(s) here.

Oh, btw, you'll want the last field to be 2 rather than 0 for ext[2-4] filesystems. That'll make it check the filesystem during boot.

---

### Post by flammenwurfer on 2010-04-23
Thanks.  I did mount -a before I rebooted and it mounted fine.  It's only once I reboot that there is an issue.  

I'll try changing the second 0 to a 2 and see what happens.  Thank you.

---

