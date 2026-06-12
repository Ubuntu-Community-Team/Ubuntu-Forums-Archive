---
title: "Need help. total novice"
date: 2011-04-27
forum: General Help
---

### Post by Apis4 on 2011-04-27
HI people, I hope this is the right place to ask, I figured I will try. 

I have two questions. 

Firstly.. I installed Ubuntu, to access my HD after a KSOD in Vista. Which I can, but I dont know what anything means... anyone ever repair this issue through using this OS to get into the borked one?

Secondly, I seem to have about 40+Gig free on my HD.. BUT.. Ubuntu only used 3gig.. I think I went with basic intall.. because I dont know what I am doing.. can I change this? I mean fairly simply change it.. and grab the other 37 GIG... or even half that? 

I will end this by saying I am a complete PC novice, but when my hell of alot more PC Savvy fiance ran into problems accessing XP on her Laptop, she loaded this OS, and some how got into something.. and fixed it all. 

I am desprately hoping I can do the same here, simply because as awesome as this is as an OS, its not for the PC inept, and being able to generally use Vista, fixing the black screen of death, for most things, anf just this for those neato little things you can add to this OS to do things online and what not that MS OS just cant do, would make things so simple.

---

### Post by Apis4 on 2011-04-27
Well maybe anyone who has some answers could just send me a message on the PM thingy.  Thanks.

---

### Post by ki4jgt on 2011-04-27
Depends on what caused the KSOD. Yes you can change this. You would have to look into partitioning your hard drive from the Ubuntu CD. Instead of clicking install, you would just click Try when you first use it. I personally don't use Ubuntu anymore I've moved onto a derivative of it, (So I can't remember exactly how this goes. but you can look up "Partitioning an Ubuntu install" on Google. Make sure you keep your Windows partition b/c if you don't, you will end up losing all your files. Because you can't say specifically what caused your KSOD to happen (Your fiance probably knew) I don't think we'd be able to assist you. So If I were you, I would backup all my personal files off of your Vista system and then reinstall Vista or stick with Ubuntu.
Generally your files are C:/Users/Your-Username/
You can find all your personal documents there, just copy them from the HDD to a USB drive.

---

### Post by Apis4 on 2011-04-27
Well I already installed Ubuntu... I need to know if I can, with Ubuntu installed.. go for grabbing that extra 30 odd Gig of disk free space for Ubuntu? 

My KSOD was caused by an attempted System Restore, after my screen began locking up and flickering, at first in games, then just in general, I managed a restore from Safe mode.. to 10 days previous.. but then I was using outdated Java/Flash.. (not really sure what they, sound like coffee brands).. and needed to update them, but couldnt because of a missing Windows Security thing.. so I system restored to just 2 days previous.. and boom, System Restore went through, but KSOD was the result. 

So.. do I have to uninstall Ubuntu, or what... to get me this extra space? Or can I do it from within Ubuntu?

---

### Post by grahammechanical on 2011-04-27
Installing another operating system alongside the original one will allow you to copy all your data and documents out of the old operating system and into the new one. Then you can re-install Vista and you do not lose important files. Linux operating systems will let you do that because they can read and write to Windows file systems. But you cannot do it the other way around because Windows does not recognise Linux files systems.

If you need you need to change or edit Windows system configuration files in order to get Windows working again then you can use a text editor in Ubuntu called Gedit or just text editor on some menus.

You do not say what is wrong with your Windows Vista installation. How can anyone advise you on how to correct it? We do not know what is wrong. A BSOD can happen for any number of reasons. Perhaps a Microsoft forum is the best place for this kind of help. Or, simply re-install the operating system.

I would suggest that you clarify what it is you want from us. Help in using Ubuntu to copy files out of Windows? Help fixing Windows? Or help changing the partition sizes of the hard disc.

Regards. Oh, by the way, be patient.

---

### Post by Blasphemist on 2011-04-27
Can you tell us what choices you made during the install of Ubuntu? Did you choose to install along side another OS, windows, and do you now get a screen that gives you a choice of which OS to load when you boot?

How are you seeing that Ubuntu only used the space you describe? If Ubuntu only used a little space it was likely unable to compress the windows installation due to fragmentation of the windows installation or just not much space available. 

You should already be able to get to the files you have in windows and make a copy of them for backup purposes. In the Ubuntu file manager, to use windows terminology, you should see in the left pane a folder that is the windows partition. This could have a name that is just letters and numbers but it should be there. I'd do this first so you don't loose anything no matter what you do. Copy these files to a cd or usb if you can.

You can run a program called GParted in Ubuntu and attach a screen shot to let us see the partitions that would help us. If you have any troubles, pass us as much detail about it as you can. I have included screen shots from my system of what I've described here.

---

### Post by ppv on 2011-04-27
> **Apis4 said:**
> HI people, I hope this is the right place to ask, I figured I will try. 

I have two questions. 

Firstly.. I installed Ubuntu, to access my HD after a KSOD in Vista. Which I can, but I dont know what anything means... anyone ever repair this issue through using this OS to get into the borked one?

Secondly, I seem to have about 40+Gig free on my HD.. BUT.. Ubuntu only used 3gig.. I think I went with basic intall.. because I dont know what I am doing.. can I change this? I mean fairly simply change it.. and grab the other 37 GIG... or even half that? 

I will end this by saying I am a complete PC novice, but when my hell of alot more PC Savvy fiance ran into problems accessing XP on her Laptop, she loaded this OS, and some how got into something.. and fixed it all. 

I am desprately hoping I can do the same here, simply because as awesome as this is as an OS, its not for the PC inept, and being able to generally use Vista, fixing the black screen of death, for most things, anf just this for those neato little things you can add to this OS to do things online and what not that MS OS just cant do, would make things so simple.

So, 1) You want to recover the ksod in vista using ubuntu? Or just recover the files stored in Vista using Ubuntu?
2) Still keep ubuntu and use the hard disk space? how did u check that you cannot use the other 37G?

