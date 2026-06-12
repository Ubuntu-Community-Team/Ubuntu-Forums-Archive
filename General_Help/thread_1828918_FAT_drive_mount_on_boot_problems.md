---
title: "FAT drive mount on boot problems"
date: 2011-08-19
forum: General Help
---

### Post by NXTreme on 2011-08-19
I guess I should say something about my level of experience, computer(s) and other such things before I continue. I got started on this whole "Linux thing" about a year and a half ago. The first Linux OS I installed was Ubuntu 9.10. As a intermediate (no programming skills, but enough know-how to get along very well and help others) Windows user, I was not used to terminal commands and the frustration of not having a GUI for lots of things. However, I quickly learned and became somewhat addicted. By now I can get along decently in the terminal, though not as well as I wish I would and I understand the some of the "quirks" in working between Linux OSs and Windows.

I've worked with Ubuntu 9.10, 11.04 and Puppu 5.2. I actually find Puppy easier to use than Ubuntu now, maybe it's the fact that, since it's a smaller OS, it seems somewhat simpler. I've also convinced some of my friends to try out Ubuntu and did the job so well that one or two of them ditched Windows completely.

The computer I'm working on right now is not my main computer, that has and will stay, Windows 7. The computer I'm working on now is running 11.04 and is completely updated. It has an AMD Sempron @ 1.8GHz, 1 GB memory and a 20 GB IDE/PCI (or whatever it is...) for the OS. I'm trying to get it set up to run SAMBA as a home file server but I'm having troubles with the additional hard drive I'm using to store files on, an 80 FAT GB SATA drive.

I'm trying to setup the 80 GB drive to keep all the files on as it's newer and aside from having been used quite a bit, it's in perfect condition. That way I'm also keeping the system files away from inexperienced mice and keyboards, not that I'm doing that great myself. I can't get the drive to boot automatically and in the process *of* trying to get it working, I've messed up the fstab boot config file bad enough that the sda drive (20 GB with OS) started appearing as sdb and the sdb (hopefully, the 80 GB server drive) started appearing as sda. I've tried both editing the fstab manually and I've tried using "Storage Device Manager" or pysdm GUI to (try to) get things working.

Now when I boot I get an error message towards the beginning of the boot sequence that says something to the tune of "Unable to mount drive. Press S to ignore and continue or M (or something like M) to mount the drive yourself." Because of this, the GUI I use to configure SAMBA ("Samba Server Configuration") doesn't see the drive even if I manually mount the drive later. I've searched for answers but most of them have to do with older Ubuntu releases and don't apply, or they don't work. I've attached the contents of my fstab config file and if there are any other files needed, I can grab the contents and post them here.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0
# swap was on /dev/sda5 during installation
UUID=d57b76d5-ad51-4ac1-a925-799ab0f9916a  none            swap  sw,owner                  0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda1                                  /media/sda1     ext4  owner                     0  0  
```

---

