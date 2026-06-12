---
title: "Dapper unable to read NTFS partitons from 'live cd'"
date: 2006-06-01
forum: General Help
---

### Post by pjman on 2006-06-01
When I try to access my NTFS partition from Dapper Live CD (not a hard drive install) I get an error about the device not being removable so pmount could not execute. Is this a bug or am I doing something wrong? I have attached the error message.

Thanks!

---

### Post by blackjack6.21.91 on 2006-06-01
You may need some kind of program to read NTFS..

try scanning the repos

---

### Post by philoushka on 2006-06-01
Is there a GUI tool do mount NTFS partitions? This is a basic need for this newbie.

---

### Post by rcarring on 2006-06-01
My understanding is that Ubuntu can read NTFS but not write to these type partitions which is why there wasa whole slew of comments about using a fat32 partition as a transfer area.

---

### Post by aysiu on 2006-06-01
You don't need a special program to mount NTFS.

Mounting from the live CD is the same procedure as mounting from an installed Ubuntu:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by pjman on 2006-06-02
[QUOTE=aysiu]You don't need a special program to mount NTFS.

Mounting from the live CD is the same procedure as mounting from an installed Ubuntu:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]

I don't understand why this isn't done automatically like Knoppix..? Is it a bug or is that the way the Ubuntu devs want it to work? I've read that some people use the Ubuntu Live CD to fix issues with their Windows install. Now that's probably not the intended use of the Live CD but it would be nice if it mounted NTFS partitions automatically correctly upon bootup.

---

### Post by Qrk on 2006-06-02
It does, but you'll typically need to browse them as root. Its a privacy thing I believe, as Linux will ignore window's file permissions.

---

### Post by aysiu on 2006-06-02
[QUOTE=pjman]I don't understand why this isn't done automatically like Knoppix..?[/QUOTE] I have no idea. I love Knoppix for this.

---

### Post by jetpeach on 2006-07-21
Will they automount in Edgy?  If not, we should all file a bug to get them to do it...
I also read on slashdot there is a new opensource program that can read AND write to NTFS, and reliably.  I wonder if that will be incorporated...

---

### Post by Poka64 on 2006-07-21
> **jetpeach said:**
> Will they automount in Edgy?  If not, we should all file a bug to get them to do it...
I also read on slashdot there is a new opensource program that can read AND write to NTFS, and reliably.  I wonder if that will be incorporated...

Read this thread: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

