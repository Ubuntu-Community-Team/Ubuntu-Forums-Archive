---
title: "freeze on &quot;starting hotplug subsystems&quot;"
date: 2006-02-27
forum: General Help
---

### Post by liger13 on 2006-02-27
to start off-> this is the first ever linux version i have ever tried, and i have never used linux. i installed ubuntu 5.10, and when i load it it freezes on "starting hotplug subsystems."

there seems to be a few threads about this already, talking about put this code in here and blah, blah, 
i have no idea what these are talking a bout!

can anyone talk me through this?

---

### Post by dcstar on 2006-02-28
[QUOTE=liger13]to start off-> this is the first ever linux version i have ever tried, and i have never used linux. i installed ubuntu 5.10, and when i load it it freezes on "starting hotplug subsystems."

there seems to be a few threads about this already, talking about put this code in here and blah, blah, 
i have no idea what these are talking a bout!

can anyone talk me through this?[/QUOTE]
It would probably be better to post in the Installation and Upgrade Help forum, with details of what PC hardware you have so those people have some chance of being able to give you the right solution:

[http://ubuntuforums.org/forumdisplay.php?f=94](http://ubuntuforums.org/forumdisplay.php?f=94)

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]to start off-> this is the first ever linux version i have ever tried, and i have never used linux. i installed ubuntu 5.10, and when i load it it freezes on "starting hotplug subsystems."

there seems to be a few threads about this already, talking about put this code in here and blah, blah, 
i have no idea what these are talking a bout!

can anyone talk me through this?[/QUOTE]

"If your computer has onboard video, make sure to set "onboard",not pci in your BIOS setting ,im not sure i think the option was under advanced tab.Thats all i had to do to get "my system"pass the "hotplug SubSys" message.For some reason my BIOS set my onboard video reference to pci,it should be set to onbard since thats what i have, onboard video.(theres an options to set video to  pci,onboard...ect in bios ).

---

### Post by K.Mandla on 2006-02-28
I've had this problem in some older laptops. In my case it was an older model that was trying to probe the PCMCIA ports, and invariably it happened after a warm boot. I was able to circumvent the issue by powering down completely between restarts.

The only other thing I can think of is to try CTRL+C at a freeze, and see if it will snap out of it. No promises, though. Good luck.

---

### Post by liger13 on 2006-02-28
i have an onboard video, but it is disabled because i use a pci geforce 5200 card. it works fine in windows xp. (i have a dual boot system) and the base system is a dell 2350. with 768 mg of ram.

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]i have an onboard video, but it is disabled because i use a pci geforce 5200 card. it works fine in windows xp. (i have a dual boot system) and the base system is a dell 2350. with 768 mg of ram.[/QUOTE]

Make sure in your BIOS when it ask(in question form)for Video "location" you put PCI. Even tho you might of disabled with "Device manager",Bios setting can overide in "some instances".

I Also dual boot but i use a two monitor setup, so i have my onboard video activated.

:-k .....let me see, try this,its only a test:You could disable pci and enable
onboard (to see if Ubuntu will boot,so you can see and hear ubuntu laod up :p

---

### Post by liger13 on 2006-02-28
k thnx ill try that.

---

### Post by liger13 on 2006-02-28
k, when i switch to the integrated graphcis it works fine, but when i switch back to the pci it hangs on the hotplug stuff.

---

### Post by liger13 on 2006-02-28
anyone know how to fix this? 

and another question-> 

whenever i log in and try to acces my hard drive it says i dont have enough acces to view it. anyone know y?

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]anyone know how to fix this? 

and another question-> 

whenever i log in and try to acces my hard drive it says i dont have enough acces to view it. anyone know y?[/QUOTE]

We need more info! are you trying to access your xp partition ? are you trying to gain access with Disk manager,File Browser,Terminal? if terminal type, sudo -s -H and put in your password,If your xp is on one partiotion then i believe there are issues with accessing ntfs partitions(the issue can be worked around tho)when i had the nfts issue i chose to just make a few f32 partitions ,one called Data,Workarea,ect.... and just kept winxp on a small 5 gig   partition,Ubuntu has no issues playing your movies ,mp3 ,data files stored on f32.

BTW, is there a  "disk drive icon"on your desktop and when you click it it gives the no access message?


As for your Hotplug problems= boot to your Bios settings (restart and hold f1)
when at Bios screen go to Advanced tab,scroll down with arrows to highlight "PRIMARY VIDEO ADAPTER " set it to "ONBOARD" by using  "PAGEUP, PAGE DOWN" buttons on keyboard.I have a two card system and had the same hotplug problems but the above solved it "on my system".

              \\:D/  hope for the best.

---

### Post by liger13 on 2006-02-28
the acess thing is->
after ive logged on, there is a harddrive icon on the desktop, i double click on it, and the error comes up, saying i dont have acess to it.

ubunto is installed on a hd that is partioned to 2 drives. one has windows on it and the other has ubuntu. i think it is ntfs.

with the video adapter thing. whenever i do that it only uses the onboard graphics and not the pci card

---

### Post by liger13 on 2006-02-28
can i have a partition thats ntfs and one that fat32 on the same drive? and can i switch it without having to reinstall?

---

### Post by liger13 on 2006-02-28
i just looked at partition magic and it says that the partition is a linux ext3. dono what that means though

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]the acess thing is->
after ive logged on, there is a harddrive icon on the desktop, i double click on it, and the error comes up, saying i dont have acess to it.

Exactly!its Nfts,this link should answer and hopefully solve the accessing NTFS issue:  [http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems](http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems)

