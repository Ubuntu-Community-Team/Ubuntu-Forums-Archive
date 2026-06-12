---
title: "Problem with Windows recongnizing partition"
date: 2009-09-19
forum: General Help
---

### Post by Alan502 on 2009-09-19
Hi :)
first of all, i wanna say how satisfied i am with ubuntu, it is so sleek! and fast! and the installation was pretty easy; just wonderful.

I got it installed yesterday, with a usb stick because my 10" laptop does not have a cd drive. I had windows previously installed, with two partitions: one with 30gb for the system(C:) and another one with 120gb for data and program files(D:). When i decided to install ubuntu, i took 20gb from the 120gb partition(D:) and formated them into a new etx3 partition. I thought it was a simple as installing ubuntu in this new partition but apparently it is not. I dont know what i selected on the installation but it seems it installed inside "D:" i assume it from what i can see in paragon partition manager, windows: [http://imgur.com/Abge7.jpg ]("http://imgur.com/Abge7.jpg")(sorry for the resolution but i had all my programs installed on D:, the damaged partition). Now, i can boot into ubuntu, and into windows too, with no problems. But, i cannot access D: in windows, although in ubuntu i can.

I think the solution might be something similar to moving the ubuntu installation to the etx3 partition i had previously made, as it seems ubuntu is messing up when windows tries to access D:.

Please help! it will be very appreciated ;). Thanks!

---

### Post by Megrimn on 2009-09-19
I would try running chkdsk on that disk first.  

just go into my computer, right click the disk and go to properties.  under the 'tools' tab, there is an option to check the disk for errors.  click 'check now', and it should prompt you to restart your computer, in which it will run once it restarts.  I am not sure if it will affect your ubuntu partition, but I don't think it should.

[double-edit]  oh, and don't forget to check the box in the next window that says 'fix disk errors' as well.

[img]http://i.ehow.com/images/GlobalPhoto/Articles/2269183/LocalDiskProperties_Full.jpg[/img]



[edit] [*SORRY here's the link for the picture.*](http://www.ehow.com/how_2269183_do-basic-maintenance-pc.html)

---

### Post by trikster_x on 2009-09-19
sorry, I didn't see the link for the screenshot.

---

### Post by Soley on 2009-09-19
Looks like your D: drive is an Extended partition with other logical partitions on it. I honestly have no clue how to fix this without possibly breaking something on your system. It looks like you can see the drive in Windows...but just with a partion editor. Is that right?

---

### Post by Megrimn on 2009-09-19
> **trikster_x said:**
> sorry, I didn't see the link for the screenshot.

well, you could have just right-clicked the image and went to properties, and seen the web address there, but for your sake I went and edited my post. the link is now there.

---

### Post by Alan502 on 2009-09-19
> **Megrimn said:**
> I would try running chkdsk on that disk first.  

just go into my computer, right click the disk and go to properties.  under the 'tools' tab, there is an option to check the disk for errors.  click 'check now', and it should prompt you to restart your computer, in which it will run once it restarts.  I am not sure if it will affect your ubuntu partition, but I don't think it should.


Thanks, i thought about chkdisk but it does not run because of the same error, D: not accessible. Any other solution?

> **Soley said:**
> Looks like your D: drive is an Extended partition with other logical partitions on it. I honestly have no clue how to fix this without possibly breaking something on your system. It looks like you can see the drive in Windows...but just with a partion editor. Is that right?

I can see the drive in my pc but when i double click on it i get an error "Cant access D:\ directory damaged or ilegible."

Thanks for your replies :D

---

### Post by Alan502 on 2009-09-20
Any ideas?

---

