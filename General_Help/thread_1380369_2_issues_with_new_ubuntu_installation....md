---
title: "2 issues with new ubuntu installation..."
date: 2010-01-13
forum: General Help
---

### Post by BA_UO on 2010-01-13
I just installed ubuntu yesterday,(dual boot, vista was there first) and from what I can tell everything went fine except for these two issues that have arose:

1. 
Ubuntu boots fine every time, but when I try to boot vista, it seems to be slower, and sometime freezes up.  

It also always wants to go through the automatic chk disk procedure, and from what I could tell, there are no errors once the chk disk is done and the computer just restarts and I have to attempt to boot vista again.  

Is this normal? Should I manually hit a button to skip the chk disk, or let it run through?

2. 
I have an HP dv6000 desktop, and it wont recognize my wireless network at home.

I ran the command (lspci -v less) which is posted to display my wireless card type (sorry if my terminology is not perfect) and her is what was displayed:

Broadcom Corporation BCM43111 802.11b/g WLAN

I'm sorry if the information to help me connect to my wireless when running ubuntu is already posted, I have done some digging around and have come up short.

Thank you very much to anyone who takes the time to help an Ubuntu N00b! :D

BA

---

### Post by howefield on 2010-01-13
> **BA_UO said:**
> I have an HP dv6000 desktop, and it wont recognize my wireless network at home.

I am pretty sure I have that laptop, and as long as you can connect wired to your router, you'll be able to get the driver using System > Administration > Hardware Drivers.

Are you able to do that ?

---

### Post by BA_UO on 2010-01-13
Correct me if what I am saying makes no sense at all, but I am pretty sure that I did that and got a msg that was approximately like "there are no proprietary drivers"...that isnt exact, but what I can remember!

Should I try to re-load my ubuntu system and go through those menus again?

---

### Post by BA_UO on 2010-01-13
I totally mis-read what you wrote, sorry!

Did you mean go ahead and plug my laptop into the router with an ethernet cable, and then go through the menus that you listed so the system can recognize the card?

---

### Post by howefield on 2010-01-13
Yes, that was what I was saying.

I just checked my laptop, it is the DV8000, but I think it is the same wireless, any time I reinstall Ubuntu on it, wireless doesn't work out of the box. 

By connecting the laptop to the router with an ethernet cable to get an internet connection, I am then able to do a sudo apt-get update in terminal and get the drivers via Hardware Drivers.

---

### Post by BA_UO on 2010-01-13
Howfield, 

Thank you for the quick replies!

I have a class/Lab from 5:30 until 8:30 tonight, but I will be sure to post results as soon as I can!

To the rest of the UBUNTU community: any advice to deal with my slow vista boot ups etc.?

THANKS!

BA

---

### Post by gandgcomputer on 2010-01-13
I've got a similar problem.

My Ubuntu/Windows 7 dual boot Gateway laptop wants to run chkdsk every time I boot to Win 7. :(

The Gateway touch pad also quit working in Windows 7 after Ubuntu resized the Windows partition to install itself, the touch pad was working just fine before. :(

I also dual booted my Acer Aspire laptop with Ubuntu and Win7. Win7 ran chkdsk just once and all the hardware works on the ACER in windows after the Ubuntu install. :D

---

### Post by BA_UO on 2010-01-14
I am on my UBUNTU system right now, and have it connected by hard wire to my modem...I tried searching for drivers to install again, but it is giving me the same "no proprietary drivers" messege.

Can anyone help me!?

Also, any way to stop vista from wanting to run chk disk at every vista boot?

Thanks!

BA

---

### Post by TBABill on 2010-01-14
Have you enabled the non-free repositories? And enabled proprietary devices before, such as for your video card? You may not find the proprietary driver without first enabling the non-free repository. If you need help with that, post back.

---

### Post by howefield on 2010-01-14
... and done an update.

From a terminal, (Applications > Accessories > Terminal) type

```
sudo apt-get update
```

You probably have done that, but just in case :)

---

### Post by Leppie on 2010-01-14
you could check this thread: [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by BA_UO on 2010-01-14
This will show my true n00bness to Linux and Ubuntu...but I did not do the update using this command: sudo apt-get update

I just ran it now, and the drivers have been recognized...I will download them, restart the system and be back with an update.

Thanks again everyone!

---

### Post by BA_UO on 2010-01-14
Wireless is up and running! 

Thank you everyone!

If there are any suggestions about the chk disk running at vista boot up, please send them along.

Veterans/mods, should this be marked as solved now or wait for chk disk comments?

Thanks!

---

### Post by howefield on 2010-01-15
> **BA_UO said:**
> This will show my true n00bness to Linux and Ubuntu...

Like everything else, it's only easy when you know how,  keep asking the questions. ;)

> If there are any suggestions about the chk disk running at vista boot up,

I've only seen this happen with windows running chk disk once, not every time it starts, in the way you seem to have it.

Were it mine, I'd load up windows and run Partition Magic (or similar) to see if it complained about the way partitions were set up, ect. 

> Veterans/mods, should this be marked as solved now or wait for chk disk comments?

It is often best to make a new thread for each question/topic, 2  questions = 2 threads, (unless the questions are closely related). You're more likely to get maximum help that way, as one question may get "lost" as another gets answered, and also might be best suited in a different section of the forum, where other potential respondents may lurk. 

Also helps people searching for the same answers to find "clean" threads.

---

