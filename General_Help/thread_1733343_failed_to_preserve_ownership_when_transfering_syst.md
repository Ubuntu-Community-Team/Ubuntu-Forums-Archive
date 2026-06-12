---
title: "failed to preserve ownership when transfering system for netboot setup"
date: 2011-04-19
forum: General Help
---

### Post by iconoclast hero on 2011-04-19
Ok, I was following
[http://www.linuxpoweruser.com/?p=281](http://www.linuxpoweruser.com/?p=281)
and when I started transferring my file system with
```
sudo cp -Rax * /mnt/server 
```as root, I got
```

cp: failed to preserve ownership for `/mnt/server/bin/stty': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/chvt': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/mv': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/ps': Invalid argument
cp: failed to preserve ownership for /mnt/server/bin/netcat: Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/lsmod': Invalid argument
cp: failed to preserve ownership for `/mnt/server/bin/zfgrep': Invalid argument
.
.
.
```Should following this guide [http://ubuntuforums.org/showthread.php?t=1420413](http://ubuntuforums.org/showthread.php?t=1420413) work to get around the issue?  I'm concerned because in the discussion it was a problem setting up group permissions and I just want to maintain what is on my present system when I transfer it over for a netboob setup.

---

