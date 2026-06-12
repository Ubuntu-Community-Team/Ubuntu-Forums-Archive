---
title: "henry"
date: 2011-04-04
forum: General Help
---

### Post by Henry54 on 2011-04-04
Please help, I bought a new acer aspire 1 d255e that had windows 7 starter on it. I successfully got ubuntu 10.10 to pick up the broadcom  network card and thought all was well and decided to install to the hardrive and replace windows. After that I had no wireless or eithernet conection. I tried on flashcard ,puppy,mint 10.10 all with success on my large acer5552-3691. Everything worked great on that laptop but had many problems on the netbook. I decided I want to send the netbook back and maybe get a system 76 starling netbook that is set up right with good compatable hardware. 
     I have a samsung dvd writer and had made system restore dvds as backup so I could get windows back on if I decided not  to keep Linux ubuntu. Trouble is the samsung dvd will not install and wipe ubuntu off the drive and restore windows.
      What I need to know is if there is an easy way to wipe linux off and reformat the drive to nfts instead of fat 32. I want to send the netbook back with the original program and all it's crapware and Mcaffee which the restore disk should do. I am kind of new to all this so please realize I am far from a geek but know a few things about windows. I do know how to use the linux terminal to some degree. Thank's, just think that being a newbie I might be better off with a compatible ubuntu system like system 76 offers.

---

### Post by matt-fender on 2011-04-04
You could use a Ubuntu LiveCD, and run GPARTED once it's loaded up.. you could format to ntfs from there

---

### Post by Henry54 on 2011-04-04
> **matt-fender said:**
> You could use a Ubuntu LiveCD, and run GPARTED once it's loaded up.. you could format to ntfs from there
  I appreciate your answer I will also consult with a friend who does know some about Ubuntu to be sure I do it right and don't mess anything up. I want to be sure my samsung dvd writer can boot and  put windows back on.More detailed steps might help. I will take a look at the gparted program and see if I can figure it out. Thanks

---

### Post by Henry54 on 2011-04-04
> **matt-fender said:**
> You could use a Ubuntu LiveCD, and run GPARTED once it's loaded up.. you could format to ntfs from there
Ok, I went to GPARTED using my working flash drive that has unbutu installed. I saw how to bring up and highlight the large 200gb+ hard drive and found the partition that has the boot flag. Just to be sure I do it right; if I click reformat with ntfs will that take everthing off including the boot flag for ubutu and grub? Just want to be sure I don't delete anything that the Samsung would need to boot on and install the recovery. Thanks for your help.

---

### Post by matt-fender on 2011-04-04
> **Henry54 said:**
> Ok, I went to GPARTED using my working flash drive that has unbutu installed. I saw how to bring up and highlight the large 200gb+ hard drive and found the partition that has the boot flag. Just to be sure I do it right; if I click reformat with ntfs will that take everthing off including the boot flag for ubutu and grub? Just want to be sure I don't delete anything that the Samsung would need to boot on and install the recovery. Thanks for your help.

It should do yes, when i erase a partition i usually right click it in gparted and click delete. this will turn the partition into un-used space, then i right click again and format to NTFS or whatever file system you need for windows :)

EDIT: How are you going to restore the operating system which came with it? cd or recovery partition on the hard drive? it might be an idea to print screen your partitions in GParted for us too look at.

---

### Post by Henry54 on 2011-04-05
> **matt-fender said:**
> It should do yes, when i erase a partition i usually right click it in gparted and click delete. this will turn the partition into un-used space, then i right click again and format to NTFS or whatever file system you need for windows :)

EDIT: How are you going to restore the operating system which came with it? cd or recovery partition on the hard drive? it might be an idea to print screen your partitions in GParted for us too look at.
  Oh no! I went to GPARTED highlighted main 232 gb hard drive;deleted it; reformated it to ntfs Pluged in samsung writer and recovery disk worked as far as copying the three disk. Then it prompted that it was rebooting but did not bring up windows 7 starter. Now it won't even boot on to a ubuntu flash drive where I can look at it. I took some screen shots of my BIOS and the error messages I got. Any help will be appreciated.

---

### Post by Henry54 on 2011-04-05
> **Henry54 said:**
> Oh no! I went to GPARTED highlighted main 232 gb hard drive;deleted it; reformated it to ntfs Pluged in samsung writer and recovery disk worked as far as copying the three disk. Then it prompted that it was rebooting but did not bring up windows 7 starter. Now it won't even boot on to a ubuntu flash drive where I can look at it. I took some screen shots of my BIOS and the error messages I got. Any help will be appreciated.

 UPDATE from Henry. Somehow my flash drive got messed up or corrupted. I was able to get in with puppy and another flash drive that had 10.10 netbook on it. Maybe I didn't shut down from the flashdrive right after doing the reformat; don't know, I thought I did but it would seem something in the process of doing the operation went wrong. I am just glad I can get back in. Any suggestion about what might still be going on will be appreciated and I can submit shots of the partitions or whatever someone need to see to help me get it right.Thanks for all the help and I'm glad I've got a way to get in again.

---

### Post by mastablasta on 2011-04-05
from your grub message all you need to do is fix the main boot record using windows recovery disk:
 
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
It should boot from the disk after that.

---

### Post by Henry54 on 2011-04-05
> **mastablasta said:**
> from your grub message all you need to do is fix the main boot record using windows recovery disk:
 
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
It should boot from the disk after that.

Thanks I'll look into that I'm no geek and don't trust myself; If you will Look at these shot's of what the partition looks like now. The nfts file looks like it is flagged to boot; not sure. There are two linux looking files with the key symbles; one is the swap file. I don't know if thats supposed to be on there.Anyway here are the two shots I took of the partitions. Thanks for the info on the windows repair disk.

---

### Post by mastablasta on 2011-04-06
yah it seems to be flagged as boot, but that is not enough. It also need some small windows boot files which you get by using the link (it explains how to install them on the very beginning in the boot sector to replace the Ubuntu Grub boot launcher).
 
If you have problems with it and since you are using a legal windows copy you can just call microsoft support and they will give you step by step instructions live. Though they are not as hard to do as it looks. It's just a few commands you need to put in and away it goes.

---

### Post by Henry54 on 2011-04-06
> **mastablasta said:**
> yah it seems to be flagged as boot, but that is not enough. It also need some small windows boot files which you get by using the link (it explains how to install them on the very beginning in the boot sector to replace the Ubuntu Grub boot launcher).
 
If you have problems with it and since you are using a legal windows copy you can just call microsoft support and they will give you step by step instructions live. Though they are not as hard to do as it looks. It's just a few commands you need to put in and away it goes.

Thanks for your help right before you posted i finally got windows back on it with the help of Dban bootable iso disk wiper. A friend of mine in Texas thats into Linux suggested it. I chose the quick disk wipe and after a couple hours I started the the windows recovery disk and walla, it went on without a hitch. It took the linux file and grub right off. Can someone tell me how to mark this thread solved? I looked around but can't seem to find it. Thanks to everyone here that helped me.:guitar:

---

