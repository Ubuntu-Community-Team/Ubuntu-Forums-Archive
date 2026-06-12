---
title: "need to get into my bios"
date: 2010-12-24
forum: General Help
---

### Post by no2498 on 2010-12-24
everex gPC2 tc2512 they went under
ubuntu 804 hardy
no windows 
single boot

my onboard video is going bad
i have a radeon 9250 pci 256mb v/d/vo card
i would like to install before the onboard goes all the way out
how and what all do i need to do
what do i look for and change in the bios

i need to know every thing

and yes i have looked for self help
yes it may be the power pack but if not i can not install the video card later
 please put all answers in  the email so i can read them as i fix this computer i have 2 more computers on line

---

### Post by Frogs Hair on 2010-12-24
Pressing the F2 key during boot is supposed to access the bios screen. I can't find any further information.

---

### Post by no2498 on 2010-12-25
will this help me


echolink
November 17th, 2007, 03:14 AM
How to Install a Nvidia/ATI PCI Video Card on Linux


Hello my name is echolink, and the PCI Nvidia/ATI video card, issue seems to be a plague for a lot of Linux, or aspiring Linux users, and has actually been one reason that a lot of users, have dismissed Linux, because of this one issue. Simply due to the fact that they cant use there video card. I don't blame them who wants to use on board video when you have a perfectly good Nvidia/ATI PCI card laying around. Thats why I have decided to write this simple how to article for people in hopes that it will open up more users to the world of Linux. I have found it to be somewhat sad that people wont use Linux because of a simple hardware issue that has not been corrected as a default action by many Linux Distribution Developers and Companies. So go ahead and proceed below and we will get your video card up and running. :)



Before you proceed ask yourself a question have you ever wanted to use Linux, but are stuck with a pci only motherboard with a pci card, and there is no option in the bios to disable the damn on board video card. Well I have a surprise for you there is a simple easy way to do this provided you follow the instructions below!!!!!. To do this however you need to understand why the pci video card does not automatically detect as default on most Linux distros, when windows, or other operating systems will. Well thats simple the Linux system is going to detect the closest default motherboard video chip set regardless of what you bios is set on because most Linux distributions overlook the bios and detect all the hardware that is on the machine regardless if you have something disabled in the bios this all has to do with PCI bus issues. Lets just say Linux is a very intuitive operating system far superior to windows. So the fact that the Linux distribution you have chosen detects the hardware is a good thing because we all know that Linux is picky when it comes to hardware detection. The reason that AGP, and PCIe do not have this issue is because they are not on a PCI bus system, they are on a different bus, to were PCI cards, and On Board cards are on the same PCI bus system, but we will discuss more about this later in the article. So lets go ahead and set up your PCI video card so you can get the performance you expect instead of using the crappy on board video driver that the motherboard manufacture provided with the motherboard.

Step 1

First off all install the operating system on the on board video card this will save hassles later on.

Step 2 

