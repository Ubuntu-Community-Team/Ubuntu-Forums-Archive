---
title: "ecryptfs fails to mount chroot(ed) home"
date: 2011-06-21
forum: General Help
---

### Post by elianto on 2011-06-21
Hi all,
I've setup a chroot where I boostraped a 32bit lenny (from a 64bit lenny)
The chroot works (with schroot and dchroot) but I can't see the content of my encripted home. At the begging I got the Error locking counter then I tried the suggestion [in this bug]("https://bugs.launchpad.net/ecryptfs/+bug/573518") and now ecryptfs-mount-private fails without reporting any error and doesn't ask for passphrase, nothing, just as I hadn't issue the command.
I'm probably doing something wrong or it's another bug. this is what I did
I've setup my chroot as [official instruction here]("https://help.ubuntu.com/community/DebootstrapChroot")
cat /etc/schroot/chroot.d/natty-i386.conf
```

[ubu32]
description=ubuntu 32bit
type=directory
personality=linux32
directory=/srv/chroot/ubu32
users=es
groups=es
root-groups=root
root-users=es
#run-setup-scripts=true
#run-exec-scripts=true
aliases=default

``````
sudo debootstrap  --arch i386 natty /srv/chroot/ubu32 http://archive.ubuntu.com/ubuntu/
```/etc/schroot/mount-defaults
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/proc           /proc           none    rw,rbind        0       0
/sys            /sys            none    rw,rbind        0       0
/dev            /dev            none    rw,rbind        0       0
/home           /home           none    rw,bind         0       0
/tmp            /tmp            none    rw,bind         0       0
/dev/pts        /dev/pts        none    rw,bind         0       0
tmpfs           /dev/shm        tmpfs   defaults        0       0

``````

schroot                                                                                                                                                                                                                                            
(ubu32)es@studio:~$ ls
Access-Your-Private-Data.desktop  README.txt
(ubu32)es@studio:~$ ecryptfs-mount-private 
(ubu32)es@studio:~$ cd ..
(ubu32)es@studio:/home$ cd
(ubu32)es@studio:~$ ls
Access-Your-Private-Data.desktop  README.txt

```I would appreciate any pointer.. ecryptfs-mount-private just silently does nothing

---

### Post by zagaberoo on 2011-08-03
I'm having the same issue, but it doesn't look like anybody has the answer.  I'll report back if I find anything.

---

