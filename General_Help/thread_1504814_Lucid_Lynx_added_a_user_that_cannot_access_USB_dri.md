---
title: "Lucid Lynx added a user that cannot access USB drive"
date: 2010-06-08
forum: General Help
---

### Post by Cavsfan on 2010-06-08
I added my wife to my system and gave her adm admin access. I compared my access to her's and it is the same. 
Yet, when I log on as her, the 1TB USB drive does not show up in Places.
I tried mounting it and it said it was already mounted in /media/Fantom
Did find with "ls" command that is indeed mounted there, but since it doesn't show in Places, it cannot be accessed.
Been searching and hunting and cannot find out why this is. 
If I would have made up her userid from the start, I wouldn't have this problem, but since I just added her, 
I cannot find a way to get her UID to "see" the Fantom USB drive.

Any help is always sincerely appreciated.
PS I cannot believe i cannot figure this out on my own!  ](*,)

---

### Post by Smart Viking on 2010-06-08
So when you open "/media/fantom" it does not show you the files? What error does it give?

This is just guessing but you could try to make a hard link to "/media/fantom". :)

---

### Post by Cavsfan on 2010-06-08
Here is what I get with this command -  ls -al /dev/disk/by-uuid/*

lrwxrwxrwx 1 root root 10 2010-06-08 12:01 /dev/disk/by-uuid/1CFC7A8DFC7A60C6 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-06-08 12:01 /dev/disk/by-uuid/53d632f0-bfe2-4588-a9a1-23b6a030090b -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-06-08 12:01 /dev/disk/by-uuid/55dbbec1-8a02-4677-90bf-bfa1a7ac11d4 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-06-08 12:01 /dev/disk/by-uuid/78B8D1A1B8D15DE6 -> ../../sdb1
(sdb is the fantom)

When I go to System > Admin > Disk Utility (This is the only place I can actually see the 1TB USB drive.

When I click on /Media/Fantom/ from her login a box comes up with a red line though it saying:

[COLOR=Red]The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "Fantom".[/COLOR]

Her user must just be missing some privilege, but I cannot figure out which one.
Thanks!

---

### Post by Cavsfan on 2010-06-08
Now, my login doesn't show the 1TB USB drive! I thought a reboot solved the problem, but I guess not...

---

### Post by Cavsfan on 2010-06-08
Well after another re-boot it is back on both logons...:confused:

---

### Post by Cavsfan on 2010-06-12
It appears that if I "logout" and switch users, I loose the USB drive and the CD/DVD ROM,
but if I reboot, it works OK. :confused:

---

### Post by Cavsfan on 2010-06-12
That is a confirmation. When I logout and log back in it looses access  to CD/DVD and external USB drive.

This is what the CD/DVD and USB drive look like in Media and they are unaccessible.

[[IMG]http://img194.imageshack.us/img194/6637/screenshot2xue.png[/IMG]]("http://img194.imageshack.us/i/screenshot2xue.png/")

If I re-boot all is OK. But, re-booting should not be necessary...
Should I report this as a bug maybe?

---

