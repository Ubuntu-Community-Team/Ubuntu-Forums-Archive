---
title: "Certain things become extremely unresponsive"
date: 2009-09-10
forum: General Help
---

### Post by tauntedflail on 2009-09-10
For example when I click System > Preferences > Display.

Everything will start to lag like mad, I can hardly move the mouse. A weird black bar appears that sort of flashes across the middle of the screen every now and then. This happens with various other things, too, such as installing some software or using WINE. Is this a well known issue? I cant find it being asked anywhere else on the forums. It happens regardless of whether I'm using screen effects. I installed a 3D game just to check the graphics card was working properly, Extreme tux racer. This works fine with 120+ FPS (I have installed a driver for my card using System > Administration > Hardware drivers) So I dont think its my GPU (radeon x2600)

What can I do? Thanks.

---

### Post by ckonestroh on 2009-09-10
Sounds like a mouse problem..

Replace the mouse bought a cheap one at TJ MAX... Got it for 10 bucks... Works great no driver issue?????

Didn't need a driver picked it up and runs great...

You might want to look to see if your video card is supported and maybe people are having problems with that video card????


later....



good luck...

---

### Post by tauntedflail on 2009-09-10
> **ckonestroh said:**
> Sounds like a mouse problem..
 
Replace the mouse bought a cheap one at TJ MAX... Got it for 10 bucks... Works great no driver issue?????
 
Didn't need a driver picked it up and runs great...
 
You might want to look to see if your video card is supported and maybe people are having problems with that video card????
 
 
later....
 
 
 
good luck...
 
Hehe, thanks for the reply - but no it isnt a mouse problem. Its like the CPU is getting so clogged up it can barely move anything else. My mouse is fine, if I dont click something like what I said above then everything works fine.
This is on a vista system, with vista still installe - if that helps.
As for the video card thing, it is supported - I checked.

---

### Post by P4man on 2009-09-10
Have a look in system monitor (in system > adminstration)
Perhaps something (like Xorg?) is leaking ram badly leading to excessive swapping, or some other process went berserk.

---

### Post by tauntedflail on 2009-09-10
> **P4man said:**
> Have a look in system monitor (in system > adminstration)
Perhaps something (like Xorg?) is leaking ram badly leading to excessive swapping, or some other process went berserk.

Thanks for the help, but it doesnt show me much of anything.. just that my CPU useage has maxed to 100%.

Whatever is causing the issue, its causing it during the loading of WINE or whatever, once its fully loaded the CPU usage returns to normal. I just don't understand, is there something I have missed while installing? after installing with the disk, I instaled the new updates and installed my graphics driver. Is that it? Or have I missed some steps?
Thanks again guys.

---

### Post by P4man on 2009-09-10
> **tauntedflail said:**
> Thanks for the help, but it doesnt show me much of anything.. just that my CPU useage has maxed to 100%..

Well, that *is * "much of something" :)

What process is hogging the cpu ?  Have a look in the process tab (and make sure in "view" you select ALL processes, not only yours.

---

### Post by ckonestroh on 2009-09-10
> **tauntedflail said:**
>  This works fine with 120+ FPS  So I dont think its my GPU (radeon x2600)

Ok, I get what your talking about gaming on linux machine....

What can you do ????

Better yet you should put this question in the Gaming and Leisure Forum????

---

### Post by tauntedflail on 2009-09-10
> **P4man said:**
> Well, that *is *"much of something" :)
 