Okay no that we have the Linux distro of your choice installed, and you are now booted up on clean fresh install. Go ahead and open up the terminal/konsole (some distro's call it different things), Ohhh NO did you say TERMINAL!! :) now before you get scared this is actually easy :) go ahead and log on under root, by first typing su now it will ask you for your password that you provided as the root password during the installation. so go ahead and enter your password. Now that you have done this go ahead and copy and paste, or type the following command sudo dpkg-reconfigure xserver-xorg. Now that we have completed this step go onto step 3.

Step 3

Okay now that we have started the xserver-xorg configuration tool, the next few steps will be fairly easy. Basically all you need to do is answer the following questions that the system asks you Type of video card, PCI bus, keyboard, mouse, monitor, etc. IMPORTANT: MAKE SURE YOU READ EVERTHING BEFORE YOU JUST START DEFAULTING ON STUFF!!!!!!! IF YOU DO IT WRONG YOU HAVE TO START OVER, BUT THIS TIME IN TEXT MODE OF THE OPERATING SYSTEM!!!. The one thing that you need to pay particular interest to is the PCI bus number, because by default if you are running a pci only mobo, the xserver-xconfig tool will detect the pci bus for the on board video card not your Nvidia/ATI card. This is the Ghost Problem That Cause PCI Cards Not To WORK THAT WAS MENTIONED AT THE BEGINING, And Is Why PCI Cards Dont Work By Default!!!! So we need to find out what bus the Nvidia/ATI card runs on. So we need to look into your hardware manager to find you what the bus is. So go ahead and MINIMZE (Not Close), your terminal to the task bar. Go ahead and navigate to were ever your hardware manager is located on your particular distribution. Once you are inside of your hardware management area you need to locate the Nvidia/ATI video card and look at the bus, the bus will read like this for example: bus:1:9:0 (which is default for most motherboards, the on board is usually bus:0:2:0, but make sure just to be safe what yours is). Okay now that you have your bus ID go ahead and bring back up your terminal and enter the bus ID into the xserver-config tool. Once you answer this go ahead and answer the rest of the questions . Now that you have correctly set up your xconfig file and saved it. You can close the terminal and you can reboot the system. When your computer brings up the settings screen at the beginning of reboot go into bios and set your video to pci, and plug the moniter into the video card, again reboot, and bam you have a working PCI ATI, Nvidia video card. After you complete these steps follow the proper procedures, related to your specific distribution and install the nvidia/ati drivers, after installing the drivers, you need to reboot, and your Nvidia/ATI installation will be complete. You can go into the nvidia control panel and adjust settings for things like dual monitors, etc later. 

So in closing I hoped this little tip helps a lot of you frustrated Linux users who want that PCI card to work but just cant seem to get it going. This is echolink saying see you later. And happy Linux......

---

### Post by no2498 on 2010-12-27
that did not help is to much missing for me

---

### Post by cchhrriiss121212 on 2010-12-27
The easiest way for me would be like this:
Physically install new GPU to the motherboard
Download and install Ubuntu 10.04

You are still using 8.04 so it would be a good opportunity to upgrade. Back up your files externally first if you don't have a separate /home partition. A fresh install will probably be quicker than fixing compatibility issues from changing display devices.

---

### Post by julianb on 2010-12-27
re: previous post... 

if you are shopping for a graphics card, you might want to use a google search to find out which graphics cards work well with linux.

---

### Post by no2498 on 2010-12-27
cchhrriiss121212

how you make it stay if you upgrade again

btw i did go to 10.04 yesterday

i have the radeon 9250 pci 256mb v/d/vo card

i just need to fix the onboard 

i can take it back out if it turns out to be the power pack
but i can not fix a black/blank screen

its starting to not power back up
fans run hard drive comes on but stops at a black screen
fans still running hard drive light on black screen

after it comes on i get power like lines across the screen at times
they come and go
i have parts to fix every thing but the mother board
so it needs to be a 1 time fix in my mined

---

### Post by cchhrriiss121212 on 2010-12-27
> i have the radeon 9250 pci 256mb v/d/vo card

i just need to fix the onboard 

i can take it back out if it turns out to be the power pack
but i can not fix a black/blank screen
If you install a dedicated video card, you won't need to fix the onboard GPU as you will no longer be using it. First you must boot into BIOS using f12 and disable onboard video, that way the system will know to use the PCI card.

---

### Post by no2498 on 2010-12-28
the del key gets me in the bios
now what to change
when to put the card in 

found the del by looking for
bios everx/computer
its a
everx gpc2 model TC2512

---

### Post by cchhrriiss121212 on 2010-12-28
Put the card in first, then disable the onboard graphics in BIOS, or do it the other way round. Just make sure you have a GPU available to output to your monitor.

---

### Post by pricetech on 2010-12-28
More than likely all you need to do is reset your BIOS to defaults in order for it to look for an addon card before the onboard video.

Once you have a display using the addon card, then disable it onboard if you can.

Just make sure you make a note of any customizations you've made to the BIOS before resetting it.

---

### Post by no2498 on 2010-12-29
resetting the bios is a BIG NO NO
that cleans out your user name and pass word
then you can not log back in to the computer using linux/ubutu

---

### Post by no2498 on 2010-12-30
the onboard video is not jumping out at me in the bios
i need to know every thing

---

### Post by pricetech on 2010-12-30
> **no2498 said:**
> resetting the bios is a BIG NO NO
that cleans out your user name and pass word
then you can not log back in to the computer using linux/ubutu

No it doesn't.  Reseting the BIOS simply reset the BIOS to factory defaults.  It has nothing to do with your credentials in Ubuntu, or any other OS for that matter.

---

### Post by pricetech on 2010-12-30
> **no2498 said:**
> the onboard video is not jumping out at me in the bios
i need to know every thing

Since none of us is in front of the computer, there's not a lot we can tell you that we haven't already.

You may not be able to disable the onboard video in the BIOS.  Some computers don't offer you that ability.  You may have to settle for reducing the amount of memory allocated to it to the smallest amount and hope it's automatically disabled when your BIOS finds another card and uses it.

---

### Post by no2498 on 2010-12-30
the best thing i seen yet
but reseting bios is why im on 10.04 now

---

### Post by no2498 on 2011-01-02
let this die
turns out i have 2 monitors going bad at the same time
well make that 3 the 1 i had on this computer has a bad wire going to it too

i would like to still to install the video card  so i can use 2 monitors
but ill wait for a bit 

thanks for trying to help anyway

---

