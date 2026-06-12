---
title: "I wrecked my ubuntu install"
date: 2010-10-11
forum: General Help
---

### Post by sitheplayer on 2010-10-11
Hello!

I will try to explain what happened, but i'm still pretty new to linux, so if you need more information to make suggestions let me know. 

Onto the problem: I was thinking, why don't i just highlight all the folders(the folders like bin usr and such) and set their permissions to create and delete for every single one of them so i don't have to use command prompt or log into root and i can just copy and paste them where ever i please. 

Thats exactly what I did...

which leaves me here: When I logged out of Root, to copy the files i wanted on my account, I got sent back to black screen with white text. This was not at all what i was expecting, so I rebooted the system. Now when i boot into ubuntu, it says something about Permission denied to a file and won't boot. I tried recovery mode, but that gets stuck at the same point.

So, if anyone has any ideas besides reinstalling or if you need more information let me know.

---

### Post by nothingspecial on 2010-10-11
If you have recursively changed the permissions for every directory under root then you have hosed your system. 

If you have only changed the permissions for the directories directly under / and not every directory and file underneath them then you should be able to change them back.

Which have you done?

---

### Post by sitheplayer on 2010-10-11
The only folder I can remember the name of that i set permissions for was usr, since that was the one i was copying to. I did every folder on that page though. When i boot it the actual problem i'm getting is Sbin/Init permission denied, and then the kernel panics.
Thanks for the reply!

Edit: I put in a linux live dvd and now i can see the files. The ones i changed are bin boot cdrom dev etc home lib lib32 lib64 lost+found media mnt opt proc root sbin selinux srv sys tmp usr and var. I can see now what the permissions are set at, but not edit them. I guess now my question is how do i edit them If i can?

Edit 2: in root on the live cd I can edit all the permissions, but still saying it doesn't have permission when i boot, any ideas are appreciated!

---

