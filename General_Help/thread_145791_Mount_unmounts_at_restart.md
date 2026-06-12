---
title: "Mount unmounts at restart"
date: 2006-03-17
forum: General Help
---

### Post by jazee on 2006-03-17
I have just put togeather a webserver running well of course the best Linux Distro Ubuntu. I am how ever having the problem of the second harddrive that I placed in the system not remaining mounted after restarting the computer. I have set apache to use the second harddrive as the root for the website. So I need the mount to stay mounted so that I don't have to log-in remount it and then log off. Also not sure but does apache start up before anyone logs-in. I just want to be able to turn the server on and walk away and it will start up all the servers on the system. Apache/ProFTP/Bind9/MySql

---

### Post by noob_Lance on 2006-03-17
Open a terminal and enter:

sudo gedit (or kate if kde) /ect/fstab

and then in the file enter this:

/dev/hda6       /media/Internal     vfat         defaults        0       0

first part- location of HD
second- Mount Point
3rd- partition type
4th-6th- leave those the same as above. 



that mounts my partition hda6 to /media/Internal as hda6 is just a partiton on my hard drive. yours will probally be something like hdb1 or something rather close to that... you know it anyways as you have mounted it already. but now everytime you start up.. it will auto mount,

~Lance

---

### Post by jazee on 2006-03-17
Not sure if I should start another thread for this problem. But after I mount the second harddrive the systems seems to come to a slow down. I try to just run some very basic commands like saving a simple 3 line file out of vi takes forever for it to complete. Any ideas how to speed this up.

---

### Post by noob_Lance on 2006-03-17
as for your apahce starting up... no it dosnt. but you can always jsut allow the main user account to automatically sign in when the computer is booted.

---

### Post by jazee on 2006-03-17
BTW noob_Lance I thank you that work just fine. It seems to be mount alright. Thanks again.

---

### Post by noob_Lance on 2006-03-17
no problem :)

---

