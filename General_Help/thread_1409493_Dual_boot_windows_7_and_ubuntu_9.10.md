---
title: "Dual boot windows 7 and ubuntu 9.10"
date: 2010-02-17
forum: General Help
---

### Post by sieck on 2010-02-17
hey everybody. (im from denmark so im not good at englinsh)
i really so badly want to dual boot windows 7 and ubuntu 9.10 og just want windows to play on and ubuntu to everything else.. because we all know that windows sucks... 
but my problem is that i want til partition som space for ubuntu off cause 
but when im trying to do that it says something like "theres not enough space to do it" and theres 910 GB free space... and i have no idea what to do..
thank you for your help
regards. 
sieck

---

### Post by OrangeCrate on 2010-02-17
These dual booting instructions should be of help...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Yvan300 on 2010-02-17
If windows is already installed then all you have to do is right click computer and click manage. Then i thinking you double-click storage and a partitioner comes up. Resize your windows partition to make space for ubuntu and you're all set. Sorry for the lack of instructions. Haven't used windows in 6 months :)

---

### Post by jsriz on 2010-02-17
Havent been onto windows 4 a long tym but i believe computer management utility creates primary partitions.
You can have only 4 primary partitions.
Try backing up and deleating any small partition
If that was not not your problem jus try after defraagment

if you don want 2 worry about partitioning jus use the install ubuntu beside windows during the installation of ubuntu 
There is also install inside windows option (not preffered as i don like windows:p)

---

### Post by sieck on 2010-02-17
when i wanna creat a new partition i am doing that on windoes like your guys said.. but yes i do have 4 partitons.. so that must kinda be the problem

---

### Post by wilee-nilee on 2010-02-17
In the Administrative W7 type disk management in the search in start and use the virtual partitioner to adjust, but 1st defrag your computer completely. Here is a very good free defragger. 
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)
You also want a cleaner for the extra files MS saves that you don't necessarily need.
[http://www.ccleaner.com/](http://www.ccleaner.com/)

Since you have multiple partitions now, it is probably attached to a reformat partition. So you may want to check about if you ever have to do a shredd/reformat if removing partitions is going to impede a reformat.

So also all you need to do with the W7 partition adjustment for the Ubuntu install is leave a blank space for the install to format.

I might also add here that it is important to use the W7 partitioner to adjust W7 gparted and others are not advised for changing Vista, or W7 partitions.

The W7 partitioner will also resize XP partitions on the computer without a chkdsk start.

---

### Post by sieck on 2010-02-18
i have allready defragt it 2 times . and i got my computer for 4 days (completly new) so i dont think theres much trash files,
my harddrive is setup like this

1: no letter: OEM-partition 1 GB

2: BOOT C: Boot sidefil crashdump primær partition 910 GB

3: RECOVER D: primær partirion 20 GB

4: System reserved : system arkiv primær partition 100 MB

---

### Post by sieck on 2010-02-18
primær = primary

---

### Post by terrapin893 on 2010-02-18
Hm, I wonder whats on the OEM partition of 1 GB . . . . . 

Here is what I did.  I bought a new computer with Windows 7 on it, and a lot of OEM junk.  Nowadays you just dont get copies of discs with windows when you buy a windows computer.  A real shady move, if you ask me.  

So I torrented a copy of Windows 7 and then used it to wipe everything out and reinstall a base copy of Windows 7, with one partition.  I was even able to use my Windows product key on the side of my computer, so my version of Windows 7 is activated and legitimate.  

After that I used the Windows partitioner to resize the main harddrive down to about 460 GB ( of 1 TB ).  Thats as low as it would let me go, but heh, it works for me.  

Lastly I just installed ubuntu 9.10 on the other partition and Ive been doing fine ever since.  

Thats what I would recommend.  Why does a computer come with four partitions?  Is that really necessary?

---

### Post by sieck on 2010-02-18
it seems like the only option i have. thow im not to happy for that selution.. i better get i friend to help me if im going to do that.. 
thank for your help

---

### Post by terrapin893 on 2010-02-18
I would say its either that or get rid of one of those partitions that you have going on.

---

