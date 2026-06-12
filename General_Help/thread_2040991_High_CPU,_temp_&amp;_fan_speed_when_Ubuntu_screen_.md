---
title: "High CPU, temp &amp; fan speed when Ubuntu screen goes black (screen saver??)"
date: 2012-08-11
forum: General Help
---

### Post by st2000 on 2012-08-11
Hi All,

Could use some help not only for this problem, but also for where to put this question.  I think it is a Ubuntu desktop issue.  But it makes absolutely no sense to me why an idle Ubuntu laptop gets so warm.  So I'm a bit lost.

I think I literally burned through my first HP laptop in 18 days.  It was running Ubuntu and was left idle for about an hour in an air conditioned office.  When I got back to it the screen was black, the fan was running fast and the case was warm to the touch. I was never able to revive it. HP took it back and gave me a brand new laptop.  I think it was because the failed laptop had just come onto the market.

But now the new laptop gets warm.  But only when the screen goes black.  I've googled and most say a CPU running Ubuntu jumps to 100% after locking the screen.  But I am sure it does not.  I am sure the CPU jumps to 100% only after the screen goes black (when the screen saver kicks in).  Which, in a default Ubuntu configuration, happens later.  

Now, I've been told that the Ubuntu community decided to have a black screen saver to save on energy.  Hence my confusion.  Why would the CPU (or GPU) go to 100% if it is (obviously) not doing anything? Could this really be a problem with something other than the Ubuntu desk top?  If so, where should this thread be posted?

Further googleing didn't help much.  Most solutions (there are several and the posters usually do not explain why they do not always work) appear to deal with something called the "Catalyst Control Center".  What is this? I think it is part or all of a video driver package down loaded directly from Radeon/AMD.  But all my graphics software was install using Ubuntu tools.  So, as far as I know, I don't have anything called "Catalyst" installed.  Can anyone explain this?  Maybe I've missed something here.

-thanks for any help

Laptop particulars:
uname -a
Linux HpLapTop 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 athlon i386 GNU/Linux

lspci | grep -i vga
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9903
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]

---

### Post by GreatDanton on 2012-08-11
Catalyst control center is control center (:D) for Radeon Graphic cards. In there you have many options to change. If you have installed drivers for your graphic card then you have Catalyst control center installed. In Dash (super or windows key) type Catalyst and you will see if you have it installed. Maybe you should check this link: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI .]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Unfortunately I don't know why is your computer overheating.
[]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by quadproc on 2012-08-11
Regarding the overheating, you didn't say which OS you are running.  I do know that one of the older ones (10.04 or 10.10) had an intermittent problem that would occasional;y make one of the CPUs 100% busy; this would run up the power usage and the heat.  I think that this was fixed a while back.

I am running a dual HD4870 system here and I do not know why anyone would say that a black screen would result in increased power consumption.  It was true with conventional broadcast TV (NTSC; pre-digital) that black video was sent at maximum power level.  In fact, it used to be a rule at some stations that the operator never left a black screen on for longer than a few seconds because of the heating problem.  But today's systems do not have this problem.

You can look for a couple of things related to the video: amdcccle is a program that allows the user to change graphics hardware settings, and ccsm is the Compiz settings manager which allows the user to select many software options for the graphics displays.  If you can run these then they are installed.  You could also look for the /etc/X11/xorg.conf file; if present, it contains details about the graphics hardware.

quadproc

---

### Post by st2000 on 2012-08-11
Hi again,
> type Catalyst and you will see if you have it installed
> catalyst
catalyst: Command not found.
> which catalyst
catalyst: Command not found.
> locate catalyst
> whereis catalyst
catalyst:
> 

> Maybe you should check this link: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Ah!:
[INDENT]You can make configuration changes through the AMD/ATI Catalyst Control Center, it can either be found in your Application menu or you can launch it through a terminal like this:

sudo amdcccle [/INDENT]

