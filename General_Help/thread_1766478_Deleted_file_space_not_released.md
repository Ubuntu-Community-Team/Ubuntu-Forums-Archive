---
title: "Deleted file space not released"
date: 2011-05-24
forum: General Help
---

### Post by kaizo2560 on 2011-05-24
Hi 

I updated my computer yesterday and ever since when I delete something from my second hard drive it no longer goes into the trash. It not only does that but does not release disk space so now I have a blocked hard drive.

I have tried deleting .trash-1000 as root but that only created a folder called .trash-0 and did not do anything. 

I am running kubuntu lucid lynx  kernel ver. 2.6.32-31-generic

Any ideas to solving this problem?

Thanks in advance

---

### Post by ph3d on 2011-05-24
I thought this was happening in mine and ended up doing a complete reinstall but i think a reboot was free-ing the space for me also before i reinstalled

---

### Post by kaizo2560 on 2011-05-24
Hi 

Thanks for the reply.

Yeah I did try a few reboots but nothing seemed to improve in my case I really hope I do not need to reinstall...

By the way ph3D did it happen to you on lucid lynx as well?

---

### Post by plucky on 2011-05-24
Try this [HOWTO: Recover Lost Disk Space](http://ubuntuforums.org/showthread.php?t=1122670&highlight=drs305)

Good Luck

---

### Post by psusi on 2011-05-24
You need to empty the trash then.  It sounds like you just moved the trash from yours to root's trash bin.  Hold down shift to delete instead of move to the trash.

---

### Post by kaizo2560 on 2011-05-24
Thank you :) problem solved

For those who is having the same problem in the future please refer to plucky's link section 6 c

In a nut shell:

gksudo dolphin (or nautilus for gnome)

navigate to your drive which does not free the disk space

go to view  -> show hidden files -> highlight the .Trash folder with the un-deleted files

!!! the following process is irreversible so please double check!!!

press shift + delete and agree to delete

Problem should be solved :) 

The files deleted from the second hard drive also now goes to the dust bin.

Again thank you all for helping me.

---

### Post by fishman35 on 2013-01-25
When I follow this and show hidden files, the Trash folder does not show up. I cannot get anything to delete and I am running sudo, gksudo, and nothing.

---

### Post by Bucky Ball on 2013-01-25
[I][B]Thread Closed

Reason:[/B][/I] Necromancy. This thread is over a year old. Please post a new thread with a descriptive title and outlining your current issues.

---

