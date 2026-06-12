---
title: "Windows 7 &quot;loops&quot; at grub loader"
date: 2011-07-05
forum: General Help
---

### Post by eidasadie on 2011-07-05
Basically the issue is that after I installed ubuntu 10.04 (on the same drive as Windows 7) I can no longer boot windows 7 from grub.  When I select windows 7 in the grub boot menu it returns me to the boot menu.

I looked through other posts who had similar problems, however, I wanted to post my own thread as I was unsure how to fix the problem based on information from other threads.  

Any help/ walk through of this problem would be EXTREMELY appreciated as I need the windows 7 partition for work.

Thanks again, 

eidasadie

---

### Post by gandaran on 2011-07-05
try running the grub update command in ubuntu
```
sudo grub-update
```
check the output for any errors if any post them.
also if you can post a screenshot of your drive it would help to figure out the problem, install 'gparted' to check the drive then take a screenshot.

---

### Post by eidasadie on 2011-07-05
Thank you so much for the response.

the *sudo grub-update *did not work in terminal.

here is a link to the screenshot of my drive in gparted

[http://img89.imageshack.us/i/gpartedscreenshot.png/](http://img89.imageshack.us/i/gpartedscreenshot.png/)

sorry if it is hard to make out.  the first partition is windows 7, then BT4, then ubuntu and swap, then a recovery partition for windows vista (which i had before installing windows 7)

---

### Post by gandaran on 2011-07-05
sorry, it should be 
```
sudo update-grub
```
I don't see the windows 7 100MB boot loader partition in the screenshot, maybe you deleted the boot partition when installing ubuntu or your windows install is different but I believe all windows 7 installations use the boot loader, you will have to fix the windows boot, try using [rescatux]("http://www.supergrubdisk.org/category/download/rescatuxdownloads/") to fix the windows boot first and the ubuntu grub next.

---

### Post by eidasadie on 2011-07-05
I will try to run rescatux and then try sudo update-grub

do I want to restore grub to the MBR, or fix the windows MBR when I use rescatux?

---

### Post by eidasadie on 2011-07-05
So I used rescatux to restore the MBR, installed ubuntu grub to the MBR and updated the grub, however, it boots to grub and i select windows 7 it goes to a blank screen with a flashing cursor and does nothing.


not sure where to go from here, maybe I am using rescatux incorrectly.  I tried using rescatux another way (used the amd64 version) and it booted to a blank screen with MBR and does nothing.

---

### Post by Mark Phelps on 2011-07-05
> **eidasadie said:**
> Basically the issue is that after I installed ubuntu 10.04 (on the same drive as Windows 7) I can no longer boot windows 7 from grub.  When I select windows 7 in the grub boot menu it returns me to the boot menu.
...

This generally happens when folks use the side-by-side option that allows the Ubuntu installer to SHRINK the Win7 OS partition to make room for Ubuntu.  Sometimes, that ends up with a corrupted Win7 partition -- which, ordinarily, is easy to fix provided one of the following is true:
1) You used the Backup feature in Win7 (back when it would boot) to create and burn a Win7 Repair CD.
2) You have Win7 Installation media (an MS DVD, not a Recovery CD)

If neither of these is true, you are basically stuck right now -- because NeoSmart, which USED to host links where you could download a Win7 Repair CD image and burn it to CD -- has pulled their links.

So, at this point, you would need to borrow either 1) or 2) from someone else who has Win7.  If you can do that, post back here and we can provide more details.

---

### Post by eidasadie on 2011-07-05
v
v
v
v
v
v
v
v
v
v

---

### Post by eidasadie on 2011-07-05
guess im stuck

i got the copy of windows 7 from school as a direct download so i have no CD, unless someone else can provide it.

i didnt use sidebyside installation. i manually installed and sized my partitions.

why wont gandaran's suggestion work?

----- if i can find a MS DVD (which i beleive i can now) how should i proceed using #2 from your suggestions?

---

### Post by Mark Phelps on 2011-07-06
> **eidasadie said:**
> guess im stuck

i got the copy of windows 7 from school as a direct download so i have no CD, unless someone else can provide it.
OK, so check with the school and see if they will let you "borrow" install media to fix your PC.

> i didnt use sidebyside installation. i manually installed and sized my partitions.
OK, but, did you use Win7 Disk Management to resize the Win7 OS partition, or did you use the Ubuntu Installer (or GParted, or Disk Utility)?

> why wont gandaran's suggestion work?
Because all that will do is regenerate the GRUB configuration file -- and GRUB is likely NOT the problem.  More likely, the problem is that the Win7 boot loader got corrupted when you resized the partition -- and GRUB has nothing to do with that.

> if i can find a MS DVD (which i beleive i can now) how should i proceed using #2 from your suggestions?
Boot from the MS DVD and use the option to run Startup Repair (I think you will see an option when the desktop comes up to Repair windows).  Run Startup Repair three times, that's right, three times.  IF that works, you'll get Win7 booting again.

After that, post back here and we'll tell you how to get access to Ubuntu again.

---

