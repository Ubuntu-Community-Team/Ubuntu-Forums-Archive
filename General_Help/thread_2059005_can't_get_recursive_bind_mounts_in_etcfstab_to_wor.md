---
title: "can't get recursive bind mounts in /etc/fstab to work"
date: 2012-09-17
forum: General Help
---

### Post by roy.nico on 2012-09-17
Hello. 

I would like to use recursive bind mount with fstab but i can't get it.

A "normal" bind mount in /etc/fstab  looks like : 
```
 /dir /home/user/dir none rw,bind 0 0 
```

which means, that the directory tree /dir will be mounted in /home/dir. This works. The correponding command line is :
```
mount --bind /dir /home/user/dir
```

The problem occurs, when /dir contains itself subdirectories which are themself mount point. In this case, one should use instead the "recursive" bind :
```
mount --rbind /dir /home/user/dir
```

This works, but i can't do it in the fstab file. The following 
```
 /dir /home/user/dir none rw,rbind 0 0  
```
makes no differences with "bind", this means the sub mount point is not mounted in /home/user/dir.
On the other hand, if i mount in manually (with --rbind) and a look in /etc/mtab, then it shows exactly the same line , as if i used --bind.

I'm a bit lost...

Thanks for any comments...
nicolas

---

### Post by muemarco on 2012-10-09
I have the same problem:
my fstab looks like this:
```
UUID=3AB293E1B293A045 /media/Windows7 ntfs-3g rw,auto,nls=utf8,user,fmask=0111,dmask=0000,uid=1000,gid=1000 0    0
ubuntuserver:/export/public   /mnt/public   nfs4    _netdev,auto,rw  0  0
//pch-c200/share /mnt/MediaTank    smbfs iocharset=utf8,dir_mode=0777,uid=1000,gid=1000    0    0
#/media/Windows7/Users/marco/Videos /home/marco/Videos none rbind 0 0
#/media/Windows7/Users/marco/Documents /home/marco/Documents none rbind 0 0
#/media/Windows7/Users/marco/Music /home/marco/Music none rbind 0 0
#/media/Windows7/Users/marco/Pictures /home/marco/Pictures none rbind 0 0
#/media/Windows7/Users/marco/Downloads /home/marco/Downloads none rbind 0 0
#/mnt/public /home/marco/Public none rbind 0 0
```all those lines with the #-sign do not work in fstab. So I created a file /etc/init/home-mounts.conf that is supposed to be called after the mountall command has finished at boot time. But this is not the case obviously. The home-mount.conf looks like this.

```
#home-mounts - mount home directories

description "mount marcos working - home directories"

start on stopped mountall

script
    mount -R /media/Windows7/Users/marco/Videos /home/marco/Videos 
    mount -R /media/Windows7/Users/marco/Documents /home/marco/Documents 
    mount -R /media/Windows7/Users/marco/Music /home/marco/Music 
    mount -R /media/Windows7/Users/marco/Pictures /home/marco/Pictures 
    mount -R /media/Windows7/Users/marco/Downloads /home/marco/Downloads 
    mount -R /mnt/public /home/marco/Public 
end script
```despite the statement "start on stopped mountall" it does nothing in fact.
I have to manually start this script from the command line, after I logged in, with the command: sudo start home-mounts.

This is really a hassle. Any idea how to make this rbinds work within the fstab file?

---

### Post by joonpy on 2012-12-18
> **muemarco said:**
> 
This is really a hassle. Any idea how to make this rbinds work within the fstab file?

I have successfully mounted one of the windows (which is already mounted at /windows/c) directory. I have the following in my /etc/fstab:

```

/dev/sda2            /windows/c           ntfs-3g     uid=joon,gid=users,umask=0022        0 0
/windows/c/Users/Joon/Downloads           /home/joon/Downloads           ntfs-3g    rbind,nosuid,gid=users,umask=0222        0 0
```

I think none should be ntfs-3g. Hope this is helpful.

Also, take a look at [http://superuser.com/questions/251537/mount-specific-ntfs-directory-on-linux](http://superuser.com/questions/251537/mount-specific-ntfs-directory-on-linux) as well.

-Joon

---

### Post by joonpy on 2012-12-18
Also, it seems the target directory must exist before mount the directory - for example, 
/home/marco/Videos

---

