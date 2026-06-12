---
title: "Hardrive trouble"
date: 2006-01-27
forum: General Help
---

### Post by ockertom on 2006-01-27
Hi Peeps how are you :) I am converting to ubuntu and I like it a lot but I am seeming to have some problems with my other hardrive which is ntfs. I went and read a couple of posts on this but my problem seems a bit weirder I think. this is what my fstab reads

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Now that error thats in there? As root I made a new folder called /shares I mounted it to this and it took, when i tried to do chown -R /me /shares it seemed to do the job, but when i went to look at it it had a big X on the folder lol. Now this isnt goin to be a dual boot system, but there is some gear I would like to backup on that drive b4 if I have to format it. errr hangon? sda1 is the main drive with the  system on it. Where is the sdb? Hell lol might be more probs then i thought :)

---

### Post by GreyFox503 on 2006-01-27
See this page for mounting NTFS partitions:  [http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

Your /etc/fstab looks fine right now.  There's nothing wrong with it, except of course, that it isn't mounting your NTFS partition.  Everything else there looks ok.

---

### Post by ockertom on 2006-01-28
even with that erro stuff? ok thanks for the help mate

---

