---
title: "HOWTO: Give access to NTFS partition to all users"
date: 2009-11-07
forum: General Help
---

### Post by Umang on 2009-11-07
I installed Karmic today, and found that all non-admin users were not able to access NTFS partitions. 

Here's how I fixed it:

1. Download and install pysdm using Synaptic Package Manager (or apt-get)
2. System -> Administration -> Storage Device Manager
3. Click on one of the NTFS partitions and then click "Assistant". (You may be asked whether you want to set it up, click yes)
4. In the new window that appears, check "Allow any user to mount the file system".
5. Repeated steps 3 and 4 for all the partitions.
6. Reboot

Anyone knows why regular users can't mount (or access) NTFS partitions by default on Karmic?

Umang

---

### Post by darshana on 2009-11-07
Because of the security in Ubunt. it wont allow to mount disks if you are not a root user.. Generally all the Unix systems are like this

---

### Post by Umang on 2009-11-07
I installed Gutsy, and upgraded all the way till Karmic, when I began having loads of problems. So I have now done a clean install. However, before this clean install, this was never an issue. With Gusty, all users had access to NTFS partitions. 

Through the upgrades, nothing has happened to change this.

---

