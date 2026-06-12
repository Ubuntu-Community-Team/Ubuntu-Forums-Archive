---
title: "Having trouble editing nano /etc/fstab"
date: 2009-12-09
forum: General Help
---

### Post by husskii on 2009-12-09
Hi I just installed webmin on my new ubuntu server 9.04, its been setup as raid0 with 1.79TB as the main HDD and and 20GB for boot directory. on my previous server which I setup about 1week ago, after installing apt-get ```
install quota quotatool
``` I went to ```
nano /etc/fstab
```  and changed /dev/md7 /home ext3 defaults 1 2  to look like this dev/md7 /home ext3 defaults,usrquota,grpquota 1 2 and from there I was good to go, I typed a few commands into the home dir & logged into webmin and enabled disk quotas and was able to create hdd quotas for each user, but this time ```
nano /etc/fstab
``` and fstab looked like this

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md2 during installation
UUID=d65da424-0650-40e6-8547-fcbb14bcb82e /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=30b433b9-5b7e-44dc-acbd-7915e65743b0 /boot           ext3    relatime        0       2
# swap was on /dev/md1 during installation
UUID=f1818854-4232-4ef4-8851-af7af890b320 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
 
and as you can see the layout is different and am not sure how to correct it.. I see some sort of error in relation to #/
```
# / was on /dev/md2 during installation
UUID=d65da424-0650-40e6-8547-fcbb14bcb82e /               ext3    relatime,errors=remount-ro 0       1
```

I know that is were I'm meant to add ```
usrquota,grpquota
```
but am not sure how. I think maybe first I should unmount and remount, but maybe I'm wrong.. 

As I really don't want to wreck the server, I would appreciate any advise that can help me resolve this issue..

Greatly appreciated..
Husskii

---

