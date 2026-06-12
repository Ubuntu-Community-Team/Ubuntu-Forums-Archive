---
title: "Samba share permissions oddity"
date: 2012-09-09
forum: General Help
---

### Post by QIII on 2012-09-09
I recently decided to make some changes to where my wife's Windows machine does its backups.  I decided to use a Samba share that I had a drive mapped to in Windows but had never done anything with on her machine.

My test backup failed because of permissions on the mapped drive.  I can see the partition and browse the files, but can't write.  I'm free to do anything stupid I want to do with the other two shares.   So I decided to dig a bit.

The machine with the shares has five HDDs.

sda -- Precise, entire disk, no shares
sdb -- Windows 7 partition, NTFS storage partition "Freya"  <-- contains the share that's not "working".
sdc -- NTFS storage partition "Thor", entire disk 
sdd -- Ubuntu Quantal, Xubuntu Quantal, NTFS storage partition "Loki"
sde -- Fedora 17, entire disk, no shares

The storage partitions are all in my fstab by UUID and are mounted on startup.

What follows is how far I dialed down anything security and safety to get everything on the same level -- so no smart remarks like "WOW! You shouldn't do that!"

The relevent parts of smb.conf

```

[Freya_Public]
    path = /media/Freya/Freya_Public
    read only = no
    writeable = yes
    browseable = yes
    guest ok = yes

[Thor_Public]
    path = /media/Thor/Thor_Public
    read only = no
    writeable = yes
    browseable = yes
    guest ok = yes

[Loki_Public]
    path = /media/Loki/Loki_Public
    read only = no
    writeable = yes
    browseable = yes
    guest ok = yes

```The results of mount:

```

/dev/sdb2 on /media/Freya type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Thor type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd3 on /media/Loki type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```Top level partition permissions:

```

drwxrwxrwx 1 root root  4096 Sep  8 00:50 Freya
drwxrwxrwx 1 root root 12288 Sep  8 00:50 Thor
drwxrwxrwx 1 root root  4096 Sep  8 00:55 Loki

```Samba shares permissions:

```

drwxrwxrwx 1 root root           0 Sep  8 01:13 Freya_Public
drwxrwxrwx 1 root root        4096 Sep  8 19:55 Thor_Public
drwxrwxrwx 1 root root          48 Sep  8 19:55 Loki_Public

```Right now, it seems like from my wife's Windows computer the permissions on Freya_Public are drwxr-xr-x or drwxr--r--, but I don't see anything obviously different than the other two Samba shares.

Is it possible that the fact that the first partition is NTFS containing a Windows installation is doing something evil to the Samba share?

---

### Post by mastablasta on 2012-09-09
> **QIII said:**
> 
Is it possible that the fact that the first partition is NTFS containing a Windows installation is doing something evil to the Samba share?

can NTFS file system have same permissions levels as EXT4?

as i know permissions are different in windows OS (rahs and 0/-).read only , archive, system i don't know what h is  and no attribute.

---

### Post by redmk2 on 2012-09-09
> **QIII said:**
> ...
Is it possible that the fact that the first partition is NTFS containing a Windows installation is doing something evil to the Samba share?
The file permissions do not follow from the remote host to the local host.  The structure does however.  By that I mean that you must use the ntfs-3g driver to mount the partition.  The tools chmod and chown do not work with ntfs-3g so you can't change the owner or the permission levels from the command line.  You must set the permissions at mount time.  See the options with the mount.ntfs command ```
man mount.ntfs
```

You can use these options from the command line ```
mount -t ntfs-3g
```... or from /etc/fstab.

The "top level permissions" only provide path access to the share (the mounted partition), they do not set the share owner or group or the permissions of the partition file system.

Post the content of the */etc/fstab* file please. 
+++++++++++++++++++++++++++

@mastablasta -- "can NTFS file system have same permissions levels as EXT4?"  

Nope.  As described above, the NTFS file structure and the ntfs-3g driver does not allow you to apply EXT style ownership or permissions to NTFS formatted partitions from the command line.

The NTFS RASH attributes (Read, Archive, System, Hidden) are either implemented differently (RH) or have no equivalent (AS).  The hidden is implemented by using a leading . (dot) or the tool *chattr* ```
man chattr
```... and there are no special "system or archive" files with Linux.

---

### Post by QIII on 2012-09-09
"The "top level permissions" only provide path access to the share (the  mounted partition), they do not set the share owner or group or the  permissions of the partition file system."  -- well understood, thanks.

The NTFS partitions are all mounted identically in fstab.

Again:  Two shares, Thor_Public and Loki_Public, work fine.  Only one, Freya_Public, does not.

I've simplified this all down to the least complex solution for all three shares to troubleshoot this.

From fstab, UUIDs redacted:

```

UUID=xxxxxxxxxxxxxxxx                                 /media/Freya    ntfs  defaults      0  0  
UUID=xxxxxxxxxxxxxxxx                                 /media/Thor     ntfs  defaults      0  0  
UUID=xxxxxxxxxxxxxxxx                                 /media/Loki     ntfs  defaults      0  0  

```

---

### Post by Morbius1 on 2012-09-09
This is a long shot but run the following command and see if you also create a samba userhsare of /media/Freya/Freya_Public:
```
net usershare info --long
```Samba allows both methods but "weird" things happen when you use both classic ( smb.conf ) and usershare methods on the same target and their definitions are different.

---

### Post by QIII on 2012-09-09
Good idea.  Alas, no help.  Sigh.  I thought you might have been on to something.

Shows nothing.

```

xxxxs@xxxx:~$ net usershare info --long
xxxx@xxxx:~$ 

```

But I do think this is just something that will cause me to smack my forehead when I find a typo or something somewhere.

So, I have two Samba shares that are working just as I expect them to, and one that is read-only from my wife's machine.

Funny thing is I'm just horsing around with where I'm going to move some machines and what they are being used for. The one I am backing hers up to right now is going to get put on a closet shelf for a while.  I'll just use one of the other shares for the immediate issue, but I'd sure like to solve this because it's just bugging me.

---

### Post by redmk2 on 2012-09-09
> **QIII said:**
> "The "top level permissions" only provide path access to the share (the  mounted partition), they do not set the share owner or group or the  permissions of the partition file system."  -- well understood, thanks.

The NTFS partitions are all mounted identically in fstab.

Again:  Two shares, Thor_Public and Loki_Public, work fine.  Only one, Freya_Public, does not.

I've simplified this all down to the least complex solution for all three shares to troubleshoot this.

From fstab, UUIDs redacted:

```

UUID=xxxxxxxxxxxxxxxx                                 /media/Freya    ntfs  defaults      0  0  
UUID=xxxxxxxxxxxxxxxx                                 /media/Thor     ntfs  defaults      0  0  
UUID=xxxxxxxxxxxxxxxx                                 /media/Loki     ntfs  defaults      0  0  

```What do you mean by "I've simplified this all down to the least complex solution"?  Did you change something?  What permissions show for the ***share root*** and below (e.g Freya_Public, Thor_Public and Loki_Public) from this host (where the shares are mounted).

---

