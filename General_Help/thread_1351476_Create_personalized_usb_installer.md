---
title: "Create personalized usb installer"
date: 2009-12-10
forum: General Help
---

### Post by spydeyrch on 2009-12-10
I have an idea on how to do something but would like everyone's input on possible issues and possible solutions to those issues, please.Any input would be extremely helpful. Thank you!
 
**My idea:**
 
For some time now I have wanted to create a USB flash drive that I could run a live version of ubuntu on, one that would allow me to keep my files (docs, pics, videos, **apps, settings**, etc) and access them once I booted off of the USB flash drive.
 
I know that I can create a bootable usb flash drive using several different methods. My preferred is [Unetbootin]("http://unetbootin.sourceforge.net/"). It is simple, fast, efficient. Although this allows me to have a live distro on my usb flash drive, it does not place a persistent file on the flash drive to store my changes/files/etc.
 
I also know that I can use the built in usb installer from within the ubuntu system. I believe that it is under the system menu somewhere. I have used it on rare ocassions. This installs a persistent file which allows me to have my files (docs, phtos, videos, etc) on the usb drive and access them when I boot off of the usb flash drive.
 
The only issue that I have run into is that I can not update ubuntu while I am running off of the UFD (Usb Flash Drive) and have the updates remain persistent (Unetbootin doens't keep updates either). Also, I can't install any apps that I want, i.e games, media, office, internet, etc., and have them be persistent too. Once I reboot the machine, any and all changes are wiped clean, except my documents, photos, and videos (if there is enough space on the UFD), because those are in a persistent file which keeps changes made to it.
 
**So, what I want is a UFD that I can install unbuntu on, update it, install apps, remove apps, add files, remove files, etc. All while running from the UFD. I also want to be able to take the UFD and use it on other systems (ie. school, work, other home systems, friends systems, etc.).**
 
I think that I found a way to do almost all of that but it might have some drawbacks and issues that I need some help looking at. The way that I am thinking won't allow me to update on the fly, install apps, remove apps, etc. while I am running from the UFD, but it is pretty close. 
 
After reading through tons and tons of posts, following links that led to links that led to even more links and some of them dead ends. I eventually came across this site [here.]("http://www.psychocats.net/ubuntu/remastersys") (credit to the author of that site for posting the guide. Thank you!!!!!!!) It explains how to make my own remix of ubuntu and make an .iso from it!!! If I can get a working .iso of my current system, then it will already be updated and all the apps will be installed that I want. This is most likely the best way to go for the moment.
 
So I figured I would do this:
 
1.) Install ubuntu 9.04 x32 on my main system. (I usually use an x64 based OS on my main system but to make this more compatible with older hardware on other machines, in case I want to use my UFD at school, work, friends house, etc., I need to go with an x32 based version of ubuntu. Also, I like 9.10 but 9.04 just seems a little more stable from what I have experienced personally. I know that many will say that 9.10 is VERY stable. And you are right, I have it on my system right now and it is EXTREMELY stable ......... about 99% of the time. But every once in a while it will just give up the ghost for some reason. So 9.04 it is. :lolflag:)
2.) Update ubuntu with all the latest updates (Not upgrade!)
 
3.) Install all apps needed/wanted (games, office, media, internet, etc)
 
4.) Personalize any and all settings wanted for apps, desktop, etc.
 
5.) Back-up my Documents, Pictures, Videos folders.
 
6.) Remove Docs, Pics, Videos from my main system. (Remove the files, not the directories!!! I have them backed-up in case something goes wrong.)
 
7.) Follow the directions [here.]("http://www.psychocats.net/ubuntu/remastersys") Once the whole process is over, I should basically have an exact copy of my system, but without my documents, pics, vids., in .iso form. (If I understand everything correctly)
 
8.) Use the built in USB start up installer in ubuntu: system menu -> Admin. -> USB Startup Disk installer (It might be called something different but pretty close) The installer will use the .iso file I just created of my re-mastered/re-mixed system and install it onto my USB Flash Drive. It will also creat a persistent file where I can copy over my files that I backed up (i.e. docs, photos, videos, etc.)
 
9.) Enjoy my newly updated, fully cutsomized, complete with all apps I want, ubuntu system on a bootable flash drive; complete with all my personal files. :p
 
-------
 
So before I start into the problems that I foresee, I have a few questions, hopefully someone can answer. In the guide that I linked above, it says to un-hide any hidden folders in the /home directory. Then to copy any "appropriate settings directories to the /etc/skel directory"
 
First off, what is the /etc/skel directory, what part does it play in my system, and why should I copy the appropriate settings directories to that directory? Also, when it says "appropriate settings directory" I am assuming 1 of 2 choices: that either 1.) it means only directories that are required for the apps that I want to run on my re-mastered .iso, or 2.) it means a specific set of directories (which one, I don't know because they aren't mentioned). Which is it? I am betting it is option #1.
 
**Possible problems:**
 
So, I foresee some possible issues/problems by doing everything this way. I want to try and find a possible solution to these issues, in case they show up, so that I will already have an idea on how to solve them.
 
If I understand the whole re-mastering / re-mix process correctly, and correct me if I am worng, it keeps my system exactly the way that it was once I started the whole process (step 7 from above). It makes an .iso out of it, makes that .iso bootable and instalable. By using unetbootin, I can create a persistent file that will allow me to keep my photos docs, videos, etc, on the usb and use them when I boot from that usb flash drive. I do realize that I won't be able to update any of my apps, system, programs and have the updates remain persistant. I will, however, be able to update, add, remove, and change my personal files.
 
I am worried about a few things though. If the re-mastering of the system to an .iso really does work the way that I think it does, then wouldn't that mean that it would have hardware specific drivers, such as video, sound, cpu, etc, etc., for just my system on/in it, because that is what the re-mix was made from? That wouldn't allow me to boot off of another completely different system, right?
 
I was originally planning on using either a 4GB or 8GB USB Flash Disk. Do you see any downsides to this? Also, if I got a big enough UFD, like a 16GB or a 32 GB, would I be able to update my the system on my UFD and have the updates remain persistent? I always assumed that in previous attempts of updating the system, while running off of the UFD, it failed because of lack of storage space. I was using a 2GB UFD. Would i be able to keep updating the system on the UFD while running from the UFD and have the updates remain persistent? If so, then I will have accomplished my initial goal of making a complete system on a USB Flash Drive. One that keeps EVERYTHING persistent and allows for updates and for use on other machines, independent of their hardware/configuration.
 
PHEW!!!!!!! I think that that about does it! Thanks to those that have taken the time to read this and actually post something. I know it is SUPER long but I had to get the entire idea out there in details.
 
