---
title: "Used Wubi install - shut down improperly, now Ubuntu won't boot"
date: 2010-01-14
forum: General Help
---

### Post by Anothen on 2010-01-14
I've installed Ubuntu 9.10 approx 1 week ago and it's been fine. Last night, Ubuntu froze while I was running several programs. I wasn't sure how to pull up any type of 'task manager' and the mouse didn't move so after several minutes I was forced to hard reboot the computer. Grub starts and allows me to select Ubuntu but won't get past the log-in screen (allows me to log-in but freezes immediately after hitting enter). I started the recovery mode and the errors show what I believe to be sector errors (?)... 
 
Do I need to run a 'chkdsk' from Windows or re-install Ubuntu? If deleting/un-installing Ubuntu (through Wubi) is necessary, is this a problem directly related to Wubi (i.e. is a clean install on a seperate partition better than installing through Wubi)?
 
Any help is greatly appreciated!

---

### Post by Saiko Berry on 2010-01-14
This happens with Wubi because the Wubi version comes packed with an old Grub loader and tries to update to a new one. Did this by any chance happen after you updated grub?

---

### Post by Anothen on 2010-01-14
No- all I had done prior to shutting the computer down was install gnome-do and avarok. It was Avarok scanning media that caused the computer to freeze (I had Firefox, Avarok and gnome-do running all at the same time).

---

### Post by Saiko Berry on 2010-01-14
Personally, I don't recommend Wubi. Ive experienced a lot of problems with it because it isn't up to date and such. I recommend just installing Linux or dual booting. Wubi.. has weird errors. Like being locked in the grub screen saying you have no kernel. oO

---

### Post by Anothen on 2010-01-14
the only reason I installed Ubuntu through Wubi was because I've heard nightmares about the Master Boot Rec. being destroyed when trying to dual-boot. Unforuntately, with the software I rely on, I have to use Windows but I really like Ubuntu. I wish I could make wubi work...

---

### Post by Saiko Berry on 2010-01-14
I don't know why Dual Booting Linux would touch your MBR. I guess you can do it wrong and mess it up.. but I think that's like.. as rare as dieing from a bug crawling into your nose while you sleep.

---

### Post by garvinrick4 on 2010-01-14
Fix Wubi when will not boot  
 

 How can I access my Wubi install and repair my install if it won't boot?  
 

 Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

---

### Post by garvinrick4 on 2010-01-14
If that does not do it check here.

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

---

### Post by Anothen on 2010-01-14
I think I'm gonna skip Wubi and try a new install with partition instead- thanks!
 
has anyone else heard of issues with Wubi after a hard reboot?

---

### Post by ubu_nub on 2010-05-13
This solution saved my a**.  I was looking for a way to restore my home dir after an upgrade to 10.04 died.  
 
Thanks!!!
 
 
 
> **garvinrick4 said:**
> Fix Wubi when will not boot 
 
 
How can I access my Wubi install and repair my install if it won't boot? 
 
 
Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition: 
 
 
sudo mkdir /win 
sudo mount /dev/sda1 /win 
 
 
Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 
 
 
sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 
 
 
Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access. 
 
 
To check the filesystem you can use: 
 
 
sudo fsck /win/ubuntu/disks/root.disk

---

