---
title: "Freeze (blank white screen)"
date: 2010-10-06
forum: General Help
---

### Post by @lpha on 2010-10-06
Hello everyone. After logging in, if I do something like opening an application, the screen will go blank and freeze up. The mouse does not show and CTRL+ALT+F1 doesn't work either. If I go to System > Administration > Hardware Drivers, my graphics chip shows up empty with nothing on the list. I have to reset the computer by force every time. Forums talk a lot about the problem being "compiz" or a video driver "ati."
How do I fix this?


Specs:
*Elite Group RS482-m motherboard with integrated(built in) ATI Radeon Xpress 200 graphics
*AMD64 3500+ Cool N' Quiet processor
*1GB Ram

---

### Post by ipatfrmww on 2010-10-06
You shouldn't normally need to do a hard power off unless your computer is totally unresponsive.
If nothing else works then try Alt + SysRq + "REISUB"
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
It is nicer on the hard drive since it doesn't actually ever spin it down, the computer just reboots.

To see if it is compiz you can go into System>Preferences>Appearance> Visual Effects Tab
Then set to none. If the problem still persists then it is not compiz.

Has this install of Ubuntu been installed and working fine before. Or have you just installed it and then had problems straight away?

---

### Post by @lpha on 2010-10-06
> **ipatfrmww said:**
> You shouldn't normally need to do a hard power off unless your computer is totally unresponsive.
If nothing else works then try Alt + SysRq + "REISUB"
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)


Wow. Thanks for this invaluable info. The article meant that you should first try typing **ALT + SysRq + R,E,I,and U** before typing in **B(reboot)** right? This reminds me of PEMDAS for Algebra, way back when I was in jr. high. :)

I will try to disable compiz and get back to you ASAP. I am also a complete newbie with Ubuntu; Problems were present since I installed it this past weekend - even skipping live cd & going straight to installation.

---

### Post by @lpha on 2010-10-06
Disabled compiz, opened Firefox, and still got a full, white screen. ALT+SysRq+REISUB didn't work after it froze so I had to do a manual restart again. Would it be a driver problem?

---

### Post by @lpha on 2010-10-10
SOLVED!

Thought people would be a little more helpful here.. The problem was the Cool & Quiet a.k.a. powernowd feature from my AMD processor. It just so happens that C&Q conflicts with the graphics driver and causes a system crash when it tries to speed or slow down the processor. Its a horrible bug! I simply disabled it inside the system bios and ubuntu hasn't frozen since. I understand other people don't know how to get into the bios or the option to disable it isn't easy to find for some but the instructions for this method are in the **second** **link** below. The **other method** would be to follow the steps in the **first link** below, but that method does have its drawbacks (being that the feature will be re-enabled every time you update to newer versions of Ubuntu). I recommend disabling the feature through the system bios. 
Disabling Cool & Quiet hasn't made my PC any louder and I don't think it has made it any hotter, either. In Microsoft Windows, I heard this feature is already turned off by default and those that tried to enable it started getting the same crashes as in Linux. I would only see this cool & quiet feature useful for conserving laptop battery, and thats it! Hope this helps.


how to disable powernowd inside Ubuntu:
[http://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy](http://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy)


how to get inside the bios to disable Cool & Quiet:
[http://www.computerhope.com/issues/ch000192.htm](http://www.computerhope.com/issues/ch000192.htm)
[make sure you search through every menu for **C&Q** (powernowd), and set it to** off** ]

---

### Post by Jombib on 2011-03-11
You have just saved me from reverting back to XP. I really wanted to keep Ubuntu but this problem was bugging me too much, been a week since i tried this fix and not one single annoying white screen

---

### Post by ChrisOfBristol on 2011-09-15
> **@lpha said:**
> SOLVED!
The problem was the Cool & Quiet a.k.a. powernowd feature from my AMD processor...
This works for me too! I disabled 'Enhanced Intel Speedstep Technology' in the BIOS. It looks like it solves more problems than you thought, as my PC hasn't got an AMD processor, it has two Intel processors and the screen didn't go white, it just locked on whatever was on it at the time. 
Thanks, I'd tried everything else I could think of.

---

### Post by TheOctagon911 on 2012-03-06
This has not helped me and I am having this same exact issue. I need help ASAP. 

My machine is: 

AMD Athalon 64 +3500 with Award (Phoenix) BIOS V. 4.05B
ATI Radeon Xpress 200G Built in graphics
512 MB RAM

I have gone through FIVE versions of Ubuntu trying to resolve this problem. I am about to revert to XP (which I Frakking hate) but I can find no other options. Every time I log in and open Firefox, at random points it blanks out the screen in full white and the whole system freezes and I have to do a hard reset. 

I have tried:
Video driver updates (which ATI don't really seem to have anymore for that one in linux)
Which leads me to NVIDIA configurations. ARRRRGGHHH

I have tried finding the dang "Cool and Quiet" settings in my BIOS, to no avail. It is not listed in the BIOS under any heading. 

I can't fix this and I am royally pissed off. I'm giving this feed one day, because thus far I've found no support out there in the so called 'community' for this. I keep getting led around in circles and no resolution to my problem. Please someone help! I will provide any information you need, just frakking ask!!

Desperate in Michigan

---

