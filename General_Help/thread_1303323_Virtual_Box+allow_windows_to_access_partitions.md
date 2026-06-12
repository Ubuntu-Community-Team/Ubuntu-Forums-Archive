---
title: "Virtual Box+allow windows to access partitions"
date: 2009-10-28
forum: General Help
---

### Post by jayeshbhat55 on 2009-10-28
I have virtual box OSE in ubuntu 9.04 64 bit with windows XP 32 bit as my VM..How to enable windows to access my hard disk. All partitions except linux are NTFS. 
 
Thanx..Any help is appreciated!

---

### Post by P4man on 2009-10-28
You do it through network shares. setup a share for the ntfs drives in virtualbox and access it on the client OS through \\vboxsvr\name-of-share. You can map it to a network drive for convenience.

I dont think you can access those drives directly (unless they are USB drives)

---

### Post by yeats on 2009-10-28
I run the non-free version of VirtualBox, so I don't know if OSE has this feature, but I'm able to create a shared folder that lives in my home directory (on the host machine) and is visible on my virtual XP as a network share.  If I recall, it is one of the "VBox Additions" that get added to the guest OS after installation...

---

### Post by jayeshbhat55 on 2009-10-28
thanx guys. that resolved the issue.. However during the process, i had to add a statement usershare owner=false  to the /etc/samba/smb.conf  to allow sharing of the drives. Everything else went smoothly.

:-)

---

