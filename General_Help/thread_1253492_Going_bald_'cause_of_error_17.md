---
title: "Going bald 'cause of error 17"
date: 2009-08-30
forum: General Help
---

### Post by DemonicInnocents on 2009-08-30
A while ago I installed Ubuntu 8.10 on my laptop, all was well for a couple of months until I just got sick of not being able to run all my usual Windows applications and tried to reinstall Windows XP Home (I know, I know, it's a stupid reason to want to go back to Windows). After Windows refusing to install I found that Ubuntu wouldn't work either now, so I put my Ubuntu 8.10 disk in and chose to reinstall it and start fresh again but it told me that it could not do the partition. By this stage I was getting extremely frustrated with it and just turned off the laptop and left it for a couple of weeks. Now whenever I try to boot my laptop I get the following message just after the POST screen:

GRUB Loading stage1.5


GRUB loading, please wait...
Error 17

This error is driving me crazy. I have tried searching the forums for a solution but they are all for people that are running both Windows and Ubuntu.

Any and all solutions will be very much appreciated.

Thanks in advance.

---

### Post by DFlame on 2009-08-30
Try installing Ubuntu again, but pay particular attention to the hard disk partitioning part. Instead of having it shrink a drive (to try and co-exist with another operating system), tell it to use the entire drive. This should remove any half baked Windows or Ubuntu installations from the system.

Note, that you'll lose any data on the laptop too, so don't do this if there's something vital you want from it.

If you don't manage to get it to go, note down any error messages and post back. If it does work, you may be interested in [WINE](http://www.winehq.org/about/).

Keep us posted :)

---

### Post by DemonicInnocents on 2009-08-30
I tried to install Ubuntu again but when I clicked on "Forward" at the keyboard layout I got an error that was just "??? ???".

Another bit of information... Before I tried to install again I found this tread that looks helpful [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368) but when I checked to see if I had what is required I have found that I don't have any of them including the grub file in the /boot folder and don't know how to fix it just in case this is the reason for my error 17.

---

### Post by SuaSwe on 2009-08-30
I wonder if the botched Windows installation perhaps messed up your MBR, causing this problem. 

Are you able to get into a live environment using your Ubuntu CD? If so, you can always go in there, save over anything on your broken Ubuntu drive that you want to keep to disk/USB drive, then try again for a reinstall. If you're not able to reinstall with this LiveCD, perhaps try burning another?

---

### Post by DemonicInnocents on 2009-08-30
I have tried installing from LiveCD and I still get the ??? ??? error in the same place of installation.

I have 3 Ubuntu disks 2 are 8.10 and aren't burnt (had them sent to me from America) and the third is a burnt copy of 8.04. I have tried all 3 and get the same error.

Also now when I start my laptop with the disk in I get the following message:

SMART Failure Predicted on Hard Dish 0: ST9100824ASTBD

WARNING: Immediately back-up your data and replace
your hard disk drive.    A failure may be imminent

Press F1 to Continue

Also when I go to the Live session I get literally get hundreds of media errors like "[   124.805075] (and then a whole heap of words, numbers and letter)" and I have no idea what they mean. (I don't know if this is of any significance)

---

### Post by Liolikas on 2009-08-30
>and I have no idea what they mean. (I don't know if this is of any significance) 
Kernel boot log. For kernel hacker it may provide very important info. If possible get video or sth of them and consult kernel skilled ppl (not newbie question for sure)

>SMART Failure Predicted on Hard Dish 0: ST9100824ASTBD
Is not much related to Ubuntu sad new may it mean look here:
[http://www.techsupportforum.com/hardware-support/hard-drive-support/115897-smart-failure-predicted-hard-disk-0-a.html](http://www.techsupportforum.com/hardware-support/hard-drive-support/115897-smart-failure-predicted-hard-disk-0-a.html)

---

### Post by DFlame on 2009-08-30
How old is this laptop and what model is it? Your hard drive is failing, as the SMART screen said. If your drive is failing then it would explain all the trouble you have been having with partitions, etc.

It looks like your computer will need repair before you can do anything further with it. Specifically, a new hard drive.

---

### Post by PorkyPie on 2009-08-30
I got that error, and i simply had to plug out a usb device and restart. I don't know whether this will help, but I would recommend a new HDD.

---

### Post by DemonicInnocents on 2009-08-30
I have an Acer Travelmate 8100 and I have no idea how old it is as my Father got it for me from a friend over in America.

If I have to get a new HDD for it I may as well just buy a whole new laptop.... Any suggestions? Haha.

---

### Post by yanceypd on 2009-08-30
Have you been able to capture the bios settings as the system boots?  If so try to disable smart boot and set first boot device to cd.  Might help get live cd started.

---

### Post by DemonicInnocents on 2009-08-30
The first boot device is CD-ROM and I can get into the Live session or LiveCD as some call it.

I think it's probably safer for me to just go out and buy a new laptop... I know it's a bit off topic but some help choosing a good laptop would be appreciated. :)

---

### Post by DFlame on 2009-08-30
Sure. What would you use the laptop for (anything it absolutely must have?), and what would you be willing to spend? That'll help us make some recommendations.

---

### Post by DemonicInnocents on 2009-08-30
Well I'm a gamer so I would want a laptop that would be able to handle good graphics also I love listening to music so one that can handle the bass of techno would be good.

As far as price goes $2,000NZD would probably be the max that I could afford being an I.T student.

I have found a laptop that I wouldn't mind getting but I'm not sure if it's any good as I have more knowledge of PC's then laptops, but here is the link for it anyway: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834115571](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115571)

---

### Post by DFlame on 2009-08-30
That looks pretty good to me. The laptop in my sig can get Fallout 3 running. The one you have linked to has an extra gig of RAM, double the graphics memory and a touch more juice in the CPU. It also has a "Tuba" kind of subwoofer built into it, the same as mine. From experience, this definitely improves overall sound quality but it can never be a match for a good sound system (obviously). I prefer headphones anyway :P

---

### Post by DemonicInnocents on 2009-08-30
So the one I chose is a good one then? And worth getting due to the overall performance and cheap price?

---

### Post by DFlame on 2009-08-30
It's got good reviews and I can't find anything in the spec that would be a letdown. If I were buying, I would be happy to come home with this :)

---

