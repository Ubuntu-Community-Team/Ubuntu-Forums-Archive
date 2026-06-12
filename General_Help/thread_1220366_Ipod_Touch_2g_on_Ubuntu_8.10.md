---
title: "Ipod Touch 2g on Ubuntu 8.10"
date: 2009-07-22
forum: General Help
---

### Post by fluizp on 2009-07-22
Hello folks! I'm trying to access my Ipod Touch through Ubuntu 8.10. Following the instructions of an article, I installed gtkpod, then I created the folder /media/ipod as the default mounting point and added the following line to /etc/fstab:

/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

After all, I tried to access the Ipod without success. When I launch the gtkpod and press "Load Ipod", a pop-up window asks this:

"Could not find iPod directory structure at '/media/ipod'.
If you are sure that the iPod is properly mounted at '/media/ipod', gtkpod can create the directory structure for you.
Do you want to create the directory structure now?"

I press yes and after selecting the mounting point (/media/ipod) and the ipod model, I press Ok and then appears the following pop-up window:

"Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'."

I seek some solutions and I find that the Ipod shoud work if it was first plugged in a computer with the Windows XP because in this case the Ipod is formatted in fat32 format, but in my case I first used it in a Windows Vista computer and I am don't know which is the file system of my Ipod. It is ntfs?

Searching for an answer I find a way to access the Ipod through SSH, after installing a SSH server on it. I finally have accessed the Ipod and played in my laptop a music that is located on it.

This confused me a little bit, because I can't access it through a wire but I can do it by wireless. The problem is that by wireless it is so much confused to manage the files, so I don't wanna change files this way to keep all things fully functioning.

My question is: how to solve the gtkpod issue and finally access the ipod by wire?

Anybody has an idea on what can I do?

---

