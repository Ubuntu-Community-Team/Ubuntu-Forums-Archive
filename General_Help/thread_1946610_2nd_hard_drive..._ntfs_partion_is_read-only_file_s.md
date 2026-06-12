---
title: "2nd hard drive... ntfs partion is read-only file system"
date: 2012-03-25
forum: General Help
---

### Post by viperdvman on 2012-03-25
I have just installed Ubuntu 11.10 alongside my Windows 7 install on my desktop. Before, I had Ubuntu 11.04 alongside Windows XP. Note, my desktop has two hard drives; The main one for my OS's and apps... and the second much bigger one as a Data drive.

I can mount the data drive just fine. However, I am unable to write to the drive, nor am I able to change the permissions on the drive. All files open as **read-only**. When I try to change permissions to any of the folders, I end up with *"Error setting permissions: Read-only file system"*

I have not had this problem on my netbook which runs the same Windows and same Ubuntu. Nor have I had this problem with my Windows XP/Ubuntu 11.04 combination. How the bloody hell do I get my data drive to mount with read/write privilages and not as a read-only file system?

---

### Post by agillator on 2012-03-25
I assume you have checked /etc/fstab to make sure it's options are default or a list that indicates rw and not ro. Also make sure your mount instruction, if mounting manually, does the same. You might try unmounting it and then manually mounting it with a specific option of rw and see if that accomplishes anything.

---

### Post by oldfred on 2012-03-25
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a
Typical fstab entires:
```
UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0

```

---

### Post by viperdvman on 2012-03-25
I thank everyone for their input. I actually discovered that installing the **ntfs-3g** package from the repository fixed the problem. It can get complicated working with NTFS volumes, especially if it's a secondary hard drive or an external that's shared between Windows and Ubuntu.

But... this is the first time I've installed Ubuntu in nearly a year.... well, since October when I put Oneric on my netbook. So I didn't remember all the processes. I know using the /etc/fstab methods is good if you want to automount the NTFS volume at start-up.

I thank everyone for their help. I guess I still have some learning to do :D

---

### Post by coffeecat on 2012-03-25
> **viperdvman said:**
> I actually discovered that installing the **ntfs-3g** package from the repository fixed the problem.

Just a FYI - that means that you must have *uninstalled* ntfs-3g in the first place and the system defaulted back to the read-only kernel ntfs module. It's an all-too common mistake, but I'll post the explanation anyway.

Prior to 11.10, you needed the package ntfsprogs for various utilities associated with NTFS. With effect from Ubuntu 11.10, the ntfs-3g package - which comes as default - includes the utilities previously supplied by ntfsprogs. If you install ntfsprogs in 11.10, this removes ntfs-3g because the two packages now conflict. The package manager (whether Software Centre, Synaptic or apt-get) will have prompted you that it wanted to remove ntfs-3g and you would have OK'd this.

Moral - double-check which packages the package manager says it is going to uninstall before you OK this.

---

### Post by viperdvman on 2012-03-26
> **coffeecat said:**
> Just a FYI - that means that you must have *uninstalled* ntfs-3g in the first place and the system defaulted back to the read-only kernel ntfs module. It's an all-too common mistake, but I'll post the explanation anyway.

Prior to 11.10, you needed the package ntfsprogs for various utilities associated with NTFS. With effect from Ubuntu 11.10, the ntfs-3g package - which comes as default - includes the utilities previously supplied by ntfsprogs. If you install ntfsprogs in 11.10, this removes ntfs-3g because the two packages now conflict. The package manager (whether Software Centre, Synaptic or apt-get) will have prompted you that it wanted to remove ntfs-3g and you would have OK'd this.

Moral - double-check which packages the package manager says it is going to uninstall before you OK this.

It's possible that an update or restricted-extras (usually the first thing I install in Ubuntu or any of its flavors) or something killed ntfs-3g. I read somewhere that ntfsprogs was read-only while ntfs-3g was the read/write package. But once I saw that online, and installed ntfs-3g from the repositories, it cleaned up that problem. I'll remember that when I go to install 12.04 stable in May(-ish).

---

