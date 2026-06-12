---
title: "Mounting NTFS Issue/Question"
date: 2010-10-12
forum: General Help
---

### Post by Warthaug on 2010-10-12
I am running ubuntu 10.10, 64bit, desktop version, although I had the same issue with 10.04.

I have a laptop with several partitions - recovery drive, win7, shared data drive, ubuntu ad swap.  I have the data drive (NTFS) set to mount at boot.  However, while it mounts properly, the data drive gets listed 2X in my places menu, as well as in all side-bars (see attachment for an example).  

One of these 'data' mounts works (i.e. clicking on it opens the partition), one does not.  When I click on the one which doesn't work get the error:
```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

How do I prevent this incorrect icon from loading at boot?

My fstab, btw:
```
UUID=62D67BA0D67B7361 /media/Data ntfs-3g users 0 0
UUID=207e8955-d735-4f23-b523-46b17c74eec8 swap swap sw 0 0
UUID=7bda9b9b-5df7-4d0c-9dcc-b71962608211 / ext4 defaults 0 1
```

Thanx

Bryan

---

### Post by oldfred on 2010-10-12
I think it creates the duplicates for mounts to /home and /media. My workaround is just to mount elsewhere and link it into /home.

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/shared

run this from home so it is the default:
ln -s /usr/local/fred/shared

fstab:
```
UUID=44332FD360AA9657                      /usr/local/fred/shared  ntfs-3g      defaults                             0  0 

```
another suggestion:
Prevent duplicates in places
[http://ubuntuforums.org/showthread.php?t=1278039&page=2](http://ubuntuforums.org/showthread.php?t=1278039&page=2)

---

### Post by TeoBigusGeekus on 2010-10-12
Hmm... improper shutdown from windows?

---

### Post by srs5694 on 2010-10-12
> **oldfred said:**
> I think it creates the duplicates for mounts to /home and /media. My workaround is just to mount elsewhere and link it into /home.

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/shared

run this from home so it is the default:
ln -s /usr/local/fred/shared

fstab:
```
UUID=44332FD360AA9657                      /usr/local/fred/shared  ntfs-3g      defaults                             0  0 

```

If you're the only user, mounting it directly in a subdirectory of /home/fred is perfectly reasonable. The /etc/fstab entry would look like yours, except with /home/fred/shared rather than /usr/local/fred/shared as the mount point. (The UUID would also have to be changed for other computers, of course.) If the system has other users who must be able to access these files, mounting the partition outside of a user's home directory makes more sense, though.

FWIW, /usr/local is intended to hold locally-compiled software. Although mounting a partition with user files there won't break anything, it is rather odd and could cause confusion if anybody else needs to administer the system. It's conceivable that an automated script could get confused and misbehave, too, although that doesn't seem very likely unless you mounted the partition at an existing subdirectory, like /usr/local/bin. (That specific location would be very bad for other reasons, too.) It's likely that /mnt would work for your purpose and not create problems for the automounter; or you could create a mount point that's not in any other directory -- say, /shared.

---

