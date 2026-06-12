---
title: "Ubuntu 10.04 stuck in reboot"
date: 2012-03-19
forum: General Help
---

### Post by Muiske on 2012-03-19
Hello fellow Ubuntu-users,


Yesterday (Sunday, 18/03/2012) I booted up my Ubuntu machine and after a while the update-manager notified me that there were new updates available. I installed them, but after rebooting the system got stuck. It loads until the point where Apparmor (I don't know what that is) comes into view, then nothing happens for a while. After 10 seconds or so the systems just plainly reboots, after which the whole process is repeated (virtually indefinitely). 

Does anyone have a clue which might cause this? It must be some library inconsistency, I don't think it is the video-driver (no changes to xorg.conf whatsoever were initiated by the update). Since I don't have GRUB installed, is there a way to boot in the safe mode? Is there some key-combination I can use? 

Or, is there some way to roll back the update?

Please, help! :confused:

Thanks.

/ Harm.

---

### Post by ajgreeny on 2012-03-19
I think you must have grub installed, unless you use another bootloader of some sort, but let's leave that for the moment.

When you see the apparmor flash on screen have you noticed if it says something like **/etc/apparmor.d/disable/usr.bin.firefox?** 
I see that flash onto screen every time I boot my netbook with Lubuntu 11.04, even though it then goes on to boot properly.

There is a page on the use and possible problems of apparmor at [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor) and if the firefox message appears as above, it is because firefox has its own profile to use instead of the system profile.  You may be able to overcome the problem either by removing apparmor, or by enforcing the system apparmor profile.  Go the link above for more details, but the command you need seems to be ```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```Now back to the grub problem.  Is this a dual boot system in which you are using the windows bootloader in some way, or is it a dedicated ubuntu system?  If it is dual boot, and grub menu does not show, I can not help as I do not know anything about windows any more.  If it is ubuntu alone you should be able to get the grub menu by holding shift after power-on, and from there go to recovery mode, where you can temporarily remove apparmor with ```
apt-get remove apparmor
```no sudo needed in recovery.

---

### Post by Muiske on 2012-03-19
ajgreeny,


Thanks for your answer. I think you're right in that there must be a bootloader of course, but what I meant is that it is 'hidden' because Ubuntu is the only OS installed on the machine. So, no, it is no dual-boot.

The tip for holding shift is exactly what I am looking for, I did not know how to access the menu. 

I am not sure if it is AppArmor that causes the whole problem, but since reboot often starts at that point, it might be the guilty one. I remember that firefox was also updated, so hopefully it is (then I can pinpoint the problem). 

I will let you know if I succeeded tonight.

/ Harm.

---

### Post by Muiske on 2012-03-19
Ok, update:


The system is up and running again. I got it working by booting into the recovery mode (thanks for the "Shift"-tip, ajgreeny!). The system then immediately complained that it had to use the safe graphics mode, so then I knew what the problem was.

I have quite a new videocard (AMD Radeon HD 6770) installed, for which no Ubuntu-developed driver that I know of exists. So I have to use the linux driver made available from the manufacturer. This sometimes gives compatability issues, for example when a new kernel version is installed without the proper graphics module, or when - in this case - the xorg package is updated. I then have to install the fglrx driver again to make it all work. 

Apparently, the new xorg package had some severe issues with the driver that made the system go haywire. Now everything works just as it used to though.

/ Harm.

---

### Post by ajgreeny on 2012-03-19
Great!
Can you mark the thread as solved from the **Thread Tools** menu at the top, please.

---

### Post by miasmablk on 2012-03-19
sorry to hijack the thread but does anyone know of a utility availbale for ubutnu similar to windows sfc (system file checker) utility?

---