Please let me know if you have some suggestions, ideas, a better way to achieve what I am after. I am willing to try different things to get this to work.
 
Thanks again!!!
 
-Spydey [IMG]http://images.zaazu.com/img/male36-male-spiderman-superhero-smiley-emoticon-000088-small.gif[/IMG]

---

### Post by CaptainMark on 2009-12-10
You can always just do a full install onto usb with a live disk just make sure to install grub onto the usb drive too.  Forgive me if you mentioned this in your post, its really long, i just skimmed really

---

### Post by spydeyrch on 2009-12-10
Yeah, I know it is really long. Sorry about that. :(  I was kind of writing my thoughts down as I went through the process in my head.
 
I could try it your way. I am just worried that it would install hardware specific drivers. Thus not allowing me to use it in other machines.
 
Even if it were to install the hardware specific drivers, would I still be able to use it on other machines?
 
@captainMark - I saw your avatar, the little goku linux penguin, and busted up laughing! all my co-workers started to stare at me!!  :shock: Great icon there!!
 
-Spydey

---

### Post by wilee-nilee on 2009-12-10
I just skimmed to, the usb creator with the persistent file allows you to update.

---

### Post by CaptainMark on 2009-12-11
i once tried to  update from 8.10 to 9.04 on a live usb, whole thing died on me, might have been bad luck but i wouldnt recommend it. I think a full install on a usb will work fine with the drivers however i dont know about propietery drivers, they would probaly mess things around abit, maybe just stick to the open source drivers on there as default and you should be okay

---

### Post by spydeyrch on 2009-12-11
That is what I was thinking, that I should stick to the open source drivers and not install any proprietary drivers because it could mess things up but I wasn't sure. I guess that I could do everything that I mentioned before with the exception of installing any proprietary drivers.
 
The other thing was that I have tried the ubuntu usb starter install thingy (like my technical term?? hehe :D), the one that creates the persistent file. I like it because it comes in very handy. I tried to update 9.04 that was on it (not upgrade, just update 9.04). It downloaded all the updates for 9.04 that were available at that time, and then started to install them. Now keep in mind that I had booted off of the usb so I was running 9.04 from the usb flash drive. After about 1 hour of slowly updating, it failed with about 15% remaining. This was quite a while ago so I don't remember exactly what the error message was, but the jist of it was that it had run out of memory and could no longer update the components and that any changes were going to be reverted to the prior state. My system has 4GB of ram, so I doubt that it was out of memory. I am assuming that it meant the usb flash drive After that, my usb flash drive wouldn't boot up again until I reinstalled on it via the usb starter install thingy in ubuntu.
 
It could be that my usb flash drive was too small. It was only a 2GB flash drive.
 
@wilee-nilee 
 
you said that the usb creator with the persistent file allows me to update, are you sure? Have you done it it sucessfully before? How big of a usb flash drive were you using? did it keep any custiomizations and setting that you made to any apps, desktop background, etc? If it does work, then perhaps it was just my USB drive that was at fault, not enough storage space.
 
Thanks for your input guys, it allows me to find the best way to handle this issue.
 
-Spydey
 
:popcorn:

---

### Post by CaptainMark on 2009-12-15
How did this go in the end, ive got a new usb and im trying to decide what to do with it, i want more or less the same thing you do, it would be nice to have the option of installing ubuntu on another machine with the usb too though, but at the same time, any thing i put in the home folder wont be readable on a windows pc will it? unless theres some way to have a seperate partition formatted as fat32 for your home folder on a live usb, ive never heard of this on a live disk though. any thoughts?

---

### Post by spydeyrch on 2009-12-15
As of right now, no I haven't had a moment to try it. I just got finished with finals for this term at school so that was taking up all my time. Plus I need a larger usb flash drive to really give it a whirl.
 
I like your idea!!!!:KS
 
I was thinking about making a remastered ubuntu .iso based upon my desktop, apps, settings, etc, and then using the built-in ubuntu usb startup installer. The only thing that I was worried about was not being able to update the ubuntu system with the frequent updates that come out. So to get around that, I was going to do just a regular install of my remastered .iso to the usb, which would allow me to take it with me and have it be updateable. I haven't been able to test either theory yet, but in theory, they are sound.
 
But you have taken it a step further!! Allowing windows (and possibly even macs) to view your /home directory and access the files. Yes, I think that you would need to have two partitions on your usb flash drive, which is possible. Like I mentioned before, I believe that to get this to work you would need to have quite a large usb flash drive. I was going to use at least an 8GB but now that I think of it, perhaps a 16 or even 32 GB drive would be best.
 
The only issues that I can think of is if you install ubuntu via the normal methods (via live cd or remastered, either way) to the usb flash drive and install grub, it wouldn't be a live usb anymore, right? Therefore you couldn't use it to install ubuntu on other machines. I have a couple other ideas/concerns but to tell you the truth, i think that the best thing at this point is to just try it.
 
So i will do that tonight and let you know how it goes.
 
Oh, how big of a usb thumb drive did you get?
 
-Spydey

---

### Post by CaptainMark on 2009-12-15
i got 8gb, ive since found out you cant have a fat32 /home partition (its to do with fat32 not supporting the same permissions) , im trying to think of a way around that one but havent come with anything yet,
 i think the best option for now is 2 partitions one ext4 for the system and one fat32 mounted outside of /home which i would have to transfer files to if i wanted them on windows. i may opt for 8.04 LTS, for it being more stable, a usb system doesnt have to be bleeding edge.

EDIT: Tried symbolic links, they dont work on FAT at all, damn

---

### Post by spydeyrch on 2009-12-16
@Captainmark: thanks for the update. I wasn't aware that fat32 wasn't allowed to be used for home partitions. But it makes sense.
 
I am still waiting to get my new usb flash drive. i should have it here in the next few days.
 
Yeah, it looks like having two partitions might be the only way to get a "shared" folder or drive for linux/wndows to play nice.
 
Captainmark, Can I ask you a favor? Being as I don't have my usb flash drive yet and you have an 8 GB one, would you mind trying a few things for me with yours? I want to see if by using the built-in usb startup installer, it is still possible to update the system on the usb flash drive. I ahve tried it in the past but I believe that it failed because of not having enough space on the usb drive.
 
So, if you would please do this:
 
backup any files that you have on it to a different place.
 
format the drive: fat32 (you can do this in ubuntu or in windows)
 
start up ubuntu (if not already in it)
 
insert your 8GB usb flash drive
 
from in ubuntu, system menu -> admin. menu -> usb startup installer (the name may not be exactly the same but it is close)
 
select the appropriate .iso (preferably ubuntu 8.04LTS or 9.04 (make sure you have them already on your machine))
 
Select your 8GB usb flash drive, move the persistent file slider all the way to the right, to give it all the extra space that it needs. I know that my 2GB drive showed as 1.9GB and that after I installed the os onto it, there was 1.3GB left, so I moved the slider over to the 1.3GB mark, to use up the extra space.
 
Install the system to your usb flash device.
 
Once the install is done, restart the machine and boot off of your new install on the usb flash drive.
 
Once you are booted up, this is the crucial part and what I am hoping will succeed, try to update the system. run update and see if it will update your ubuntu os on your usb flash drive. it might take it a while to update everything. 
 
When I did it a while back, it took like 2 hours to get to 85% and then it failed. I am hoping that that is not going to be the case with your larger flash drive.
 
If it works or doesn't let me know please. Thanks!
 
Also, when you start up the built in usb starter install program, take note please if it asks you to format your usb flash drive because it is fat32. i am hoping that it won't and that it will let you install on the usb flash drive even though it is a fat32 file system.
 
Lets hope everything works out!! Thanks for your help. :-)
 
