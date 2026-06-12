---
title: "Windows XP &amp; Grub No Boot"
date: 2010-12-09
forum: General Help
---

### Post by dowtish on 2010-12-09
Hi People
 
I had Ubuntu 10.4 & Windows XP installed on one PC but they were on completely seperate hard disks. Just recently Windows XP would boot from the grub selection but when login appeared I could see something was amiss (screen display all over the place). Ubuntu 10.4 booted fine no problems. I decided to revert back to a previous image of XP and also decided to upgrade to Ubuntu 10.10.
 
Firstly I cleared all the partitions on the hard drives in question and created some anew via the ubuntu live cd & Gparted.
 
I then copied my XP image to disk.
 
I tried to install 10.10 but for some reason the install froze half way through so I booted into the live cd and performed all the previous operations again but this time I installed Ubuntu 10.4.
 
The issue I'm having is that XP will not load even though it's listed in the Grub.
 
After hours of trying to get my head round it I'm at a loss on how to move forward.
 
I even tried to do a fresh install of XP but it doesn't recognise the hard disk that I originally had XP installed on.
 
Gparted recognises the the Ubuntu disk & the XP disk and is happy to perfom any operations that I request.
 
Anyone have any ideas.

---

### Post by garvinrick4 on 2010-12-09
Did you format the Windows disk in NTFS?

---

### Post by dowtish on 2010-12-09
> **garvinrick4 said:**
> Did you format the Windows disk in NTFS?
 
Yes sir!

---

### Post by sikander3786 on 2010-12-09
I would suggest to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You need to run that script from your Ubuntu install or an Ubuntu Live CD/USB.

While posting, click the # icon in post menu and paste your data in between the generated code tags.

That output will help us better understand your setup and diagnose the issue. There are many experienced members on boot issues around here and **garvinrick4** are also one of them. So, you are not alone ;-)

---

### Post by dowtish on 2010-12-09
> **sikander3786 said:**
> I would suggest to post the output of bootinfoscript as per instructions here.
 
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
 
You need to run that script from your Ubuntu install or and Ubuntu Live CD/USB.
 
While posting, click the # icon in post menu and paste your data in between the generated code tags.
 
That output will help us better understand your setup and diagnose the issue. There are many experienced members on boot issues around here and **garvinrick4** are also one of them. So, you are not alone ;-)
 
Thanks for the speedy response guys I will be back soon!

---

### Post by dowtish on 2010-12-09
Hi sikander3786 & garvinrick4
 
I'm currently in the process of copying the XP image to the disk where I had Ubuntu installed as I need to access some info from the XP image.
 
Would the bootinfo script still be a viable option or have I caused more problems?

---

### Post by Krytarik on 2010-12-09
I ran into a similar problem recently, but with Windows 7. After moving Win7 to another partition I couldn't boot into it via GRUB2, no matter what I tried (and I really searched for a solution on the web!). The only way to success was to downgrade from GRUB2 to GRUB.

---

### Post by sikander3786 on 2010-12-09
> **dowtish said:**
> Hi sikander3786 & garvinrick4
 
I'm currently in the process of copying the XP image to the disk where I had Ubuntu installed as I need to access some info from the XP image.
 
Would the bootinfo script still be a viable option or have I caused more problems?
If the XP image was not corrupt and your partition setup was ok, the initial issue with XP was definitely fixable. I suspect it won't work that way, whichever partition you over write with that image. And by erasing the Ubuntu partition, now Grub would no longer work. I fear you've brought some more trouble to yourself.

So, what is the plan now? For Windows specific problems, there are Windows specific forums ;-)

---

### Post by dowtish on 2010-12-09
I've managed to get XP booted and it can read all the disks ..... I don't think the bootinfo script would have worked as I had three hard disk on my system 1 for XP & 1 for Ubuntu & 1 for Storage (NTFS). For the last 2 days I had been juggling data around on all 3 trying to get XP up and running.
 
The original XP hard disk was 120GB patitioned for system and storage (NTFS).
 
The original Ubuntu was 40GB whole disk used (auto partition during install).
 
The original storage (NTFS) was 40GB no partitions.
 
For some reason the 120GB disk doesn't want to boot xp anymore?????
 
I'm dubious about putting Ubuntu on that particular system again which is a shame because I enjoy the OS.
 
Oh well if I get a bit brave over the next couple of days I will give it a bash.

---

