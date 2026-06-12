---
title: "Need help with 'chown'"
date: 2009-10-22
forum: General Help
---

### Post by viluve on 2009-10-22
Hi hi,

I've just moved my home folder (/home/abc) to a separate partition, and somewhere along the process the ownership of /home/abc (and all its content) were changed to 'root'. As a result, when I restart my ubuntu I can't get to my desktop, because ubuntu requires the home folder to be owned by the user (ie. 'abc').

Now I'm trying to change the ownership of /home/abc back to user 'abc'. 

So, from recovery mode, as a root, I run this:
   chown -R abc:abc /home/abc
But I get: operations not permitted.

Can anyone help?? Thanks in advance

FYI: 
- the new partition is FAT32
- I have this line in my /etc/fstab: "/dev/sdb2 /home vfat nodev,nosuid 0 2"
- tried running the chown using my login+sudo

---

### Post by KeLa on 2009-10-22
Have you tried to use sudo?
sudo chown -R abc:abc /home/abc

---

### Post by viluve on 2009-10-22
> **KeLa said:**
> Have you tried to use sudo?
sudo chown -R abc:abc /home/abc

yup (login as abc, then sudo chown ....), same result.

---

### Post by mcduck on 2009-10-22
> **viluve said:**
> Hi hi,

I've just moved my home folder (/home/abc) to a separate partition, and somewhere along the process the ownership of /home/abc (and all its content) were changed to 'root'. As a result, when I restart my ubuntu I can't get to my desktop, because ubuntu requires the home folder to be owned by the user (ie. 'abc').

Now I'm trying to change the ownership of /home/abc back to user 'abc'. 

So, from recovery mode, as a root, I run this:
   chown -R abc:abc /home/abc
But I get: operations not permitted.

Can anyone help?? Thanks in advance

FYI: 
- the new partition is FAT32
- I have this line in my /etc/fstab: "/dev/sdb2 /home vfat nodev,nosuid 0 2"
- tried running the chown using my login+sudo
Your problem is the FAT partition. FAT and NTFS don't support ownerships and permissions as they are used by Unix/Linux systems, so you really can't use a FAT or NTFS partition as your home.

---

### Post by sisco311 on 2009-10-22
FAT partitions don't support unix/linux type file permission. 

You can't use a FAT partition as your /home.

EDIT: i'm slow :)

---

### Post by revanb on 2009-10-22
mcduck is correct.

FAT32 and NTFS are Microsoft filesystems and while you can access these from linux they do not cater for linux specific requirements. That is why chown can't change the owner.

You have to use a native linux filesystem, ext3 or ext4

---

### Post by viluve on 2009-10-22
sisco & mcduck: Thanks for the info.

Damn.. the reason i want /home on FAT32 is so that I can easily share the content on non-Linux PC.

Any suggestions?

---

### Post by mcduck on 2009-10-22
> **viluve said:**
> sisco & mcduck: Thanks for the info.

Damn.. the reason i want /home on FAT32 is so that I can easily share the content on non-Linux PC.

Any suggestions?

Create a partition with some Linux file system and use that for your home, and then make another FAT partition for sharing your files with Windows. If you want you can mount the FAT partition inside your home (or mount it into /media or /mnt and symlink it into a directory inside your home).

---

### Post by can2002 on 2009-10-22
I'd also recommend a proper Linux filesystem - as indicated, permissions on VFAT mounts are global.  What you could do is move the mount down a layer (e.g. mount it as /home/abc rather than /home) and then specify the user and groups at mount time.  Something like the following in /etc/fstab might work:

/dev/sdb2 /home/abc vfat uid=abc,gid=abc,nodev,nosuid 0 2

I've never tried this with a home directory, but if you have no choice other than Fat32 it might get you working.

Cheers,
Chris

---

### Post by sisco311 on 2009-10-22
You have several options. 

You can mount the partition directly in your home directory. i.e. /home/abc/data.

You can mount in /media/data and create symbolic link(s) in your home dir to the partition (or files/directories).

Mount it in /media/data and *bind* files and/or directories.

i.e. you can add something like:
```
/media/data/MyDocuments /home/abc/Documents auto bind 0 0
``` to the fstab.

IMHO the ntfs support is stable/mature enough for daily usage, so I would format the partition to ntfs.

---

### Post by psycho5 on 2009-10-22
Or you could just leave your /home as an ext3 partition and in windows just use an ext3 partition mounter, there are a few out there that let you mount ext3 partitions and let you read from them. However, don't enable the write function just to be safe. 

But can2002's solution is better. In that case whenever your /home is mounted you own it, but when its not it belongs to root in your case.

---

### Post by QLee on 2009-10-22
[QUOTE=viluve]Damn.. the reason i want /home on FAT32 is so that I can easily share the content on non-Linux PC.

Any suggestions?[/QUOTE]

You probably don't have any need to share configuration files for your GNU/Linux software, I'm guessing you want to share data files of some type. 

One possible solution would be to create a separate partition with the FAT32 filesystem on it and then mount it inside your /home directory (folder) and save data files there. That partition (perhaps call it /Ubuntudata) would show up in mycomputer if you booted to a Redmond OS but the rest of your home would not. There are other possible solutions, what will work best for you depends somewhat on exactly what you need to share. I doubt you want the .* files to be available while you are working in Windows.

---

### Post by mcduck on 2009-10-22
> **can2002 said:**
> I'd also recommend a proper Linux filesystem - as indicated, permissions on VFAT mounts are global.  What you could do is move the mount down a layer (e.g. mount it as /home/abc rather than /home) and then specify the user and groups at mount time.  Something like the following in /etc/fstab might work:

/dev/sdb2 /home/abc vfat uid=abc,gid=abc,nodev,nosuid 0 2

I've never tried this with a home directory, but if you have no choice other than Fat32 it might get you working.

Cheers,
Chris

Mounting a FAT or NTFS partition as /home/username would still fail, since there are some files in user's home that require certain permissions and ownerships.. while you could handle the ownership in fstab, the lack of support for permissions would still become a problem.

---

### Post by viluve on 2009-10-22
Thanks everyone for your help, will try the symbolic link solution.
Case closed

---

