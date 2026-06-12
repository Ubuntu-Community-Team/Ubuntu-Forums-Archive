---
title: "Issue with external USB HDD and Plex Media Server"
date: 2012-07-11
forum: General Help
---

### Post by alfo7 on 2012-07-11
I'm having an odd problem. I have a 160GB NTFS-formatted USB HDD which I plugged into my machine running 12.04. The drive auto-mounts, and on the desktop I can make folders, add files, etc.

I can also add files to it through the command line, and read them, so no problem there.

However, when I put all my new media on this drive, Plex Media Server could not read from it as permission was denied. I have an FTP server, and I can read and write files to the drive through that, although FileZilla says that the permissions for /media/srv (where the drive is mounted) are 700.

I have tried sudo chmod -R 755 on the drive but to no avail. I've also tried changing the permissions through FileZilla, which returned a 200 success code, but that made no difference either. What should I do now? I heard of sudo umount -l /media/srv and then  sudo mount -o umask=0022 /dev/sdb1 /media/srv, but that didn't work either :(

Please help!

---

### Post by gsenechal on 2012-07-23
Exact same issue here.  External HD.  Can read and write to it.  But Plex doesn't seem to find any of the media on the drive.

---

### Post by politenessman on 2012-11-23
I have a similar problem, and started a thread about it here: [http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341)

In my case, the external drive is a FAT32 drive, and the in addition, includes some files in my /Home as well that cannot be found by Plex.

Did you get a resolution to this in the end?
I suspect a permissions issue but I'm not sure where to start.

---

### Post by jualin on 2013-01-16
> **politenessman said:**
> I have a similar problem, and started a thread about it here: [http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341)

In my case, the external drive is a FAT32 drive, and the in addition, includes some files in my /Home as well that cannot be found by Plex.

Did you get a resolution to this in the end?
I suspect a permissions issue but I'm not sure where to start.

See my reply on [this post]("http://ubuntuforums.org/showpost.php?p=12459273&postcount=8").
Hope it helps!

---

