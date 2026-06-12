---
title: "In need of help"
date: 2009-11-07
forum: General Help
---

### Post by ferret man on 2009-11-07
recently upgraded from 9.04 to 9.10, and long story short, all of the permissions got changed on my computer, and I can not log on as anyone (even the superuser). Now, I tried to reprogram ubuntu on my computer, but it doesn't give me the permission to mount my USB drive. I need help. I have a Dell Mini 9 with Ubuntu 9.10 NetBook Remix installed on. If someone could maybe tell me how to maually install the new ubuntu, or uninstall my last one, it would be great.
 
P.S. Please, help me. Thanks for your time.
I apologize. 
Timeline:
1st: Program Ubuntu 9.10, everything is fine.
2nd: Permissions get changed, cannot log on.
3rd: Attempt, but fail to reprogram ubuntu 9.10, because the permission is denied.
4th: I need help.
 
Meaning of all of this: I cannot use my computer, and when I try to reinstall the OS, it is denied. I need to reprogram it so that it can run. Perhaps I can delete the partition and create a new one? I don't know. I am new to Linux and know nothing, in depth, about computer programing. 
 
I do have a "live USB drive" with Ubuntu 9.10 on it, so if I can find out how to install that on my laptop, that would be great.
 
Finally, the OS currently on my computer is not a "healthy", or freshly installed one. It is the damaged, permissions are out of whack, one.
 
If it is possible, will it help to wipe my hard drive except for the BIOS.
 
If someone can please help me, thank you, because I got the laptop for Christmas, and all I want is to be able to use it.

---

### Post by ST3ALTHPSYCH0 on 2009-11-07
I'm assuming that the live USB is the same as the live CD. 

Boot from the USB. 
Transfer any files you need from your hard drive onto another drive.
 Open Gparted from System>Administration.
Delete the messed up partition. 
Mount and format new partition.
Reinstall.

If you can't get to things any other way, that's how I'd go about it, but you might want to see what anyone else offers.

---

### Post by ferret man on 2009-11-07
> **ST3ALTHPSYCH0 said:**
> I'm assuming that the live USB is the same as the live CD. 
 
Boot from the USB. 
Transfer any files you need from your hard drive onto another drive.
Open Gparted from System>Administration.
Delete the messed up partition. 
Mount and format new partition.
Reinstall.
 
If you can't get to things any other way, that's how I'd go about it, but you might want to see what anyone else offers.
 
THANK YOU SO MUCH FOR RESPONDING!! :p 
 
I just cannot boot from USB, it says permission denied. Do you know anything else to do?

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
I've never played with making a bootable USB drive. Sorry I can't be of more assistance. Do you have the ability to remake the Live USB? Also, double check that there isn't an external, mechanical lock of some sort in the wrong position.

---

