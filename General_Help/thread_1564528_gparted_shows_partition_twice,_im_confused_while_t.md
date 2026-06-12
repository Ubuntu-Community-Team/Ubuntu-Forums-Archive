---
title: "gparted shows partition twice, im confused while trying to setup auto mount.."
date: 2010-08-30
forum: General Help
---

### Post by xfearxnxloathing on 2010-08-30
why is this like this?!  

[IMG]http://i556.photobucket.com/albums/ss10/xfearxnxloathing/gparted.png[/IMG]

sda2 and sda5 are the same partition.  i set up sda5 because i wanted it to be ext4 just like sda1. i thought if i went ahead and formatted the second partition to ext4 it would just show up, automount and always be there.  in my case it hasnt worked that way.  is anything wrong with this, if so, how do i fix it?

---

### Post by oldfred on 2010-08-30
What you have is normal. Partition rules are that you can have 4 parimary partitions numbered 1 thru 4 or 3 primary and one extended where the extended is a container for many logical partitions starting at sda5. Since your logical takes up all the extended then they are the same size.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

It will not automatically mount and give you permission to write into the partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by xfearxnxloathing on 2010-08-30
> **oldfred said:**
> What you have is normal. Partition rules are that you can have 4 parimary partitions numbered 1 thru 4 or 3 primary and one extended where the extended is a container for many logical partitions starting at sda5. Since your logical takes up all the extended then they are the same size.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

It will not automatically mount and give you permission to write into the partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

thank you for shedding light on this subject, i will read more into everything as i have my two kids right now.  if i have any further questions i will post another reply.  =]

---

