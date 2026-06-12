---
title: "Please help. Mount HDD from live CD after 11.04 screwed everything up"
date: 2011-04-30
forum: General Help
---

### Post by teddy101 on 2011-04-30
11.04 was a total disaster. I can't get to anything, I have exams looming. I need to get my computer working. So I am going to do a total re install of 10.10. Much saver idea. however to do that, i need to get move my files over.

When I plug my external HDD in it appears in computer as USB drive. it can't be mounted and can't be accessed.

How do I get this working.

I am running from a live disk in one of the 9s i think 9.10.


thankyou

p.s I warn you, I am a noob/

---

### Post by Hedgehog1 on 2011-04-30
You may need to do this in two steps:

Using the 9.x liveCD, download the 11.04 or 10.10 or 10.04.02 ISO to your hard drive and then create a LiveCD/LiveUSB from that.

From the 11.x or 10.x LiveCD/LiveUSB, you can mount the USB drive using 'places' and save your data.

By the way, do you have a separate '/home' partition?  That can save you a step once you have the updated LiveCD/LiveUSB.


***The Hedge***

:KS

---

### Post by teddy101 on 2011-04-30
I have a pen drive. 10.x which i will install on my computer. I have some files that I would like to save before I wipe the harddrive. However when I click on the external HDD a error comes up saying 'unable to mount'. How can I mount the external HDD so I can save the files?

Sorry for not being clearer.

I have been up for way to long :L 

thank you.

Tom

---

### Post by matthewbpt on 2011-04-30
try mounting it using the command line. first do 'sudo fdisk -l' . This will give you a list of the disk drives plugged in and their partitions. Find the path for your external hard drive partition something like /dev/sdb1. Then do 'sudo mount /dev/sdX1 /mnt' where /dev/sdX1' is the partition of your drive. You should now be able to navigate to it from the file manager at /mnt/ .

---