Now the hotplug thingy ,did you enable both onboard and pci card  in device manager?

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]can i have a partition thats ntfs and one that fat32 on the same drive? and can i switch it without having to reinstall?[/QUOTE]


Yes you can have ntfs and fat32 on one drive(one partition ntfs and others fat32 .Depending on how full your drive is,i would lets say squeeze ntfs to 5 gigs,with the rest of free space i would create 1 or 2 (or 3 depending on your needs)fat32 partition,use partition magic but dont use partition magic  to create linuxfile systems.u can  use Ubuntu to do the partitioning also or a Live Cd.

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=liger13]i just looked at partition magic and it says that the partition is a linux ext3. dono what that means though[/QUOTE]


Your Ubuntu is on ext3 filesystem ,yes.
xp should be ntfs.

what size hard drive are you using and what are the partition sizes your using for windows and ubuntu? and is your xp partition full or is there free space?

---

### Post by liger13 on 2006-03-01
these are my partitions:
hard drive one
-> 26.6 gig ntfs for windows xp
-> 22 gig linux ext3 for ubuntu

external
-> 158 gig (dono)

is there a way for linux to be able to read ntfs?

and for the graphics i am not able to have both the pci and onboard turned on at the same time.

---

### Post by liger13 on 2006-03-01
dono if this will help. 
in the bios this is what i do.
advanced->peripheral config->primary video adapter (there isnt a second one)
  then i can either select pci or integrated. (not both)

---

### Post by DOtSlaSHuCantCME on 2006-03-01
[QUOTE=liger13]dono if this will help. 
in the bios this is what i do.
advanced->peripheral config->primary video adapter (there isnt a second one)
  then i can either select pci or integrated. (not both)[/QUOTE]

OK..good!  we want to put the" primary video adapter" as  Integrated.

this link will help you solve the harddrive access question:[http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems](http://wiki.serios.net/wiki/Accessing_NTFS_and_FAT_filesystems)

---

### Post by liger13 on 2006-03-01
yah but when it is set to integrated-> i cant use the pci, and with that i have to run a 19 inch moniter in 1024-768. 
and thnx for the site:-D

---

### Post by liger13 on 2006-03-02
bump

---

### Post by DOtSlaSHuCantCME on 2006-03-02
[QUOTE=liger13]bump[/QUOTE]




Sorry i couldnt get the issue fixed :(   
When u get to hotplug problem press ctrl-D
try it and see what happens.

---

### Post by liger13 on 2006-03-02
i tried ctrl-d and nothing happened. i hope somone else can solve my problem:-?

---

### Post by DOtSlaSHuCantCME on 2006-03-02
[QUOTE=liger13]i tried ctrl-d and nothing happened. i hope somone else can solve my problem:-?[/QUOTE]

Well! for now just keep going foward(learning about Ubuntu),might be a pain having to disable and enable the Vidcards , but at least your still moving ahead.

Do you have Automatix set up?

---

### Post by liger13 on 2006-03-02
i have no idea what that is.
i have my moniter pluged into both cards at the moment, so i dont have to go behind my computer to switch them. but its still a hassle and the onboard is really bad. :(

---

### Post by DOtSlaSHuCantCME on 2006-03-02
[QUOTE=liger13]i have no idea what that is.
i have my moniter pluged into both cards at the moment, so i dont have to go behind my computer to switch them. but its still a hassle and the onboard is really bad. :([/QUOTE]


Oh you will love it  [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

it installs many program for you without needing to go here and there, its a must check it out.

---

### Post by liger13 on 2006-03-02
i cant figure out how and were to install it.

---

### Post by DOtSlaSHuCantCME on 2006-03-02
[QUOTE=liger13]i cant figure out how and were to install it.[/QUOTE]


I looked and did not find the Download thread for automatix, but u can use this link to install quite a few things.

[http://www.ubuntuguide.org/#gainrootwithoutlogin](http://www.ubuntuguide.org/#gainrootwithoutlogin)

---

### Post by liger13 on 2006-03-02
k thnx

---

### Post by liger13 on 2006-03-04
i had to reformat my comp because of alot of issues and such. though now when i reinstalled ubuntu, i was able to use the ritgh screen rez on my onboard graphics. but the pci card still doesnt work.

---

### Post by DOtSlaSHuCantCME on 2006-03-04
[QUOTE=liger13]i had to reformat my comp because of alot of issues and such. though now when i reinstalled ubuntu, i was able to use the ritgh screen rez on my onboard graphics. but the pci card still doesnt work.[/QUOTE]


Wazup! :)    have a look at your  /etc/x11/xorg.conf file ,to see if your pci card is listed,you will be spending a" little time" in x11 and messing with your xorg.conf, to get your monitors,"video cards" to function.

---

### Post by liger13 on 2006-03-06
anyone know how to disable hotplugs? or disable only the pci hotplug system? or how to fix this problem?

---

### Post by DOtSlaSHuCantCME on 2006-03-07
[QUOTE=liger13]anyone know how to disable hotplugs? or disable only the pci hotplug system? or how to fix this problem?[/QUOTE]

I dont recommend this as a first step,iwould read about hotplug to make sure if i disable it no other part of my system is damaged,with that said "use Synaptic Package Handler" and install "sysv-rc-conf"(put it search field in synaptic ),after it is installed type"sysv-rc-conf" in a terminal ,once program starts,use ctrl+n to navigate to "hotplug" entry (they will be 2 entry), use arrow keys to go entry and then use spacebar to clear hotplug entry,when done press q to quit, reboot pc and cross fingers.

PS. you have to be super user , so type "sudo -s -H"  in your terminal,then type  your password,and do above steps.

---

### Post by liger13 on 2006-03-07
k thnx. im currently at school so ill try it when i get home. :)

---

