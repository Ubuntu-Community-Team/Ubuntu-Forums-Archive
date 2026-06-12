---
title: "mount a drive to home folder"
date: 2010-08-28
forum: General Help
---

### Post by bardic on 2010-08-28
Hey all,
I have a few drives that I would like to mount in my home directory. 

I know I need to add something like this to my fstab: /dev/hda2 ~/Music ntfs-3g defaults,locale=en_US.utf8 0 0

I just don't know how to find the /dev/hda2 part

Thanks!

---

### Post by oldfred on 2010-08-28
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

After you under stand some of the parameters:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

If you want to manually edit:
sudo cp -a /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

to find your UUID:
sudo blkid

my entry
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

after editing fstab

sudo mount -a

if it just returns it remounted ok, or it will give error message

---

