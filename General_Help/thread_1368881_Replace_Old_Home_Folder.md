---
title: "Replace Old Home Folder"
date: 2009-12-31
forum: General Help
---

### Post by Fahim123 on 2009-12-31
Hi Guys,

I need your help i am using Ubuntu 9.10 i have 250 gb with partitions i installed root in 80tb and home in another 80 gb i installed winxp in another partition which deleted my grub so i installed again ubuntu 9.10 only formatting root and reinstalling root in it now i want my old home folder to be the home folder which is in another 80 gb how to do that please let me know. Thanks for your help.

---

### Post by john newbuntu on 2009-12-31
You need not have re-installed Ubuntu. Instead you could have just repaired Grub2.  The way I understand it now, you have a new install of Ubuntu with /home in your first partition and a completely our of sync /home in the second.

Your /etc/fstab will require a /home entry(modify this suitably).  I am not sure on where your swap is.
/dev/sda3       /home           ext4    nodev,nosuid    0       2

You will then need to remove /home.
You are not done yet.  Remember you have set up a few users in your original home directory.  They need to be added to /etc/passwd, /etc/shadow and /etc/group.
Finally a reboot.

Others please correct me if I missed something or need something else to be added.

---

