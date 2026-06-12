---
title: "Backup Windows Files?"
date: 2012-03-10
forum: General Help
---

### Post by jacklotsofstars on 2012-03-10
Hi, I have a PC that runs (ran) Windows 7 64bit. Recently I have messed up the C: drive causing my PC to no longer be able to boot into windows. I burned an Ubuntu LiveCD iso on another computer, and have used the "Try Ubuntu" function to get into my computer. I can view all the files in my C: drive in Ubuntu, and I want to reinstall Windows 7 (with my original CD that came with my computer). But, I have around 95GB of files that I want to save. Is there anyway I can reinstall Windows while transferring those files into the new installation?

EDIT: I also have another Windows7 PC that is connected to a wireless network (the same one my PC running Ubuntu is connected to).

---

### Post by lrgmmc on 2012-03-10
do you have an external harddrive that you could use. it would be alot faster that way. you could just mount both the external and windows partition in ubuntu and transfer the files you wanted from windows partition to the external.

---

### Post by jacklotsofstars on 2012-03-10
> **lrgmmc said:**
> do you have an external harddrive that you could use. it would be alot faster that way. you could just mount both the external and windows partition in ubuntu and transfer the files you wanted from windows partition to the external.
i dont have an external harddrive. but is there any way i could transfer the files to my other computer and then transfer them back after the reinstall of windows?

---

### Post by Habitual on 2012-03-10
> **jacklotsofstars said:**
> i dont have an external harddrive. but is there any way i could transfer the files to my other computer and then transfer them back after the reinstall of windows?

USB drive?

---

### Post by evilsoup on 2012-03-10
I *think* that you can do this over ethernet. You'll need a 'cross over' cable (an ethernet cable that has a 'head' on each end). Can't help you with the specifics, I'm afraid, but hopefully you should be able to start with this... try searching google for 'transfer files over ethernet ubuntu' or something similar ([this](http://www.webhostingtalk.com/showthread.php?t=1042718) looks like it might be useful to you).

But doing it with an external hard drive really is the simplest option, and HDDs are always useful to have, and they are not *that* expensive.

---

### Post by lrgmmc on 2012-03-10
what I would do is since both are on the same network I would setup a samba share on the windows machine then on the Ubuntu machine use rsync to transfer the files over your network. sorry for not going into too much detail about the process. I'm using my phone at the moment. when I return home I can do a write up of the process. also if you are using a router you will not need cross over cable.

---

### Post by jacklotsofstars on 2012-03-11
> **lrgmmc said:**
> what I would do is since both are on the same network I would setup a samba share on the windows machine then on the Ubuntu machine use raunchy to transfer the files over your network. sorry for not going into too much detail about the process. I'm using my phone at the moment. when I return home I can do a write up of the process. also if you are using a router you will not need cross over cable.
Thanks for your help! I've already tried sharing the folder and stuff via Windows share but it always prompts me to log in on the Windows computer. I will try to install samba on the Windows pc and then I will look in to rsync

---

### Post by lrgmmc on 2012-03-11
Yea windows is kinda picky like that :D

---

### Post by coldraven on 2012-03-11
If you don't have much money a cheap option is to buy a HDD enclosure like one of these:
[http://www.amazon.co.uk/tag/hdd%20enclosure/products](http://www.amazon.co.uk/tag/hdd%20enclosure/products)
Then remove the HDD from your Windows machine insert it into enclosure and plug it via USB into an Ubuntu PC.
You can then copy all your data.
I have bought them on eBay for £5 and had no problems.
Or you could buy a HDD dock but they cost a bit more.
[http://www.amazon.co.uk/Icybox-IB-111StUS2-Wh-Docking-2-5-inch-3-5-inch/dp/B00485FCIS/ref=pd_cp_ce_0](http://www.amazon.co.uk/Icybox-IB-111StUS2-Wh-Docking-2-5-inch-3-5-inch/dp/B00485FCIS/ref=pd_cp_ce_0)

---

### Post by lrgmmc on 2012-03-11
double post

---

### Post by lrgmmc on 2012-03-11
double post

---

### Post by Mark Phelps on 2012-03-11
What could be a LOT less trouble is trying Boot-Repair to see if it can repair the Win 7 boot problems:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by lrgmmc on 2012-03-11
That program look like it's mainly for grub 2. so if he's not dual booting i don't think it's gonna help much, and if its a windows error it's not going to fix that. I did find an easier to read guilde on the sysresccd site. it covers this whole process very well. [http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer]("http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer")
you can easily use the ubuntu cd instead of theirs.

---

### Post by jacklotsofstars on 2012-03-11
hmm. I am so confused. I'm pretty sure the reason Windows is messed up is because I may have replaced or deleted something in the actual Windows folder. I don't have any system repair tools or anything. And I don't understand anything about partitions... Like I said, I've been running ubuntu as a trial off the live cd. I have ubuntu installed on the working PC using Wubi. When I try to share the folder on Computer 1 (the messed up one), it works and all, but then when I go to the network on Computer 2 (the working one), I open the Ubuntu network drive and double click the shared folder, but then it either asks me to log in (which I don't know how to do) or sometimes it says it can't locate the Ubuntu drive.

---

### Post by lrgmmc on 2012-03-11
here i did a write up. [http://therevpc.blogspot.com/2012/03/backup-over-network.html]("http://therevpc.blogspot.com/2012/03/backup-over-network.html") should be easy enough to follow. Hope it helps. it bypass windows shares and what not.

---

### Post by Mark Phelps on 2012-03-12
> **lrgmmc said:**
> That program look like it's mainly for grub 2. so if he's not dual booting i don't think it's gonna help much, and if its a windows error it's not going to fix that. 

Then you should have read it in more detail ... as it also works for MS Windows boot problems.

---

### Post by mastablasta on 2012-03-12
with original windows 7 CD you can fix the master boot record
 
additionally you can reinstall windows over current instalation. as long as you chose not to format the drive you data will stay on the disk. however you might need to arange shortcuts to some programmes.
 
furthermore this is actually a windows 7 issue :-P
 
but redobackup (based on Ubuntu) is designed for simple and easy backup of data (baremetal backup i.e bit by bit...).

---

### Post by jacklotsofstars on 2012-03-12
UPDATE: So I've somehow managed to get sharing via Windows Share to work, and have opened the shared folder on the working PC. I've already copied around 3GB of files to the working computer. But for the rest of it, (60GB), is there anyway I can transfer it quickly? or at least back it up online while I do a reinstall of Windows 7?

---

### Post by lrgmmc on 2012-03-12
not really. over the network backup is kinda slow.> Then you should have read it in more detail ... as it also works for MS Windows boot problems. it will not fix missing windows files. yes it can repair mbr. but if windows is missing files it wont help.

---

### Post by jacklotsofstars on 2012-03-12
it is very slow.... hah 283 KB/second.... 40.7 GB left to go.

---

### Post by Basher101 on 2012-03-12
just a thought...why not create a 100 GB partition, copy all your files over, just NOT touch it during install, then copy all the stuff back, delete it or use as storage..

interesting that no one has come up with this..

---

### Post by jacklotsofstars on 2012-03-12
> **Basher101 said:**
> just a thought...why not create a 100 GB partition, copy all your files over, just NOT touch it during install, then copy all the stuff back, delete it or use as storage..

interesting that no one has come up with this..
sounds like a good plan, but i have no clue how.

---

