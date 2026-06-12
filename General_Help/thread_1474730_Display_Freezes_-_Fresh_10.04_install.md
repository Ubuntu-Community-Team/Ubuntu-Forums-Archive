---
title: "Display Freezes - Fresh 10.04 install"
date: 2010-05-06
forum: General Help
---

### Post by theantidj on 2010-05-06
Hello all, I'm hoping someone can point me in the right direction. I've tried Google searching and searching this forum, but haven't found something similar to my issue.

Yesterday, I installed 10.04 off of the live CD onto my Toshiba Satellite A45-S250 laptop (P4 2.8, 1GB RAM).  

The main problem is:
 
-if the computer sits idle for more than about 5 minutes, the display will freeze. Image stays on screen, but the computer appears to be non responsive to all input.

-I thought it was a screen saver at first, but it happens even with the screen saver disabled. 

-I can still SSH into the machine from my desktop computer.  I get a normal prompt, and it seems to be working fine from the shell.  This is how I have been restarting or shutting down the machine after a freeze.  

Secondary issues (that may help diagnose the problem):

-Even when this laptop appears to be functioning normally (pre-freeze), I cannot switch to any virtual terminals.  Well, I can, but when I get there, something is not right.  The text does not display properly.  It sort of strobes on and off near the top right hand of the screen.  

-On shutdown, I get a weird colorful displays of what I can best describe as "static".  The closing splash screen may just blink on for a second.  Other than that the screen stays black until the machine shuts down. 

-I've run versions of Ubuntu going back to Breezy on this machine, mostly without issue, and it has been a full time Ubuntu machine since the release of 8.04.  

These symptoms all appear to be related to video / display.  Any help you could provide would be super super super appreciated.  Unless I get this sorted I will need to roll back to 9.10.  

I am willing to post whatever log files or do any experiments that might help to diagnose and solve the problem.

---

### Post by dino99 on 2010-05-06
first place to glance at: system admin hardware driver, is it activated ?

---

### Post by theantidj on 2010-05-06
Experiment update: 

I opened up a streaming internet radio station in Movie Player for the last 30 minutes.  When I returned, the computer was responding normally, without a freeze.   

I'm not sure if this helps to clarify or confuse the problem.

---

### Post by theantidj on 2010-05-06
> **dino99 said:**
> first place to glance at: system admin hardware driver, is it activated ?

Hi there, thanks for the response!

Ok, I went to the "Hardware Drivers" option on the Administration menu.

I got a searching dialog box with a progress bar that floated back and forth a little bit. 

Then the larger box popped up and said "No Proprietary drivers are in use on this system"

The white boxes in this dialog are empty and there is nothing to select to enable, so the enable button is grayed out.

---

### Post by theantidj on 2010-05-06
Experiment #2:

While the laptop was off, I connected an external monitor and then booted the machine. 

The laptop automatically used the external monitor, and never turned on it's built-in display.  I can log into ubuntu normally, and have none of the weird video effects that I get on the built in display:

-I can switch to and use other virtual terminals
-shutdown splash screen displays normally.

Additionally, I don't appear to get the freezing issue.  At least, I haven't been able to replicate it yet.  


Does this help or further confuse the issue?

Are there other tests anyone can think of me trying?

Thanks in advance for your help.

---

### Post by AlexDudko on 2010-05-06
Can it be screensaver which by default is activated after 5 minutes of idleness? What happens if screensaver is off?

---

### Post by theantidj on 2010-05-06
> **AlexDudko said:**
> Can it be screensaver which by default is activated after 5 minutes of idleness? What happens if screensaver is off?

Thank you for your reply.

It happens even if the screen saver is disabled.  Upon further observations, it may freeze after just 5 minutes, or after a longer time, say 20 minutes or so.  

And to update my external monitor experiment:
The display did just freeze even using the external monitor.  I had to ssh in to reboot.

---

### Post by theantidj on 2010-05-07
Bump.  

Issue still exists, no solution found so far. I'm not sure if it is because people don't know, or if the thread gets buried too quickly for the right people to see it. 

Again, any assistance is appreciated. 

Thank you.

---

### Post by Catharsis on 2010-05-07
What graphics card do you have?
```
lspci | grep VGA
```

Also, you might want to check that your computer isn't going into suspend, or that the monitor isn't either. Suspend typically breaks things. System -> Preferences -> Power Mangement.

---

### Post by dnguyen1963 on 2010-05-07
> **theantidj said:**
> Bump.  

Issue still exists, no solution found so far. I'm not sure if it is because people don't know, or if the thread gets buried too quickly for the right people to see it. 

Again, any assistance is appreciated. 

Thank you.