-Spydey

---

### Post by CaptainMark on 2009-12-16
Right ive already done my usb by the time i read this but its pretty much what ive done anyways,
A usb livedisk will always format as fat 32, this is automatic but the persistance file is ext2 inside the fat32 (but you cant see it as a seperate partition) kinda weird 

Updates run fine but it seems its a good idea to only run a few at a time, not loads in one go, that seems to crash the usbs.

Anything thats left in the home folder of a live usb cant be accessed via mounting the usb normally on ubuntu or windows, you seem to have no option but to boot from the usb or transfer everything to a shared partition before you shut the live usb down.

I think thats about the best i can get, i had the idea to just put a bash script on the desktop which copies everything from the live usb music/videos/documents etc. to the shared partition. Just click before you shut down the live usb, confusing but this way i have most bases covered for what i could need the usb for.

EDIT: Oh and i had to format the usb before using the usb creator, make two partitions both fat32 and make sure the live usb system goes in the second partition, otherwise windows wont see the shared (1st) partition

---

### Post by miniyak on 2009-12-16
I'm also working on getting something like this working, see here-[http://ubuntuforums.org/showthread.php?t=1352307]("http://ubuntuforums.org/showthread.php?t=1352307")

I now have 16gb flash stick but haven't got it to even the intended working state of a live usb after 2 attempts try unetbootin and the one included with jaunty.

Personally i dont see the point of a "live" usb install... i mean if you have write power why not just treat it like a persistent drive?

going even further to question the way things have been accepted. Why cant I install a second persistent os from whatever OS im already using? especially when that second persistent OS is on a separate storage volume? ( i can understand same disc OS getting in the way of the partitioning process.... +2gb of ram though... the os could live on the ram disc for the partitioning process.)  

just rhetorical brainstorming questions to be honest. May be something like suggested has been done?

---

### Post by sgosnell on 2009-12-16
You're going about this the wrong way.  Put the .iso on a small USB drive or SD card.  1GB is big enough.  Boot from that live CD version, and **then** use it to install Ubuntu onto your large USB drive.  DO NOT confuse a 'persistent' live CD version with an installation.  If you want the full capability of Ubuntu, you need to do an install onto the drive, not use a liveCD.  You need two drives to do this, but the small one can be reused if you want.

---

### Post by CaptainMark on 2009-12-16
How do have a second persistant os inside another os and also on a seperate storage volume, that would  just be 2 os's on different drives.  Youd need a program to put an os inside an os, like how wubi puts ubuntu inside windows, and we looking to keep these usb os's small to save on space. 

Were really not talking about os inside of os anyway were talking about a single usb stick that can do 3 things

1. Be run as full persistant version of ubuntu capable of updating.
2. Act as a live cd would by having the ability to install ubuntu onto another machine.
3. Be fully usable as a mass storage usb accesable from ubuntu and windows, just as you would with a normal usb. 

Either youve got the wrong idea from our posts or im getting the wrong idea from yours, feel free to elaborate because im confused

PS, we have managed to do all three of these on the same usb stick were just trying to decide which way would make it most efficient and versatile

EDIT: @ sgosnell, were not confusing live installs with full installs, read the whole post.

---

### Post by spydeyrch on 2009-12-16
> **CaptainMark said:**
> Were really not talking about os inside of os anyway were talking about a single usb stick that can do 3 things
 
1. Be run as full persistant version of ubuntu capable of updating.
2. Act as a live cd would by having the ability to install ubuntu onto another machine.
3. Be fully usable as a mass storage usb accesable from ubuntu and windows, just as you would with a normal usb. 

 
 
I couldn't have said it better myself. Great work by the way with your usb, glad to see that we can update them!! That is going to make a world of difference!! I CAN'T WAIT to get my new one and try this out!! :KS :guitar:
 
Thanks for pointing out the fact that I would need to use the 2nd partition for my persistent install and not the 1st. I wouldn't even have thought of that!!
 
---------------
 
Now that you have tried it this way, I am wondering if doing it a different way would yield better results.
 
What if we were to do this:
 
via a live cd, actually install the os to the usb.
 
I was thinking that we could do it like this:
 
unconnect all hdd from mobo (obviously with the machine turned off and power cable disconnected)
 
boot up computer, with both live cd in optical drive and the 8GB usb flash drive in place
 
Install from live cd to usb drive. (we disconnected the other hdd just to make sure that grub didn't get installed to them and was forced to install to the usb flash drive. I don't know of another way to do it so I figured this would be the safest.)
 
after install is done, reboot and boot off of usb thumb drive. See if it works, can you get it to boot properly? 
 
Boot again but this time with your hdds connected. Boot off of your primary hdd. Does the option to boot into the usb device appear in the grub menu from your local/primary hdd? (I would assume not and that we would need to edit the grub boot list on the primary hdd, but I don't know the specifics on how to make it search for a bootable usb flash drive, that is if it doesn't see it off the bat. I am not too familiar with Grub and it's internal workings.)
 
Boot again but this time, via a boot selection menu (usually something like F12 during POST) boot off of the usb flash drive with the other HDDs connected, in the usb flash drive's grub menu, does it give you the option to boot into the other hdds (windows, other ubuntu on your local/primary hdd)?
 
something else we need to test is if, once we are booted into the system on the usb flash drive, can we update (we should be able to, and we should try it in chuncks, like you previously mentioned captainmark)
 
If all goes well (which hopefully it does!!), then the ideal setup for this method (don't confuse it with the first method of using the persistent file!!) would be to make three partitions on the usb
 
1.)system os
2.)live usb (use unetbootin, NO PERSISTENT FILE)
3.)fat32 for shared docs/music/videos/etc.
 
