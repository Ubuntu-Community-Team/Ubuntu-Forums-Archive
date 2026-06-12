---
title: "fstab help after storage device manager"
date: 2010-07-06
forum: General Help
---

### Post by romeo26222 on 2010-07-06
Hello
I just installed storage device manager just to test it and see what it can do..
Now after installing it my mounting is screwed up..
I can't Mount/unmount drives anymore..

I am running ubuntu 10.04 on WUBI partition..

thats whats inside the fstab
```

proc                          /proc        proc  nodev,noexec,nosuid                                 0  0  
/host/ubuntu/disks/root.disk  /            ext4  loop,errors=remount-ro                              0  1  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                                             0  0  
/dev/sda1                     /media/sda1  ntfs  defaults                                            0  0  
/dev/sda5                     /media/sda5  ntfs  defaults                                            0  0  
/dev/sda6                     /media/sda6  ntfs  nls=iso8859-1,ro,users,noauto,umask=000,user,owner  0  0  

```I am very new on ubuntu so if somebody will help please give me instructions..
Regards

---

### Post by bodhi.zazen on 2010-07-06
What error message do you get when trying to mount a partition ?

Also, wubi has some issues sometimes, I do not know if this is one of them. wubi is for giving Ubuntu a try, if you wish to keep it, I suggest you do a standard install .

---

### Post by romeo26222 on 2010-07-06
thanks for reply
this problem didn't happens until i installed the storage manager
and there is no problem mounting the wubi drive at all,
thats what i get
[IMG]http://img818.imageshack.us/img818/2061/screenshotge.png[/IMG]

---

### Post by bodhi.zazen on 2010-07-06
You can either edit /etc/fstab and add the optin "users" or mount the partition using sudo

```
sudo mount /dev/sda1
```

although sda1 may already be mounted by default in wubi.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by bcbc on 2010-07-06
Whatever you installed wubi on, it's already mounted. It'll be under your /host directory. It likely isn't happy if you try and mount it again somewhere else. Maybe your storage manager isn't wubi-aware.

That's my best guess.

If you find wubi is on /dev/sda1, then just remove the mount for /dev/sda1 from fstab.

---

