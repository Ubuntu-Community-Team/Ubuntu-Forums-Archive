---
title: "No permission"
date: 2009-07-25
forum: General Help
---

### Post by superman736 on 2009-07-25
Okay I haven't used Ubuntu in about a month so I have no idea how this happened. When I start my computer everything is the same, I choose to boot Ubuntu and the start up bar goes about 1/8 of the way. Then it stops and I get a bunch of text saying everything is Permission Denied. The only way I can boot is with a live cd. I have tried changing the permission via a live cd but it doesn't save anything. Please help.

---

### Post by aesis05401 on 2009-07-25
Were you running AppArmor or SELinux? 

Can you tell us the first message that says permission denied?  That should tell us what stage of the boot process you are at.

---

### Post by superman736 on 2009-07-25
> **aesis05401 said:**
> Were you running AppArmor or SELinux? 

Can you tell us the first message that says permission denied?  That should tell us what stage of the boot process you are at.

I haven't used any of those. Last time I used Ubuntu it worked fine and I didn't install or uninstall anything. I think this occurred in Windows but it is hard to tell as this is a family computer so it could of been anything. But I doubt it occurred in Ubuntu because not many people use it here. Here are the first couple of lines:
* Cannot initialize /etc/mtab.
/etc/init.d/rc: 390: sh: Permission Denied

It repeats  /etc/init.d/rc: 390: in the beginning of every line but after 390: it changes. I can record a video if that helps but it might not be great quality as it will be from a cell phone.

---

### Post by aesis05401 on 2009-07-25
Ok, and you don't feel that the partitions on the machine were changed by anyone for any reason?

/etc/mtab is a file that is supposed to be transient (ie: it gets re-written to keep it current when mount/umount commands are issued).  The info it stores is similar to fstab entries, but it describes mounts, not filesystems.  The boot process is either not finding the /etc/mtab location, or is not able to read/write mtab.

You can boot with a livecd, mount the partition that contains your /etc directory, and check the following: 
/etc/mtab exists
/etc/mtab has 0644 permissions (use 'stat /etc/mtab' once you have access to the drive)
Check for oddly named files that say mtab somewhere in the title (ie:mtab~22) - delete these additional files if they exist, leaving only the base mtab file. 

You should not delete mtab itself, but as a last resort you could clear any information located in the mtab file.  I don't know what that would help, but you could give it a try.  My feelng is something about where grub is looking for these files has changed.

Does this help?

Edit: Upon further reading, you should attempt to fsck the partition from your livecd if none of the above stated conditions apply to your /etc/mtab.  If this does not work then delete mtab altogether and attempt a reboot.

---

### Post by superman736 on 2009-07-25
Partitions are the same. Tried both but it doesn't work. Also I think the problem is with init.d folder as the message only mentions mtab once and repeats init.d over and over. I just booted xubuntu on a live cd, sudo thunar and tried changing the permission of init.d. It did change the persmission after about an hour because it have to change the permission of every file and folder in that folder. But the changes did not save at all. I think I found the culprit on my brother's vista account, he installed a program to read a linux partition in Windows. One program is LTOOLS and another is fs-driver. I have tried working with both but it doesn't seem to help at all since it won't connect to the partition at all.

---

### Post by aesis05401 on 2009-07-26
Firstly, I am sorry that you are experiencing this issue.

You are seeing the init errors for the same reason the mtab error exists most likely.. the partition is not being located or mounted properly.  The initial problem may be that *no* file-systems are being mounted properly.  

There are several file-systems that are mounted for use by the system during the early 'run-levels,' and without these file-systems in place you will not be able to operate properly.

If you are sure no partitions have changed, then you need to look into grub settings.  

/boot/grub/menu.lst contains a copy of the grub boot options.  

Unfortunately, this sort of problem I only know how to solve by working through boot process step by step.  If you have your user data on another partition then it may be much faster to reinstall.

Does anyone have an easier solution to this issue?

---

### Post by superman736 on 2009-07-27
Thanks anyways, I guess I will reinstall.

---

