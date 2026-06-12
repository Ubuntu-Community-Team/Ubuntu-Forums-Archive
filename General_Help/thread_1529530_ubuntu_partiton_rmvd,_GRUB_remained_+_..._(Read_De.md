---
title: "ubuntu partiton rmvd, GRUB remained + ... (Read Details)"
date: 2010-07-12
forum: General Help
---

### Post by Milkman08 on 2010-07-12
+I can't recover MBR by winXP CD since I forgot admin's password

I guess my only options are;
to remove grub
to remove mbr and re-instal a new one (thruought ubuntu live CD or something else since I don't have XP's admin pass)
remove XP's admin pass

I just don't know how to do the above.
please help if you know how to and if you know some other ways other than the ones stated above.
thanks :)  

I ONLY have access to the following Disks;
GPartED
SYS Rescue CD (Dont know how to use though)

And I don't have access to highspeed internet.

---

### Post by egalvan on 2010-07-12
> **Milkman08 said:**
> 
I ONLY have access to the following Disks;

GPartED
SYS Rescue CD (Dont know how to use though)

And I don't have access to highspeed internet.

System Rescue CD should have a "restore Windows MBR" option, but I can't recall it, and don't have access to it at the moment.

I can suggest you download SuperGRUB. it has a boot-time option to replace the MBR.

And it's small... only 1.4 megabytes, so it should be OK even on dial-up.

home page

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

download link is on the upper-right side,
 follow the "Download CDROM" link,
choose the **SG2D Cdrom (OLD)** version (recommended by the authors)

burn to cd
boot
choose the option to restore the Windows MBR

---

### Post by Milkman08 on 2010-07-12
thanx but I can't download anything, i'm using gprs mobile phone connection and it's too expencive.
 can anyone help me fix it via sys rescue cd ? :s

---

### Post by egalvan on 2010-07-12
> **Milkman08 said:**
> 

I don't have access to highspeed internet.

I can't download anything,

Sorry, those are two different things...
which is why I recommended SuperGRUb for it's tiny size
(about 1/3 the size of most songs on iTunes, as a comparison)

You might try searching the System Rescue site for info on restoring the Windows MBR.

It has a large number of "how-to's" and documents

---

### Post by Milkman08 on 2010-07-12
Well, i couldnt find any useful guides and I were in a rush so I  downloaded it.
I burned it and booted my system with it, but there is no "mbr restore" option in it?Can you explain a bit more about it?

---

### Post by egalvan on 2010-07-12
> **Milkman08 said:**
> Well, i couldnt find any useful guides and I were in a rush so I  downloaded it.
I burned it and booted my system with it, but there is no "mbr restore" option in it?Can you explain a bit more about it?


go to this link... 

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

it has pretty screen-shots of the process.

---

### Post by Milkman08 on 2010-07-12
Thanks :) you have been very helpful.
one little note;
By saying I can't download anything I meant the gprs internet is so slow and expencive in here that I can't download anything.
although i did because I was responsible for making my cousin's computer un-bootable :D 
I installed ubuntu on his computer without gaining his permisrion.after he figured I did he forced me to remove it without listening to me talking about linux's advantages.
My poor cousin, he's a prisoner of windows :D

---

### Post by Milkman08 on 2010-07-12
the tutorial link you gave me has screen shots that my version looks nothing like it. 
the one i have doesn't ask me for language setting and that os chosing menu.
mine gives the following options;
Detect any os
detect any grub2 config file (grub.cfg) **tried this but ìt didnt find any cfg file**
detect any..
 it's grub version 1.98
how should i fix mbr with it?

---

### Post by Milkman08 on 2010-07-13
anyone has any suggestions?

---

### Post by Milkman08 on 2010-07-18
Ok, problem solved.
I have downloaded "super_grub_disk_hybrid-1.98s1.iso" instead of Old CD-Rom version.
When I booted with the SGD I chose "WIN ==> MBR and "WIN!!" )))))))))" and Viola!, problem was solved.

To people who have no internet connection and are stuck in my situation: make sure you have a SGD already burned up on a CD or a ReWritable one before you remove Ubunut Partitions from a Dual boot PC!
If you don't have and you are stuck like me, I have to say that you can't fix this unless you can fix MBR using "Sys Rescue CD" (Of course if you already have it on CD!)
EDIT: Also, before you remove ubuntu partition, you should check if you can go to the recovery section of Win XP cd (ie. check if it doesn't ask for administrator password)

**If anyone knows how to fix MBR using "Sys Rescue CD" please explain it here so I can mark this thread as Solved.**

---