---

### Post by Apis4 on 2011-04-27
I wanted to know.. if anyone had like.. idk.. made sticky keys or task managers, which are the most direct routes with a Black Screen of Death.. apprently.. work through Ubuntu.. or some other tricks to get access to the tools, or mimic the tools, of the most common basic fixes for the condition. Now. thats not somehting anyone at a MS forum is likely to have done.. is it? I mean, if I asking if anyone has used Linux, specifically Ubuntu, becuase is seems to the one my fiance used due to there being ALOT of people having used THIS os of Linux for getting to and fixing borked XP.. well.. if I am asking that.. doesnt it make the best sense to ask a Ubuntu forum? Isnt this where the Ubuntu people are? 

I thought I was pretty clear. I dont mean to be unappreciative.. but I cant be much clearer... 'Anyone fixed a Black Screen of Death in Vista by using Ubuntu to get in and access ... well what ever (enabling the task mangers ctrl-alt-del hot keys for example)'... and A).. alot of Linux users use dual OS, and of that very large number, many seem to run Ubuntu. 

B).. how would anyone using a MS OS be able to answer that Q? 


Now.. part two>? 

YES.. I ALSO.. want help in expanding the size of the partition I used for Ubuntu.. there has to be a way, surely.. I am hoping its rather easy for a PC novice to do, because if I can grab the extra 30 gig.. I should be able to use this system for a bit until I find someone who can answer Q.1.. as it is atm, I only have 145.8 MB... of 3 GIG, free.. and desperately need to grab some more space... theres 310GIG on the HD.. and only 270 of its being used via Vistas section.

---

### Post by ppv on 2011-04-27
1) Have you tried booting into Vista again after ksod. If yes, what happens.
2) From Ubuntu, pls post the screenshot of Gparted that Blasphemist suggested.

---

### Post by Apis4 on 2011-04-27
I dont know why I only got 3Gig.. I cant really explain much, I dont kow anything about PCs, jyust tools for the net and the odd game I play.. and of course, a couple of metaverses and networking sites I use to keep in touch with partner who lives on another continent atm after some crazy immigration issues.. 

