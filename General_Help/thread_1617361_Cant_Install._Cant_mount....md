---
title: "Cant Install. Cant mount..."
date: 2010-11-09
forum: General Help
---

### Post by kamohammed on 2010-11-09
Ok. installing 10.04 fresh... 

Booted CD, select install Ubuntu

the logo is there... and after... a long while I got this error:
(initramfs) mount: mounting dev/loop0 on //filesystem.squashfs failed: Input/Output error Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
... 

on searching on the net, I got suggestions like maybe I lack memory (i Have 2gb...) 
and others stated it could be checksum error (though most re-assured that the checksum is ok and the burned image is perfect) 

What I havent got was a solution.

I installed 10.04 from the same CD on the same laptop successfully. Only difference was I had an older hdd before (that hdd failed so replaced with new one)... 

Any ... solutions? ... except holy candles and vodka?

---

### Post by Hippytaff on 2010-11-09
The live cd works? I mean ubuntu runs ok in the liveCD environment?

---

### Post by TheAnachron on 2010-11-09
I had the same issue, redownloading and reburning the iso fixed the issue.

---

### Post by regala on 2010-11-09
> **kamohammed said:**
> 
burned image is perfect


how do you check a burned image is perfect ? with your eyes ?
your experiment shows it's actually not perfect

br

-- 
Mathieu

---

### Post by Hippytaff on 2010-11-09
> **regala said:**
> how do you check a burned image is perfect ? with your eyes ?
your experiment shows it's actually not perfect
 
br
 
-- 
Mathieu
 
I think the fact that it worked previously suggested it was ok :-)

---

### Post by kamohammed on 2010-11-09
there is an online guide... (and somewhere in this forum) that shows you step by step how to do a check sum test... I cant remember it off hand, but it was done and compared with the checksum of the iso source... 

It checked out ok... Plus I read about others doing the same thing... and burning lke 10 cds/dvds/dvd-rw etc to see if it wasnt the burn or the media...

so... I just didnt want to type all the details... 

I will try the live CD... 
in the meantime i am donwloading 10.10... 

If all fails... i will try an install 8.04 and see if that works...

if all fails then... ... holy candles and vodka...

---

### Post by kamohammed on 2010-11-09
GOT IT TO INSTALL!!

we just had to follow instructions!

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 			**95 / 98 / ME / 2000 / XP / Server 2003 / Vista: Infra Recorder**

 		
 		 			
[LIST=1]
[*]Download and install [Infra Recorder]("http://infrarecorder.sourceforge.net/"), a free and open-source image-burning program.
[*]Insert a blank CD in the drive and select **Do nothing** or **Cancel** if an autorun dialog box pops up.
[*]Open Infra Recorder and click the 'Write Image' button in the main screen.
[LIST]
[*]Alternatively you can select the 'Actions' menu, then 'Burn image'.
[/LIST]
 				
[*]Select the Ubuntu CD image file you want to use, then click 'Open'.
[*]In the dialog box, click 'OK'.
[/LIST]


etc etc... there was a section "SHOW ME HOW"

I downloaded Infra Recorder (CD iso i had downloaded) and i used that to burn my cd... well.. IT IS INSTALLING RIGHT NOW XD!..... yays...

---

### Post by bazerka on 2010-11-09
the way i did it was i mounted the .iso on a virtual drive in windows. Than i opened Wubi that was in the cd (just explore the cd and open it) and in the wubi menu there is an option to install through windows. If thats what your lookin for at least... good luck!

---