What process is hogging the cpu ? Have a look in the process tab (and make sure in "view" you select ALL processes, not only yours.
 
Unfortunatly I cant see what process is bogging the machine down because clicking 'display' causes everything to become unresponsive and greyed out.
I'm stumped.. :S.
 
> **ckonestroh said:**
> Ok, I get what your talking about gaming on linux machine....
 
What can you do ????
 
Better yet you should put this question in the Gaming and Leisure Forum????
 
Well this problem has nothing to do with gaming... I dont see what you're trying to say?

---

### Post by tauntedflail on 2009-09-11
Sorry to double post, but I just wanted to bump this topic in the hopes that someone has heard of this problem before or has any suggestions.

---

### Post by P4man on 2009-09-11
try something else then; open a terminal and run "top". Keep it visible, then open something you know causes it slowdown.

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> try something else then; open a terminal and run "top". Keep it visible, then open something you know causes it slowdown.
 
Thanks! That did the trick. All the CPU is being hogged by xorg, just like you said.
Where do I go from here?

---

### Post by P4man on 2009-09-11
before trying to hunt down a bug thats already fixed, have you installed all available updates for you system?

If you have, then tell me how much memory xorg is using, and if the problem occurs also right after a fresh boot, or only after some time of usage?

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> before trying to hunt down a bug thats already fixed, have you installed all available updates for you system?
 
If you have, then tell me how much memory xorg is using, and if the problem occurs also right after a fresh boot, or only after some time of usage?
 
Xorg took up 30%-50% of my memory, it fluctuated a bit. I installed all of the available updates when I installed. They didnt throw up any errors when installing. On a fresh install of ubuntu I dont get the error, everything runs wonderfully and I can open most applications without problem. I could go to the driver update thing, for instance, and it worked fine. I could open up various games without issue. However whenever I click 'display' or other things (such as starting WINE) xorg takes up all of the memory - I get a black bar that occasionally flashes on the screen and whatever i'm trying to load takes a long time. However, once it has fully loaded then everything runs smoothly again (under some circumstances).
Sometimes, like when clicking 'display' the CPU hogging wont go away and even when I restart the computer, it remains on the reboot. Eventually it does go away.. but when or why I couldnt tell you.

---

### Post by P4man on 2009-09-11
Im confused. are you saying the problem does not occur on a fresh install (after installing wine and videodrivers) but does occur once you do an update?

Also, you say xorg uses 50% of your memory (ouch!). How much is that? Xorg shouldn't use more than 100-150 Mb or so. If its using >250 its a bug or memory leak in xorg or in the videodrivers. Again, let me ask: does this occur on a fresh boot, does xorg use 50% of your ram  then (and how much is that?) or only after using the machine a while or only after running a wine app or similar?

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> Im confused. are you saying the problem does not occur on a fresh install (after installing wine and videodrivers) but does occur once you do an update?
 
Also, you say xorg uses 50% of your memory (ouch!). How much is that? Xorg shouldn't use more than 100-150 Mb or so. If its using >250 its a bug or memory leak in xorg or in the videodrivers. Again, let me ask: does this occur on a fresh boot, does xorg use 50% of your ram then (and how much is that?) or only after using the machine a while or only after running a wine app or similar?
 
Sorry. The problem does occur on a fresh install. From the second I install ubuntu the problem is there. All I have to do is click 'display' to trigger it off.
I'm going to try it before installing the updates, as I havent done that yet. Will edit back.
 
EDIT: Okay I just checked the memory usage again and I was wrong. Its 3.2, not 32 :P. My bad!
Does that help at all? or should I go ahead and reinstall the entire thing.

---

### Post by P4man on 2009-09-11
> **tauntedflail said:**
> Sorry. The problem does occur on a fresh install. From the second I install ubuntu the problem is there. All I have to do is click 'display' to trigger it off.

So to be clear, this problem happens even *before* you installed the restricted ATI drivers through system>adminstration>hardware drivers? Does it occur in a livecd session?

> or should I go ahead and reinstall the entire thing.

Thats not likely to help if the problem occurs on a fresh install...

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> So to be clear, this problem happens even *before* you installed the restricted ATI drivers through system>adminstration>hardware drivers? Does it occur in a livecd session?
 
 
 
Thats not likely to help if the problem occurs on a fresh install...
 
I just checked the livecd session and the error does *not *occur! After clicking display it will load up instantly without any fuss.
 
As for whether it occurs before I install the ATI drivers, I couldnt tell you for sure. I'm prtety sure it did happen before that, but like I said - i'd need to do a new install to be sure.

---

### Post by P4man on 2009-09-11
Well, everything seems to suggest a problem with the ATI drivers. You can test that without reinstalling, just run the "hardware driver" applet again, and disable your current driver. Upon reboot, it should revert to the opensource ATI driver. See if the problem persists (mind you, the opensource driver will probably not give you acceptable 3D performance, if anything 3D works at all).

If it turns out to be the ATI driver, you perhaps try and see if there is a newer one available from ATI, though its usually a bit tricky to install them from there.

---

### Post by bruno9779 on 2009-09-11
before doing a fresh install maybe you could try disabling ATI driver

---

### Post by tauntedflail on 2009-09-11
I just disabled the driver, and the problem is still occuring with it removed. So it cant be that..
Perhaps the issue was introduced with one of the automatic updates that install when you first run ubuntu?
 
EDIT:
Would you guys like my DXDIAG from windows vista? Would that help at all?

---

### Post by tauntedflail on 2009-09-11
I just did another fresh install of ubuntu and click 'display' before installing the new updates and it works fine!

Any ideas which update it is which is causing the problems?

---

### Post by P4man on 2009-09-11
No clue. I would have blamed the videodrivers, other than that, no idea. If you're bored, find out, install all updates one by one :). Well, its probably related to Xorg somehow..

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> No clue. I would have blamed the videodrivers, other than that, no idea. If you're bored, find out, install all updates one by one :). Well, its probably related to Xorg somehow..
 
Bah. Scrap what I put just now. I didnt realise the video driver needed a restart to install correctly. After rein-stalling the problem came back. So it **is **the driver.
thankyou for your help letting me track this down!
 
Where can I go from here? How exactly can I find a driver that wont destroy the computer? Is getting a new driver the only option..? Or can I just fix whats breaking with the current recommened and tested one?

---

### Post by P4man on 2009-09-11
Your best bet now is trying newer drivers from ATI website. Usually not recommended, but clearly the ones in the repo's aren't working for you, so head over here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)

