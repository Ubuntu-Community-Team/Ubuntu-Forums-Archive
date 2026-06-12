---
title: "2nd HD Mounts, But I Can't Write to IT"
date: 2010-01-19
forum: General Help
---

### Post by wmichaelb on 2010-01-19
Hi, I added a second HD to my standard Ubuntu 9.04 system, and partitioned it to install a second Kubuntu system. That part works fine.

But I had a lot of space left over, and so I repartitioned that space with Gparted, and then used Pysdm to automount that partition (/media/Basement), which it does. The problem is, Nautilus won't let me create folders or otherwise write to the partition.

I tried:   sudo chown myname /media/Basement -R

no luck. I tried

           sudo chown 777 /media/Basement -r

Still no luck. 

My fstab file looks like this:

proc                                       /proc            proc         defaults                    0  0  
UUID=c2a2d1b5-ee33-4b69-962d-dd959c8e8db1  /                ext4         relatime,errors=remount-ro  0  1  
UUID=ab86c2c3-eaaa-4864-a5a6-8f070fd75637  /home            ext4         relatime                    0  2  
UUID=5f49ce02-9b27-45be-8036-2478a3a6c65c  none             swap         sw                          0  0  
UUID=ec8fca3d-bcd4-4f05-8c86-cf713796465f  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0   auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda4                                  /media/Basement  ext4         defaults                    0  0  


where the partition I'm concerned about is /dev/sda4 mounted at /media/Basement. Does anyone have any suggestions? I'd like very much to use this space for backing up the system. 

Thanks in advance!

---

### Post by audiomick on 2010-01-19
you could try starting nautilus with root privileges
```
gksu nautilus
```
and using right click> properties to change the ownership and permissions.

---

### Post by wmichaelb on 2010-01-19
Audiomick, that worked, thank you very much! I figured that it was something simple.

---