So, I dont really know HOW or WHY its only using 3 Gig.. I just know it is.. it is telling me theres only 3 Gig of Space.. 3.5.. and of that.. only 145.8 KB remain.. where as the other partion only uses 270GIG of a 311GIG HD.. 

As to if I want to move files from Windows using Ubuntu.. no.. thats self evident.. but I have had experiences in the past of people accessing and activiating/repairing, things in their Windows after BSOD or Black Screen of Death, by loading Linux, and working on their stuff from there.. simple things like activating the short cut for getting task manager working etc etc... but seems they;re all incommunicado.. so, leaves me with asking the most likely place I might find an Unbuntu user.. here.. well.. it makes sense to me. 

So.. asside from my off chane hoping someone using a dual system, or having had MS OS of Death issues and used Ubuntu as a fix reading this and being able to help me... how can I make this ubuntu OS get more space?

---

### Post by ki4jgt on 2011-04-27
Sorry, LOL my bad. I jumbled my sentencing together and missed half the steps :-)

look up "How to partition Ubuntu LiveCD GParted" on Google

It doesn't matter that you have it already installed

You will be partitioning the HDD from the CD, so when you're done looking up how to partition. . . It's kind of hard to explain without pictures. Plus like I said, I no longer use this OS, but a darivative, so I don't remember exactly.

Insert the liveCD

Restart your computer

Boot from it

When it asks if you want to install or try it. . . try it

When you get to the desktop and everything is loaded, Hold down ALT and press F2.

Type gparted into the blank and press "ENTER"

This will allow you to mess with your Ubuntu/Windows install. and the hard drive space alloted to them both. Do not mess with anything beside those respective spaces. If you can not shrink one beyond a certain point, it is because that partition is full and probably needs to be stretched a little (For breathing room)

You still need to know more details on the KSOD issue, like what is causing it, system restore is too vague. It may be some files are out of place or that a very important file was not written correctly. Your best bet is to MAKE SURE YOU HAVE ALL OF YOUR FILES backed up and then reinstall Windows or if you want to just use Ubuntu simply reinstall it using all of your hard drive. You may use them both, but to get Windows back up, it would be best to start from scratch. Reinstall Windows and then Ubuntu.

To backup your files:
simply visit your hard drive and navigate to /Users/Your-Username from the LiveCD or your Ubuntu install. and copy the files you want onto a USB flash drive.
If you have saved files elsewhere, you need to know where they are, otherwise you're just going to get all the files in the My documents/pictures/music and all the other document folders Vista has. You'll also get your Desktop files. If you have anything saved in another location on your computer, you'll have to find it yourself. There are just too many folders to look through.

---

### Post by Apis4 on 2011-04-27
OK cart before the horse here.. for me.. whats gparted, do I need a CD? I dont knowif I have to hand and its not likely I will get one tonight.. and I dont know how to print screen shots.. I dfont even know if I have enough space to save any.

---

### Post by ppv on 2011-04-27
There could be various reasons for black screen of death, and not sure but probably there will not be something like activating "ctrl+alt+del" from Ubuntu and the ksod gets fixed. 

For this, it would be better to use Vista disc and try the recovery mode, but before that you may want to backup all your files using Ubuntu. Backup files first.

If you can let us know, what happens when you try to boot back into Vista maybe there could be some options.

For your partition issues, pls post the screenshot and also tell how did you install Ubuntu.

---

### Post by Apis4 on 2011-04-27
Lve CD? is that the CD I would have burnt to get the OS onto disc?

---

### Post by ki4jgt on 2011-04-27
> **Apis4 said:**
> OK cart before the horse here.. for me.. whats gparted, do I need a CD? I dont knowif I have to hand and its not likely I will get one tonight.. and I dont know how to print screen shots.. I dfont even know if I have enough space to save any.

Read my comment.

---

