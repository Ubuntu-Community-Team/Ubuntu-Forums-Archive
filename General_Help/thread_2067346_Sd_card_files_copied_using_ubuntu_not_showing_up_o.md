---
title: "Sd card files copied using ubuntu not showing up on windows 7"
date: 2012-10-06
forum: General Help
---

### Post by TheTrueRaven on 2012-10-06
Hello! After having libreoffice convert one of my 139 page work in progress stories into a 0 byte txt file with no chance of recovery. I am promptly tapping out. However it seems that all of the data I placed on a sd card using ubuntu 12.04 is not showing up on my windows machine. The files are on the card  show up with ubuntu, yet, with windows the only thing I get is a single file that is named a few random characters that is the entire size of the rest of the files. I would really love to get back my files, so I can continue writing without the risk of libreoffice completely tearing them to absolute shreds.

 ( If this post sounds a little digusted it is because of the fact I lost over 2000 words of a major story I am writing... thank the gods I have a backup though it was only at the 137 page mark. I just want my files back that is all.)

---

### Post by TheTrueRaven on 2012-10-06
Bump. I will rephrase this. I put files onto an sd card using ubuntu... they are not showing up on any other system. Help please.

---

### Post by ajgreeny on 2012-10-06
How is the sd card formatted?  If it's fat32 or ntfs it should be possible for windows to see anything on it; if you formatted it in ubuntu it could be ext# which can not be read by windows.

With the card plugged in run ```
sudo fdisk -l
``` in terminal and report the output back here.

---

