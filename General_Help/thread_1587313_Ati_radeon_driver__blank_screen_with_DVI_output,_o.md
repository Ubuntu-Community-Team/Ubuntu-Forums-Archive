---
title: "Ati radeon driver : blank screen with DVI output, ok with VGA, both ok with radeonhd"
date: 2010-10-03
forum: General Help
---

### Post by fanf42 on 2010-10-03
Hello guys,

To start, a bit of configuration:
> 
% lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
...
It's a card with a VGA and a DVI output.

My monitor is a Samsung SyncMaster 2232bw (it seems to have something to do in the story). Its native resolution is 1680x1050

I just switch to 10.10 and discovered that the radeonhd driver is no more supported.
Problem: the "radeon" (or "ati", as it's the same) driver does not work well for me:
- if I use the DVI output, I just get a blank screen
- with the VGA output, I get a really *really* bad image, difficult to describe: its blurred, or with kinds of waves, as if there was a lot of interferences. It's almost not usable at 1680x1050, better at lower resolutions

Fglrx does not work either, at 1680x1050 I get a "flashing" image (screen goes blank every 2 seconds or so), and at lower resolution the screen is flashing (but less frequently)

"Vesa" driver works perfectly, both on VGA and DVI, but I can not use 1680x1050 with them, only 1280x1024.

It uses to work perfectly at 1680x1050 with radeonhd driver.

So, it seems that there is something wrong with either my card, the screen, or the combination of the two. But for now, with Ubuntu 10.10, I have no solution to have a clean display at my screen native resolution.

Changing from KMS with radeon.modeset=0 as no consequence.

What could be the problem ? Bad EDID from the screen ? Hardware problem (but if so, why it workred with radeonhhd?) ?

Any idea ?

Joined: Xorg.log for VGA and DVI

---

### Post by fanf42 on 2010-10-03
Precision: when I use DVI cable and have a blank screen, I'm able to switch to a console with ctrl+alt+F1. 

So, perhaps it's something with the resolution... but if I try to specify lower modes in xorg.conf, I still get a blank screen.

---

### Post by fanf42 on 2010-10-05
Some more information: the radeon driver works with DVI output if I connect my TV on it in place of my screen. 

So, it seems that somehow, when I use the DVI connection with the screen, the driver configuration is not accurate (bad modes ?), and that is really a missfit between my video card and that screen...

Anybody has an idea about what I could try to solve that problem ?

For example, I don't see any "corrupt EDID" related things on the Xorg.log, but perhaps somebody with some more knowledge in X log than me could try to see if something seems wrong in that log ?

Thanks in advance,

---

### Post by fanf42 on 2010-10-07
I opened a bug for that[1], as I'm really *really* annoyed: actually, with Ubuntu 10.10, I just can't use my monitor with its native resolution, and I'm forced to look at a distorted screen - something I won't do until 11.04 is out.  

I would be glad to test and/or bring other information, anything to try to understand what is going on. 

[1] [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/655200](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/655200)

---

### Post by fanf42 on 2010-10-14
Really, nobody has any idea ?

I posted a Xorg.log file from the working radeonhd/ubuntu 10.04 driver in the bug report.

I noticed that the reported  PixClock max is 140 with that driver and 145 with the (not working) radeon / ubuntu 10.04 and 10.10 driver. Does it ring a bell for someone ?

Thanks,

---

### Post by Mark Phelps on 2010-10-14
IF you're complaining specifically about bugs with the radeonhd driver, you're simply out of luck -- because, from what I've read, development on that driver has stopped.  So, it's highly unlikely that any bug already not fixed are going to be fixed in the future.

---

### Post by fanf42 on 2010-10-14
@Mark : thanks for your reply, but I fear I wasn't clear in my question.

I *used* to use the radeonhd driver under 10.04, and it was working great.
I updated to 10.10 where this driver is no more used and so, now I would like to use "radeon" driver.

The radeon driver is not working with my hardware configuration. It wasn't working any better on 10.04, but as there was an alternative, that wasn't a big problem.

I posted Xorg.log for both radeon and radeonhd in the hope that someone who is able to understand them will be able to spot a difference and help me configure the radeon driver in the same way radeonhd was (automatically).

Moreover, it seems to have something to do with the use of DVI and "radeon" driver on that very screen of mine, because VGA works (but is ugly, not usable) and everything work perfectly on my TV (but for some reason, my wife does not want that I switch the monitor with the TV)

I attempted to spot a difference in all the Xorg log, but I don't see many relevant things, save a parameter named "PixClock" reported at 140 with the working radeonhd driver and at 145 with the broken "radeon" driver. 

Thanks again, in the hope to have been clearer with my problem :/

---

### Post by nutellajunkie on 2010-11-08
An excuse to bump this thread.. Cause I am getting fed up of this lovely effect that this buggy thing has!

Is there a solution anywhere been found?

Thank you.

---

### Post by dcstar on 2010-11-09
> **nutellajunkie said:**
> An excuse to bump this thread.. Cause I am getting fed up of this lovely effect that this buggy thing has!

Is there a solution anywhere been found?


You have a read of the bug report and tell us.

---

### Post by nutellajunkie on 2010-11-09
oh thanks, just expect everyone to know what a bug report is, that&#8217;s hardly the community spirit of Ubuntu..

as per your signature dcstar, I did search. And your how to ask a question the smart way, well.. heh.

---

### Post by spaceduel on 2010-11-19
I only have minimal experience with Ubuntu - I was running 8.04 on a spare computer just for fun. I tried to install 10.10 on my main desktop and experienced the same symptoms as fanf42 - blank and flashing screen. As the install cd began booting, when it gets to the point where you can choose "Try" or "Install," the screen flashes on for about a second, then goes blank (black) for about 5 - 10 seconds before it flashes again, but the time in between flashes is random.

I have an ati Radeon X1600 video card w/ 512mb ram and an Acer P244W 24" widescreen monitor.

The problem only seems to be with the DVI connection - not with the VGA connection.

While trying to troubleshoot the problem, I connected an older Samsung monitor (15" non-widescreen) with the VGA connnection (that's all the samsung has available) just to see if the problem was with the monitor, and sure enough, every thing looks fine after rebooting the Ubuntu install cd. I was able to "Try" Ubuntu by running the live cd - everything looked great. 

My next test was to try the VGA connection with the Acer monitor instead of the DVI (the Acer offers both connection types). Once again the flashing and blank screen went away. I was able to change resolutions while running the live cd. It defaulted to 800x600 - I changed it to 1024x768 (this was the only other resolution available on the live cd.)

So now I hesitate installing Ubuntu 10.10. I don't want to have to change my video cable to VGA. 

Last point is this would be a duel boot. I'm currently running XP sp3 with no video issues.

---

### Post by mas_sergio on 2011-01-04
crap man im in the same situation as you and im begining to think its my old monitor. My theory is that if some how I can edit the config file in recovery mode (selected at start up of grub) that i can some how, some way, via text input force the driver to be configed to use DVI + a resolution my monitor supports. I am getting a new monitor (TV) soon but this is so annoying to deal with until I get it im bummed. I don't like this one bit. ATI make good cards but this lack of linux support is very frustrating I mean seriously who likes linux without compiz? (Excluding the few terminal hard core linux users lol). I was mad/bummed. I don't hate linux I just hate all this configuring required to just see the darn screen. Rrrr.. This kind of stuff happens in windows to btw but is fixed very simply via vga port(if ur monitor supports it). what sux is my video card does not have a vga only hdmi dvi and some other inpute wich i don't know what it is. I'm screwed. >:/

BTW on 10.4 I noticed the same artifacts your complaining about it's maddening. People have mentioned in forums upon using different monitors they get different results. I find that odd.

My problem with my theory is this:
I don't know what text to input to get my resolution @ 1280x1024 (Max this monitor will support)
and I don't know what text to enter or where to FORCE DVI to be the main input...


any info on that will help me grately... btw i have no internet in my ubuntu/mint distro yet. I would take this to the mint forums but I swiped ubuntu with mint hoping it would fix something (i noticed a little less tearing but artifacts where still present) but mint did not fix the problem. same issues and its based off of 10.10. so yeah... i figgured it would be appropriate to post here.

Much thanks,
Mas Sergio :)

---

### Post by JDorfler on 2011-01-04
Ok, I have that monitor back in the States.  Never had a problem with the DVI, but I have a SyncMaster T240 here.  Now.  As of 10.04 with a RadeonHD 5870 you must use the top DVI port, and not the bottom one.  Now.  With this in mind, what ATi card do you have, how many DVI ports does it have, and who is the manufacturer?

---

