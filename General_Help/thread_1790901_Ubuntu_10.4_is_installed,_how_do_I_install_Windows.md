---
title: "Ubuntu 10.4 is installed, how do I install Windows 7 over it?"
date: 2011-06-25
forum: General Help
---

### Post by Haloman800 on 2011-06-25
I originally had XP on my desktop, it went corrupt so I used Ubuntu to get my files off it. Now I'm trying to install Windows 7 with a disc, but when I put in the disc, it doesn't show up like I put anything in. I went to Places > Computer, but it's not showing up.
 
I tried booting from disc, but it just boots up Ubuntu like normal..
 
It also looks like Ubuntu is in, what would be the equivalent of Windows "Safe" mode, all the graphics have been simplified, the bars on top and bottom are grey, and all the windows are more basic.
 
 
I've never had any experience with any Linux distro until this.. Please give me instructions on how to re-install Windows. Thanks.

---

### Post by haqking on 2011-06-25
> **Haloman800 said:**
> I originally had XP on my desktop, it went corrupt so I used Ubuntu to get my files off it. Now I'm trying to install Windows 7 with a disc, but when I put in the disc, it doesn't show up like I put anything in. I went to Places > Computer, but it's not showing up.
 
I tried booting from disc, but it just boots up Ubuntu like normal..
 
It also looks like Ubuntu is in, what would be the equivalent of Windows "Safe" mode, all the graphics have been simplified, the bars on top and bottom are grey, and all the windows are more basic.
 
 
I've never had any experience with any Linux distro until this.. Please give me instructions on how to re-install Windows. Thanks.


Windows installations are best dealt with in a Windows forum.

however is your BIOS set to boot to Disc ? and is it a Install disc ?

