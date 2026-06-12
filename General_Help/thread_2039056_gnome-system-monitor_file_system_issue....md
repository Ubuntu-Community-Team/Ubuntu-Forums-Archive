---
title: "gnome-system-monitor file system issue..."
date: 2012-08-08
forum: General Help
---

### Post by mardybear on 2012-08-08
Sorry if this has already been covered...couldn't find a similar problem in the forum.

My primary linux/ubuntu partition shows up twice (both instances display similarly) under the file system tab of gnome-system-monitor. Not sure if this has something to do with my fstab file (output below). I've also attached a gnome-system-monitor screenshot. I'm running lucid 10.04 and the system is otherwise running fine - this just bugs me.

# /etc/fstab: static file system information.
#
# marty commented out: UUID lines x 2, dev/hdc, dev/sdb1
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda2 -- converted during upgrade to edgy
#UUID=3cbd33cb-0d0c-4508-9b18-c9f2ad86500d  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5 -- converted during upgrade to edgy
#UUID=86d4dbc9-6a59-4d05-8d5a-b2b980f50e41  none           swap         sw                          0  0  
#/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
#/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5    swap         defaults                    0  0

---

### Post by dcstar on 2012-08-08
> **mardybear said:**
> Sorry if this has already been covered...couldn't find a similar problem in the forum.

My primary linux/ubuntu partition shows up twice (both instances display similarly) under the file system tab of gnome-system-monitor. Not sure if this has something to do with my fstab file (output below). I've also attached a gnome-system-monitor screenshot. I'm running lucid 10.04 and the system is otherwise running fine - this just bugs me.

# /etc/fstab: static file system information.
#
# marty commented out: UUID lines x 2, dev/hdc, dev/sdb1
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda2 -- converted during upgrade to edgy
#UUID=3cbd33cb-0d0c-4508-9b18-c9f2ad86500d  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5 -- converted during upgrade to edgy
#UUID=86d4dbc9-6a59-4d05-8d5a-b2b980f50e41  none           swap         sw                          0  0  
#/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
#/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5    swap         defaults                    0  0

You should **not** - under ANY circumstances - mount things in /media.

/media is a System Folder for exclusive use by the system to mount removable devices, it is not for users to muck up with their own mount points.

Create /mnt and use that as it is supposed to be done for user mount points.

---

### Post by mardybear on 2012-08-08
Thanks David.

I don't have the smarts to have added the /media mounts myself...wonder if this was leftover when i upgraded from hardy (8.04) to lucid (10.04).

I reconfigured my fstab below and gnome-system-monitor now appears to display my system correctly. My updated fstab is pasted below and an updated gnome-system-monitor screenshot is attached.

I will mark this thread solved in a moment...just a few quick questions. Simple yes/no will suffice.

Is fstab still required for lucid 10.04 to boot/run or can it be removed?

Does fstab still need a pathway to the swap file or can it be commented out (i assume the swap file is not necessary for boot and utilized later on an as needed basis)?

Thanks in advance, hopefully David still has his ears open.

mardybear

updated fstab:
# /etc/fstab: static file system information.
#
# marty commented out: UUID lines x 2, dev/hdc, dev/sdb1
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda2 -- converted during upgrade to edgy
UUID=3cbd33cb-0d0c-4508-9b18-c9f2ad86500d  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5 -- converted during upgrade to edgy
UUID=86d4dbc9-6a59-4d05-8d5a-b2b980f50e41  none           swap         sw                          0  0  
#/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
#/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
#/dev/sda2                                  /media/sda2    ext3         defaults                    0  0  
#/dev/sda5                                  /media/sda5    swap         defaults                    0  0

---

### Post by mardybear on 2012-08-26
Just replying to myself to close this thread off properly. Consider the issue solved, as per my previous post (updated screenshot and fstab file).

Did my homework, as all of us newbie linux users are encouraged to complete. As far as i can tell a linux system won't boot/run without a proper working fstab file and won't utilize the swap partition if the swap pathway isn't correctly setup in the fstab file.

Hope this helps others with similar issues,

mardybear

---