### Post by ki4jgt on 2011-04-27
> **Apis4 said:**
> Lve CD? is that the CD I would have burnt to get the OS onto disc?

Yes.

---

### Post by Apis4 on 2011-04-27
I installed Ubuntu from a CD. I dont kow HOW to post screen shots. 

 KSOD can be fixed in most cases, it seems, from massive ammounts of data I collected, by setting MSCONFIG data a certain way, and disabling old logs, enabling a newly created folder,these can be done through accessing task manager.. which requires the hot keys activated, which one cant do, once the KSOD has been activated, if disabled previously.. but one could perhaps access something within the OS via the HD if one could access it one would assume.. which one can through this OS.. .. I know it must be really hard to fathom, for some people.. I am sure.. I know I dont speak geek.. no insutls inteneded.. but I know a few tricks to fix the issue and save my only PC which I can in no way afford to replace.. so I kinda figured wouldnt hurt to ask.. though it is hurting a bit now....not to be rude.. but seriously. I dont know how many more ways I can say simply, that I know poeple have fixed mega bugs in XP, and at least BSOD in Vista, by making some simple tools which wouldnt work normally, work by accessing the MS OS via the HD accessed through this OS.. 


Now.. as for the partition.. I cant just do as asked.. because I dont know what you are asking.. yet.. bare with me.. and I will learn, and do, and psot pics even if I can.

---

### Post by Apis4 on 2011-04-27
OK gonna restart my PC and hope for the best, if it asks me to just tyr.. I will do that gparted thing. 

Thankls you

Xs fingers

---

### Post by ki4jgt on 2011-04-27
> **Apis4 said:**
> I installed Ubuntu from a CD. I dont kow HOW to post screen shots. 

 KSOD can be fixed in most cases, it seems, from massive ammounts of data I collected, by setting MSCONFIG data a certain way, and disabling old logs, enabling a newly created folder,these can be done through accessing task manager.. which requires the hot keys activated, which one cant do, once the KSOD has been activated, if disabled previously.. but one could perhaps access something within the OS via the HD if one could access it one would assume.. which one can through this OS.. .. I know it must be really hard to fathom, for some people.. I am sure.. I know I dont speak geek.. no insutls inteneded.. but I know a few tricks to fix the issue and save my only PC which I can in no way afford to replace.. so I kinda figured wouldnt hurt to ask.. though it is hurting a bit now....not to be rude.. but seriously. I dont know how many more ways I can say simply, that I know poeple have fixed mega bugs in XP, and at least BSOD in Vista, by making some simple tools which wouldnt work normally, work by accessing the MS OS via the HD accessed through this OS.. 


Now.. as for the partition.. I cant just do as asked.. because I dont know what you are asking.. yet.. bare with me.. and I will learn, and do, and psot pics even if I can.

Could you post a link to this data you've collected about fixing KSOD? and reinstalling will not break your computer in any way. It often runs fast after a reinstall. Software can not in anyway break hardware. It can cause the hardware to break itself by telling it to, but it can't actually break it. The hardware has to be instructed to overheat or to destroy itself in some way, so just as long as you're not telling it to do something, you will NOT break it by simply using programs.

---

### Post by ppv on 2011-04-27
It is ok if you do not speak certain terminology and it is also ok that if all posted things do not make sense. Just try and see if what is being asked can be done by you. If it does, then it can help others to help you solve the problem. Do post your results after the reboot.

---

### Post by Apis4 on 2011-04-27
ki4jgt: I will PM you some links, when I sort this partition issue out.. but theres alot of data out there.. YT is a good place to look.. and most of it says the same things, about msconfig, and disabling the logs. As for reinstall.. this PC came with it preloaded, no disc, no back up, I was out of the country for 2-1/2 yrs, and returned to find nothing such as back up discs had been made in that time on this machine.. I couldnt make them, as the system was being unstable since just before I got back.. we have had it fixed.. but they effed it more it seems.. if I can access, and save, and stabalise Vista though, I can possibly sort it out enough to get it to a point where making a backup restore CD makes sense. 

