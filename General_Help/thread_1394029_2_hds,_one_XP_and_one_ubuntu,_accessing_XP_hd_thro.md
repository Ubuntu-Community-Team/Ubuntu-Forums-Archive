---
title: "2 hds, one XP and one ubuntu, accessing XP hd through ubuntu problem.."
date: 2010-01-30
forum: General Help
---

### Post by sathyashrayan on 2010-01-30
My system specification: 
 
I am using is in my PC(stand alone) with the following system config.. 
 
AMD Sempron(tm) processor 
2500+ 
704 MB RAM 
ASUS mother board.. 
ubuntu version 9.10 
 
Problem: 
 
If I go to places->other drives (I have 2 drives, one is having windows partition) I used to open the windows drives from linux by asking root password. But it is not working now. It just tells that it can not mount and never asked any password.  I have not imported any information from windows during ubuntu installation, ie, I never checked the tick button.

---

### Post by coldraven on 2010-01-30
Try ```
gksudo nautilus
``` and check that the drive appears

Or install krusader (two panel file manager) after it's installed look under the "Tools" menu and you'll find "Root mode Krusader"
After typing your password you can access your entire system.
You select the drive with the little cubes icon near the top left of each panel.
Be careful not to change files that you don't understand!

Or you could try editing your fstab file so that the drive is mounted at boot up time.
I'm not an expert but the information is out there if you look.
**Make a backup of the file first!**

---

### Post by oldfred on 2010-01-30
If you hibernated in windows or windows has a need to run checkdisk repairs Ubuntu will not mount it as a flag has been set by windows. 

Go back in windows and run the chkdsk, it will require another reboot normally and may need to be run more than once. (until there are no errors)

---

