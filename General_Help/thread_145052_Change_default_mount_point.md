---
title: "Change default mount point?"
date: 2006-03-15
forum: General Help
---

### Post by xiaoxin on 2006-03-15
Hi

All media gets mounted in /media.
How can i change it so it will get mounted in another folder?



thanks

---

### Post by halfvolle melk on 2006-03-15
If the desired mount doesn't yet exist, you can open a terminal and make it:
```
mkdir /mnt/mymountpoint
```
I always use /mnt cause I guess that's what it's there for.
Then do this:
```
sudo gedit /etc/fstab
```
and change
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
into
```
/dev/hdc        /mnt/mymountpoint   udf,iso9660 user,noauto     0       0
/dev/fd0        /mnt/myothermountpoint  auto    rw,user,noauto  0       0
```
Save the file afterwards.

---

### Post by xiaoxin on 2006-03-15
aha mooi zo, zo te zien kan het in nederlands.

wat ik eigenlijk bedoel, alles word automatisch gemount in /media

dus als ik een usb drive aansluit komt het bv in /media/usb te staan
wat ik dus wil is dat als ik een usb drive aansluit dat het gemount word in bv /blahblah/usb.

Enig idee hoe dat voor elkaar te krijgen?


bvd

---

### Post by halfvolle melk on 2006-03-15
I'll stick to English though, Dutch support can be found here ; )
[http://www.ubuntu-forums.nl/](http://www.ubuntu-forums.nl/)

Changing the standard moutn point of an usb device, good question. I just tried adding the line
```
/dev/sda        /mnt/usb        auto    rw,user,noauto  0       0
```
to /etc/fstab, and that seems to work. My usb device is now mounted at /mnt/usb. I haven't found where the default is set though.

---

### Post by xiaoxin on 2006-03-16
that will work if the usb drive is always connected.
but since i'm using ubuntu on my notebook and i have two usb drives.
the drives are not always connected so i will get a fail on startup and after i connect the drive at another time it will still get mounted in /media.

So this isnt a solution for me.

---

### Post by ashmew2 on 2006-12-06
Thanks for the gr8 solution halfvolle melk   :) , i had mistakenly mounted all my partitions to /hda/media lolz..instead of the regular /media/hda
Thanks a Lot!!

---

