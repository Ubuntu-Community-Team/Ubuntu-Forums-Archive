---
title: "mounting requiring authentication"
date: 2010-12-14
forum: General Help
---

### Post by csckid on 2010-12-14
Hi. I am using dual OS. My XP OS got infected with Microsoft Security essesntial alert virus. In order to remove that online guide mention to rename folder in C drive inside AppData folder. 

I was trying to do that using ubuntu. But whenever I click on c: drive from ubuntu 8.10 it asks for password. As far as I remember it never used to ask for password before mounting. 
Here is the complete msg:
System policy prevents mounting internal media
An application is attempting to perform an action that requires privileges. Authertication as one of the users below is required to perform this action.
In details section:
Application: /user/bin/gnome-mount
Action: org.freedesktop.hal.storage.mount-fixed
Vendor:
I have typed the password correctly and pressed on authenticate. it didn't work
This message is displayed
DBus error org.freedesktop.DBus.Error.NoReplly: Did not receive a reply.

---

### Post by sohail_linux on 2010-12-14
with which account are u trying to do so ?  root or non-root ?

---

### Post by csckid on 2010-12-14
I was supposed to be root, since there are no other user created.

I clicked on places> computer> c drive

---

### Post by sohail_linux on 2010-12-14
not necessarily , checkout ur account name by :  whoami   in terminal
it should display root (in case of root) if not , do :  sudo su 
then enter ur password , and the in terminal run nautalius /media  , and the try accesing it.

---

### Post by csckid on 2010-12-14
root@myname-desktop:/home/myname# nautalius /media
bash: nautalius: command not found

can't open, I'm using ubuntu 8.10. 
Can this access my c drive of xp?

---

### Post by sohail_linux on 2010-12-14
you r running as root ,its sure . now u have to do two things , 
1st : find out the name of your folder browser whether it is nautalius or anything else (when u type **nau** and press tab its auto completing ? )
2nd: find out the mount folder of your c drive , is it in /media ? check it using **mount **or **fdisk -l**

---

### Post by csckid on 2010-12-14
nautilus /media:
it opened a explorer and showed two folders only. Both were CDROM
Please Note: I'm not able to boot windows

I haven't yet tried repairing windows using widows CD nor the recovery console. Do you think it will be a good idea to use them?
Even if the installation fails, I think ubuntu will disappear as well(since boot file changes). Do you think if I reinstall ubuntu, it will come back?


root@myname-desktop:/home/myname# mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/myname/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=myname)
root@nowshad-desktop:/home/myname# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa597a597

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       19456   140922149+   f  W95 Ext'd (LBA)
/dev/sda5            1913        5099    25599546    7  HPFS/NTFS
/dev/sda6            5100        7011    15358108+  83  Linux
/dev/sda7            7012       19456    99964431    7  HPFS/NTFS

---

### Post by sohail_linux on 2010-12-15
partitions related to NTFS and W95 are seemed windows partitions , create new directory in /mnt and try mounting them one by one , use **mount /dev/sd*.. etc**

---

### Post by csckid on 2010-12-15
I have reinstalled xp. Everything are back to normal accept for ubuntu.
Boot file may have been changed, now the list is not shown to select OS.
Please help me get the list back?

I have tried ubuntu 10.04 it freezes unexpectedly. Can I fix this issue too?

---

