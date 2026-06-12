---
title: "root access on upgrade is blocking me"
date: 2010-12-09
forum: General Help
---

### Post by Roger N on 2010-12-09
I have just upgraded to 10.4 and I have an odd problem that is beyond my limited experience with linux - it is probably simple - but I cannot see any help on the boards. 

It is a problem with Root access 

My hard drives attached to the USB are  shown as being owned by me (Roger). 

But the internal drives ( such as my photos) are shown as being owned by root. 

If I try saving files from Firefox I get a warning that I do not have permission to save to that Directory/ file. and I am told to change the permissions. 

When I use gksudo nautilus - I can see the permissions and have the ability to change them - but when I change them from root to roger - it just snaps back to root. Obviously something else needs to be changed - but I don't know what  - the drives are NTFS - because I duel boot. 

I can happily save to the USB drives without any problem 

my fstab is 

proc /proc proc defaults 0 0
UUID=33fdc306-38ee-49df-8fe6-3e912706cf64 / ext3 relatime,errors=remount-ro 0 1
UUID=60496650-4d30-4c4a-befe-8060f1269d98 /home ext3 relatime 0 2
UUID=62858c54-c700-47e8-9a0f-e27688fb7477 none swap sw 0 0 
/dev/sdb1 /media/INTRIM_DISK ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda1 /media/System_XP ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda5 /media/Photos_images ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/fd0 /media/floppy auto rw,user,noauto 0 0

---

### Post by Verbeck on 2010-12-09
could you try adding the option uid=**1000** to your fstab line
(where 1000=your user id)

---

### Post by WorMzy on 2010-12-09
Verbeck is on the right lines with the uid option. Follow this tutorial for more info: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by Roger N on 2010-12-09
Thanks for that - I knew it would be simple - once you know. 

Strange thing is that I found out that I could save the info to a usb drive and then move it using one of the file browsers - it was saving it from within Firefox that was the problem - but that is now working OK.

---

