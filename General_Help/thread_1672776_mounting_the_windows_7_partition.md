---
title: "mounting the windows 7 partition"
date: 2011-01-21
forum: General Help
---

### Post by bigthugs0 on 2011-01-21
hey all ,, i have installed kubuntu from inside windows 7 on my new laptop cuz im afraid of losing the windows 7 partition after installing it from boot , 

well after installation , everything goes well , except that i cant mount the windows 7 partition so i can see the windows 7 partition data and files from kubuntu , i have these 

sda1 
sda2
sda3
sda4 

and windows 7 partition is sda3 , but when i try to mount it , it gives me another partition data (sda2) i guess instead

anyhelp plz ???

---

### Post by silkworm2.5 on 2011-01-21
Hi Bigthugs0.
Try booting Windows 7, then opening a command prompt and typing "chkdsk /f" to check the disk for errors, then try accessing it again. 
Hope this helps!
Also, what do you mean you installed from inside windows? Do you mean you used a Wubi install?

---

### Post by bigthugs0 on 2011-01-21
yes i have used the wubi installer

---

### Post by silkworm2.5 on 2011-01-21
When I used wubi, It didn't mount the windows drive separately because Linux was on the Windows partition. I had to go into the root of my drive and into a folder called "Host". Are you sure that the windows partition is separate, or is it the Windows 7 Bootloader?
Did chkdsk make any difference?

---

### Post by bigthugs0 on 2011-01-21
ohhhh thank you very much , didnt know that i can see it from the root , u saved me :D

---

### Post by silkworm2.5 on 2011-01-21
Glad to be of help! :)

---

