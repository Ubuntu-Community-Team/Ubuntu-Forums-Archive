---
title: "grub2 problems"
date: 2010-04-30
forum: General Help
---

### Post by mattgyver83 on 2010-04-30
Hey guys, just recently upgraded to 10.04 from 9.10 and suddenly grub is causing me a world of hate.

I get different results each time I reboot, or power on the machine from grub.  

1. Sometimes grub will load the machine properly and right into the gdm without any problems.  

2. *most common* Sometimes it will sit at the 'ubuntu' splash for a long time, i notice that by pressing ESC it shows it was trying to run fsck on the filesystem however hangs at

> /dev/sdd2 is mounted
WARNING!!!  The filesystem is mounted.  If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.
Do you really want to continue (y/n)

From there I cant even press anything on the keyboard like N to not continue, however if i crtl+alt+delete it takes me right into the GDM.

3.  I have recieved the ubuntu boot splash which also says
> failed to mount /media/beta, press S to skip mounting or M for manual recovery
/media/beta is my main hard drive, and only about 3-4 mos old so I dont think its bad.

Selecting S runs fsck on the drive which then results in a clean drive, and loads into the gdm.

4.  The last oddity is i will recieve a message that says:
> Open /dev/null failed: no such file or directory
This merely flashes on the screen and then it loads the gdm.

This is pretty irratating and didnt happen with prior versions with grub2.  Any assistance would be greatly appreciated and I can make available any log files that are necessary, not included to not bloat this post.  Thx.

*note i just noticed that running df shows that /dev/sdd2 is mounted on 2 different mountpoints

/home
/media/beta (this is assigned in fstab on 9.10)

im wondering if this is causing the problem, any ideas?

---

### Post by dino99 on 2010-04-30
let me know about your exact config:

- is grub1 still installed ?
- are your repo only Lucid official ones ? ( no ppa or third party)
- before upgrading, have you made some cleanings ? (autoremove, install -f)
- you should unmount with nautilus all the non active partitions
- what is your graphic card ?

---

### Post by mattgyver83 on 2010-04-30
dino99 thanks for your quick reply.

1.  No, grub 1 was never installed, initially this was a fresh install of 9.10 with grub2 and i just updated to 10.04
2.  Currently i only have lynx repos configured.
3.  No, i didnt do anything like that.
4.  NVidia GeoForce nForce2, seems to be working properly.

I did have a major find in my /etc/fstab file somehow I had duplicate UUID entries for /sdd2 pointed to both /media/beta and /home.  After commeting out the /media/beta it appears less random, however now I experience some logical block I/O errors here and there.  Im going to run a check on the drive to see if I cant address those and see if thats was what was causing this issue.

---

### Post by mattgyver83 on 2010-04-30
Well, months back in my infinite wisdom I had added the same UUID at 2 mont-ponits in fstab, why I have no idea but after removing one instance and running fsck on the drive I have much more stable results.

I can successfully reboot the machine, and out of 10 attempts, each one worked perfectly.

From a cold start things arent so keen however not terrible, i did recieve one kernel panic and an instance where the grub loader hung, but crtl+alt+delete successfully booted into the system.. Not sure what it was doing.

Im pretty sure that these problems are unreleated to the initial question so I will mark this thread as solved and begin a more specific thread for these issues.

---

