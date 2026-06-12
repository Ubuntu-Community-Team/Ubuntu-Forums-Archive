---
title: "Dual Boot MBR Linux/Winxp"
date: 2006-05-04
forum: General Help
---

### Post by donvella on 2006-05-04
Hello, I have been a windows user for a long time, also used a few different distros of linux breifly. Just to jog my memory i was going to ask a few simple questions;

1: I have just killdisked my PC, then used qparted (knoppix) to split my 70gb HDD into first half for NTFS winxp and i left 12gb for linux. My question is, will i have any problems placing a /boot after the ntfs?

2. I know there is thousands of methods, but i am thinking i should have a partition boot 100mb, swap 1gb, root 5gb, home 5gb, but i wanted more space for home though im limited.

3. If i were to just install kubuntu now my main worry is that it will screw my MBR and i wont be able to boot back into windows since its been quite awhile since i installed linux and im not sure. And, if theres no worries installing kubuntu after windows with the boot and all how can i edit my boot loader so that it only waits 3 seconds for a decision then auto boots into windows.

Cheers for your time
Don

AMD64 3000, 1GB DDR, ATI Radeon 9250.

---

### Post by Qrk on 2006-05-04
1) Thats fine.

2) With that little space, you may just want to combine /boot, / and /home. Also, I would only have half the 1 GB swap space. With 1 GB RAM you won't touch it.

3) This problem happens, but it is rare. If you have a windows installation disk, it is also easy to fix. When selecting partitions, do not select your Linux partition to get the "boot flag," that should be kept on windows. This seems to solve most problems.

---

### Post by donvella on 2006-05-04
Cheers, only one thing i heard though was that some dos 1024 cyclinder or something, could bugger up if the /boot wasnt infront of windows or something. But in general if i was just to insert the cd, and install it now i shouldnt have a problem, i do however remember going into that bootup menu and changing it to 3 seconds, i forgot what it was called and wheres it located. That information would be great since if i cant boot back into windows i can edit the boot myself and get it working.

---

### Post by cwhamsun on 2006-05-04
Answer to 1) I have installed ubuntu and kubuntu on several machines with win xp, win 2000 or win 98, also have some colleagues who have that I gave cds to. I have had zero problems with the bootloader setting up the MBR correct on 4 machines of my own installations and have been told the by the colleagues they had no problems either.

2) I guess that is up to personal preference I am not sure what to recommend, but the auto configuration during install usually seems to advise a good setup concerning that, just shows you how much for / and how much for swap unless you pick custom though(If I recall correctly).

3) I also worried about MBR some older distros I have used in the past caused me MBR problems with a dual boot machine, but I can tell you with as much confidence as I can that this distro will not, I have had zero problems with that either ubuntu/kubuntu breezy(5.10) or dapper (ubuntu and kubuntu) beta, and xp/2000/98, various combinations. I have used suse/fedora/RHEL 3 and 4, have used linux since I had to download redhat and slackware on floppies, and I have more confidence in this distro than I have had in the any other distro in the past, I wouldn't hesitate to install it on any machine that I have. I have had redhat or suse mess up my mbr on a dual boot in the past, but in my opinion you should not have a problem what so ever. 
In another thread I found:

Default Re: Grub question
In Ubuntu it is the /boot/grub/menu.lst

You need root permission to make changes to it
Code:

sudo gedit /boot/grub/menu.lst
.......
Within that file there is an entry called timeout, which sets the time for bootup default, the file explains this setting in the comment. (Thanks to the previous poster in the other thread, not sure if that was the proper way/etiquette to point out a previous post and give credit)

---

