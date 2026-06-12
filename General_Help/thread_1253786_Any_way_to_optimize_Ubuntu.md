---
title: "Any way to optimize Ubuntu?"
date: 2009-08-30
forum: General Help
---

### Post by dtrot55 on 2009-08-30
I am using the computer in my signature...and the pent m's were pretty much crap processors and seems that even with 2 gigs of ram that the computer is struggling a little...I have disabled Compiz..but is there anything else i can do to help optimize OS performance?

---

### Post by P4man on 2009-08-30
Pentium M's didn't suck.. they rocked, and they still do! One of my laptops is very similar to yours, Dothan (Pentium M)  1.86 GHz, 1GB Ram, and its a joy to use ubuntu on really. Just no compiz and stuff, due to crappy (and actually faulty) X300 onboard graphics. 

Can you elaborate on your problem? What is slow or sluggish?

---

### Post by CatKiller on 2009-08-30
If Ati still support your card, you can install the proprietary driver in System &#8594; Administration &#8594; Hardware Drivers. If they've dropped support, you'll have to use the open source driver, which can be hit-and-miss.

Compiz can *improve* performance, if you turn off the resource-hungry animations, since it offloads drawing windows to your specialised graphics hardware.

---

### Post by aesis05401 on 2009-08-30
Once you get into modifying Ubuntu under the hood you are introducing complexity in staying compatible with upgrades and whatnot.  I would suggest looking at replacing your default desktop environment, and leaving the system underpinnings in tact.

Here is the wikipedia comparison of Xorg based desktop environments.  I believe xfce via XUbuntu would provide a good starting point.
[U][B]
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments")[/B][/U]