these partitions don't have to be in this particular order.
 
this is just an idea and it might be that it requires more work/customization to get it to work. It might be that it also take more work to do than the other and that the results aren't better than the first, but hey, I figured that at least it should be tried to see if it will work or not. To be honest, I don't think that it will be better than the first way but I figured that we should at least explore the option, no. 
 
also, the live usb partion would be based off of a remastered .iso that we would have created prior to this process. That way, we could install our already setup system (user settings, book marks, backgrounds, etc) on another computer. The only thing that I can foresee is that we should not install proprietary drivers for any hardware on the host system until AFTER we have made the remastered .iso. Just to make srue that the remastered .iso contains only generic drivers. This would allow us to install it on other systems without hardware headaches on the new computer, at least I am hoping so. Does that make sense? Let em know.
 
also, @captainmark, on the first USB, the persistent one, do the settings that you change, such as firefox settings, desktop background settings, etc, revert back to default when you exit the system or are they saved too? I have used several usb persistent systems but never really paid much attention to if the user settings were saved or disregarded at shutdown.
 
Thanks for all your work and help in the project, it is a HUGE help to me!!! I appreciate it a ton!!!
 
let me know when you can and once I get my new usb flash drive, i will start helping too (assuming that we haven't reached a conclusion from just your efforts, hehehe:lolflag:)
 
-Spydey

---

### Post by miniyak on 2009-12-16
yah sorry simple miss wording i'm not talking bout VMs or anything the like

by saying "inside" the OS, i really meant "from" the OS. for example in my case of wanting to install full ubuntu on a 16gb thumb stick. I would like to just be able to get an installer in my jaunty set-up that would push a real install onto the usb drive, or in another use case, install karmic on a second partition from my jaunty install. (of course there are some technical partitioning issues with the latter)

the installer would negate the need for a live set-up as required by requirement #2

the only real road block is requirement #3 in which i think even in the best case scenario there would have to be 2 partitions on the drive, first one being something windows reads by default preferably (like fat32)   

.... just got an idea... may be i can just copy my current root partition to the usb drive, i think it will still need the bootloader though.. im going to do some experimenting

---

### Post by sgosnell on 2009-12-16
If you want one drive to do all that, then yes, you need 3 partitions.  The partition for the liveCD needs to be the size of a CD, about 700 MB.  You can make the FAT partition whatever size you want, but you need the Ubuntu system disk to be fairly large.  Putting the bootloader on the disk in the proper place may be tricky, though.  I've never tried to do what you want, because I have different sticks for different uses, and don't want or need one stick to do everything.  I think you want the bootloader to be installed on the Ubuntu system partition, not on the device root, thus sdb2, for example, not sdb.  The liveCD will have its own bootloader, and you may not be able to put both on one drive.  I think that may be the limiting factor here, but like I said, I've never tried to cram that many things onto one drive.

---

### Post by spydeyrch on 2009-12-16
> **miniyak said:**
> yah sorry simple miss wording i'm not talking bout VMs or anything the like
 
by saying "inside" the OS, i really meant "from" the OS. for example in my case of wanting to install full ubuntu on a 16gb thumb stick. I would like to just be able to get an installer in my jaunty set-up that would push a real install onto the usb drive, or in another use case, install karmic on a second partition from my jaunty install. (of course there are some technical partitioning issues with the latter)
 
the installer would negate the need for a live set-up as required by requirement #2
 
the only real road block is requirement #3 in which i think even in the best case scenario there would have to be 2 partitions on the drive, first one being something windows reads by default preferably (like fat32) 
 
.... just got an idea... may be i can just copy my current root partition to the usb drive, i think it will still need the bootloader though.. im going to do some experimenting
 
I think that I understand what you are saying. Correct me if I am wrong or don't understand.
 
You have ubuntu installed on a hdd and are running from it. while using that running ubuntu, you would like to install ubuntu on a connected usb drive, the 16GB one you mentioned earlier. so the basic issue is, why can't you install an os (os#2, in this case ubuntu), to another drive (16GB usb thumb drive), while already currently running in os#1 on hdd#1. Is that the jist of it?
 
If I did udnerstand it correctly, why would you want to do it that way and not just boot from a live cd and install to the usb thumb drive? What benefit is there to installing the os to the usb while already running in an os? 
 
Thanks for the contribution though, anything will help and make us think of possible isues and possible solutions. :guitar:
 
-Spydey

---

### Post by miniyak on 2009-12-16
Ok i remember watching this episode of Hak5 a while back, i think its a good reference considering what we are talking about. here-[http://revision3.com/hak5/usbmultipass]("http://revision3.com/hak5/usbmultipass")

Its not talking about ubuntu in particular just any distro 

... i think you need to have access to a windows machine for the initial set up though, and if thats that case im going to have a hard time

talking about windows.. they also recently recommended this- [http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

---

### Post by miniyak on 2009-12-16
> I think that I understand what you are saying. Correct me if I am wrong or don't understand.

You have ubuntu installed on a hdd and are running from it. while using that running ubuntu, you would like to install ubuntu on a connected usb drive, the 16GB one you mentioned earlier. so the basic issue is, why can't you install an os (os#2, in this case ubuntu), to another drive (16GB usb thumb drive), while already currently running in os#1 on hdd#1. Is that the jist of it?

If I did udnerstand it correctly, why would you want to do it that way and not just boot from a live cd and install to the usb thumb drive? What benefit is there to installing the os to the usb while already running in an os?

Pretty much the gist of it

why do it that way? lol, because CDs are archaic and often times unreliable, ive seen a lot of hosed installs or fail start-up over something simple like a disc smudge or writing the disc to fast. Which by fast, meaning the 15 minutes of watching a progress bar. On top of that it takes 10minutes to startup the live CD. All this vs the fraction of second it would take to wake from stand-by and run an installation program... (well after you download the iso.. but that takes the same time either way) 

an other thing that is an obstacle to me is the fact that i own 4 computers all having either missing or having a non-functional cd drive. In the future i would rather not need to even have the need for one as there not particularly useful for anything other then live cds...

---

### Post by spydeyrch on 2009-12-16
> **sgosnell said:**
> If you want one drive to do all that, then yes, you need 3 partitions. The partition for the liveCD needs to be the size of a CD, about 700 MB. You can make the FAT partition whatever size you want, but you need the Ubuntu system disk to be fairly large. Putting the bootloader on the disk in the proper place may be tricky, though. I've never tried to do what you want, because I have different sticks for different uses, and don't want or need one stick to do everything. I think you want the bootloader to be installed on the Ubuntu system partition, not on the device root, thus sdb2, for example, not sdb. The liveCD will have its own bootloader, and you may not be able to put both on one drive. I think that may be the limiting factor here, but like I said, I've never tried to cram that many things onto one drive.
 
Thanks snosnell for your input. Much appreciated.
 
Yeah, I thought about the fact that the liveCD has it's own bootloader but I forgot to include it in my post, thanks for mentioning it. :)
 
Something that I thought of that might help with that issue is the chameleon bootloader. Have you heard of it? During my days of dabbling ing the hackintosh community, it was the bootloader that I used. AWESOME BOOTLOADER!!!!! It would detect all partitions, and installed OSes and then, via a gui, allow the user to select which one they wanted. It also allowed one to go to a terminal for the specific os and other things. Great little bootloader!! Loved it.
 
what if we were to install that on the usb thumb drive and/or the primary hdd? that then would allow us to choose to boot from either the primary hdd drive's OSes, or the two on the thumb drive (installed os & liveCD). 
 
Just to clarify, we are still talking about method #2.
 
Method #1 - install persistent file OS (with second partition for shared files)
Method #2 - full install of actual OS on the thumb drive (three partitions: full installed OS, liveCD, shared partition for folders)
 
Any thoughts on this? thanks guys. this is exciting to me, to get get input from others. I usualy just run ideas by my father. He had his own business for 7 years. did consulting for Microsoft, FEI, Adaptec, HP, etc. then he worked for Adaptec/Roxio/Sonic Solutions. Currently he is working for HP. He is a great resource but having just one source of feedback can kind of make projects go down just one road. thanks a ton for all your help, comments, and effort!!! :guitar::KS:popcorn::)

---

### Post by spydeyrch on 2009-12-16
> **miniyak said:**
> Ok i remember watching this episode of Hak5 a while back, i think its a good reference considering what we are talking about. here-[http://revision3.com/hak5/usbmultipass](http://revision3.com/hak5/usbmultipass)
 
Its not talking about ubuntu in particular just any distro 
 
... i think you need to have access to a windows machine for the initial set up though, and if thats that case im going to have a hard time
 
talking about windows.. they also recently recommended this- [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
Great sites, thanks. I will have to take a closer look at the first link when I get home from work today.
 
About linuxliveusb.com, what is the difference between what they do and unetbootin? Unetbootin can run on windows as well as linux. It creates a bootable liveUSB from any distro that you have and if you don't have it, it will download it for you. Plus I think that if you have the .iso of other OSes, it will even make those bootable on the usb, for installation. i haven't tested the "other OSes" theory yet, but I would think that it can.
 
Also, good point on why you would want to run an installer from inside an os. avoid the cd.
 
i might have a solution to that issue that you were mentioning, the CD, install os in os, etc., issue. You mentioned linuxliveusb.com. It can install a .iso of linux to a usb thumb and make it a liveUSB for use to install on machines that don't have optical drives. The only issue that I see is that it requires windows, which you said is an issue for you.
 
As I previously mentioned in this same post, unetbootin can run in both windows and linux. it will download the selected distro of linux or use an already downloaded .iso, and install it to a usb thumb drive, making it a live USB. It does not make it a persistent file, just alive USB. Maybe that will help.
 
It is an app/program that you runu while already running your main os (ubuntu/linux/windows) and it installs the .iso onto the usb to make it live. So you could wake the computer up from hibernation, run the program, and BAM!! have your livUSB, all without windows!!! YAY!!!
 
Hope that helps!!!
 
:popcorn:
 
-Spydey

---

### Post by miniyak on 2009-12-16
I have used unetbootin about 4 or 5 times, i've never been successful with it.

Out of 8, i only have 1 xp machine... it only has 64mb of ram though...works, but its not the particularly useful type of working.

now that i really think of it, i did install puppy from the HDD inside of win 98 at one time... but i think that the method i use was exclusive to that situation... If recall correctly the set-up allowed me to reboot from 98 into puppy using ms-dos commands... so i guess what I'm saying is that the type of thing that I mentioned is possible.

---

### Post by spydeyrch on 2009-12-16
> **miniyak said:**
> I have used unetbootin about 4 or 5 times, i've never been successful with it.
 
 
What kind of issue did you have with unetbootin? i have used it on numerous ocassions and it has always worked for me. Does it give you any error messages or anything wierd happen?
 
To be honest, I don't know if there is a way, via the terminal, to install an os to an usb/other device.
 
-----
 
@captainmark - how are things going? Any updates? anything new tried?
 
Have you heard of the chameleon bootloader? Look at my prior post about the chameleon bootloader.
 
Thanks!:)
 
-spydey

---

### Post by miniyak on 2009-12-16
Ok i just retried the included usb creator on my karmic install. 

it was a real pain, i had to reinstall usb creator for it to work properly. After it was done plugged it right into my tc4400 ... no jazz, got past the main live menu, the two logo screens, black screen with the hourglass then froze up

I just installed unetbootin on karmic, maybe ill have better luck the jaunty... may be ill try a different distro

---

### Post by spydeyrch on 2009-12-16
that is wierd that you are having problems with the built in usb starter. I don't think that I have ever had an issue. Try this:
 
start your machine and log into your desktop (ubuntu, right?)
 
connect your usb thumb drive to your machine
 
when the icon comes up on the desktop, right click it and unmount the drive.
 
go to system menu -> admin menu -> disk partitioner (if you dont have it, get it from synaptic software, type in partitioner, I believe that it is "gnome disk partitioner" or something familiar. really it is just gparted. 9.10 uses a different partitioning program, I would recommend gparted because I know how to do it using gparted.)
 
upper right corner of disk partitioner, select your usb thumb drive.
 
format the thumb drive to fat 32, the entire thing. (if you have files on there that you are saving, back them up to a different location.)
 
when done, unplug the thumb drive and then plug it back in.
 
when it comes up, go to system menu -> admin. menu -> liveusb install program
 
in the upper section of the liveusb creator program, select your .iso (i would recommend either 8.04LTS or 9.04), then in the bottom section of your liveusb creator program select your thumbdrive, there should be a button that says that it needs to be formated, do so.
 
Once it is done formatting, select the amount of space that you want for your persistent file. then install everything.
 
Once done, give it a whirl on your machine. You probably already knew all of what I just mentioned but I thought I would at least give my two sense worth.
 
What are the specs on your tc4400?
 
also you say that you installed unetbootin? how did you do that? in my experience, i just downloaded it from the unetbootin website, right clicked on the application, set app to run with permissions, and away it went. no need to install anything really.
 
Hope that helps. let me know.
 
-spydey:)

---

### Post by miniyak on 2009-12-16
For formating, Its also possible to right click on the icon that shows up to be presented with an option to format the volume

I didn't think to unplug and replug the drive, maybe that will help

i'm going to also try using the 9.04 iso vs. 9.10 

though i still havn't tried that last install i did... maybe that will work, it will have to wait to tomorrow though.

I got unetbootin through synaptic btw, what version do you have? i have 304-1

the tc4400 is in pretty ruff shape (got it for free) but its only about 3 years old 1gb ram w/ 2.0ghz centrino duo. its a tablet so it was definitely meant to boot from usb. ive also been testing on my panp5 which is only a few months old, so i really shouldn't being seeing conflicts as far a capabilities go.

---

### Post by spydeyrch on 2009-12-16
Yes I realize that you can just right click on the mounted drive. Gparted was the first thing that came to my mind. :)
 
I believe that the latest version for windows is 3.77 and the same for linux. go straight to the site and download it via there. Give it a whirl and see if it works.
 
-Spydey:guitar:

---

### Post by sgosnell on 2009-12-17
It slipped by me earlier, but you don't need a separate liveCD partition.  Ubuntu has the same installer included, plus a USB boot disk creator.  There is no need for a liveCD if you have the installed version on a USB drive, so you're just making more work than necessary by trying to add it to your USB drive.  Just use gparted to make the necessary partitions, format one to FAT, install Ubuntu to the other, and you have everything you need.  I prefer to put /home on a separate partition, so I can save my settings and data if I need to reinstall the OS, or install a new one, but that's not absolutely essential.

---

### Post by spydeyrch on 2009-12-17
> **sgosnell said:**
> It slipped by me earlier, but you don't need a separate liveCD partition. Ubuntu has the same installer included, plus a USB boot disk creator. There is no need for a liveCD if you have the installed version on a USB drive, so you're just making more work than necessary by trying to add it to your USB drive. Just use gparted to make the necessary partitions, format one to FAT, install Ubuntu to the other, and you have everything you need. I prefer to put /home on a separate partition, so I can save my settings and data if I need to reinstall the OS, or install a new one, but that's not absolutely essential.
 
Excuse the obvious, it is getting a little late where I am at and I just put two small super hyper kids to bed, so I am a little tired.
 
Do explain a little please. An actual installed ubuntu has an installer in it? How would we access it and use it to install to a hdd?
 
So I am assuming that it would go something like this:
 
insert usb thumb drive (already has two partitions: installed ubuntu os, and shared partition for windows)
 
boot computer off of usb.
 
once it is up and loaded, then what?
 
how would we run the installer to install ubuntu onto that particular comptuer's main hdd?
 
Thanks for the insight!!):P
 
