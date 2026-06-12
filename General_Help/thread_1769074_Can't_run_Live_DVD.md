---
title: "Can't run Live DVD"
date: 2011-05-27
forum: General Help
---

### Post by ecampbell on 2011-05-27
I purchased a new HPE-210f desktop PC with Windows 7 installed.  I wanted to install Ubuntu 10.04 x86_64 but have been unsuccessful in getting the Live DVD to run.  It give message about "Can't find image to boot", although it does boot the DVD and ask me the questions about language and keyboard then it goes to the "Can't find image to boot" message.  The system will successfully boot a Fedora 13 x86_64 discs and run live with  no problems.  I have also tried the Ubuntu 11.04 x86_64 release and I get the same result.  

The system consist of a Quad-Core AMD945 processor, 8G memory, 1 Tb hard drive, ATI Radeon HD5450 graphics card, hp BDDVDRW CH20L CD/DVD drive.  The bios doesn't support boot from USB.

I would really like to try Ubuntu so any help would be appreciated.

Thanks

---

### Post by linuxinstalledfromhdd on 2011-05-27
Have you updated your BIOS from the manufacture? How old is the MB?

---

### Post by ecampbell on 2011-05-28
The system is approximately 6 months old, bought off the shelf from HHGregg.  Don't understand how the Motherboard or the Bios could be the problem since I can run a Live Fedora session.  This seems to say to be that it is supported fully in Linux.

I don't understand what Ubuntu might be doing differently than Fedora which keeps it from booting the image that I know is on the DVD.   I didn't post earlier that I know the DVD is good since I can run live from it on another system.

Thanks

---

### Post by dandnsmith on 2011-05-28
I'd offer a tentative guess that there is an initially loaded image which is used to get the main stream going, and this isn't set up to handle DVDs (but will probably handle CDs).
Can you try to verify/disprove this conjecture?

---

### Post by ecampbell on 2011-05-28
If you mean download the 64 bit CD version of 10.04, I can try that.  I checked for BIOS update and HP hasn't issued any.  Let me get the  CD version and try that and I'll let you know.

Thanks for the reply.

---

### Post by linuxinstalledfromhdd on 2011-05-28
I would try running it with an Ubuntu 10.10 32-bit Persistant USB live stick of Ubuntu and see if the problem remains.

---

### Post by ecampbell on 2011-05-29
Thought I had tried this once before, anyway I downloaded the 10.04 64 bit image and tried it.   It boots; I get the Ubuntu splash screen with the dots that rotate turning red and then it goes to the Busybox ash shell with the following message:  "(initramfs) Unable to find a medium containing a live file system".

I have also tried the 10.10 and the 11.04 CD images from [http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/) with the same result.  I also tried the 32 bit version of 10.10 with the same result.

I don't understand Fedora boots and lets me run the live CD or DVD version with no problems on the same hardware.

---

### Post by linuxinstalledfromhdd on 2011-05-29
There is a review that shows that someone got it running (From Amazon reviews):

         **This review is from: [HP Pavilion Elite HPE-250f [B]Desktop** **PC** (Personal Computers)]("http://www.amazon.com/HP-Pavilion-Elite-HPE-250f-Desktop/dp/B003AOB1K6")[/B]       
  "I've been using this **PC** for a couple of weeks and tested on different tasks, always getting performance over the average. 
Windows 7 runs smoothly, all the 3D effects on. If you use **Ubuntu** or downgrade to xp64, even faster 
Tested **PC** games in full resolution, no lags found, "

Strange....

---

### Post by ecampbell on 2011-05-29
I was really wanting to give Ubuntu a spin.  I've used Fedora for several years and have tired of the constant update cycle.  It is just so strange the Fedora 64 bit comes right up and I can run from the Live DVD, also Knoppix 6.4 32 bit will boot and run no problems.

I must not be playing right with the God's because all I hear is how easy Ubuntu is to get going and I have failed miserably.

Thanks for listening and trying to help.

---

