---
title: "Looking for easy bootable backup ideas"
date: 2009-09-02
forum: General Help
---

### Post by mingtien on 2009-09-02
I've recently started a new job, and find myself in a unique situation...  I've got to run Windows on my work laptop, but prefer to use Linux when I am not working.  I also have a demo machine that is a rather nice config (AMD Turion 64 X2, 4 GB RAM and a reasonable amount of disk), but this gets wiped clean every day during training labs and customer demos.

What I would like to be able to do is burn an exact image of the machine onto a USB key every morning (about 12 GB onto a 16 GB key) -- then when I get back from work at night, boot off the USB key and burn everything back to the hard drive, reboot, and be back in my environment.

Could anyone suggest some ways to handle this sort of backup?  I've considered Remastersys, but as I recall, it takes ages to create the image, and would be too cumbersome for a daily routine.  I think there would have to be extra steps to turn a handful of ISO's into a 10 GB image, then burn that onto a USB key and make it bootable.

I'm using Ubuntu 9.04 at the moment, and have grown very fond of it!

Any insights would be greatly appreciated :)

---

### Post by jerrrys on 2009-09-02
[http://clonezilla.org/](http://clonezilla.org/)

but even this will still probably take 15 minutes from start to finish

---

### Post by P4man on 2009-09-02
why not just use the key? Do a full install on the USB key, and use it at work or at home. And perhaps rsync your home folder to a harddrive

---

### Post by fluffman86 on 2009-09-02
I haven't had much luck with booting from an installed system on a USB stick.  It's very slow, and all the reading and writing tends to get corrupted pretty quickly so you end up with a still functioning, but non-booting, USB drive.

Instead, maybe look into using usb-creator and set it to use a persistant home.

edit: I think Jaunty comes standard with usb-creator, located under System > Administration > USB Startup Disk Creator

otherwise, install from synaptic.

---

### Post by C.S.Cameron on 2009-09-02
Running a full install or even persistent disk image install from the flash drive is not a bad option but is a little slower than running off internal SATA hard drive.
You should be able to clone from Internal drive to USB key and vice-versa using dd:
sudo dd if=/dev/sda of=/dev/sdb
You should first confirm that your internal drive is sda and the USB key is sdb.

---

### Post by winotree on 2009-09-02
I saw this in a post last week or so -- it's essentially as described, above, but with visual feedback.  May be interesting.  ;)  [http://madberry.org/2009/02/dd-with-progress-bar-try-dcfldd/](http://madberry.org/2009/02/dd-with-progress-bar-try-dcfldd/)

---

### Post by mingtien on 2009-09-02
Clonezilla Live looks to be about the best option -- thanks for that, jerrys!  I will test it out next week, when I have high speed Internet access again :)

---

### Post by snakepit # on 2009-09-02
Just cannibalize another laptop at work for it's HDD so you only have to deal with a screwdriver each night.

---