And here is the XUbuntu overview:**[http://en.wikipedia.org/wiki/Xubuntu]("http://en.wikipedia.org/wiki/Xubuntu")**

---

### Post by dtrot55 on 2009-08-30
computer is very sluggish when it comes to internet browsing and flash related stuff...also very sluggish when I am streaming music from my ubuntu desktop over the wireless to my ubuntu laptop...so if I am multi-tasking..say browsing and listening to music over wireless..computer is slow and actually annoying to be on...

---

### Post by dtrot55 on 2009-08-30
> **aesis05401 said:**
> Once you get into modifying Ubuntu under the hood you are introducing complexity in staying compatible with upgrades and whatnot.  I would suggest looking at replacing your default desktop environment, and leaving the system underpinnings in tact.

Here is the wikipedia comparison of Xorg based desktop environments.  I believe xfce via XUbuntu would provide a good starting point.
[U][B]
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments")[/B][/U]

And here is the XUbuntu overview:**[http://en.wikipedia.org/wiki/Xubuntu]("http://en.wikipedia.org/wiki/Xubuntu")**

I tried using Xubuntu in the beginning but the networking issue was what turned me off from it ... so i went back to ubuntu

---

### Post by earthpigg on 2009-08-30
my personal controversial opinion:

if your objective is to optimize, then ignore all the talk about ubuntu tweak and other silly things that **_distance_** you from the inner workings of your system.

**_all roads to customizing/optimizing/etc Ubuntu eventually lead to the same place:_**

a minimalist command-line only install that you build up from while avoiding any/all metapackages.

install the command line system.
then install X.
then install a WM of your choice.
(optional) then install a DE of your choice.
(optional) then install ease-of-use apps of your choice.

it is much easier to build **_up_** from that CLI install than to take things away after the fact.... once you have ubuntu-desktop intalled, you have kernel modules and services coming out of your ears, and removing anything risks placing you in reverse [dependency hell]("http://en.wikipedia.org/wiki/Dependancy_hell").

all roads to customizing/optimizing/etc _**your computer's software as a whole**_ eventually lead to the same place, too:

distributions wherein a command line install is the _**default**_.

examples:

Gentoo Linux
Arch Linux
Slackware Linux
*BSD
FreeDos (thrown in for the purposes of Affirmative Action)




if you want a lean mean and truly personalized machine, then you want to get to know the command line. a system installed this way _**stays**_ installed.

---

### Post by Shpongle on 2009-08-30
you could always try crunchbang , its based on ubuntu and uses the openbox wm and ubuntu repos, its still ubuntu under the hood but stripped down  its really fast, and it has built in transparency if you wanna use docks and stuff, you can check it out here   [http://crunchbanglinux.org](http://crunchbanglinux.org)   


 im using it as my main os at the min and im learning a hell of a lot, or theres always puppy linux :P

---

### Post by dtrot55 on 2009-08-30
Yeah I just really want to stay with Ubuntu...but I was hoping for some little tricks like in XP where you can kill pointless programs from starting up and running in a Classic mode..stuff like that

---

### Post by Shpongle on 2009-08-30
you could always have a look at this, be careful though [http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast](http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast)

---

### Post by Kristofer Van Orton on 2009-08-30
Here is a little tip to optimizing your performance:

1. Go to System-->Preferences-->Appearance
2. Navigate yourself to the Visual effects tab, if it is on Normal or Extra than set it down to none if you don't mind sacrificing eye candy for a little better performance... If it is already on None than I'm sorry to have wasted your time :P

I mention this because when I installed Ubuntu by default this was set to Normal, I set it to extra because my grapics card handles it find.

---

### Post by dtrot55 on 2009-08-30
compiz already set to none

---

### Post by P4man on 2009-08-31
what videocard do you have, and what (if any) drivers are you using?
If you dont know the videocard, run lspci in a terminal

---

### Post by dtrot55 on 2009-08-31
ATI Mobility Radeon 9700.... went to hardware drivers and nothing in there

---

### Post by scouser73 on 2009-08-31
First off I disable certain applications like; Bluetooth, log in sound and so on.  This increases the booting up time of Ubuntu, also it's very important to have an understanding of the programs that you are diabling.

There is a tutorial that shows you certain processes that you don't need when starting your computer up, this can be found [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491"). Hope this is of some help to you, as it was to me, I've shaved off three seconds in boot time & I know it doesn't sound much but you'll notice the difference.

---

### Post by dtrot55 on 2009-09-10
> **scouser73 said:**
> First off I disable certain applications like; Bluetooth, log in sound and so on.  This increases the booting up time of Ubuntu, also it's very important to have an understanding of the programs that you are diabling.

There is a tutorial that shows you certain processes that you don't need when starting your computer up, this can be found [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491"). Hope this is of some help to you, as it was to me, I've shaved off three seconds in boot time & I know it doesn't sound much but you'll notice the difference.

I've been trying to locate how to disable blue tooth...could you point me in the right direction?  Thanks!

---

### Post by XCan on 2009-09-10
System -> Preferences -> Startup Applications -> Untick Bluetooth manager.

---

### Post by longtom on 2009-09-10
> **XCan said:**
> System -> Preferences -> Startup Applications -> Untick Bluetooth manager.

Don't have that, don't find it in Synaptic.  I am on Hardy.  Could you elaborate were I would find this application?

---

### Post by earthpigg on 2009-09-10
> **longtom said:**
> Don't have that, don't find it in Synaptic.  I am on Hardy.  Could you elaborate were I would find this application?

if your machine does not have bluetooth capabilities, it is possible ubuntu was smart and did not install the corresponding software.

edit: oh, you are on hardy and talking about the menu item itself.... i think they called it the more GNU/Linux traditional name of 'sessions' back then in the menus...

---

### Post by longtom on 2009-09-10
> **earthpigg said:**
> oh, you are on hardy and talking about the menu item itself.... i think they called it the more GNU/Linux traditional name of 'sessions' back then in the menus...

Indeed they did - thank you very much.  Jaunty is not working to well with the organs of this machine and Intrepid got slower and slooower.  Since I need it to be reliable I installed Hardy some time ago.  That works fine and I'll keep it until support expires and/or the next LTS is past its initial bumps and hurdles.

I just upgraded all the programs I needed to be up-to-date and that's it....but I have lost the thread again....

---

### Post by kerry_s on 2009-09-10
turn on reduced_resources in gconf-editor.

---

### Post by XCan on 2009-09-10
> **kerry_s said:**
> turn on reduced_resources in gconf-editor.

Didn't know about that, does it help much?

---

### Post by kerry_s on 2009-09-10
> **XCan said:**
> Didn't know about that, does it help much?

every little bit is suppose to help. :lolflag:
i think it does, my gnome setup is as fast as xfce4 would be. i am using faster apps for the normal stuff, like mousepad instead of gedit, abiword to read doc's, etc...

the only program i removed was gimp, i prefer kolourpaint from kde, well worth it. everything else is there, i just set it up to use the lighter programs.

---