I have had the same problem a week ago with 10.04 on a desktop (Integrated Intel graphic card).  Here was what I did to keep the computer from locking up.

1.  Removed all of Firefox add-ons.
2.  Reconfigure Firefox (sudo dpkg-reconfigure firefox).
3.  Set the screen saver to "Blank Screen".  Do not select anything else.  It will lock up your computer.

Good luck.

---

### Post by StuartN on 2010-05-07
> **dnguyen1963 said:**
> 1.  Removed all of Firefox add-ons.

Interesting - I just checked my ~/.xsession-errors file and find a lot of **(firefox-bin:3097): Gdk-WARNING **: XID collision, trouble ahead**, which leads on to this thread and bug reports:

[http://ubuntuforums.org/showthread.php?p=7506398](http://ubuntuforums.org/showthread.php?p=7506398)

---

### Post by dnguyen1963 on 2010-05-07
> **StuartN said:**
> Interesting - I just checked my ~/.xsession-errors file and find a lot of **(firefox-bin:3097): Gdk-WARNING **: XID collision, trouble ahead**, which leads on to this thread and bug reports:

[http://ubuntuforums.org/showthread.php?p=7506398](http://ubuntuforums.org/showthread.php?p=7506398)

let me know if you still experiencing freezes.

---

### Post by theantidj on 2010-05-07
> **Catharsis said:**
> What graphics card do you have?
```
lspci | grep VGA
```

Also, you might want to check that your computer isn't going into suspend, or that the monitor isn't either. Suspend typically breaks things. System -> Preferences -> Power Mangement.

Hey there, Catharsis, thanks for the response!!

Double checked power management.  Machine is not set to suspend after any length of time, so I'm pretty sure it's not that.  

As far as the graphics, here's what I get:

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
``` 

So, it's an integrated Intel graphics, like the gentleman who posted below you.   I will try some of his suggestions to see if it helps at all.  I'm a bit skeptical, though, as I had my screen saver turned off and Firefox wasn't open at the time.  We'll see though, I'm willing to try anything at this point, as I really like the rest of what 10.04 has going for it.

---

### Post by joejvj on 2010-05-07
I've got the exact same problem, 10.04 running on an ACER 5536 laptop AMD-64 version. 

Never had any problems running 9.10- until I upgraded to 10.04. If I move the mouse, I can see the mouse pointer on screen but the screensaver is in the background and frozen.

---

### Post by theantidj on 2010-05-07
> **dnguyen1963 said:**
> I have had the same problem a week ago with 10.04 on a desktop (Integrated Intel graphic card).  Here was what I did to keep the computer from locking up.

1.  Removed all of Firefox add-ons.
2.  Reconfigure Firefox (sudo dpkg-reconfigure firefox).
3.  Set the screen saver to "Blank Screen".  Do not select anything else.  It will lock up your computer.

Good luck.

Hi dnguyen, thanks for your reply!  

I also checked and I have integrated intel video.   I will try the things you have set out.  It's interesting as I had my screen saver turned off and I don't think firefox was open the last time it froze but I will try.  Who knows how all the stuff affects everything else. 

Thanks for the advice!!

---

### Post by theantidj on 2010-05-07
> **dnguyen1963 said:**
> I have had the same problem a week ago with 10.04 on a desktop (Integrated Intel graphic card).  Here was what I did to keep the computer from locking up.

1.  Removed all of Firefox add-ons.
2.  Reconfigure Firefox (sudo dpkg-reconfigure firefox).
3.  Set the screen saver to "Blank Screen".  Do not select anything else.  It will lock up your computer.

Good luck.

Were you considering all plug-ins (such as flash, etc) as add-ons?

---

### Post by dnguyen1963 on 2010-05-07
> **theantidj said:**
> Were you considering all plug-ins (such as flash, etc) as add-ons?

I still have Flash running so I can still watch news clips on the internet...mostly things like ad-block etc...You can go to manage add-on in Firefox and manually disable all the junks.

---

### Post by theantidj on 2010-05-07
> **dnguyen1963 said:**
> I still have Flash running so I can still watch news clips on the internet...mostly things like ad-block etc...You can go to manage add-on in Firefox and manually disable all the junks.

Ok, great.  I did that.  Also, the computer just did a bunch of updates, including a new kernel, it looks like.  

I'm going to walk away and see if the computer still freezes.  

What ever the updates were, they didn't fix my problem with the video at the virtual terminals, so we'll see if I still get the (possibly related) freezing thing.

---

### Post by dnguyen1963 on 2010-05-07
> **theantidj said:**
> Hi dnguyen, thanks for your reply!  

I also checked and I have integrated intel video.   I will try the things you have set out.  It's interesting as I had my screen saver turned off and I don't think firefox was open the last time it froze but I will try.  Who knows how all the stuff affects everything else. 

Thanks for the advice!!

Same here...I had screen saver disabled and nothing was running during all those crashes.  I even set the power management to "never" for everything. What I did was the compilation of things that people tried and had success.  It worked for me, but I have no explanation as to how.

---

### Post by theantidj on 2010-05-07
Ok, so despite today's updates, and trying dnguyen1963's suggestions, I'm still freezing up.  It was working fine for a while, and then I went away and came back about 30 minutes later, and we have another display freeze.  ssh is working.  

This is such a frustrating and odd problem.

---

### Post by Catharsis on 2010-05-07
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by theantidj on 2010-05-07
Ok, here's another piece of information.  

When I ssh'd in, i typed the following:

```
glxinfo | grep "GLX version"
``` 

as I've read that some people are having problems if they're running version 1.4.  

Here's what I got back:

```
Error: unable to open display
```

Note that this is while the screen on the laptop was frozen, and I had ssh'ed in from my desktop. 

As a side note, after a reboot I was able to confirm that I'm running GLX version 1.2, not 1.4. 

Ok, folks, what next?  Any specific error logs I should check and post.

I really appreciate everyone who has responded today!

---

### Post by dnguyen1963 on 2010-05-07
> **theantidj said:**
> Ok, so despite today's updates, and trying dnguyen1963's suggestions, I'm still freezing up.  It was working fine for a while, and then I went away and came back about 30 minutes later, and we have another display freeze.  ssh is working.  

This is such a frustrating and odd problem.

Bummer!  sorry it did not work for you.  BTW, I did not install any update from Ubuntu at all.  I am a bit leery of any update until I know most of the bugs have been cleared.

---

### Post by theantidj on 2010-05-07
> **Catharsis said:**
> [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Hi Catharsis,

Thanks for the link!  I didn't see this before I made my last post.  I will try everything listed here to see if it clears things up. 

I really appreciate your help!

---

### Post by theantidj on 2010-05-08
> **Catharsis said:**
> [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

So, I'm not fully ready to say "solved" yet, but we're close. 

I did the fix "A" listed on the above link, and it's looking good so far..

No freezes after 3 hours.  Going to go for a reboot now, to see if the fix sticks.  Also, I can now switch to the virtual terminals; no more video flicker making them unusable.

Thanks for everyone's help!

---

### Post by theantidj on 2010-05-09
Well, after a couple of days, the fix has held.  

I'd say Solved!

---

### Post by dnguyen1963 on 2010-05-10
> **theantidj said:**
> Well, after a couple of days, the fix has held.  

I'd say Solved!

Great.  I have not seen any freezes lately.  Despite this problem, I really like 10.04.

---

### Post by dnguyen1963 on 2010-05-11
I spoke too soon...10.04 froze on me again last night.

---

### Post by ky5u on 2010-05-15
My problem is very particular.  Every time I try to boot 10.04 on 2 different d Dell d-500 laptops, I get the purple loading screen with "ubuntu" but it ends in a blank screen freeze.  I never get into UBUNTU.  These machines run fine on 9.10.  I tried the fix suggested and it does not work.  Both laptops have 1GB ram and 1.3 Ghz processors.  They have the native intel/dell video as delivered installed with the computer.

I have been running 9.10 for a few months without a hint of a problem with the OS.  

I really want to get a laptop up with 10.04.  Can someone make a suggestion please?

Thanks!!

---

### Post by Catharsis on 2010-05-15
> **ky5u said:**
> My problem is very particular.  Every time I try to boot 10.04 on 2 different d Dell d-500 laptops, I get the purple loading screen with "ubuntu" but it ends in a blank screen freeze.  I never get into UBUNTU.  These machines run fine on 9.10.  I tried the fix suggested and it does not work.  Both laptops have 1GB ram and 1.3 Ghz processors.  They have the native intel/dell video as delivered installed with the computer.

I have been running 9.10 for a few months without a hint of a problem with the OS.  

I really want to get a laptop up with 10.04.  Can someone make a suggestion please?

Thanks!!

Are you trying to boot the LiveCD or did you install it? Background info plz.

See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Also try booting into recovery mode in GRUB.

---

### Post by ky5u on 2010-05-16
> **Catharsis said:**
> Are you trying to boot the LiveCD or did you install it? Background info plz.

See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Also try booting into recovery mode in GRUB.
I was trying to install it and never got past the first purple screen.  I tried an "upgrade" download, and same thing.  I found and tried the your suggested link before I posted my request above and it did not work.  Thanks.

BTW, I tried Live CD too and same result.

---

### Post by Catharsis on 2010-05-16
In the kernel parameters (see the link to get there through GRUB), try replacing "quiet splash" with, one at a time:
1) Nothing
2) "nomodeset"
3) "noacpi"
4) "xforcevesa"
5) "xforcevesa noapic noapci nosplash irqpoll"

---

### Post by ky5u on 2010-05-17
I will try replacing quiet splash as you suggested and edit this with the results.

Results:

1. removing quiet splash causes a crash at initial kernal load
2. nonodeset and noacpi both execute the last command "Sensor Limits" and "OK" then CD activity as if loading somethig, a flash of ascii jiberish on screen and then freeze.
3. xforcevesa boots up the kernal in the root mode.  Control<D> or Exit or Quit or Control<C> just reinit the root screen.
4. Same thing.

Success!

I am a bit dyslexic (I belong to DNA, the National Dyslexic Association).  I went back and looked at my notes and determined that I had read "i915.modeset=1" as "i915.modest=1".  Going on the faithful premiss that I am an idiot, I tried again and it worked.  Can you interrupt the boot from hd like you can from CD?  If I can, I'll go ahead and install, reboot and edit the boot file.

Thanks for your help.  And I already slapped myself in the back of the head for you.

---

### Post by Catharsis on 2010-05-17
> **ky5u said:**
> I am a bit dyslexic (I belong to DNA, the National Dyslexic Association).  I went back and looked at my notes and determined that I had read "i95.modeset=1" as "i95.modest=1".  Going on the faithful premiss that I am an idiot, I tried again and it worked.  Can you interrupt the boot from hd like you can from CD?  If I can, I'll go ahead and install, reboot and edit the boot file.

Yes, you can interrupt the boot on an hdd. Instructions are at:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Just make sure you use "i915.modeset=1", not "i95.modeset=1" ;).

---

### Post by ky5u on 2010-05-17
> **Catharsis said:**
> Yes, you can interrupt the boot on an hdd. Instructions are at:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Just make sure you use "i915.modeset=1", not "i95.modeset=1" ;).
Yeppers.  I used the correct command.  Going to install now.  Yeaaaa!

---

### Post by GarthS on 2010-05-19
> **Catharsis said:**
> Yes, you can interrupt the boot on an hdd. Instructions are at:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Just make sure you use "i915.modeset=1", not "i95.modeset=1" ;).


I did this (work around A) and still lost keyboard and mouse after about 2 hours. I was using kernel 2.6.32.22. I have been booting this morning to kernel 2.6.32.21 and have not yet experienced freezing, although it did get so slow it almost locked up on me at one point.
I have the i845 chipset.

This issue should be the #1 priority of all Ubuntu engineers who were involved in the release of 10.04. I can't even imagine how many folks who use Ubuntu have 8xx chipsets and are now having these freezing issues after upgrading or fresh install. What a disapointment for the heralded 10.04. 10.04 was supposed to bring more people to Ubuntu, my fear is that this issue is scaring them away, giving folks who were curious about Ubuntu the feeling that Ubuntu is still not perfected enough to be relied on as a users primary os. :(

Here is another link with relevant information 
[http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html)
This info was provided by StuartN in the thread titled "[B]Ubuntu 10.04 (Lucid Lynx) Random Freeze / Hang-up". 


[/B]

---

### Post by ky5u on 2010-05-20
Garth,

I agree completely.  Freakin' Intel chipset used in DELL computers?  

After I installed Lucid, the computer would run for about an hour then freeze.  I followed all the suggestions, one at a time and NONE worked.  The best I could do was get a screen that offered to go to low resolution, which I accepted, then it booted.  I checked xorg.conf in /etc/X11 and it was missing but the xorg.conf.failsafe was there so I copied it over and found it uses "fbdev" as the Device Driver. ](*,)

Once I did that and with the "options i915 modetest=1" added to the boot file, it booted normally with the latest kernel and it has not crashed one time.  I notice on the screen saver (i use the rotating computer name), my 9.10 on the adjacent identical computer was more smooth and faster.  Do I assume fbdev kills video acceleration.  But every thing else works fine.

The screen resolution and graphics quality look the same on the two side by side machines (one with 9.10 and the other 10.04).  Guess if I had a 25" monitor it might hurt me.  

Good luck with yours and good luck to the guy who decided to blacklist INTEL chipset.  Must been good dope.[-X   Seriously, thanks for all you guys do.  We p|$$ and moan but we love it!




P.S.   Boot time, side by side identical computers with same chipset, ram, and proc speed:  10.04 is fastest by 30 seconds over 9.10.

---

