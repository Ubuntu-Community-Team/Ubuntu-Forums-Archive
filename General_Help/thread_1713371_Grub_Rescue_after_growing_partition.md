---
title: "Grub Rescue after growing partition"
date: 2011-03-24
forum: General Help
---

### Post by sami8519 on 2011-03-24
Hi,

Please help me. I was having two ubuntu partitions(both 10.04) and decided to get rid of one of them(it was not the default booting partition, grub was installed on the other partition) and use the freed space to feed the other ubuntu. I used the KDE live partition manager to do that and it finished within 40 minutes and no error messages appeared after the process finished. After reboot grub rescue is all I have. I used the instructions here to reinstall grub but it gives me this message:
#mkdir /media/sda5
#sudo mount /dev/sda5 /media/sda5
#sudo grub-install --root-directory=/media/sda5 /dev/sda5

grub-probe: error cant find a device for /boot (is /dev mounted?)

/usr/sbin/grub-setup: warn: attempting to install grub into partition instead of MBR. This is bad idea
/usr/sbin/grub-setup: warn: Embedding is not possible. Grub can only be installed in this setup by using blacklists. However, blacklists are unreliable and its use is discouraged.
/usr/sbin/grub-setup: error if you really want blocklists, use --force

Please help.

Best Regards,
Sami

---

### Post by wilee-nilee on 2011-03-24
Try this you can load it without the chroot, and not in a partition but the disc=sda=mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by sami8519 on 2011-03-24
Thank you very much mate. It works now.

Best regards,
Sami

---

