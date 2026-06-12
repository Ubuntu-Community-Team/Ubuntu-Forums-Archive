---
title: "-- bind not holding after re-boot"
date: 2012-07-17
forum: General Help
---

### Post by toyoracer on 2012-07-17
Hello, I have just done a fresh install of 12.04 on SSD. I then used --bind on all folders from HDD partitions into corresponding /home folders. Works perfectly until I opened today to find /home folders empty. Tried --bind again works, did a re-boot and empty.

Here are the steps taken,

#mkdir /mnt/music
#chown -R user:user /mnt/music
#chmod -R 766 /mnt/music
#mount /dev/sdb9 /mnt/music

edit_ /etc/fstab
test_mount -a __ no errors

#mount --bind /mnt/music/Music /home/user/Music

Works until pc is re-started then empty in /home/Music works in /mnt/music/Music

Thank you for any insight.

---

### Post by toyoracer on 2012-07-17
Okay found out that an upstart job is required. More research needed.

---

