---
title: "Device paths change after ever reboot"
date: 2011-05-02
forum: General Help
---

### Post by Delphinus369 on 2011-05-02
Hello everyone, I have a strange problem that I would really like an answer too. I have searched google high and low and haven't seen anything relating to my issue or most of all how to solve it.

My problem: After I reboot my Ubuntu 10.04.2 LTS \n \l machine my device paths change (even the boot drive) and this causes havoc on my two RAID5 arrays. The device paths change and causes a mismatch in my fstab and I have to manually mount both RAID arrays every time. It's quite frustrating and annoying and I would love for it to stop. This even happens for the boot path.

Example:  my boot path is /dev/sde5  I reboot my machine and my boot path changes to /dev/sdm5

Why does this happen? And more importantly how can I stop it from happening so it stops messing with my RAIDs?


I can provide any additional outputs and information that anyone would require to help solve this problem.

Thanks!

-Del

---

### Post by matt_symes on 2011-05-02
Hi

Read this. It's an old post but i am pretty sure the principle is still the same.

[http://ubuntuforums.org/showthread.php?t=582775](http://ubuntuforums.org/showthread.php?t=582775)

Kind regards

---

### Post by Delphinus369 on 2011-05-05
Matt, thanks for the link but it wasn't really helpful. That just explains how to reference the drives by their disk ID instead of their dev name. I still have to reassemble the RAID array every time I reboot as I have the same problem as the second poster in that thread, the RAID array doesn't build itself on boot.

Is there no way to make UBuntu keep the currently assigned dev names to the disks it assigns them to? Why do they (seem to) change at random after a reboot?  It's wreaking havoc on my RAID arrays.

---

### Post by srs5694 on 2011-05-05
My understanding was that Linux's software RAID generally did a good job at handling this. Are you using that, or motherboard-based software RAID (aka "fake RAID")? If your system is Linux-only it might make sense to switch from the latter to the former, although that would be a major undertaking if you've got much data stored on the disk already.

A more direct solution might be to use udev rules to assign specific names to specific drives; however, I'm not sure this works for disk devices. I know that it works for network devices and optical disc devices (Ubuntu's udev configuration includes rules to do that). Check [this MythTV wiki page](http://www.mythtv.org/wiki/Device_Filenames_and_udev) for a general introduction with examples for video devices (which probably won't be directly applicable, since that wiki is about creating symbolic links; but it should at least help you understand how udev works). You might try Googling on "udev hard disks" or some such to come up with a page that more directly addresses your specific issue. If you do it this way, you'll probably have to write udev rules that key off of features like the hardware ID of the SATA port, since you've presumably got a bunch of identical disks that won't be easily distinguished by model numbers or the like.

---