-Spydey

---

### Post by miniyak on 2009-12-17
with the type of fail rate im seeing (11/1) I really have a hard time seeing why any normal person would want to create one these completely retarded "live" usbs. I got one working (9.04 right via unet from 9.04) but I couldn't find anything allowing for persistence so i formated it again to try something else that also didn't work... "Live" isn't going to help replace my tc4400's dying hard drive.

I'm going to take a break for a while, but i'll keep following

seems all the good tools to do what were talking about are ironically windows based..

oh, again with the windows, i found another site yesterday,[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")
looks like its all windows solutions, maybe im wrong though, i just took a glance. I'm really just looking for a time effective linux solution that dosen't involve using bash. Because i dont really have the time to mess around with that either

---

### Post by spydeyrch on 2009-12-17
> **miniyak said:**
> with the type of fail rate im seeing (11/1) I really have a hard time seeing why any normal person would want to create one these completely retarded "live" usbs. I got one working (9.04 right via unet from 9.04) but I couldn't find anything allowing for persistence so i formated it again to try something else that also didn't work... "Live" isn't going to help replace my tc4400's dying hard drive.
 
I'm going to take a break for a while, but i'll keep following
 
seems all the good tools to do what were talking about are ironically windows based..
 
oh, again with the windows, i found another site yesterday,[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
looks like its all windows solutions, maybe im wrong though, i just took a glance. I'm really just looking for a time effective linux solution that dosen't involve using bash. Because i dont really have the time to mess around with that either
 
Seriously, you are having that high of a failure rate? WOW!! I think that I had maybe one failure in 25. Not saying anything against you, just surprised at the high failure rate.
 
so just to make sure that things are clear, there are basically two methods of making a "liveUSB". One requires you to use an external program, such as unetbootin, or the ones that you can find on livelinux.com (the link was previously given in this thread) and pendrivelinux.com. This method is just like a livecd but on a usb, nothing fancy about it. It takes the .iso and "burns" it to the usb flash drive.
 
The second is the Persistent LiveUSB. this is found in the Ubuntu system. If it exists outside of the ubuntu os, I am not too sure, haven't looked. It does basically the same thing as the first method but allows you to create what is called a persistent file, where you can store your settings, files, changes and they will be kept.
 
I am still surprised at why it is failing so much! Do you happen to have access to a different computer, like perhaps a friend's or public computer? Also, even though the pendrivelinux.com, livelinuxusb.com, and unetbootin do run in windows, I know for a fact that the unetbootin is not limited to only windows, I have used it numerous times in ubuntu. As far as the other two, I can't comment, never used them.
 
If you could get to a different computer and try it there, I am hoping that you might have a different outcome.
 
Hope everything goes well.:)
 
-Spydey:guitar:

---

### Post by miniyak on 2009-12-17
I've been been testing with two separate computers... all my the other computers have under 256mb of ram at the moment, so i'ld rather not waste my time with them. This has to work on the tc4400 anyhow.

I might be able to get a hold of an other windows machine to use, but out of principal i'd rather not.

I'm thinking its a stroke of bad luck or something, most people i've heard from have had an easier time also.

however i did hear somewhere that sometimes the make of the jump drive can be a factor in how successful you are. I'm not sure how true that is, so I started a thread on it that I linked to earlier in this thread i think. Seems the only bad luck to speak of was with a sandisc U3 drive (which can be solved)

---

### Post by sgosnell on 2009-12-17
@spidey: In Ubuntu, at least with the 9.04 version, you open System/Administration, and select Install.  That runs the same installer as is on the liveCD, and you can install to any drive you can access, including an internal HDD.  Make sure you have gparted installed, of course.

You can make a liveCD USB from System/Administration/USB Startup Disk Creator, but that's obviously not the same thing as installing to HDD.

---

### Post by spydeyrch on 2009-12-17
I have NEVER liked those stupid scandisk U3 usb drives, NEVER!! They always cause me such a headache when I use them in windows. Poping up and letting me know that I can do X with them and then installing software without my permission. ANNOYING!!!! They remind me of stores that continuly ask me if I want to save 10% by opening a card with them!!!
 
I would recommend that if you can, go out and buy a 2GB flash drive, just as a trial/test device. See if a different flash drive works/doesn't work. Honestly, I bet that it is the U3 causing issues. But I have been wrong before. :confused:
 
Let me know, I am interested in seeing the results.:P
 
-Spydey:guitar:

---

### Post by spydeyrch on 2009-12-17
@sgosnell - thanks a ton for the info. I wasn't aware of that. I must have never noticed it before. Hmmmm ........ this gives me an idea. Do you know off the top of your head if the liveusb (like through unetbootin) and/or the persistent liveusb have this option in them too? Thanks!!  :)
 
@miniyak - perhaps this would help you in your endeavors? This would allow you to install an OS from inside an OS. What do you think? :KS
 
-Spydey:guitar:

---

### Post by sgosnell on 2009-12-17
Read the last sentence of my last post.  To make a liveUSB, just select System/Administration/Make USB Startup Disk.

Or maybe I'm misunderstanding you.  The LiveCd version obviously does installs, that's the whole point.  Every installed version has it.

That was the point of my first post.  There is no need to put a liveUSB on an installed disk, because the installed version has all the capabilities already included, along with much more.

---

### Post by spydeyrch on 2009-12-18
Yes, I am aware that the live version has it, hense it wouldn't be able to install if it didn't have it. Yeah, I know how to make a liveUSB, I have posted it several times in this thread already. :) I was primarily asking for the benefit of miniyak. He was trying to install an OS from within an OS and I wasn't aware of the fact that in the system menu -> admin. menu there was an "install" option, which would install the already running system onto the computer. So I was just asking a few probing questions to see if something might work for him.  :KS
 
