---
title: "bad update in 10.04 causes no start how to revert?"
date: 2010-04-18
forum: General Help
---

### Post by dartdog on 2010-04-18
After much pain I finally got a fairly good install of 10.04 (apparently due to my large disk earlier versions like 9.1 are a no go on my machine a Gateway mx6028 laptop with a new 160 gb drive.)

I bricked the machine several times applying the bulk auto updates after the initial install  so this last time I applied the updates in smaller batches,, I believe the problem is associated with some of the open GL stuff,, any way to 
A) go back one update?? 
and 
B) anyway to permanently mark an update to never come in?

---

### Post by klemes on 2010-04-18
a. I don't think there is an easy or not even a hard way in most cases to go back once an update has been applied.

b.maybe you should google up apt-pinning for that purpose but what update could it be that which you definately don't want and why is that?

and c. note that most updates have dependencies that must be also satisfied so be very cautious when breaking up offered update packages into partial upgrades.

---

### Post by dartdog on 2010-04-18
Well the update I don't want is the one that is bricking my install :-)
I believe it is the open GL updates..
I was successful in installing several hundred updates in blocks,, rebooting after each set then did that series and could no longer start up..
So I'd like to permanently remove them from the auto-update list.. as well as a bunch of other stuff I don't need like thai language support and various bluetooth things since my machine does not have  as well as updates for all the graphics adapters my machine does not have..

---

### Post by klemes on 2010-04-18
The fact that you are offered an update means that you ALREADY have this particular package in your system taht is being updated.
So I cannot understand how an update (propably bug-fix or security update never mind )to an ALREADY installed package in your system can break your and only yours system without affecting the others.
Anyhow both the procedures of committing to a certain version of a package and removing packages from your system require the use of command-line and if you are not familiar with that you must leave it be for the moment.
But for answering your question there is no way once a specific package is installed in your system to not to be offered an update from update-manager once one such becomes available in the repositories.

---

### Post by klemes on 2010-04-18
The fact that you are offered an update means that you ALREADY have this particular package in your system that is being updated.
So I cannot understand how an update (probably bug-fix or security update never mind )to an ALREADY installed package in your system can break your and only yours system without affecting the others.
Anyhow both the procedures of committing to a certain version of a package and removing packages from your system require the use of command-line and if you are not familiar with that you must leave it be for the moment.
But for answering your question there is no way once a specific package is installed in your system to not to be offered an update from update-manager once one such becomes available in the repositories.

---

### Post by dartdog on 2010-04-18
Thank you for your reply,, I sure don't know why that particular update is crashing my machine but in fact it is.

I'm also not sure why I'm getting all the video drivers for radeon, ati and intel,, I only have intel... And I never asked for thai language packs! (even though I really like the Thai people...)

Further I would love a pointer to the un-install on packages (command line)

---

### Post by dartdog on 2010-04-18
There must be some "better" practices so I don't have to reformat everything when an update goes bad,, I'll be really risking my data??

So far for various reasons I'm going on 10+ installs 2 successful So I clearly need some better idea how to just do the OS/apps wo affecting data (once I get to using the system)

---

### Post by dartdog on 2010-04-18
FWIW the main reason for the 'excessive" re-installs is that the install is not properly giving me a new "virgin" Grub loader.. so I end up having to go through excessive gyrations to reformat the disk so I get a clean install..with an operative Grub... It is a mess...

---

### Post by J V on 2010-04-18
Tried using an older kernel version? (At the grub menu)

---

### Post by dartdog on 2010-04-18
Unfortunately the Grub is a big part of the problem,, apparently the earlier versions cannot support my HD I now have it running again on 10.04 and must now carefully "update" the install, I think avoiding the newer open GL stuff... If my experiments are correct :-)

---

### Post by Mark Phelps on 2010-04-18
At least for now, 10.04 is still in the testing stage -- not ready for release yet.  So, there are bound to be things to don't work, and it's not unlikely that an update might "break" what was there before.  That's what testing versions do sometimes.

But the problem with doing a roll-back is the same regardless of the version of OS being used -- there basically is no built-in Ubuntu equivalent of MS System Restore.

Your best bet to insure against update-related problems is to back up your setup before applying the updates.  There are a variety of free solutions available: remastersys and clonezilla being two of the most popular.

---

### Post by dartdog on 2010-04-22
Remastersys FTW but I have to do the backup PRIOR to installing all the Open GL updates,, a backup taken after does not work,, even though the system does,, none the less having the remastersys backup saves a bunch of time.. Still worried about this video issue as it requires a complete reformat to get working as it is tied up in Grub and the mbr in a way I don't know how to fix

---

### Post by snake anthony on 2010-04-22
For the record, I had the same problem with the last batch of updates.  I'm using an older Acer Travelmate 290 notebook, with which 9.10 had some sort of major incompatibility graphics processor-wise.  I'm trying a re-install now and will post again if I trace the problem to the same open-gl update.