check this out [http://www.sevenforums.com/installation-setup/91611-trying-install-windows-7-over-ubuntu.html](http://www.sevenforums.com/installation-setup/91611-trying-install-windows-7-over-ubuntu.html) to see if it helps

also this might come in handy down the road [http://www.youtube.com/results?search_query=how+to+install+windows+7&aq=f](http://www.youtube.com/results?search_query=how+to+install+windows+7&aq=f)

i had a quick look but cant guarantee it is what you need so you will need ot read it but it should be staright forward as Windows likes to control over everything ;-)

---

### Post by trizrK on 2011-06-25
Did you try actually selecting the cd-rom in the boot menu?
If not try that..

---

### Post by ClientAlive on 2011-06-25
> **Haloman800 said:**
> I originally had XP on my desktop, it went corrupt so I used Ubuntu to get my files off it. Now I'm trying to install Windows 7 with a disc, but when I put in the disc, it doesn't show up like I put anything in. I went to Places > Computer, but it's not showing up.
 
I tried booting from disc, but it just boots up Ubuntu like normal..
It also looks like Ubuntu is in, what would be the equivalent of Windows "Safe" mode, all the graphics have been simplified, the bars on top and bottom are grey, and all the windows are more basic.
 
 
I've never had any experience with any Linux distro until this.. Please give me instructions on how to re-install Windows. Thanks.


If, you are 100 million percent certain you have all your personal data off of there; and, if, it is only a single boot system with the intention of staying a single boot system with the Windows install . . . If that, then:

You can run dban on it to completely wipe out the drive and then install Windows in the normal way.

(1) Make sure you are sure first though. 
(2) dban takes a long time. (For my 39 gb disk it took about 2.5 hrs)

May not be the prettiest solution but it would work if your circumstances allow it.

[http://www.dban.org/download](http://www.dban.org/download)
-------------------------

Edit:

Technically it wouldn't have to stay a single boot system, actually. Just that dbanning a sytem wipes everything out on the drive and so would not be suitable if you had another system in another partition that you wanted to keep.

---

### Post by Alwimo on 2011-06-25
The first thing to do is back up everything that is important to you and have, say, Ubuntu 10.04 on a disc on hand just in case Windows 7's installation doesn't work.

GParted is the GNOME Partition Editor and it allows you to change your computer to be compatible with Windows. It also gets rid of things.  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Download GParted and burn it to a disc. Put it into your drive, and then restart your computer. You may need to press a button, probably F12 or something, if you are instructed to on the first screen immediately after restarting.

Follow the prompts to set up GParted. There's one option that I just press Enter to get past as I don't understand it, without any issues.

Right-click on the pictures representing the partitions and delete all of them until there's just one of them. Then right-click and choose to format them, and when selecting the type, select NTFS instead of ext4.

Tell it you want to go through with it. 

You can then get out of GParted and put in your Windows 7 disc and it should now work.

---

### Post by Haloman800 on 2011-06-25
It looks like my entire HDD is partitioned in ext3/ext4... But wouldn't the disc at least be recognizable even if I can't run it? How do I partition part of it?
 
Also, every time I boot up, I have to unplug and plug in mouse, keyboard, etc. For some reason, it's not recognizing them when it boots up..

---

### Post by ClientAlive on 2011-06-25
> **Alwimo said:**
> The first thing to do is back up everything that is important to you and have, say, Ubuntu 10.04 on a disc on hand just in case Windows 7's installation doesn't work.

GParted is the GNOME Partition Editor and it allows you to change your computer to be compatible with Windows. It also gets rid of things.  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Download GParted and burn it to a disc. Put it into your drive, and then restart your computer. You may need to press a button, probably F12 or something, if you are instructed to on the first screen immediately after restarting.

Follow the prompts to set up GParted. There's one option that I just press Enter to get past as I don't understand it, without any issues.

Right-click on the pictures representing the partitions and delete all of them until there's just one of them. Then right-click and choose to format them, and when selecting the type, select NTFS instead of ext4.

Tell it you want to go through with it. 

You can then get out of GParted and put in your Windows 7 disc and it should now work.


Don't know why I forgot about that. Linux and Windoze use different file system types. That's prob why he's having those problems.

The gparted live route is probably faster too.

---

### Post by Haloman800 on 2011-06-25
Could you please post info on the gparted live route? I found some stuff on Google, but you might be able to find something more specific for my problem. Thanks.

---

### Post by westie457 on 2011-06-25
> **Haloman800 said:**
> I originally had XP on my desktop, it went corrupt so I used Ubuntu to get my files off it. Now I'm trying to install Windows 7 with a disc, but when I put in the disc, it doesn't show up like I put anything in. I went to Places > Computer, but it's not showing up.
 
I tried booting from disc, but it just boots up Ubuntu like normal..
 
It also looks like Ubuntu is in, what would be the equivalent of Windows "Safe" mode, all the graphics have been simplified, the bars on top and bottom are grey, and all the windows are more basic.
 
 
I've never had any experience with any Linux distro until this.. Please give me instructions on how to re-install Windows. Thanks.

First get another disc because if it is not showing in your file browser the disc is unreadable. With the new disc make sure it is burned as an ISO file.
Windows install discs are the only ones that override the settings in the BIOS and load giving you the option to press any key to boot from CD/DVD. If you do not see that then it has not been burned as an ISO.

Secondly you will probably lose your Ubuntu installation because the supplied partitioning tool is very clunky and recognises one file-system to install to - NTFS. So if you only have one partition on your hard drive then (temporarily) you will lose it. You can install Ubuntu or any other distro you want afterwards using a LiveCD or LiveUSB stick.

---

### Post by Haloman800 on 2011-06-25
I used ImgBurn to burn the 1st one x6, will that not work?
 
If anyone would be willing to help me over chat, my AIM is Haloman800

---

### Post by westie457 on 2011-06-25
Brasero usually works for me. Right-click the iso file in file-browser select 'Write to Disc.... So far no bad burns.

---

### Post by ClientAlive on 2011-06-25
> **westie457 said:**
> Brasero usually works for me. Right-click the iso file in file-browser select 'Write to Disc.... So far no bad burns.


Yeah, I think there's a number of reasons you can get a bad burn. I'd listen to westie457 about making sure you have a good disc before proceeding. Unless you have a second computer handy.

---

### Post by Haloman800 on 2011-06-25
The disc showed up on my laptop running Win7.. But I'll burn another copy with Brasero..
 
Would anyone please help me after that? I have fb, aim, msn, etc. I'd really appreciate it. 
 
It's my dads computer or I wouldn't be in such a rush to fix it..

---

### Post by ClientAlive on 2011-06-25
> **Haloman800 said:**
> The disc showed up on my laptop running Win7.. But I'll burn another copy with Brasero..
 
Would anyone please help me after that? I have fb, aim, msn, etc. I'd really appreciate it. 
 
It's my dads computer or I wouldn't be in such a rush to fix it..


Check your PM inbox brother.

Click: UserCP > look for the private message or PM link

---

