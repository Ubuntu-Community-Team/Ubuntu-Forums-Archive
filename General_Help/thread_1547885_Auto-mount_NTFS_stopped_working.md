---
title: "Auto-mount NTFS stopped working"
date: 2010-08-07
forum: General Help
---

### Post by Rebelli0us on 2010-08-07
I re-formatted my Windows disk and re-installed XP, since then Ubuntu automount no longer works.

I have shared profiles and data on the NTFS disk, Firefox/Thunderbird won't start... my Ubuntu is basically broken:

1) Grub boot menu will no longer boot Windows

2) During bootup, Ubuntu shows error msg -- unable to mount media and something about "manual recovery".

3) NTFS configuration tool can't fix the problem.


How to fix this Ubuntu? Why doesn't it automount all partitions anyway?

---

### Post by dino99 on 2010-08-07
reformatting have given new uuids, so the previous settings are now false, run again:

sudo grub-mkconfig
sudo update-grub

mountmanager could be the easy way to deal with partitions and devices, set prefs into : system admin mountmanager, after installation

---

### Post by oldfred on 2010-08-07
I have not used mountmanager, it looks like it does a lot but am not sure it will fix the new UUID that you need. You have to mount it the same way as you did before or your share of the firefox & tbird profiles will not be correct. If it does not work for you this is the manual way to fix it.

in terminal:
sudo mount -a
Should show error message on line(s) it cannot mount.

sudo blkid
will show UUIDs of all partitions.

Copy new UUID from results above into fstab line to mount windows partition:
gksudo gedit /etc/fstab

rerun 
sudo mount -a
if no errors it just remounts everthing and returns without error.

---

### Post by Rebelli0us on 2010-08-07
Thank you. What is "mountmanager"? Is it the "NTFS configuration tool"?

---

### Post by oldfred on 2010-08-07
After Dino's mention of it, I went into synaptic and installed it. It is different than the NTFS tool. There are several tools available for handling mounting & fstab editing from a gui.

I have used this which is just another one.
PySDM is a PyGTK Storage Device Manager

But sometimes the auto tools just do not make the settings correctly. You often need to fully understand the settings it uses or defaults to.

Even with the auto tools it pays to understand mounting and fstab editing.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Rebelli0us on 2010-08-08
Thank you.

I fixed GRUB and auto-mount problem per your instructions. But Firefox/Thunderbird/etc. won't start, "profile in use", "insufficient rights to.." my comput0r(?), and other useless error messages. I think I'll wipe the partition and re-install.

---

### Post by oldfred on 2010-08-08
Profile in use is either the lock file did not get deleted or you path is not the same. Check profile.ini.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Rebelli0us on 2010-08-10
Thanks Fred, your advice is again right on!

I deleted .lock parentlock, but it didn't work, I had to login as root. It was long and tedious, too many reboots/logins, then back to windoz for a working browser...  it's just quicker to reinstall. 

I'm grateful for the advice, we can mark the thread SOLVED if it helps others troubleshoot grub and broken auto-mount. The rest is a Mozilla issue, I still loooove their shared profile capability, I couldn't have switched to Linux without it.

---

