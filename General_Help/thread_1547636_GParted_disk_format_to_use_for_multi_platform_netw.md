---
title: "GParted disk format to use for multi platform network drive"
date: 2010-08-07
forum: General Help
---

### Post by JonathanSG on 2010-08-07
Hi
I am pretty new to Ubuntu and am practicing on an old desktop as a file print and domain controller for a work from home business while I build and configure a Linux server. My question is as follows:

I have a laptop running windows 7, my wife has a MacPro running Snow Leopard, the kids have desk top running Ubuntu 10.04, I have a 500GB additional disk in the spare desktop which I want to use as a netork drive that will:
1) Win 7 backup location from the Laptop
2) Store backups of large photoshop files and other graphicsy type stuff from my wifes macpro.
3) Act as a shared directory for all of us
4) Store large multimedia files, mpegs etc

What is the best disk partition format - Am I restricted to NTFS due to the requirements to store Win 7 Backup files

Secondly can anyone point me in the direction of a URL for getting the Samba permissions sorted for Windows 7, The kids PC dual boots Win XP and Ubuntu 10.04 Win XP is no problem to network but in Win 7 I can see all the shares in the network map but I always get permission errors both from the Ubuntu PC and Win 7 laptop. Most of the help files and manuals deal with 98/Me/XP and not windows vista / 7 that I can find.

Regards

Jon

---

### Post by Ozymandias_117 on 2010-08-07
> **JonathanSG said:**
> Hi
I am pretty new to Ubuntu and am practicing on an old desktop as a file print and domain controller for a work from home business while I build and configure a Linux server. My question is as follows:

I have a laptop running windows 7, my wife has a MacPro running Snow Leopard, the kids have desk top running Ubuntu 10.04, I have a 500GB additional disk in the spare desktop which I want to use as a netork drive that will:
1) Win 7 backup location from the Laptop
2) Store backups of large photoshop files and other graphicsy type stuff from my wifes macpro.
3) Act as a shared directory for all of us
4) Store large multimedia files, mpegs etc

What is the best disk partition format - Am I restricted to NTFS due to the requirements to store Win 7 Backup files

Secondly can anyone point me in the direction of a URL for getting the Samba permissions sorted for Windows 7, The kids PC dual boots Win XP and Ubuntu 10.04 Win XP is no problem to network but in Win 7 I can see all the shares in the network map but I always get permission errors both from the Ubuntu PC and Win 7 laptop. Most of the help files and manuals deal with 98/Me/XP and not windows vista / 7 that I can find.

Regards

Jon

You will be restricted to using Samba, but you can use any filesystem you like.

---

### Post by JonathanSG on 2010-08-09
Thanks

---

### Post by aeiah on 2010-08-09
> **Ozymandias_117 said:**
> You will be restricted to using Samba, but you can use any filesystem you like.

meaning you should go with a native linux one if you're running linux on it. ext4 is ubuntu's default and will be fine.

---