-------------
As far as what I want, my thought was just this:
 
The point was to have a full system on a USB thumb drive that would allow us to do these three things:
 
1. Be run as full persistant [or full normal] version of ubuntu capable of updating.
2. Act as a live cd would act by having the ability to install ubuntu onto another machine.
3. Be fully usable as a mass storage usb accesable from ubuntu and windows, just as you would with a normal usb.
(thanks be to captainmark for summing it up. :))
 
I wanted to take it even a little further. I was planning to install ubuntu on my main system at home, customize it in every area and aspect that I wanted to (background, icons, theme, settings for firefox, mail, dock, etc) with the expection of installing proprietary drivers (graphics, NIC, etc), I would just use the generic open-source drivers. 
 
I would then make a remastered .iso of that freshly installed system. Using that .iso I would then make either a persistent install on my usb flash drive or a normal install (with grub, swap, /home, etc, on the USB). Both types of install would have a dedicaded "share" partition that would allow the user (me in this case) to share files with other OSes, primary windows and possibly OS X.
 
By doing this, I could have my "system" (personal settings, programs, etc) with me at all times, and if I needed to install it somewhere else, I could do so and that newly installed system would have my settings, programs, etc. installed on them right off of the bat; at least that is my hope. It would also allow me to update the usb system when updates come out, which would mean that when I installed it on a new computer from this usb, not only would all my settings, programs, etc. be present, but it would already be updated. :P Then, once it is on the new "dedicated" system, i.e. home desktop or laptop machine, I would install any proprietary drivers if needed.  :)
 
