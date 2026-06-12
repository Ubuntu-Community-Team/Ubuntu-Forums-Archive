---
title: "strange curlftpfs behavior"
date: 2009-06-27
forum: General Help
---

### Post by moore.bryan on 2009-06-27
i've used curlftpfs a million times before, but now i'm getting something really strange i hope the community can help me with...

here's the steps i took to mount my website as a folder:
[LIST=1]
[*]created mount point ```
sudo mkdir /mnt/website
```
[*]made mount point completely usable ```
sudo chmod -R 777 /mnt/website
```
[*]made mount point owned by me ```
sudo chown -R bryan:bryan /mnt/website
```
[*]edited /etc/fuse.conf to allow_other
[*]restarted fuse ```
sudo /etc/init.d/fuse restart
```
[*]checked i am a member of fuse group ```
sudo groups bryan
``` i am
[*]mounted ftp ```
curlftpfs ftp.bmoore.net /mnt/website -o allow_other,user=****:****,uid=1000
```
[*]ls -al /mnt tells me i'm in-control:
```
drwxr-xr-x  1 bryan bryan 1024 1969-12-31 19:00 website
```
[/LIST]
and, yet, i cannot write anything into this folder; no new files, no moved files, no copied files. i, apparently, have no access whatsoever. what gives? any ideas?

thanks, in-advance!

---

