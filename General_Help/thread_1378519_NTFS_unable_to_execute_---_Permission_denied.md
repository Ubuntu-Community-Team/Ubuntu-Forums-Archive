---
title: "NTFS: unable to execute ---: Permission denied"
date: 2010-01-11
forum: General Help
---

### Post by Mazin on 2010-01-11
I have an NTFS partition mounted with
```
/dev/sdb1       /media/ntfs   ntfs    force,defaults,users,gid=1000,uid=1000,umask=000        0       0

```

but I cannot execute executables on that partition.  I simply get something like,
```
bash: ./t: Permission denied
```

How do I fix these permissions?

---

### Post by Leppie on 2010-01-11
remove that line from your fstab, add yourself to the fuse group:
```
sudo adduser <userid> fuse
```
install ntfs-config:
```
sudo apt-get install ntfs-config
```
set the partition to automount in ntfs-config (you'll find it in the menu under System>Administration>NTFS Configuration Tool)

---

### Post by Mazin on 2010-01-11
Can you please explain what the difference is?  I'd rather just fix my fstab as it is. (I am also already in the fuse group).

---

### Post by warfacegod on 2010-01-11
> **Mazin said:**
> Can you please explain what the difference is?  I'd rather just fix my fstab as it is. (I am also already in the fuse group).

Installing ntfs-config will allow you to toggle on and off write support for internal and external drives formated as NTFS.

---

### Post by Mazin on 2010-01-11
I already have read/write on the NTFS partition.  I cannot, however, execute binaries.  I would like to know what error is in my mount statement (if any).

---

### Post by Leppie on 2010-01-11
> **Mazin said:**
> I already have read/write on the NTFS partition.  I cannot, however, execute binaries.  I would like to know what error is in my mount statement (if any).
i'm not a fstab wiz, but i think that the gid and uid options pretty much annul the users option.

---

### Post by toadmess on 2010-03-27
Thank you Leppie.

I had the same (non)execute permissions surprise as Mazin, having provided users,gid,uid and umask options in the fstab. After removing the superflous users option, the execute permissions started behaving as expected again.

---

### Post by falconindy on 2010-03-27
FYI: users and gid/uid options aren't related. One sets the owner/group permissions, the other specifies who's able to mount the drive. Inherent to the 'users' option, however, is the 'noexec' option which prevents execution of files on the partition.

---

### Post by DarwinsBuddy on 2011-10-22
Thank you for the information.
I was going crazy for almost 1 hour, because I wasn't able to execute something on my 2nd partition.
By purging the 'users' option it started to work as expected.

Thx ;)

---

### Post by mikejonesey on 2011-10-22
rw,nosuid,nodev,allow_other,default_permissions options in fstab should work...

---

### Post by audeojude on 2011-10-22
I don't believe that what your seeing is a permissions problem. I have been battling being not able to mount ntfs partitions as read write. They would only mount read only.

A lot of people have been having this issue and I tracked down that it was in the ntfsprogs program. I finally found a fix as described below.



It seems to be a problem in ntfsprogs and the kernel. I have tried a couple kernels and no luck. Then I installed ntfs-3g which automatically un-installed and replaced ntfsprogs and my read write ability on my usb drives and even my ntfs sata drives came back.

so the solution was to go 

sudo apt-get install ntfs-3g 

allow it to uninstall ntfsprogs

it takes a while to un-install and install as it has to recompile a bunch of kernel drivers. I had upgraded to the latest stock 3.0.13 kernel in updates just before trying this.


what a pita though. in changing permissions and playing with settings I killed my ability to log into my user directory. I had to delete that and create a totally fresh user directory and then copy back into the new one all my data and application configurations. 

Mostly Ubuntu just works which is what I like. Years ago I loved digging under the hood and customising and tweaking. Nowadays I just want my applications and Internet to work.

---

### Post by Clive McCarthy on 2011-12-03
> **falconindy said:**
>  Inherent to the 'users' option, however, is the 'noexec' option which prevents execution of files on the partition.

This advice has proven VERY helpful. :popcorn: **The documentation for FSTAB is quite misleading**. It reads:
[COLOR="Red"]**[INDENT]user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.[/INDENT]**[/COLOR]:confused: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab"):confused:

But it appears that **noexec** is NOT overidden by **exec** if **user** is set.

Here is what I found useful to make best use of an NTFS formatted drive on a dual-boot system:
[LIST]
[*]In the FSTAB entry set umask=000 this makes all the files **rwx** but that's just what I expect from an NTFS drive.
[*]Use Windows to change the Volume Label -- it is much easier than with Ubuntu
[*]Make the Volume Label resemble the /media/mount_point name so that what appears on the desktop (which the label) corresponds to the actual mounting point.
[*]Use Windows to defragment the drive -- NTFS _may_ need defragging from time to time.
[/LIST]

---

