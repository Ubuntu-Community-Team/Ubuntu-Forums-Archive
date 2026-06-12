---
title: "fstab script  issue... help!"
date: 2010-06-08
forum: General Help
---

### Post by Cypher2 on 2010-06-08
Kind of bugged by the works of this little command sample i'm making to automate the mounting of my drive partitions upon install according to wether it is my desktop (MERCURY) or my laptop (SOLACE)...

It seems to work fine for the first case but not for second or third...

any help please?:confused:

thanks!

---------------------

# !/bin/bash
if hostname="MERCURY"
then
sudo echo /dev/sdb1 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
elif hostname="SOLACE"
then
sudo echo /dev/sda2 /media/Disk ext4 defaults 0 0 | sudo tee -a /etc/fstab
else
echo "Unknown hostname... Aborting"
fi

------------------------------------------

---