Now.. as for the partion.. I have gparted open... 

its telling me something call dev/sda1 is using 6/47 Gig.. called NTFS WinRe

dev/sda 3 is 3.29 GB called extended

dev/sda  5 is 3.09 GB called ext4

dev/sda 6: linux-swap is using 205.00MB


Somehting called dev/sda 2 is using 288 GB called ntfs..

and theres 1.34MB unallocated...

for a tolal of 298GB.. on a 320GB HD.   

but there is seemingly no option of extending my Linux into that spare 22GB..

---

### Post by Apis4 on 2011-04-27
Oh I dont have an programe to paste and save images into on this things.. I dont think.. running this.. atm.. so I cant past a screen shot

---

### Post by Apis4 on 2011-04-27
but.. from here.. right now.. I could wipe the HD containg everything from Vista.. to hell with what I lose.. and dedicate that to Ubuntu, right? And then have room to install all the things I need to make this OS work just as well as vista did, yeah? Like Flash and Java and Quicktime and propritary dreivers for graphics etc etc?

---

### Post by Apis4 on 2011-04-27
OK I just bit the bullet.. there was nothing irreplaceable on this PC, so I deleted the BIG partition.. the one using Vista.. kaput.. gone.. but now it WONT let me increase the size of the Linux partition, do I need to reinstall Ubuntu over the already installed one now, to access the almost 300GIG of free space I now have?

---

### Post by Blasphemist on 2011-04-27
It may depend on how you deleted the partition but yes, at this time you might as well reinstall Ubuntu and choose the option to erase the disk and reinstall.

---

### Post by ki4jgt on 2011-04-27
> **Apis4 said:**
> ki4jgt: I will PM you some links, when I sort this partition issue out.. but theres alot of data out there.. YT is a good place to look.. and most of it says the same things, about msconfig, and disabling the logs. As for reinstall.. this PC came with it preloaded, no disc, no back up, I was out of the country for 2-1/2 yrs, and returned to find nothing such as back up discs had been made in that time on this machine.. I couldnt make them, as the system was being unstable since just before I got back.. we have had it fixed.. but they effed it more it seems.. if I can access, and save, and stabalise Vista though, I can possibly sort it out enough to get it to a point where making a backup restore CD makes sense. 

Now.. as for the partion.. I have gparted open... 

its telling me something call dev/sda1 is using 6/47 Gig.. called NTFS WinRe

dev/sda 3 is 3.29 GB called extended

dev/sda  5 is 3.09 GB called ext4

dev/sda 6: linux-swap is using 205.00MB


Somehting called dev/sda 2 is using 288 GB called ntfs..

and theres 1.34MB unallocated...

for a tolal of 298GB.. on a 320GB HD.   

but there is seemingly no option of extending my Linux into that spare 22GB..

Sorry for leaving there for a bit. . . Family probs. . . I just wanted the links to find out what you wanted to do, but if you're taking Windows completely off, then you don't have to do that. As far as the programs you can install on it, 

> but.. from here.. right now.. I could wipe the HD containg everything from Vista.. to hell with what I lose.. and dedicate that to Ubuntu, right? And then have room to install all the things I need to make this OS work just as well as vista did, yeah? Like Flash and Java and Quicktime and propritary dreivers for graphics etc etc? 

Just as well, is only definable by you. Flash and Java will work. I don't know if Ubuntu has a quicktime but I know it supports all the graphics I've ever needed it to. It doesn't get viruses, but you have to understand that LINUX based OSs are NOT WINDOWS compatible. They require different software, and windows software is completely incompatible with Linux. Most windows programs have an even better Linux alternative, but rare software (Like my dad's wood working program) have yet to be replicated on Linux. But for the most part, Linux can do everything Windows can, it just has to have a program designed for it. It is more resilient to viruses and hackers. Virus is defined as a program which can run itself, on Linux this is impossible. You have to run the program (Which means a virus can't get around on linux computers) but a worm doesn't. It can find a hole in other software. This is why you always need to keep your system up to date.

---

