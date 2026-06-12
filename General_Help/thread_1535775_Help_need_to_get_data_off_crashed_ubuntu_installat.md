---
title: "Help need to get data off crashed ubuntu installation"
date: 2010-07-21
forum: General Help
---

### Post by Dr Strangelove on 2010-07-21
Hi guys
First of al I'm a bit of a Linux novice. 

A few months ago I did a clean install of the unbuntu desktop which I used to run an internal website. The OS was installed on one hard disk and two other hard disks I setup as a mirrored raid. 

Now when I start the computer I get a GNU GRUB commandline interface and I can't seem to get my installation up and running again. I've tried some of the suggestions for GRUB issues however I can't even get ls to work (gives me an error).

I am at the point where I don't really care about the OS installation but would desperately like to get the data off the raided disks and also a few files off the boot disk. I can't seem to work out how to do this using a liveCD, if I open the disk utility, select the raid and click "Start RAID array" I get a "Not enough components available to start the raid" error. 

For the boot disk the major partition is a Linux LVM partition (and I assume the data I need is on that partition) however I cannot work out how to mount it.

I really hope you guys can help me as the information is rather important. I hope I have provided enough information for you to help me out here.

Many thanks
Jacob

---

### Post by gnik1 on 2010-07-21
You may have to troubleshoot the machine itself. Maybe there is a hardware problem that's preventing you from getting any further. 
Do you have another machine that you can add the drive to or maybe a usb adapter to connect it to that extra pc temporarily in order to access your data?

---

### Post by Dr Strangelove on 2010-07-21
I got a bit of help from a friend who mentioned that I could probably mount one of the individual array disks, and it worked. (silly me for not trying)

So have gotten access to the array data which was the most important.

-Jacob

---

