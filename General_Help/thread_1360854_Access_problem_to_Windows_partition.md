---
title: "Access problem to Windows partition"
date: 2009-12-21
forum: General Help
---

### Post by Haitel on 2009-12-21
Hi there.,

I have a problem after upgrading to Ubuntu 9.10. I have Windows XP (default OS for my laptop) re-installed as well. I used to be able to see the Windows files in Ubuntu 9.4, but since I've upgraded to 9.10, it has become a problem.

After I entered my password, nothing happens and all my desktop icons are gone. Sometimes, but not always, I get an error saying that the partition is not available.

Can anyone help? Thanks

---

### Post by oldfred on 2009-12-21
I find some partitions are shown twice. I gave every partition a label and I think I see them once under label and once a default. The second one to be mounted does not mount since it is already mounted.

I added my entry to fstab and it works just fine under my defined mount. Both of these seem to work but I have slightly different parameters:

# Entry for /dev/sda1 :
UUID=04B05B70B05B6768                      /media/cdrive      ntfs-3g      defaults,locale=en_US.UTF-8,fmask=0111,dmask=0000         0  0  
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

