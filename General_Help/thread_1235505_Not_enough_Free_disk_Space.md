---
title: "Not enough Free disk Space"
date: 2009-08-09
forum: General Help
---

### Post by ColombianBootloader on 2009-08-09
hi there :)

well, I just install ubuntu 9.04, and I did it as a dual boot installation. I have windows XP professional (which I can not get rid of it!!! the pc is not mine!!)I could not defrag the pc before installing Ubuntu, because I did not have the password at the time for XP. 

Well, I plug the pc to the net and the Update manager found a few files to upgrade, the problem that I have is that as soon as I hit *Install Updates* there is a *Not enough free disk space*

I thought that it was a problem of space, then I got the password and I did the defrag to the hard disk, I have an extra 40G of free space but still the message is there. it says the following. 

*The upgrade needs a total of 390M free space on disk '/'. Please free an additional 234M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'*

Does anybody knows how to solve this problem?? 

Cheers:)

---

### Post by Kbahamut on 2009-08-09
How much disk space is allocated to your ubuntu?

---

### Post by drs305 on 2009-08-09
There is the chance your install tried to put Ubuntu in a 2.3 - 2.5GB partition, which is too small. You can check with:
```

df -H | grep /dev/

```
Check the results to see if / is about 2.5GB and almost full.

If it is too small, here are two guides I wrote that will help. The first will tell you how to reinstall and get a properly-sized / partition. 
[_2.5 GB System Partition - What Went Wrong?_]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")
Be sure to review the attached snapshot in the post so you can see what to do in Step 4 (Partitioning).

This one will tell you how to resize Windows and expand your / partition. This might be preferable if you have already installed a lot of extra apps or customized the installation to your liking. It will probably take just as long as a new install would.
[ _Expanding an Ubuntu System Partition_ ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by martinbaselier on 2009-08-09
it's better to just use **df -h** without grep, this will show the complete table, including headers.

---

### Post by Barafu Albino Cheetah on 2009-08-09
Fix up your theory before you mess up your disk, friend! Windows Defragmenter (any) can'not affect ubuntu partition at all. They live in different partitions, and share different space. You may use up all space for ubuntu, and still lots of it for windows.    
Redscript pages say - don't do any partitioning unless you surely know what you do.  

Show us output of sudo fdisk -l /dev/sda (if your disk is /dev/sda, of cause)

---

### Post by ColombianBootloader on 2009-08-10
hi there Guys

Well, I just want to say thank you for that. I already fix it ,thanks so much ds305 I just followed your guide and it is crystal clear to understand!!! If there is something that I love about this forum is how quick you can get a help. 

Cheers mate

:)

---

### Post by Dispenser on 2009-10-18
My issue is similar but when I execute 
```
df -H | grep /dev/
```
I get...
```
/dev/sdb5              24G   23G   45M 100% /
```

I'd like to just fix it without having to reinstall.  Will that guide help me too or is this different because I already have space there?

---

### Post by drs305 on 2009-10-18
> **Dispenser said:**
> My issue is similar but when I execute 
```
df -H | grep /dev/
```
I get...
```
/dev/sdb5              24G   23G   45M 100% /
```

I'd like to just fix it without having to reinstall.  Will that guide help me too or is this different because I already have space there?

Dispenser,

Your disk is full - obviously not because the partition is too small. The most common reasons, other than putting in too much data/audio/video into /home is backups saved to the wrong partition, large log files, and undeleted trash.

I'd start by going through this guide on finding what's taking up the space:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by yeeeev on 2009-10-18
What you could do (just for the sake of the update), is to mount an external USB drive as /var/cache/apt/archives (you would have to mount it using sudo and add a "partial" directory to it).

I used that to make it through an update process on a system with not enough space to store all the update packages.

---

### Post by Dispenser on 2009-10-18
Thank you for your help and your amazing tutorial.

Turns out the problem was in telling the installer to copy over settings from windows.  It ended up copying my downloads folder from My Documents and there were some large files in there.

Delete Delete Delete and, ahhh space.

---

### Post by bill23 on 2010-09-15
Hi I'm bill23,

I am having the same problem and this is what I got using the code   
df -H | grep /dev/

/dev/sr0               734M   734M      0 100% /cdrom
/dev/loop0             705M   705M      0 100% /rofs
none                   525M   222k   525M   1% /dev/shm

Does this tell you that I have a really small imprint or what?

bill23

---

### Post by drs305 on 2010-09-15
> **bill23 said:**
> Hi I'm bill23,

I am having the same problem and this is what I got using the code   
df -H | grep /dev/

/dev/sr0               734M   734M      0 100% /cdrom
/dev/loop0             705M   705M      0 100% /rofs
none                   525M   222k   525M   1% /dev/shm

Does this tell you that I have a really small imprint or what?

bill23

Bill, those results look more like what I'd expect from the LiveCD with no other partitions mounted...

**df** only reports on mounted partitions, so using the LiveCd you would have to mount any partition you wanted to get a report on.

---