Also download the PDF with installation instructions on that same page.

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> Your best bet now is trying newer drivers from ATI website. Usually not recommended, but clearly the ones in the repo's aren't working for you, so head over here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)

Also download the PDF with installation instructions on that same page.


Damn... that PDF has got a lot for me to take in. There is a whole tonne of extra stuff I supposedly need and it recommends, how do I know if I have that? Or where to get any of it?

Damn.. this is hard :S

EDIT:
I just found under user settings that the account I was using didnt have 'use 3d acceleration' enabled.
Could this have anything to do with it?

---

### Post by P4man on 2009-09-11
> **tauntedflail said:**
> 
I just found under user settings that the account I was using didnt have 'use 3d acceleration' enabled.
Could this have anything to do with it?

? Never saw that before. must be an ATI thing? Sure worth trying.

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> ? Never saw that before. must be an ATI thing? Sure worth trying.

Okay just tried, it didn't work. Completely messed everything up again... :S.
So with installing a new driver, how do I know that one you linked to me will work? (if I ever figure out the install)

EDIT: When I download the file it comes as a .run - what am I meanto to run that with?

---

### Post by P4man on 2009-09-11
> **tauntedflail said:**
> Okay just tried, it didn't work. Completely messed everything up again... :S.
So with installing a new driver, how do I know that one you linked to me will work? (if I ever figure out the install)

EDIT: When I download the file it comes as a .run - what am I meanto to run that with?

First of all, disable the current ATi driver. once you've done that, righclick the .run file you donwloaded, go to properties, permissions, and check 'allow execution".

Then open a terminal, change directory to where you downloaded the app, eg

```
cd Desktop
```

then execute it with

```
**sudo **sh ./ati-driver-blalala
```

