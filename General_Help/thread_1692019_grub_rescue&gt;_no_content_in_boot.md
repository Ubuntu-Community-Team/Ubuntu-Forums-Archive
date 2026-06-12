---
title: "grub rescue&gt; no content in /boot"
date: 2011-02-20
forum: General Help
---

### Post by iverasp on 2011-02-20
I installed Ubuntu server with software raid 5 and all went well. Then I figured I should test the raid by these instructions [https://help.ubuntu.com/community/Installation/SoftwareRAID#Disk%20Array%20Operation](https://help.ubuntu.com/community/Installation/SoftwareRAID#Disk%20Array%20Operation)

As a result mdadm would create /dev/md0 with 3 drives and 1 spare. Confused on this matter I just reinstalled Ubuntu. Now, I'm greeted with a grub rescue prompt at boot. Running set displays the correct parameters and ls (md0)/ shows the content of /. However, ls (md0)/boot/ shows no content what-so-ever. If I boot from the livecd there are all the files needed in /boot. I've tried running grub-install on all the drives without results. Tired, annoyed and kind of angry I'm now asking for help. What could possibly be wrong?

---

### Post by iverasp on 2011-02-20
It seems the "solution" was to delete all partitions using fdisk, overwriting the MBR with "dd if=/dev/zero of=/dev/sdX bs=512 count=1" and installing Ubuntu again. Not the best option but it worked (and I no longer have a cause for my headache).

---

