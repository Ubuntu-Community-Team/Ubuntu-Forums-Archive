---
title: "quota problem"
date: 2012-08-07
forum: General Help
---

### Post by wiame on 2012-08-07
hello 
i have a problem with quota configuration.
there is what i did:

the configuration of /etc/fstab :

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bd74138e-c1fc-4f54-9437-eaacb1d66caa /               ext4   usrquota,grpquota,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d752e7d3-6fc3-4fa0-9b92-e61bd366ca7f none            swap    sw              0       0


the commands i wrote in the terminal:
touch /home/quota.user
chmod 600 /home/quota.user
touch /home/quota.group
chmod 600 /home/quota.group
mount -o remount /
quotacheck -afm


after the last command, i have this message:
quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: WARNING -  Quotafile //aquota.user was probably truncated. Cannot save quota settings...
quotacheck: Scanning /dev/sda1 [/] quotacheck: lstat Cannot stat `//home/serveur/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...



would you please help me.

---

### Post by oldos2er on 2012-08-07
Post moved to its own thread.

---