(no need to type the entire name, just press TAB key to complete the name.
Follow instructions on screen.

---

### Post by P4man on 2009-09-11
once you did that apparently, you need to run

```
/usr/bin/aticonfig --initial
```

---

### Post by tauntedflail on 2009-09-11
Hey thanks for the help. I selected the 'run as an executable' box under properties... but if I type the line you said into the terminal (alex@alex-desktop:~$ sudo sh ./ati-driver-installer-9-8-x86.x86_64.run is the full line) it asks for my password, which I enter, but then says: ''sh: Can't open ./ati-driver-installer-9-8-x86.x86_64.run''

So I tried to run it by right-clicking and selecting 'run in the terminal' which did make it react but then I was told I needed to be the super user..?

Sorry to be such a pain.. where have I gone wrong?

EDIT: Oh also pressing 'tab' didnt do anything.

---

### Post by P4man on 2009-09-11
> **tauntedflail said:**
> Hey thanks for the help. I selected the 'run as an executable' box under properties... but if I type the line you said into the terminal (alex@alex-desktop:~$ sudo sh ./ati-driver-installer-9-8-x86.x86_64.run is the full line) it asks for my password, which I enter, but then says: ''sh: Can't open ./ati-driver-installer-9-8-x86.x86_64.run''

So I tried to run it by right-clicking and selecting 'run in the terminal' which did make it react but then I was told I needed to be the super user..?

Sorry to be such a pain.. where have I gone wrong?

EDIT: Oh also pressing 'tab' didnt do anything.

then you're not in the right directory. Where did you download the file to ?
You have change directories in the terminal first to that same folder (and beware, everything is case sensitive). If you downloaded it to ~/Downloads (which is the same as /home/yourname/Downloads) then open a terminal and type 

```
cd Downloads
```

then run that command again.

Also, just to be sure, you are seemingly installing the 64 bit drivers. you do have the 64 bit version of ubuntu ? If you're unsure, run 'uname -a' in a terminal and paste the output here.

---

### Post by P4man on 2009-09-11
Plan B:
```
sudo apt-get install nautilus-gksu

```

Then you can use the file manager to browse to that file, right click it, and "open as administrator". You may have to close nautilus (=filemanager) first. Edit: perhaps even reboot?

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> then you're not in the right directory. Where did you download the file to ?
You have change directories in the terminal first to that same folder (and beware, everything is case sensitive). If you downloaded it to ~/Downloads (which is the same as /home/yourname/Downloads) then open a terminal and type 

```
cd Downloads
```then run that command again.

Also, just to be sure, you are seemingly installing the 64 bit drivers. you do have the 64 bit version of ubuntu ? If you're unsure, run 'uname -a' in a terminal and paste the output here.

Awesome! Okay that worked, I now have access to a regular looking install window, but before I proceed with that i'll give you that terminal outcome. I dont think i'm on a 64bit version.. I just clicked on that link you sent earlier. Heres the return:
 Linux alex-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux''

---

### Post by P4man on 2009-09-11
ok, my bad. That driver package actually works for both 32 and 64 bit (and you have the 32 bit ubuntu).

Go ahead and install and lets cross finger, but don't have too much hope :)

---

### Post by tauntedflail on 2009-09-11
> **P4man said:**
> ok, my bad. That driver package actually works for both 32 and 64 bit (and you have the 32 bit ubuntu).

Go ahead and install and lets cross finger, but don't have too much hope :)

OH YEAAAAH!!
Wow! I installed it, restarted the system... clicked display. That black bar flashed up again, I thought it hadnt worked. But it only flashed once! The thing loaded in like two seconds flat!

So I decided to check whether it was working properly and loaded up extreme tux racer. Without this driver I was getting maybe 5-10 frames per second - its well over a thousand now!!!!!!!!!!!!

I think its fixed, all of it. I will report back if there are some other issues but for the moment it seems fine and I am[U]  over the moon.
[/U]Thank you P4Man, thankyou so much. :D

---

### Post by P4man on 2009-09-11
Excellent, glad its solved :)
happy tux racing :p

---

