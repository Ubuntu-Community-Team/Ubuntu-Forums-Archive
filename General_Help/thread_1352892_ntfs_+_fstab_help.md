---
title: "ntfs + fstab help"
date: 2009-12-12
forum: General Help
---

### Post by Narusegawa on 2009-12-12
I'm getting far better with linux slowly, and while I know how to mount my ntfs drive okay, I'd like to know the proper way if that makes sense.

1) I'd like to auto mount at boot (I don't want any users unmounting this drive ever, only root should be allowed to do that)
2) It's NTFS (from an old vista format)
3) It needs to be read/writeable by all users on my system (it will be written to/from with Windows as well as Ubuntu).

It's basically my entire multimedia drive.

```
# /mnt/media NTFS Media
UUID=759C7A27D12F28E5 /mnt/media     ntfs-3g    auto,users,rw 0       1
```

I think the above will suffice, based on my own experience. However is the above the right way about this? Have I got the right settings for my 3 aims of this mount point?

Hopefully an expert can advise me on the options that I should be using for this atleast :)

I've read through some fstab guides and just end up being more indecisive about what settings to use :(

---

### Post by sisco311 on 2009-12-12
I would mount it somewhere in the /media directory with read/write permissions for the users in the plugdev group and read permissions for others.

Devices mounted in the /media directory will show up in the *Places* menu.

```
UUID=759C7A27D12F28E5    /media/media    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    2
```

The first user created on the system is already in the plugdev group. To grant write permissions for a user simply add it to the plugdev group:
```
sudo gpasswd -a **username** plugdev
```


[thread=283131]How to fstab[/thread]
> VFAT/NTFS:

Ownership and permissios of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

Best is to set directories with executable permissions and file with read write. To do this, use fmask and dmask (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a terminal w/ ls)

---

### Post by SuperSonic4 on 2009-12-12
> **Narusegawa said:**
> 1) I'd like to auto mount at boot (I don't want any users unmounting this drive ever, only root should be allowed to do that)
2) It's NTFS (from an old vista format)
3) It needs to be read/writeable by all users on my system (it will be written to/from with Windows as well as Ubuntu).

It's basically my entire multimedia drive.

```
# /mnt/media NTFS Media
UUID=759C7A27D12F28E5 /mnt/media     ntfs-3g    auto,users,rw 0       1
```

I've read through some fstab guides and just end up being more indecisive about what settings to use :(

Did you try the Arch wiki page for fstab? It's largely distro agnostic: [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

My favourite is quite simple and just to have defaults. Assuming that's the correct UUID something like:

If you want root only to unmount then don't specify users.
Note that you should only use 1 for a fsck of root. Use 2 for any other partition

```
# /mnt/media NTFS Media
UUID=759C7A27D12F28E5 /mnt/media     ntfs-3g    defaults 0       2
```

You could then chown the contents of /mnt/media to you or a group (windows ignores the concept of ownership)

```
sudo chown -R **user**:*group* /mnt/media
```

where **user** is the username and *group* is the group name. You can specify either one of these or both of them

---

### Post by sisco311 on 2009-12-12
Yep, the Arch Wiki page it's very good. This is the one for NTFS partitions: [http://wiki.archlinux.org/index.php/NTFS_Write_Support]("http://wiki.archlinux.org/index.php/NTFS_Write_Support") ;)

NOTE: ntfs-3g is installed by default in Ubuntu.

---

### Post by Narusegawa on 2009-12-12
@[SuperSonic4]("http://ubuntuforums.org/member.php?u=624123") : Never heard of Arch linux but that wiki page looks far more informative and readable from what I've seen elsewhere. That page says defaults contains equivalent to rw,suid,dev,exec,auto,nouser,asyn. It just doesn't say what "dev" means.

@[sisco311]("http://ubuntuforums.org/member.php?u=244665"): I never considered the 'Places' thing. Good idea. [FONT=Verdana]The [/FONT][FONT=monospace][FONT=Verdana]fmask=113,dmask=002 does confuse me though as to what it means.[/FONT]


[/FONT]In this case I might mount to /media/music.

And chown that to root : plugdev once mounted (as you say Windows ingores that anyway) so it does all 16,000 files too?

```
sudo chown -R root:plugdev /media/music
```And chmod to 664 afterwards. That way only plugdev group (and root) can write, and all others can read-only.

---

### Post by sisco311 on 2009-12-12
> **Narusegawa said:**
> 

And chown that to root:plugdev once mounted (as you say Windows ingores that anyway) so it does all 16,000 files too?

```
sudo chown -R root:plugdev /media/music
```

And chmod to 664 afterwards. That way only plugdev group (and root) can write, and all others can read-only.

FAT and NTFS partitions don't support unix/linux file permissions. 

You can not use chown and chmod.

You have to set the ownership and permissions (for all directories and files) at mount time.

mount options:
```
defaults,dmask=002,fmask=113,gid=plugdev
```


EDIT:

> The fmask=113,dmask=002 does confuse me though as to what it means.

fmask - file mask 
fmask=113 - set permissions of 664 on files

dmask - directory mask
dmask=002 - set permissions of 775 on directories

---

### Post by Narusegawa on 2009-12-12
Thanks guys, you've given me enough information to be able to do this. :) And very quickly too!

I'll definately bookmarked those wiki pages.

---

