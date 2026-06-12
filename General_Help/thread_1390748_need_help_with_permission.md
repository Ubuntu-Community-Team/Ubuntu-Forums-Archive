---
title: "need help with permission"
date: 2010-01-26
forum: General Help
---

### Post by Mia_tech on 2010-01-26
I'm trying to give access to myself(not root) to a local drive, but I've tried 

chmod ugo+rwx /media/share 

didn't work, so I created group users, and added myself, so give new ownership to share

chown -R root:users /media/share

but I got a bunch of errors

>  sudo chown -R root:users /media/share/
chown: changing ownership of `/media/share/VMware-server-2.0.2-203138.x86_64.tar.gz': Operation not permitted
chown: changing ownership of `/media/share/vmware-networks': Operation not permitted
chown: changing ownership of `/media/share/vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz': Operation not permitted
chown: changing ownership of `/media/share/': Operation not permitted


what do I need to do?

---

### Post by t4thfavor on 2010-01-26
Is that a directory, or a physical drive mounted there?

sudo chmod ugo=rwx dir should do the trick, or you could do
sudo chmod 777 dir

That gives it all to everyone, so be careful.

---

### Post by Mia_tech on 2010-01-26
> **t4thfavor said:**
> Is that a directory, or a physical drive mounted there?

sudo chmod ugo=rwx dir should do the trick, or you could do
sudo chmod 777 dir

That gives it all to everyone, so be careful.

/media/share is a mount point for /dev/sdb1 physical drive, but I want to give the user access to the root of the drive: meaning the whole drive. by the way I just tried to use your command and give the world rwx to a folder and didn't work either.

chmod ugo=rwx /media/share/apps

is this something that I'm missing in the fstab file?

/dev/sdb1	/media/share	vfat	defaults 0	0

---

### Post by t4thfavor on 2010-01-26
Is it formatted in a linux file system, or is in ntfs?

If ntfs, it will act funny with permissions.

I think that should work for the whole drive as long as you use -R switch with chmod.

if you have GUI installed nautilus is pretty good at permissions if you launch it with sudo.

---

### Post by Mia_tech on 2010-01-26
> **t4thfavor said:**
> Is it formatted in a linux file system, or is in ntfs?

If ntfs, it will act funny with permissions.

I think that should work for the whole drive as long as you use -R switch with chmod.

if you have GUI installed nautilus is pretty good at permissions if you launch it with sudo.

no is fat32 partition, I changed my fstab entry to

/dev/sdb1 /media/share vfat rw,users,auto 0 0

still same results

---

### Post by raktarok on 2010-01-26
Use this line in your fstab:

```
/dev/sdb1 /media/share vfat users,umask=000 0 0
```

The umask=000 sets the permission part and gives everyone read, write and execute permissions.

Hope this helped!

---

### Post by t4thfavor on 2010-01-26
OK fat same thing, it has different permission structure than chmod can handle. If your not going to use this drive on Windows, I suggest reformatting it to ext3-4.

If not, you have to change the permissions of the mountpoint only, and hope it works the way you want it to. You can have some luck with the structure of your fstab entry, I think your on the right path with the entry you have. 

try something like this
/dev/sda3 /media/windows vfat iocharset=utf8,umask=000 0 0

damn beat again

---

### Post by mcduck on 2010-01-26
> **raktarok said:**
> Use this line in your fstab:

```
/dev/sdb1 /media/share vfat users,umask=000 0 0
```

The umask=000 sets the permission part and gives everyone read, write and execute permissions.

Hope this helped!

This is correctt.

It's not possible to change permissions directly on FAT/NTFS partitions because those filesystems simply lack the support for ownerships and permissions as they are used in Linux/Unix systems. Because of that the permissions must be set for the whole filesystem at the time when it's mounted.

---

### Post by Mia_tech on 2010-01-26
> **t4thfavor said:**
> OK fat same thing, it has different permission structure than chmod can handle. If your not going to use this drive on Windows, I suggest reformatting it to ext3-4.

If not, you have to change the permissions of the mountpoint only, and hope it works the way you want it to. You can have some luck with the structure of your fstab entry, I think your on the right path with the entry you have. 

try something like this
/dev/sda3 /media/windows vfat iocharset=utf8,umask=000 0 0

damn beat again

ok, I would format this in ext3/4, but it has happened to me that I've had to swap drive to another box in the past, and unfortunately windows does not understand ext3/4, so that's why I decided to go with fat32 or ntfs. I'll try your fstab entry... will let you know

---

### Post by Mia_tech on 2010-01-26
this worked just fine

/dev/sdb1 /media/share vfat users,umask=000 0 0

for some reason the other entry using iocharset didn't...

now, lets say I don't want to give "users" which is the world access to the drive and instead give access to a group like: netusers, and of course after adding the users to the group, can I use the group guid and uid in the fstab file? I just tried but mounting failed

/dev/sdb1 /media/share vfat uid=1001,guid=1000,umask=000 0 0

what's wrong with this entry?

---

### Post by Mia_tech on 2010-01-26
> **Mia_tech said:**
> 
/dev/sdb1 /media/share vfat uid=1001,guid=1000,umask=000 0 0



typo: guid=1000 correct gid=1000

got it working... thanks all

---

