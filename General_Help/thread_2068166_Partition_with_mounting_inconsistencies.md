---
title: "Partition with mounting inconsistencies"
date: 2012-10-08
forum: General Help
---

### Post by maghoxfr on 2012-10-08
Hello,

I have installed Ubuntu 12.04 when it came out, but this time I haven't had much time to look into it. THe problem I'm having I think it's related to mounting a partition even though is not exactly that.

When I go to a folder, I can see the partition on the left side under devices. I can click on it and it works fine. But if I use a pic from that partition as wallpaper, or my music library (clementine) or pictures library (digiKam), they fail to find it on the next boot.

Any help will be much appretiated.
Thank you

---

### Post by jerrrys on 2012-10-08
When you shutdown, you break the link to that partition.

Look into symlinks

[http://www.google.com/search?q=how+to+create+symlink+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+create+symlink+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by maghoxfr on 2012-10-08
Thank you I will read about it. This never happened to me on any previous ubuntu releases though.

I wil post my results.

---

### Post by oldfred on 2012-10-08
If a partition on your drive, you need to add a permanent mount to fstab so it is mounted. If an external drive you may just need to copy those files over to a permanently mounted location.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Specifics:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by Bucky Ball on 2012-10-08
> **oldfred said:**
> If a partition on your drive, you need to add a permanent mount to fstab so it is mounted. If an external drive you may just need to copy those files over to a permanently mounted location.



+1. What fred said. The drive with the pic is not being mounted at boot.

---

### Post by maghoxfr on 2012-10-08
Thank you both very much. I will start right now to solve it with the info you posted.

I didn't mention it is a storage NTFS partition. I use it to keep my music and pictures etc.

---

### Post by jerrrys on 2012-10-08
> **Bucky Ball said:**
> +1. What fred said. The drive with the pic is not being mounted at boot.

Yes +1; I forgot about that  :roll:

---