That appears to bring up catalyst.  So, why does everyone say to type catalyst? (It's not just you.)

> you didn't say which OS you are running
Sorry:
> lsb_release -a
[INDENT]No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise[/INDENT]

> black screen would result in increased power consumption
I gave you the wrong impression.  I was thinking that screen savers use up CPU time to calculate and GPU time to render the images.  So, black screen (no screen activity) should make the laptop run cooler.

> and ccsm is the Compiz settings manager which allows the user to select many software options for the graphics displays
Interesting.  On top of that, I've also finally executed the following command when the laptop was "running hot" with a black screen:

[INDENT]sudo sh -c "sleep 300 ; top -n1" >> ~/top_out_300.txt[/INDENT]

And look what's soaking up the CPU!:

[INDENT]2273 user    20   0  273m 105m  37m R  100  1.9  60:36.65 compiz             [/INDENT]

So, compiz is the problem here!  For some bent reason, just when it (probably) should be doing nothing, it's running the CPU up to 100%!  I there something we can do about this?  Where should this thread be moved to?  Should there be a Ubuntu bug report made?

-thanks

---

### Post by Lyfang on 2012-08-11
Try to choose "blank" for the screensaver. Maybe you are refering to the power manager settings? Maybe you are running an Open GL screensaver while to screen is shut off. Also you could try to update the AMD driver. 

I think that you should monitor your temperature with an applet. I would recommend lm-sensors, which can be installed using Synaptic. Then run from the Terminal:

```
sudo sensors-detect
```

---

### Post by st2000 on 2012-08-11
> Try to choose "blank" for the screensaver
That's all well and good. But I think this newest version of Ubuntu has-no-screen-savers installed by default.  You think that the brilliant minds at Ubuntu failed to test if having no screen savers installed makes compiz go nuts?


> should monitor your temperature with an applet
I am using psensor.  But thought it better to copy and past text from something like top instead of adding an image of psensor.  I do see the CPU and temp drop as soon as I break out of the black screen and unlock the desktop - if that is what you were interested in hearing.

-thanks again everyone for your help

---

### Post by marlow59 on 2012-08-11
is you laptop overheating even when not idle ?

---

### Post by st2000 on 2012-08-11
> is you laptop overheating even when not idle ?
I guess I should post a screen shot of psensor.  Here, I'll describe it.  When I unlock the Ubuntu desk top, the 2 CPU temperatures and the CPU usage all drop dramatically.  I can see before I unlock it the temperatures were a fairly constant 57 to 58 degrees C.  And after I unlock Ubuntu the temperatures drop by about 10 degrees C to about 46 C.  The processor on psensor goes from about a constant 43% to about a 2%.

I know I said 100% above.  What I think is going on is psensor is not seeing all 4 processors as it is only reporting one CPU percentage.  I figure tweaking psensor isn't as important as preventing my laptop from being cooked by Ubuntu from the inside out.

---

### Post by quadproc on 2012-08-12
> **st2000 said:**
> I guess I should post a screen shot of psensor.  Here, I'll describe it.  When I unlock the Ubuntu desk top, the 2 CPU temperatures and the CPU usage all drop dramatically.  I can see before I unlock it the temperatures were a fairly constant 57 to 58 degrees C.  And after I unlock Ubuntu the temperatures drop by about 10 degrees C to about 46 C.  The processor on psensor goes from about a constant 43% to about a 2%.

I don't know how much this will help, but here are a few observations from my perspective.  I am running a desktop quad processor system with dual HD4870 graphics cards in crossfire mode.  At the moment, I am running Linux Mint 13 (the Mate version) which is essentially Ubuntu 12.04 without the difficulties of Unity.  I usually run a system monitor task so that I can keep an eye on things (mate-system-monitor).  I normally have a Firefox task running.  My startup includes a set of temperature monitors which are sensing everything that they could find - the usual temperatures range from 30 to 36 degrees during idle times.  Idle CPU usage is less than 10% - it is hard to tell from the system monitor because the task reports 8 different CPUs but does not add them up.  I have my /home partition on a different drive so this makes it very easy to install a new OS; I have about 20 OS choices at boot time.  The system has up to 5 large hard disks available but I normally do not mount two or three of them.

When I lock the screen, I get the expected behavior - the system stays pretty much idle with the highest CPU usage reading at about 10%, the temperature indicators don't change much from the locked mode (assuming that they have a time constant on the order of a second or so), and this behavior is the same regardless of whether I wait a few seconds in lock mode or if I wait more than 5 minutes (my auto screenblank time) in lock mode.

All of this suggests that either the Unity software or the hardware differences are responsible for the problem.  Would it be worth installing Mint 13 for a comparison?  The Mint installation is nearly the same as the Ubuntu 12.04 installation.

quadproc

---

### Post by st2000 on 2012-08-12
@quadproc, Thanks for your input. > All of this suggests that either the Unity software or the hardware differences are responsible for the problem I am beginning to believe you are right.  I have read and re-read this bug report:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)
And I'm starting to convince myself this is the same problem I have.  That when the screen goes blank the HW is telling comp-z to "have at it".  And comp-z is going to town using all the CPU time it can get.

I have tried the work-arounds w/o much if any luck.  So I have simply turned off Ubuntu's ability to blank the screen.  I suppose I could have also installed the old Ubuntu screen savers.  As, it would appear, something on the screen is way better then a blank screen.  Funny isn't it. Ubuntu steps forward to save energy - only to, for many if not all of us, wast way more than if they had done nothing.

-thanks

edit: It's not really a Ubuntu problem.  I think it is more of a Unity desktop problem.

---

### Post by frosd on 2012-08-12
> **GreatDanton said:**
> Catalyst control center is control center (:D) for Radeon Graphic cards. In there you have many options to change. If you have installed drivers for your graphic card then you have Catalyst control center installed. In Dash (super or windows key) type Catalyst and you will see if you have it installed. Maybe you should check this link: []("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("http://kontaktniy.org") .
Unfortunately I don't know why is your computer overheating.

Catalyst control center is fun already =)

---

