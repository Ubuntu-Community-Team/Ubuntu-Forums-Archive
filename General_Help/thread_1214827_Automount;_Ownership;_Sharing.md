---
title: "Automount; Ownership; Sharing"
date: 2009-07-16
forum: General Help
---

### Post by Hengy on 2009-07-16
I am new to linux. I have two hard disks, the boot drive, and one for media. I just figured out how to automount the drive at boot using fstab:

```
/dev/sdb1 /media/internal vfat defaults 0 0
```Before that, I would go into computer, and click on the drive, and Ubuntu would mount the drive for me. I could then share the drive, and allow other users to write to it. However, after I started to automount it, it saws I do not have permission, and do not own the drive. I can't even unmount the drive, cause I don't own the drive! 

All I want to do is to automount the drive, and have it automaticaly shared, so that I can access it and write to it form my vista computer.

Any and all help is very much appreciated!

Thanks, Hengy

---

### Post by dankdave on 2009-09-22
I'm having the same problem.  My second hard drive is mounted, but root is the only user that can write or read it.  The hard drive currently automounts to /media/disk/

I would like this hard drive to automount for me and let me write to it without using sudo.

Here are the contents of /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4101a9ef-9992-45d1-b0bf-fca3f50b8586 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3d408313-7547-473d-8c0d-ad421bf0728e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Here is what I get after typing mount:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dankdave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dankdave)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


Thanks in advance.

---

### Post by StuartN on 2009-09-22
> **Hengy said:**
> ```
/dev/sdb1 /media/internal vfat defaults 0 0
```

Try add uid=hengy to the options, i.e. defaults,uid=hengy without any space.

---

### Post by dankdave on 2009-09-22
Maybe I should have posted a new thread rather than reviving an old one.  I don't know if Hengy got his problem solved, but I'm having the same problem so I revived this thread.

---

### Post by StuartN on 2009-09-22
> **dankdave said:**
> Maybe I should have posted a new thread rather than reviving an old one.  I don't know if Hengy got his problem solved, but I'm having the same problem so I revived this thread.

In which case you may have greater success with uid=dankdave in place of uid=hengy

---

### Post by dankdave on 2009-09-22
> **StuartN said:**
> In which case you may have greater success with uid=dankdave in place of uid=hengy

ahhh touch\'e!  :)  I'll try that next time I have access to this computer.

I'm still a bit confused about how mounting this second hard drive works.  Is there a way to do this manually or do I need to have that line in my /etc/fstab file?  Also, why does ubuntu know to mount this hard drive to /media/disk on startup.  I don't see anything to do with /dev/sdb1 in my /etc/fstab file.

If someone could point me to a thread that discusses this issue that would be awesome.

---

### Post by dankdave on 2009-09-22
> **StuartN said:**
> In which case you may have greater success with uid=dankdave in place of uid=hengy

When I append this line:

/dev/sdb1       /home/dankdave/hd2 ext3 defaults,uid=dankdave 0       0

to my fstab file and run "sudo mount -a" I get the following message:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by dankdave on 2009-09-22
If I change fstab to have this line:

/dev/sdb1       /home/dankdave/hd2 ext3 defaults 0       0

with a mountpoint with permission settings

drwxr-xr-x 2 dankdave dankdave 4096 2009-09-22 16:43 hd2

and run "sudo mount -a" the drive mounts, but root is still the only user that can write to it.  The permission settings for the mount point change to:

drwxr-xr-x 3 root     users    4096 2009-09-22 11:49 hd2

And my user can't write to the drive.  For example, I see the following sequence:

