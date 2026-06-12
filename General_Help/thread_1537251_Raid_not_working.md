---
title: "Raid not working"
date: 2010-07-23
forum: General Help
---

### Post by tim_m on 2010-07-23
I created a raid array and it was working fine until I rebooted my system. On reboot I got an error that the drive was not ready. I select skip mounting and the system completes the boot. If I try to mount /dev/md0 I get an error that special device /dev/md0 does not exist. When I issue a cat /proc/mdstat I get the following message:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdd1[1](S)
      488383936 blocks
       
unused devices: <none>

The two drives are /dev/sdc1 and /dev/sdd1, blkid output
/dev/sda1: UUID="b46f8913-c008-4be2-8bad-d90d4a38bda0" TYPE="ext3" 
/dev/sda5: UUID="ac19eef3-0dc7-4123-8060-14f418696c31" TYPE="swap" 
/dev/sdb1: LABEL="imusic" UUID="98c9af05-2183-41bb-bd4e-9f50b9943350" TYPE="ext3" 
/dev/sdc1: UUID="460c16dd-6810-52ac-3fb5-b59cec71e283" TYPE="linux_raid_member" 
/dev/sdd1: UUID="460c16dd-6810-52ac-3fb5-b59cec71e283" TYPE="linux_raid_member" 

Any thoughts on how to resolve this?

---

