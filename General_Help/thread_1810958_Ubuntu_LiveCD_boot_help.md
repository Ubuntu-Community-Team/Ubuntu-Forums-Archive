---
title: "Ubuntu LiveCD boot help"
date: 2011-07-24
forum: General Help
---

### Post by belele on 2011-07-24
Hi, Im a bit of noob so please be gentle:P
 
I have an Acer 5920, and it has lost it's Windows boot properties. I dont want to do a factory reset as I want to get my info off the hard drive first.
 
Have downloaded Ubuntu LiveCD onto a CDROM, and change the boot order in the bios to make 'USB CDROM' first, but just get an 'Operating System Not Found' meesage on a black screen.
 
Have had a search, and see references to Grub.. but no idea what this is :confused:
 
Amy help in how I can install Ubuntu would be much appreciated.

---

### Post by tankertuff on 2011-07-24
I'm not an expert by any means, but I have destroyed, and repaired, a few sytems... :P

If you're trying to dual-boot Windows and Ubuntu, just go ahead and click the Ubuntu install icon and install it along side of Windows. There should be a point in the installation when you have a slider bar to choose how much disk space you want Ubuntu to take up and Windows should show up there too. DO NOT use the advanced partitioner unless you know what you are doing. I would just make sure if you do go in there you stay away from changing ANY NTFS partitions or disks you may have.

If you're trying to fix the boot loader, and you want to just keep windows, also try UltimateBootCD. Great tool, and can help with your grub problems too!

I didn't quite get the total gist of the question, but I hope this helps, if it's not booting off the live cd, make sure you don't have any camera cards or anything else plugged in when you boot.



**edit- I just noticed you said "USB CDROM" . it shouldn't be the USB option. Should say something about super-multi, or 8x... unless you have a CDROM attached by USB cable... ***

---

### Post by belele on 2011-07-24
Thanks tankertuff.
 
Problem is I cant get it to load up at all, just get the lack screen of death with cursor when it tries to load.
 
Nothing is plugged in at all, and have edited the boot preferences.
 
I can get to the command prompt screen by hitting F8 at start up, which comes up with a 'Repair Computer' option... Are there any commands I can put in to manually boot from the CDROM?

---

### Post by wildmanne39 on 2011-07-24
Hi, from the message you got it sounds like you do not have a good livecd. When you download ubuntu and burn the cd you need to use infrarecorder or a program like it to burn the iso image.

All the instructions are on the download site. If you download with a bitorrent it will check the files as it goes along to make sure they arfe good.
[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by Quackers on 2011-07-24
Are you using a USB cdrom, or an inbuilt cdrom drive? If it's inbuilt there should be a bios option for an internal cdrom drive.

---

### Post by belele on 2011-07-24
Thanks for the ideas :KS
 
> **wildmanne39 said:**
> Hi, from the message you got it sounds like you do not have a good livecd. When you download ubuntu and burn the cd you need to use infrarecorder or a program like it to burn the iso image.
 
 
 
I used Imgburn to put it onto a CD, and during the process it verified OK.  I even put it into my work lapptop, and when I go to the drive it has all the necessary files (rather than just a single image, which I believe means it didnt work).
 
> **Quackers said:**
> Are you using a USB cdrom, or an inbuilt cdrom drive? If it's inbuilt there should be a bios option for an internal cdrom drive.
 
I think this may be it :P:P:P ... had the wrong one selected.
 
Loading up with a purple screen so I think it might be right... fingers crossed it's not too hard to get my info off the c drive now.
 
Will post how it goes... thank you soooo much!!

---

### Post by gigenieks on 2011-07-24
[QUOTE=belele]
I have an Acer 5920, and it has lost it's _Windows boot properties._
[/QUOTE]
What you mean with words "Windows boot properties"? You can't load Windows?

> 
Have downloaded Ubuntu LiveCD _onto_ a CDROM

"Onto"? You mean **burned as image**?

> 
Amy help in how I can install Ubuntu would be much appreciated.

Please read following --->
[LIST=1]
[*][this]("https://help.ubuntu.com/community/BurningIsoHowto")
[*][then this]("https://help.ubuntu.com/community/Installation")
[/LIST]

[QUOTE=belele]
Problem is I cant get it to load up at all,
[/QUOTE]
Seems like you did **not** make that CD **bootable**!!

> 
I can get to the command prompt screen by hitting F8 at start up, which comes up with a 'Repair Computer' option...

This is absolutely unrelated to Live CD's and Installing Ubuntu!!

---

### Post by Quackers on 2011-07-24
You're welcome, looking good now :-)

---

### Post by tankertuff on 2011-07-24
> **Quackers said:**
> Are you using a USB cdrom, or an inbuilt cdrom drive? If it's inbuilt there should be a bios option for an internal cdrom drive.

That's what i was thinkin... still not clear what's going on but his model has a built in DVD SuperMulti drive. He said he enabled USB CDROM in BIOS menus so I'm thinking it's a wrong selection in BIOS as well.

---

### Post by belele on 2011-07-24
> **Quackers said:**
> You're welcome, looking good now :-)
 
Yep, looks like I got most of the essentials onto an external HDD... any suggestions where i can find my outlook .pst files as well?

---

### Post by tankertuff on 2011-07-24
there might be something in the forums. :D

---

### Post by Quackers on 2011-07-24
I don't use Outlook. Is there an export option?

---

### Post by belele on 2011-07-24
Cheers, found it.. now doing a factory restore so all is good.
 
Thanks for the advice!

---

