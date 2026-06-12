---
title: "Problem with /proc/mounts"
date: 2009-11-22
forum: General Help
---

### Post by James- on 2009-11-22
I get on boot:
Unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to overide.

/proc/mounts
```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
/dev/disk/by-uuid/5457a33f-656e-4d57-8c77-8de798b08ec8 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sda7 /home ext4 rw,relatime,barrier=1,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/james/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

```

fdisk
```

/dev/sda1   *           1        2550    20480000    7  HPFS/NTFS
/dev/sda2            2551       60801   467901157+   5  Extended
/dev/sda5            2551        2799     2000061   82  Linux swap / Solaris
/dev/sda6            2800        4744    15623181   83  Linux
/dev/sda7            4745       60801   450277821   83  Linux

```

fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5457a33f-656e-4d57-8c77-8de798b08ec8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=33dd70df-2d5a-4ca3-93f3-79ee62478cc4 /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Barno on 2009-12-11
I have the same problem after installing the 2.6.32 kernel in Ubuntu karmic koala.

Install it using the deb packages. There is some risk that my system damage?. I had no problems, just to know if someone has that message.

---

### Post by kiwimonster on 2009-12-11
hmm

---

### Post by Lucky75 on 2009-12-19
Me too! Please help!

Ah, turns out, for some reason there were extra entries in my fstab? I don't really know what they were, but I commented out the last two lines and it worked. Needed to use a liveCD to mount my / partition though, because it wouldn't mount otherwise. I suppose I could have just mounted it manually though.

---

### Post by nickbart on 2009-12-24
Has anyone else figured out how to fix this? I have the same issue after upgrading to 9.10 and I'm at a loss. I commented everything out of my fstab, but no go.

---

### Post by luc765 on 2009-12-26
> **Barno said:**
> I have the same problem after installing the 2.6.32 kernel in Ubuntu karmic koala.

Install it using the deb packages. There is some risk that my system damage?. I had no problems, just to know if someone has that message.
I have to upgrade the karmic kernel to 2.6.32.2 of a Samsung NC20 in order to have the graphic card working correctly. 
Everything work fine except that I have each time the message "Unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to overide"
If I reboot just after receiving this message tht's OK.

An help will be appraciate

Lucien

---

### Post by adam814 on 2010-01-05
I've been having the same issue.  I'm also running a (custom-configured) 2.6.32.2 ubuntu kernel (from kernel.ubuntu.com).  I just found this:
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/482316](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/482316)
I can confirm this.  In the kernel source I built with (and those on the site are built with) there is no ubuntu/apparmor directory.  I guess I was mistaken when I thought all the ubuntu patches were applied to those kernels.

I will try building a 2.6.32.2 kernel with the apparmor directory from a stock 2.6.31 series ubuntu -generic and post back with results.

---

### Post by adam814 on 2010-01-06
Well, so much for that fixing it.  I was able to build (that was the surprising part for me).  Still getting the message at boot.

---

### Post by hadi2 on 2010-01-15
whats the problem with this warning message ?
have you ever compiled a program ? Usually you get warning messages , do you 
go and work on the source to solve those warning messages ?

---

### Post by adam814 on 2010-01-15
The problem with it for me is that AppArmor doesn't work.  It's not absolutely essential I know, but if it was something I could easily fix, why not?

---

### Post by conmat on 2010-01-17
Karmic 64-bit -  2.6.32-020632-generic #020632 SMP
Whole disk encryption w/LVM
Lenovo T400 notebook

I get the same error.  The error flashes on the screen very quickly after I enter my encryption passphrase but before I login to Ubuntu.  I can´t read the entire error but I did a search on what I did read and found this post.

I am a (very) new Linux user so I would really like some suggestions.

1.  If I don´t do anything, will anything really bad happen?

2.    If I have to compile a kernel how do I include the correct "stuff?"
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/482316](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/482316)

3.  Is there any other fix besides building a kernel?

4.  If I just wait will there be a kernel that fixes this anytime soon?

5.  Will this be fixed in Lucid?

I really don´t want to compile a kernel.  I have successfully installed a package from source ONCE and it was really, really hard.  What I mean is I encountered a LOT of dependency issues, obsolete dependency packages which were hard to find/install and which also caused problems with my system, non-standard source package (missing config file), etc.  I had to give up trying to install two other packages because I just could not meet all the dependency issues.

Danke Schöne

---

### Post by adam814 on 2010-01-17
1) It depends on what you consider "something bad."  You won't be able to use apparmor, so if you consider that bad then yes.  If you mean something bad like data loss and system lockups probably not.

2) I already build my kernels from source and I haven't figured out what needs to be included to get it working.

3) Either go back to the generic kernels in the ubuntu repos or if you need 2.6.32 run Lucid.

4) If so it'll be packaged for Lucid.  It could happen.

5) I'm pretty sure Lucid will run 2.6.32 series kernels, so yes and no.  If you install a newer kernel than the ones in Lucid you'll likely face the same issues.

P.S. Kernels don't have dependencies you have to track down, they're the OS core and are self-contained.  That being said building one isn't trivial.  Do some research before you build one.

---

### Post by conmat on 2010-01-23
adam814, Thanks very much,

Yes, by bad I meant general system mayhem.  apparmor - meh.  I guess I'll just wait for Lucid and keep a watch for any fixes.

I still have "random" system crashes.  The strange thing is I can always get my system to reboot if I play aisle riot spider!  Sooner or later this makes my system reboot, usually sooner.

I think I'll pass on building my own kernel, at least for now.

---

### Post by adam814 on 2010-01-23
There's something else going on if you're having random system crashes.

For other reasons I've installed Lucid Alpha 2 (kernel modesetting and compositing for radeon without a PPA and able to run nfs-kernel-server) and I can confirm I no longer receive the message and apparmor works as intended.

Of course I wouldn't recommend it for production systems.  It's been stable except for the occasional window manager crash (just have to run "emerald --replace" to get it back).

---

### Post by James- on 2010-01-23
I think it might be a lucid/2.6.32.x issue I have .3 installed right now

---

### Post by adam814 on 2010-01-23
AFAIK the problem is that the mainline kernels don't have all the Ubuntu patches applied.  Now that I'm running a stock kernel (2.6.32-11-generic on Lucid) I don't have this issue anymore, but I'm almost certain I would with one of the mainline kernels.

---

### Post by trevelyn on 2010-03-31
I got this error after removing AppArmor from my custom kernel.  Just simply remove the application:

```

apt-get purge apparmor

```

and remove the non-empty directory.  If you don't feel like using it of course.  If you do, simply rebuild your kernel to support it or at least check your kernel config to see if it is missing.

~trev

---

