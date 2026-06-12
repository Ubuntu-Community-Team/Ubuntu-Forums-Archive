---
title: "How to increase root partition in ubuntu installed inside vista...."
date: 2010-11-17
forum: General Help
---

### Post by mailprashant07 on 2010-11-17
Hi,

I searched the forum but could not get the desired result. Any help will be highly appreciated.

PROBLEM- I am using ubuntu 10.10 installed inside Windows Vista. Now with every start up ubuntu gives a low space warning. I alloted 10 GB inside windows while installing ubuntu using wubi. Now it says only 34 MB space is free. Is it possible to increase the root size inside windows. My both OS are on C drive and it has about 15 GB free. I would like to allocate & GB to ubuntu. Please help.

Thank you

---

### Post by Megaptera on 2010-11-17
Hi,
I think this might help:

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by mailprashant07 on 2010-11-17
> **Megaptera said:**
> Hi,
I think this might help:

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

Thank you for ur response.....I will be thankful if you can put it in simple words......because I cant figure the way to resize root partition using wubi...I am using ubuntu for 1 yr now.....and done the following-

sudo apt-get clean

sudo apt-get autoclean

additionally I removed all openoffice progrrames except Writer...leaving a space of around 120 MB......which is still very less....

Thanks

EDIT- I think it does not support beyond 10.04 as mentioned (I am using 10.10).....

For the alternative method got the follwing message-

prashant@ubuntu:~$ sudo sh wubi-add-virtual-disk /home 15000
sh: Can't open wubi-add-virtual-disk
prashant@ubuntu:~$ 

Though I want to keep Ubuntu inside windows only.....but if nothing works any help will be appreciated

---

### Post by mailprashant07 on 2010-11-17
Moved file to home thne got the following result-


prashant@ubuntu:~$ sudo sh wubi-add-virtual-disk /home 15000
[sudo] password for prashant: 
Not enough free space (10861 MB < 15000 MB), aborting.
prashant@ubuntu:~$

---

### Post by mailprashant07 on 2010-11-17
I found that there is no answer yet for this question here--> [http://efreedom.com/Question/1-3697793/Increase-Space-Root-Ubuntu-Wubi](http://efreedom.com/Question/1-3697793/Increase-Space-Root-Ubuntu-Wubi)

.....really ???

Someone please answer since I dont want to reinstall the whole thing.....

Thank you

---

### Post by mailprashant07 on 2010-11-17
Rebooted to see 124 MB space remaining......any help will be appreciated......

---

### Post by bcbc on 2010-11-17
You tried to create a new /home virtual disk that was 15000 MB in size (15GB). You said in an earlier post that you only have 15GB remaining space on your computer. You can't use this all up creating a virtual disk or windows will have problems.

Also, you can't resize (increase the size of) the root.disk. LVPM allows you to create a copy of it. So it would create a larger virtual disk, and copy the entire current install to it. Then use it. i.e. you can't add to the current install by 5GB if you only have 10GB remaining.

I recommend moving your larger data files to the /host partition which is not part of the virtual disk e.g. move all your multimedia files there, if that's what is taking the space.

Also use the Disk usage analyzer to figure out where all your space is going (if you're not sure why you've used up 10GB already). You should run this from the command line (gksu baobab) and go into the preferences and deselect the host partition (windows) or else it will take forever to run.

---

### Post by mailprashant07 on 2010-11-17
Oh thanks for the response.....I think I should go for a fresh install with root having 15 GB of memory.......

Thanks again..... :)

---

### Post by nl4m on 2010-11-17
I am not sure if this will work, but you can try to move the virtual partition to an external HDD, or Flash drive. Boot into the Ubuntu LiveCD, make a virtual drive of how much ever GB's you want, mount both the external HDD/Flash drive and the newly formed virtual partition into the liveCD, then just use the command "CP -AX" (<all in small letters) to copy all the files from your old virtual drive to the new one. In theory this works. I have not tried it in real life. If it turns out not to work, please do not blame me :)

---

