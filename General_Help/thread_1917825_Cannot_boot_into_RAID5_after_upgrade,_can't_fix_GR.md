---
title: "Cannot boot into RAID5 after upgrade, can't fix GRUB"
date: 2012-01-30
forum: General Help
---

### Post by Kreen on 2012-01-30
I have a degraded RAID 5 that I hotswapped the bad drive /dev/sdc with. I used mdadm to add the drive to both /dev/md0 and /dev/md1 (main system and swap space respectively). Additionally, before I did this I copied the partition table from one of the good drives onto the new drive.

After several hours (it's a 5 TB system) everything seemed to be fine. I downloaded some updates and upgraded to 11.10 from the update manager. In hindsight.. that wasn't a good idea.

After a reboot, I get several error messages after POST "error: file not found" "syntax error" etc etc and it goes to BusyBox. I can't bypass that by pressing alt + F2 either. Some research indicated that this was a grub issue, so I booted to a live CD and downloaded Boot-Repair to fix that. When I run Boot-Repair, it asks if I want to assemble the software RAID (using mdadm). I say yes and it goes right back to the terminal I ran the boot-repair command from, doing nothing. If I say no, it goes back to the terminal as well, I can't get Boot-Repair to reinstall the grub and fix any issues.

I'm pretty much to the end of my researching and limited ubuntu knowledge, which is why I'm returning to the forums. Additionally, now the new drive sdc is not working and shows up as a whole partition instead of separate partitions for the RAID5, and the RAID is degraded again.

Any ideas on some steps I could take to get it booting up again?

Thanks!

---