I could also share my files that I would have in the portable system, with any other OS (windows, os x, other linuxes).
 
I was exploring both options, Persistent file (which I have called persistent liveusb, because basically it IS a liveusb but with the addition of a persistent file for docs, photos, etc.) and full install onto the USB (installs GRUB, /home, etc. installed onto the USB) for comparision purposes, efficiency, amounut of time needed to configure/setup, etc.
 
Hopefully all that makes sense sgosnell. :P Basically, I wasnted to take my home system with me where ever I go and have acces to my programs, settings, etc but also have the option to install it if needs be and also share my files with other OSes, all from a USB flash Drive for convenience. :lolflag:
 
 
Let me know if you have any other ideas, you are helping a ton, I appreciate it!!
 
-Spydey:guitar:

---

### Post by miniyak on 2009-12-18
sgosnell must be speed reading our post, if i recall correctly we have mentioned the use of ubuntu's "usb start-up disc creator" multiple times. 

There is no general "installer" like the live cd in the admin menu nor is that option hidden in the menu items in 9.04. sgonell must be refering to the live usb creator that comes with ubuntu 9.04 and 9.10. In which I have used 5 or 6 times with no success. 

I just blew $40 on a 16gb pny attache, im not particularly interested in buying new drives till it works.. I'm _not_ using a U3 btw, that was someone else in the forums.

---

### Post by spydeyrch on 2009-12-18
> **miniyak said:**
> sgosnell must be speed reading our post, if i recall correctly we have mentioned the use of ubuntu's "usb start-up disc creator" multiple times. 
 
Yeah, that is what I was thinking. Hopefully with my last large post, it is a little clearer now.
 
> **miniyak said:**
> There is no general "installer" like the live cd in the admin menu nor is that option hidden in the menu items in 9.04. sgonell must be refering to the live usb creator that comes with ubuntu 9.04 and 9.10. In which I have used 5 or 6 times with no success. 
 
That is what I thought at first too, because I couldn''t find it either, but he did mention that one could use it to install to an internal hard drive. I am going to do a little more digging around and see what I can come up with.
 
> **miniyak said:**
> I just blew $40 on a 16gb pny attache, im not particularly interested in buying new drives till it works.. I'm _not_ using a U3 btw, that was someone else in the forums.
 
Man, I am sorry to hear that. At least you have a 16GB flash drive, right. sorry to confuse you with another person, my bad. :confused:
 
Hey, I was thinking about a different way to possibly help you.
 
1.) send you a copy of a usb that is working (send a copy of the partition images with data, not the actual USB.)
 
It might work, at least it is worth a try. Thanks for being patient.
 
-spydey:guitar:

---