---

### Post by dartdog on 2010-04-22
Have found that there is a Known problem with older Intel Graphics,, in the release notes,, 10.04 ([http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)) Two suggestions modify the Grub 2 boot loader and possibly try other default Intel "experimental" drivers...

I was trying to modify the grub file but it is marked read-only.. so not sure how to fix that,, (I am a newb) I was also looking at the "new driver" described sort of here [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and..[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 

but not sure how to get that either...
Got to break from this...
I just want a working system!! that does not blow up when I update it..

---

### Post by klemes on 2010-04-22
To install the latest drivers from xorg-edgers for Intel (and not only I am afraid- I am saying that because you get all the nouveau stuff as well)
you must first add the repository with the following command typed in a terminal:

```
sudo add-apt-repository ppa:**xorg-edgers/ppa**           
```After that you must do a sudo apt-get update to update the software sources
and after that a  sudo apt-get dist-upgrade to upgrade your drivers and also various xserver-xorg files.
Keep in mind that the drivers in the above repository are the latest meaning that they may not be the most stable available,in fact they used to have a disclaimer that they can break your X installation.However I used them and still use them in Karmic and they did not give me any (extra) trouble but also they did not fix the problem that I 've installed them for solving for in the first place.In any case you have been warned....;)

---

### Post by dartdog on 2010-04-22
Thanks for the instructions,, can someone also point me how to make the change in the etc/default/Grub file which only opens for me as read only?? seems to me this might be a cleaner quicker solution.

---

### Post by DawieS on 2010-04-23
I also had the same problem after the last update. I am using 10.04 beta2 on a desktop.

It seems as if my graphics card does not  support the new default graphical GRUB display. My machine locks up  hard, and I had to unplug the power to be able to reboot.

I found the following solution:
Boot from another working installation, or a Live CD. Mount the  10.4beta2 partition, and enter the following in a terminal:
```
sudo gedit /etc/default/grub
```Uncomment the following line, by removing the '**#** '  character:
```
# GRUB_TERMINAL=console 
```Save and reboot. The grub menu should now work as before.:smile:

---

### Post by dartdog on 2010-04-23
Wow thanks,, Can't wait to try!

---

### Post by dartdog on 2010-04-23
Well I put in "both" Grub mods,, no joy nomodetest and uncommented the graphics console line... So now I guess I'm up for driver fiddling... Still don't get why I get beta2 working (and thank goodness I made a good backup with remastersys that is allowing me to restore fairly quickly) and then the updates trash me...

---

### Post by dartdog on 2010-04-23
Finally some good news I used this from Klemes: (Thank You:popcorn::popcorn:):
I'm not sure what you can do if you do not have a Bootable live cd,,, this fix adds some code that at least errors out and says it cannot detect the graphics mode,,

 >>>>>seems to me this should be on the live CD<<<<<<

so I can ask the system to run in "low Graphics" mode,, which at least so far look fine. 

Now if I can set this for good I think I'm good to go... The new driver also seems to provide some debug info so maybe I can figure out how to et that to the xorg people...

Also need to make a new bootable backup with remastersys...

To install the latest drivers from xorg-edgers for Intel (and not only I am afraid- I am saying that because you get all the nouveau stuff as well)
you must first add the repository with the following command typed in a terminal:

Code:
sudo add-apt-repository ppa:xorg-edgers/ppa
After that you must do a sudo apt-get update to update the software sources
and after that a sudo apt-get dist-upgrade to upgrade your drivers and also various xserver-xorg files.
Keep in mind that the drivers in the above repository are the latest meaning that they may not be the most stable available,in fact they used to have a disclaimer that they can break your X installation.However I used them and still use them in Karmic and they did not give me any (extra) trouble but also they did not fix the problem that I 've installed them for solving for in the first place.In any case you have been warned....

---

### Post by dartdog on 2010-04-25
Well unfortunately when I had my last issue  (probably self inflicted,, but any way) I could not restore using my remaster sys disk. It kept handing control to the broken system disk.. I could not reinstall from any version of Ubuntu install,, in any sequence,, even after running Gparted standalone... so having no choice I tried Fedora13 beta and it just flat installed.. no complaints...So while I liked and wanted Ubuntu it seems that it is not a possibility on my Gateway MX6028 sadly...The install on Fedora seems at least in this instance to be more robust....

---

### Post by klemes on 2010-04-25
Sorry about your troubles with Ubuntu and wish you luck with your new choice.!!!



You fought hard and brave but it was an unequal battle You against the Machine lol......

:guitar::guitar::guitar::guitar::guitar::guitar:


What can I say sometimes we must make hard decisions however we must make them....... :)

---

