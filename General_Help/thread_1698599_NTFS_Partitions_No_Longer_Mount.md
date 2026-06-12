---
title: "NTFS Partitions No Longer Mount"
date: 2011-03-02
forum: General Help
---

### Post by stdrogo on 2011-03-02
After a reboot this morning, ubuntu will no longer mount any ntfs partitions. The error I get is Error mounting: mount exited with exit code 21. The file system is entirely intact according to both chkdsk and gparted, and the relevant fstab entry is assigned to the appropriate UUID. Manual mount doesn't work either. I am running Ubuntu 10.10 amd64. One of the partitions is a Windows installation which boots normally and from windows I can access my other NTFS partition.

Edit: From Disk Utility I get the following error when I try to mount: Error mounting: mount exited with exit code 1: helper failed with:

---

### Post by stdrogo on 2011-03-02
Bump please.

---

### Post by Thespian on 2011-03-02
Sorry to hear you've had the same problem I had, but glad I'm not alone.  I posted about this last night here in this thread:

[http://ubuntuforums.org/showthread.php?t=1698296](http://ubuntuforums.org/showthread.php?t=1698296)

Which hasn't had any answers yet.  Perhaps my debugging can help you, but I haven't found a solution yet.

Please let me know if you find a solution.

---

### Post by JC Cheloven on 2011-03-02
I remember I had the same problem some time ago. 

Weird it may be (indeed it is), I solved it simply mounting by device name (for example /dev/sda1) rather than by UUID. Even though the UUID given at mount time was correct, as far as I could see.

I know it's strange, as uuid is supposed to be a more robust way to mounting filesystems, but anyway.

Hope that helps.

---

### Post by Thespian on 2011-03-02
JC, thanks for the suggestion, but no luck with that for me.

root@laptop:~# mount /dev/sda1 /media/drv0
root@laptop:~# echo $?
21
root@laptop:~# ls /media/drv0
root@laptop:~#

---

### Post by stdrogo on 2011-03-02
I confirmed that my results mounting without UUID are the same as Thespian's. Thank-you all the same.

---

### Post by MarkieB on 2011-04-13
no longer participating in ubuntuforums.org

---

