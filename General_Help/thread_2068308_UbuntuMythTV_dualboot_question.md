---
title: "Ubuntu/MythTV dualboot question"
date: 2012-10-08
forum: General Help
---

### Post by DeadMansLife on 2012-10-08
How do I safely remove MythTV  from a Ubuntu/MythTV dualboot system?

I have found plenty of info to remove linux from windows but that is not what I'm doing.

Thanks

---

### Post by DeadMansLife on 2012-10-09
Bump;)

---

### Post by thatguruguy on 2012-10-09
I didn't know there was a stand-alone MythTV OS. Are you talking about Mythbuntu, Mythdora, or some other MythTV/OS-bundled system?

---

### Post by oldfred on 2012-10-10
This may work.

Yanni has created a easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)

Or just this:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

But if you have multiple Ubuntu or other Linux installs, boot into the one you want to keep and run this to have its boot loader in the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

