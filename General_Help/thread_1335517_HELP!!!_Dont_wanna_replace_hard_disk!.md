---
title: "HELP!!! Dont wanna replace hard disk!"
date: 2009-11-23
forum: General Help
---

### Post by blakjak02 on 2009-11-23
I downloaded Ubuntu yesterday. I put the installation disk in and it was to the part where you size the partitions. I move the slier to give ubuntu a little more space (90gb or so) then i pressed forward. It loaded a little popup and i clicked cancel to think it over. It loaded and it had a loader bar thing and it said resizing partitions. I waited a good hour for it do to that. Then i went back up and was debating whether to turn it off. I dont know why, but i press Ctrl + Alt + Delete and it shut off. So i restarted. I installed it succesfully and i logged in and it looked cool :) but :shock: i had a message "hard disk failure" i clicked the little icon and it says my Hard disk (ATA Hitachi something) has many bad sectors. I didnt think much of it so i ignored it. Until i wanted to boot into Vista again. 
 
It loads the disk checker everytime i boot on vista and it gives me the chance to skip it so i skipped it. I pdid some stuff on vista and i booted into ubuntu and i alternated a couple times to do some different stuff. I didnt think much of it until i realizesd my computer might break, s i searched everywhere and i found out that it may be a bug. I dont know if mine is a bug or not, because it did it on vista. Is this a bug? How can i fix it if not? Can i leave it like it is, will it get worse? How much is a new HDD? Where can i get one? 
 
PLEASE HELP!
 
P.S. I know nothing of any commands or anything i just installed ubuntu because i heard it was good and easy to install.

---

### Post by fancypiper on 2009-11-23
Did you do a scandisk and defrag in Windows before you tried the install?  The re-sizing can take a goodly amount of time, I have heard.

For buying hardware, I like [NewEgg]("http://newegg.com/") and [Computer Geeks]("http://www.geeks.com/").

---

### Post by blakjak02 on 2009-11-23
No i didnt.

---

### Post by wilee-nilee on 2009-11-23
Stopping a partition re-size as you realize now is not a good idea. So it seems that your only problem is the reoccurring disc check. There is info all over the web on how to reset this here is one.
[http://maximumpcguides.com/windows-vista/stop-a-scheduled-disk-check/](http://maximumpcguides.com/windows-vista/stop-a-scheduled-disk-check/)

---

### Post by dcstar on 2009-11-23
> **blakjak02 said:**
> 
.........
I installed it succesfully and i logged in and it looked cool :) but :shock: i had a message "hard disk failure" i clicked the little icon and it says my Hard disk (ATA Hitachi something) has many bad sectors.
.........

There is a current bug with false notifications of disk errors on some types of hard drives on 9.10.

Find the other posts and see if there is a solution.

---

### Post by jeb800e on 2009-11-23
You may want to do a hard format, then install the OS of your choice. After that is done, you can run fsck (if using Linux or any Uxix or Unix-like OSes) or whatever program that does a file system and/or hard drive check for your specific OS.

---

### Post by CharlesA on 2009-11-23
Also: Please don't do a fsck on a mounted file system.

---

### Post by blakjak02 on 2009-11-24
Im getting mixed messages. What should i do? Ignore the warnings in ubuntu and vista because its a bug?  Format my computer and start again? 
Will i need to buy anymore stuff for my computer? Im kinda a noob when it comes to this.

Also, if i would format it, id back it up(of course) but id reinstall vista instead because i need it and ubuntu is much easier to install.

Please help me, id really do anything if i dont have to buy a new hdd. ( or a new computer).

---

### Post by wilee-nilee on 2009-11-24
So have you let the check disc happen then the auto restart with the Vista portion? The problem here is that your information is incomplete. So if you have let the check disc happen is it still doing the disc check every time to try to access vista. Lets try to get a hold of one OS at a time.

---

### Post by dcstar on 2009-11-24
As I have previously posted, there are a multitude of posts already in the forums reporting incorrect disk warnings just like the OP described.

If you disk suddenly has errors reported by the SMART system, then you need to be 100% sure that they are real errors and not just the ones caused by the current 9.10 bug.

---

### Post by wilee-nilee on 2009-11-24
> **dcstar said:**
> As I have previously posted, there are a multitude of posts already in the forums reporting incorrect disk warnings just like the OP described.

If you disk suddenly has errors reported by the SMART system, then you need to be 100% sure that they are real errors and not just the ones caused by the current 9.10 bug.

Does this keep the OP confused? 

If he has resized the Windows partition it will automatically run chdsk, Personally I am not advising him to do anything but trying to find out exactly what has been done. I posted a link on how to stop the chkdsk.

---

### Post by Grenage on 2009-11-24
Turn off SMART (such an ironic name) and see how your system does.  I'll wager it's fine.

---

### Post by blakjak02 on 2009-11-24
Dcstar, the main question i want to know is that if it is a bug or not. 
 
I performed the Disk check in the vista boot, it was taking a while so i went to sleep. I woke up to Ubuntu and i havent actually been on my computer since i shut it down that day so i dont know if it worked or not. Thank you alot from all the responses. 
 
I will format it if the disk check didnt work, but as i said before i will have vista and ubuntu still on there because i need vista. 
 
But would the vista Error Check have found and fixed the errors?

Update: Ok, so i just logged onto vista and it says my hdd is fine :). I hope it is. I will be logging on Ubuntu later. Thank you all sooooo much for all the help.

---

### Post by blakjak02 on 2009-11-24
Ok, so unfortunately the ubuntu warning stayed the same. Palimset(or whatever) told me i had many bad sectors and recommended i replace my hard disk. Vista doesnt do that anymore. Should just i assume its a bug in ubuntu?

---

### Post by dcstar on 2009-11-24
> **blakjak02 said:**
> Ok, so unfortunately the ubuntu warning stayed the same. Palimset(or whatever) told me i had many bad sectors and recommended i replace my hard disk. Vista doesnt do that anymore. Should just i assume its a bug in ubuntu?

If you search out the other posts you will probably find that is exactly what many other people have reported.

---

### Post by fancypiper on 2009-11-25
Perhaps this link will help.

[Monitoring Hard Disks with SMART]("http://www.linuxjournal.com/article/6983")

---

### Post by jeb800e on 2009-11-25
:.:comment erased:.:

---