dankdave@gateway-monster:~$ cd hd2/
dankdave@gateway-monster:~/hd2$ ls
lost+found
dankdave@gateway-monster:~/hd2$ touch dumb
touch: cannot touch `dumb': Permission denied
dankdave@gateway-monster:~/hd2$ sudo touch dumb
dankdave@gateway-monster:~/hd2$ ls
dumb  lost+found
dankdave@gateway-monster:~/hd2$ 


What I would like to do is allow my user to write to this drive.  Currently root is the only user that can write to this drive.

---

### Post by StuartN on 2009-09-22
Have a try with:
```
sudo mount -t ext3 /dev/sdb1 /home/dankdave/hd2 -o defaults,uid=dankdave
```
and possibly check who owns the root directories on the drive to be mounted.

---

### Post by StuartN on 2009-09-22
Actually, according to man mount, the uid and gid options are **not** available for "proper" filesystems like ext3. They are for inferior systems like FAT/NTFS that have no ownerships.

For ext3 you will have to mount the drive and then "sudo chown user:group mountpoint".

I don't know how you make the ownership persistent, so that you still own the drive on the next automount.

---

### Post by oldfred on 2009-09-22
You do have a mount point of ~/hd2?

You can also mount using labels, to see labels:

blkid -L

on another thread I saw this:
Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async
The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.
For more details please read man mount.
and:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

/dev/sdb1       /home/dankdave/hd2 ext3 relatime 0       2

---

### Post by dankdave on 2009-09-22
> **StuartN said:**
> Actually, according to man mount, the uid and gid options are **not** available for "proper" filesystems like ext3. They are for inferior systems like FAT/NTFS that have no ownerships.

For ext3 you will have to mount the drive and then "sudo chown user:group mountpoint".

thanks for the pointer, I thought I tried that, but perhaps I didn't do it in the correct order.  I was able to mount my drive and write files to it, but there's still one problem lurking, and that's ....
[QUOTE=StuartN]
I don't know how you make the ownership persistent, so that you still own the drive on the next automount.[/QUOTE]

Let me recap on what worked for me.  I don't like it when other users say "awesome! got it working!" and then I say to myself, how???

I'm running Ubuntu 9.04 - the Jaunty Jackalope and I have two hard drives in my computer.  The second hard drive is located in 

/dev/sdb1

You can find this by running "sudo fdisk -l".  I created a mount point in my home directory by executing

dankdave@gateway-monster:~$ cd
dankdave@gateway-monster:~$ mkdir hd2
dankdave@gateway-monster:~$ ls -l
total 36
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Desktop
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-22 22:07 Documents
-rw-r--r-- 1 dankdave dankdave  357 2009-09-18 22:16 examples.desktop
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-22 22:38 hd2
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Music
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Pictures
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Public
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Templates
drwxr-xr-x 2 dankdave dankdave 4096 2009-09-18 22:28 Videos

Now that the mount point is created you can add the line

/dev/sdb1       /home/dankdave/hd2 ext3 defaults 0       0

to /etc/fstab

Running "sudo mount -a"  forces the system to read fstab.  Next you need to run chown to change the permissions, because they won't be correct at this stage.  Do this by typing

sudo chown dankdave:dankave hd2

If you then type "ls -l" you should see that the user and group got changed.

---

### Post by dankdave on 2009-09-22
> **StuartN said:**
> 
I don't know how you make the ownership persistent, so that you still own the drive on the next automount.

Apparently the owner and group settings aren't being changed now when I run "sudo mount -a" after running "sudo eject /home/dankdave/hd2"  They were definitely being set to user root and group root before I was able to successfully write to the drive.  

Weird.

---

### Post by oldfred on 2009-09-23
The only w permission is for the owner

drwxr-xr-x 2 dankdave dankdave 4096 2009-09-22 22:38 hd2
so only dankdave can write, owner, group & others can r-read and x-execute

drwxr-xr-x 3 root     users    4096 2009-09-22 11:49 hd2
only root can write

do you want change permissions?
chmod -R 775       /home/dankdave/hd2
will give rwx rwx rw rights to owner, group, others

---

### Post by StuartN on 2009-09-23
> **dankdave said:**
> Apparently the owner and group settings aren't being changed now

Do you mean that the ownership and permissions that you set after mounting are now persisting, and that the mounting is now working as you want it to work?

---

### Post by 3rdalbum on 2009-09-23
/media/internal needs to have the same owner and permissions that you want the drive to have. If necessary, change it using "chown" and "chmod".

---

### Post by Zimmer on 2009-09-23
Tip to end most frustrations:  (Yes, you are learning a lot here but......)

Right Click on the Gnome panel, ADD to PAnel, DISK MOUNTER... may save you some time for day to day use....  I have forgotten all the manual mount stuff now..... DOH!
:)

---

