---
title: "Pinguy 10.04  permissions/ownership internal Hard drives"
date: 2011-01-09
forum: General Help
---

### Post by labud on 2011-01-09
64 bit Pinguy 10.04 LTS Gnome Asus P5QDeluxe  c2d 3.0mhz  4.0gb ram  

Having some confusion/difficulty with permissions and ownership of my 4 storage hard drives [internal].  
After I installed OS I created mount points for the hard drives and set about taking ownership of these drives following this information.

> 
If the harddrive is currently mounted then unmount it:

sudo umount /media/harddrive



Terminal
cd /media
sudo mkdir harddrivename


Next is to mount it . You can mount it by CLI , or automatically by adding a line to /etc/fstab - -
/dev/sdd1 /media/MusicShare320SG ext3 defaults 0 0
-- and save the fstab file.

Then:
sudo mount -a

And only then do this:
Now to fix permissions - -
sudo chgrp plugdev MusicShare320SG
sudochmod g+rw MusicShare320SG


After doing this if I check my permissions in terminal, I get this:
```
dabud@dabud-desktop:~$ cd /media
dabud@dabud-desktop:/media$ ls -l
total 40
drwxr-xr-x  2 root  root     4096 2010-09-19 09:42 cdrom
drwx------  1 dabud dabud   24576 2011-01-07 10:41 MusicBUp
drwxrwxr-x  9 dabud plugdev  4096 2011-01-07 10:24 MusicLibrary
drwxrwxr-x 35 dabud plugdev  4096 2011-01-05 22:43 MusicShare320SG
drwxrwxr-x 52 dabud plugdev  4096 2011-01-04 09:07 MusicStore

```

If I right click on a harddrive link that is on my desktop or in the /media file and go to Properties/Permissions, I get:
 "The permissions of [harddrive] could not be determined."

It does seem to affect the way I can access the hard drive and do modifications to hardrive data.

I tried going into terminal and gksu and changing permission and ownership, but nothing changes, even when I reboot.

What could be causing this and what can I do to fix it?
Thank You

---