### Post by sgosnell on 2009-12-18
Well, all I can say is that on my Ubuntu machine, clicking on System/Administration/Install gives me the same install program that is in the liveCD.  If you don't have it, I don't know why.  Perhaps ubiquity, which is the installer, wasn't installed on your machine.  ```
sudo apt-get install ubiquity
``` will get it for you.  

For making a .iso of your settings after you have everything like you want it, try remastersys.  It will either make a backup of your settings or make a .iso of your entire system, whichever you select.  You'll obviously need to burn that .iso to a drive, but you can use the built-in USB creator to do that, or you can use unetbootin.  I'm not a unetbootin fan, but others prefer it.

---

### Post by garvinrick4 on 2009-12-18
I have finally got a 16 gig Flash drive to work as independent system. A lot of trial and error.
Used Live CD. 9.10 64 bit and the 16 gig flash drive.
Booted Live CD and selected install.
When it got to partitioning selected USB device of course.
1st partition was 500 meg ext3  /boot as mounting point
2nd partition was 13.5 gig ext3 / as mounting point
3rd partition was 2 gig Swap

IN THE 8TH PAGE YOU HAVE TO CLICK ADVANCED TAB AND SELECT BOOT AS THE SAME
AS YOUR 1ST PARTITION  THAT YOU SELECTED AS /BOOT AS MOUNTING POINT.

 Then add your repositories such as partners, medibuntu, backports, all the same ones as your normal install. You have over 12 gig left to work with so use what you want. Compiz works fine, the only thing in Karmic I have not gotten to work is sound and every install of 9.10 on my HP G71-34OUS has
had sound issues, I will get it. WIFI came right in. Has been a normal install.

Grub menu.  When you upgrade it installs itself onto your systems grub with no partition
number such as sba1 or any device. This works well it just installs a grub selection while
plugged in to USB port with recovery selection.

                  		  		  		 		 here is fdisk.   I am running flash drive now.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris

---

### Post by spydeyrch on 2009-12-19
> **sgosnell said:**
> Well, all I can say is that on my Ubuntu machine, clicking on System/Administration/Install gives me the same install program that is in the liveCD. If you don't have it, I don't know why. Perhaps ubiquity, which is the installer, wasn't installed on your machine. ```
sudo apt-get install ubiquity
``` will get it for you. 
 
For making a .iso of your settings after you have everything like you want it, try remastersys. It will either make a backup of your settings or make a .iso of your entire system, whichever you select. You'll obviously need to burn that .iso to a drive, but you can use the built-in USB creator to do that, or you can use unetbootin. I'm not a unetbootin fan, but others prefer it.
 
 
I will give ubiquity a try. Thanks for the update. I know tha tI had seen it before but wasn't quite sure what it was called. :)
 
As far as making the personalized .iso, yeah, I was planning on using remastersys. I posted that in the very first post, but it was EXTREMELY long, so I can understand if you just scanned it and didn't catch it. I was planning on using unetbootin to try the freshly made .iso and see if my personal setting carried over and if so, then go with the usb start up installer. But, if ubiquity really will do the trick, then perhaps I can do something alittle easier and a little less complicated. We will see. 
 
I will update here once I have tried something. Thanks again for your input on this project, it is a HUGE help. :KS
 
-Spydey :guitar:

---

### Post by spydeyrch on 2009-12-19
> **garvinrick4 said:**
> Grub menu. When you upgrade it installs itself onto your systems grub with no partition number such as sba1 or any device. This works well it just installs a grub selection while plugged in to USB port with recovery selection.
 
   ..................
 
 
@garvinrick4, would you expound a little about what you were saying about grub, please. Go into a little more detail please. Use examples if possible. Thanks for your help and from the sounds of it, it looks like you got it up and running!! YAY!!!:guitar:  Are you able to install it on another computer too? Do you like the setup? What are some of the cons that you have come across and some of the pros. 
 
Let us know.
 
-Spydey :guitar:

---

### Post by sgosnell on 2009-12-19
For writing the .iso to a USB drive, consider installing usb-imagewriter.  It's in the repositories, and will write the .iso to a USB drive.  IME it's more reliable than unetbootin, which isn't reallly saying much.  I detest unetbootin for Linux.

---

### Post by spydeyrch on 2009-12-19
@sgosnell - I wasn't even aware that there existed a usb isntaller in the repos. Thanks for the info!! You have been a huge help so far, just as everyone else has.
 
One other question sgosnell, why exactly do you detest unetbootin? Have you had a bad experience with it or any other reason? I ask because perhaps we might be able to help miniyak get what he needs up and running using this alternate meathod via the repos. Thanks again for your help and input. :P
 
-Spydey:guitar:

---

### Post by sgosnell on 2009-12-19
It's erratic for me.  Sometimes it works, sometimes it doesn't, probably doesn't more often than it does.  The Windows version seems to work better than the Linux version, for some reason.  I've had too many bad burns to trust it.

---

### Post by miniyak on 2009-12-22
ubiquity wants the language info to run. looks like it is missing some dependencies to run in a full install.

there is a third live usb installer built for kde.. but i believe it is based on the same code as usb startup creator.. could be wrong though

ill try it latter

---

### Post by spydeyrch on 2009-12-22
I installed ubiquity just fine. I don't know what dependancies are missing. I am running 9.04.
 
Have you tired the KDE version of the usb starter app yet? What is your opinion on it?
 
-Spydey :guitar:

---

### Post by deathbyswiftwind on 2009-12-27
> **spydeyrch said:**
> 
As far as making the personalized .iso, yeah, I was planning on using remastersys. -Spydey :guitar:

Okay your saying if I get my system to the way I want it (all apps and codecs and settings and then run this app it will make a backup of my whole current system to an iso and then from that when I run the cd/usb I create from that iso and install it it will be just like my system is now?

---

### Post by sgosnell on 2009-12-27
That's the way it's supposed to work.  I must admit that I haven't done a full restore using this, although I have made the .iso files.

---

### Post by deathbyswiftwind on 2009-12-27
I just tried to install remastersys but its asking me to uninstall grub-pc and install grub. So Im wondering is there any advantages to grub2? If not I wouldnt mind doing it but if there is something better I get from grub2 then I guess im screwed.

---

### Post by spydeyrch on 2009-12-29
Alright guys,
 
so Santa was so very kind to gift me a 16GB flash drive. I have to try everything that we have discussed so far in this trhead. Lack of time and needs of my kids have made it difficult. Plus my kids have priority over computer stuff. :P
 
I will report back once I figure out if it works and what doesn't. :)
 
@deathbyswiftwind - wish I could help you with your question but I don't know too much about the differences between grub and grub2. perhaps starting a different thread asking about the differences/advantages/disadvantages would get you some answers and then you could come back here with them. good luck and keep us informed. :KS
 
-Spydey  :guitar:

---

