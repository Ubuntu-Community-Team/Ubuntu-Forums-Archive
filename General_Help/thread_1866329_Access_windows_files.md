---
title: "Access windows files"
date: 2011-10-21
forum: General Help
---

### Post by jomaco on 2011-10-21
Hi

I'm new to unbuntu so please bear with me. I installed linux using the windows installer (from windows 7) so now I can choose to boot either windows or linux. The program I wish to use will only function in a unix environment but the file I wish to use with the program was originally downloaded in windows. It is a big file and would take a long time to download again - and there are other files similar in size which I will require at a later stage so this is why I need to access windows files. 

The problem is that the hard drives listed under devices do not have all of the files - in fact hardly any of them - so this is the reason why I tried to mount the hard drve (sda1) using terminal. Terminal stated that the drive was already exclusively mounted (or something on those lines). As a result I realized it must have been automounted so I unmounted everything listed under devices and then re-mounted sdb1 to my own folder (/mnt/windrive) but it still does not show all the files. Why might this be? 

Hope you can help!

Thanks

---

### Post by jomaco on 2011-10-21
Solved this! As I installed ubuntu with the windows installer all the files were available in the host directory.

---

