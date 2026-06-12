---
title: "RAID setup on Ubuntu 11.10"
date: 2011-12-09
forum: General Help
---

### Post by jdeters79 on 2011-12-09
New to Ubuntu so bear with me please. I have a desktop that I've been running Windows Vista 64-bit on with a RAID0 array and a standalone 1 TB drive. Windows was loaded on the RAID0 array and will not boot up. I decided to use Ubuntu (latest version, 11.10 I think?) to hopefully recover as much data as possible off the RAID0 drives. I was able to successfully install Ubuntu onto a USB drive with no problems (okay, minor learning curve issues, but it works fine!). After completing the USB installation, I shut the computer down and reconnected the the drives (RAID drives and 1 TB drive). After restarting, the 1 TB drive is easily recognized and I am able to access it through Ubuntu. However, no joy with the RAID0 drives. I've tried to research this, but only come up with how to setup a RAID during the initial installation of Ubuntu. My goal here is to retrieve the data off the RAID disks (if not corrupted) so I do not want to install Ubuntu onto those disks at this point. 

Any recommendations on configuring the Ubuntu installation on the USB drive to recognize the RAID0 array? Thanks in advance for any help.

---

### Post by jdeters79 on 2011-12-09
Any takers?  Sure could use some advice.   :confused:

---

### Post by txtiger on 2011-12-10
I am by no means an expert, but I do not see how you can do what you are wanting to do.  The reason is that Raid0 shares the data and parity across both drives and you need the full set to be able to get to the data.

The concern I have is that whatever software and/or controller you used to set up the Raid0 partitions in Windows will be Windows specific.  That would keep Ubuntu (or other Linux distros) from being able to see them.

About all I could recommend is boot Ubuntu and then drop back to the terminal (shell) command and run mdadm --help.  If you are exceptionally lucky (or the mdadm authors are beyond belief) then you may be able to find a way for mdadm to recognize the Windows Raid partitions.  If so you could potentially find a way to assemble them and then mount the resulting volume.

As my third year calculus prof used to say, "Good luck because this is a Non-trivial problem".

---

