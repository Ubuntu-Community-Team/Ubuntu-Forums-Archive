---
title: "CD ROM Problems"
date: 2010-07-03
forum: General Help
---

### Post by DennisMesa on 2010-07-03
[CENTER][/CENTER]I am using 10.04 After installation neither of my 2 CD ROM drives will work. Going to System:Administration:Disk Utility or Places: Computer, they are both listed. When I try to play a DVD or music or data cd, the lights in the CD drive light up then go out and nothing. When I go to Places or use Rythmbox no icons show up.
I tried Knoppix live cd and both cd drives worked, but I had to many other troubles to use Knoppix.
I was using Windows 7, they both worked fine there. After using the 10.04 cd I downloaded to switch OS's neither cd drive works.
Any ideas???

---

### Post by chaosx9 on 2010-07-03
Well, this might work: open up a terminal (Alt+F2, type in "gnome-terminal" press enter) then use the following

```
umount /dev/sr0 && mount /dev/sr0
```

if it gives you some problem about root access or admin or something, use

```
sudo umount /dev/sr0 && sudo mount /dev/sr0
```

now, just to explain it to you, "umount" unmounts the drive, and "mount"...well...self explanatory.

Make sure that the media is in your first CD Drive , so that it targets the right one. I think it should be "/dev/sr1" if it's the slave.

---

### Post by DennisMesa on 2010-07-04
Thanks for your reply, After following your advice I get the following message:
can't find /dev/sr0 in /etc/fstab or /etc/mtab.
Do you know where I can either find this in the system or download it somewhere?

---

