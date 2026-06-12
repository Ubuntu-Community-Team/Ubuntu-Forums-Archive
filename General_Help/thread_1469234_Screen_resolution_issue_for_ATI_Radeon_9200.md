---
title: "Screen resolution issue for ATI Radeon 9200"
date: 2010-05-02
forum: General Help
---

### Post by vyco10 on 2010-05-02
I just installed Ubuntu 10.04 earlier and am having an issue with the screen resolution. The issue I'm having is that I can't change the resolution to go above 1024 x 768, where I could before in Ubuntu 9.10. Well... I should say, I can change it to 1360 x 768 but it seems to be for a wide screen monitor or something. Everything looks stretched when I change it to that resolution. I tried installing the fglrx drivers from ATI, but that created an issue to where I couldn't use Compiz any longer.

I am using a Dell CRT monitor, which is probably part of the problem but I don't have the funds to just go buy another monitor at the moment. When I open up Monitor Preferences it says "unknown" monitor, as it can't detect it. I'm guessing this is something I will need to manually enter into a config file (*xorg.conf or something*) but am not sure what I need to enter.

Thanks for the help.

```
id:	
display:0
description: 	VGA compatible controller
product: 	RV280 [Radeon 9200 PRO]
vendor: 	ATI Technologies Inc
physical id: 	
0
bus info: 	
pci@0000:02:00.0
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list rom
configuration:	
driver	=	radeon
latency	=	64
mingnt	=	8
```

---

### Post by lavinog on 2010-05-02
ATI no longer supports your card with the propritary driver...attempting to install it can break your system.

do you have a /etc/X11/xorg.conf file?
if so, try renaming it to something else...xorg shouldn't need that file anymore.
Also look in synaptic for anything with fglrx and uninstall it.

---

### Post by vyco10 on 2010-05-02
> **lavinog said:**
> ATI no longer supports your card with the propritary driver...attempting to install it can break your system.

do you have a /etc/X11/xorg.conf file?
if so, try renaming it to something else...xorg shouldn't need that file anymore.
Also look in synaptic for anything with fglrx and uninstall it.

I guess I should ask the most obvious question then... why did the Ubuntu team include the driver with this latest release?

There is no xorg.conf file in that directory.

---

### Post by dino99 on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by ams_0 on 2010-05-02
Hello,
I have the same problem with my Radeon 9200.
The driver seems to be installed properly but I still get a low resolution.
I had this problem since Ubuntu 9.04 and I've been doing a fresh installation on every major release (9.10 and now 10.4).

I usually try to work around this by editing the xorg.config by adding my desired resolution manually.
This time I'm trying something new, xrandr. It gave the same result as editing the  xorg.config did. I'm still experimenting, though.

I'm anything but an expert but I had this annoying problem for sometime and still didn't figure it out. Mainly be cause I'm not satisfied with the result.
I'm not sure what the problem is exactly, and would appreciate some expert help.

--Abdullah

---

### Post by lavinog on 2010-05-02
> **vyco10 said:**
> I guess I should ask the most obvious question then... why did the Ubuntu team include the driver with this latest release?

There is no xorg.conf file in that directory.

It is included for users that have newer cards where the open source driver has limited 3d support.

---

### Post by lavinog on 2010-05-02
> **ams_0 said:**
> Hello,
I have the same problem with my Radeon 9200.
The driver seems to be installed properly but I still get a low resolution.
I had this problem since Ubuntu 9.04 and I've been doing a fresh installation on every major release (9.10 and now 10.4).

I usually try to work around this by editing the xorg.config by adding my desired resolution manually.
This time I'm trying something new, xrandr. It gave the same result as editing the  xorg.config did. I'm still experimenting, though.

I'm anything but an expert but I had this annoying problem for sometime and still didn't figure it out. Mainly be cause I'm not satisfied with the result.
I'm not sure what the problem is exactly, and would appreciate some expert help.

--Abdullah
It looks like there is an issue with the 9200 and KMS.
try disabling kernel modesetting
```

echo options radeon modeset=0 | sudo tee /etc/modprobe.d/radeon-kms.conf

```

then reboot.

KMS can be reenabled by removing /etc/modprobe.d/radeon-kms.conf

---

### Post by vyco10 on 2010-05-02
I ran across this step-by-step tutorial on how to modify Plymouth... [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Good thing is... I was finally able to raise my screen resolution. Bad thing is... my wallpaper won't appear now. I get a black background instead of the wallpaper. The icons won't show up either.

---

### Post by ams_0 on 2010-05-02
> **lavinog said:**
> It looks like there is an issue with the 9200 and KMS.
try disabling kernel modesetting
```

echo options radeon modeset=0 | sudo tee /etc/modprobe.d/radeon-kms.conf

```then reboot.

KMS can be reenabled by removing /etc/modprobe.d/radeon-kms.conf

It worked! Thanks!
However, as I said before, the result is far from satisfying. The text is too fuzzy and the resolution, though is better, is still ruining the experience.
The weird thing is when I use 1280*1024 under Windows XP I get a perfect crisp image. Using the same resolution under Ubuntu results in a stretched cropped one. So I tried (by editing the xorg.config) 1280*960 it gave the a good result.
Using your method, it automatically gave me 1152*864, which looks as good as the 1280*960. At first I didn't even notice.
That's a real head-scratcher for me since 1280*1024 and 1280*960 (and now the new 1152*864) have different aspect-ratios, 5:4 and 4:3 respectively. 
So how come that 1280*1024 works perfectly under windows but not Ubuntu?

**Edit: **I just noticed that the desktop is black, no icons no wallpaper. I re-enabled KMS and its good now but I'm back to 1024*768 :(
--Abdullah

---

### Post by vyco10 on 2010-05-02
This is getting to be very frustrating. Every release it's one thing causing problems... the next release it's yet another. How do they expect the general public to adopt Ubuntu/Linux if this is the best they can do? And don't come at me all offended over the comments I'm making. I understand a lot of hard work has been poured into the Ubuntu project over the years. But some of these problems are ridiculously absurd. Screen resolution is something very fundamental in day-to-day computing. It's not like this is a problem with some out-of-left-field application or configuration setting. This is basic computing problems people are having... problems people were having 4 and 5 years ago that are still cropping up.

I know a lot of the Linux enthusiasts don't like hearing this, but if problems like this can't be dealt with before a distribution's release you can expect to never overtake Microsoft or Apple. _Never_. Laypeople aren't going to use something out-of-box that doesn't work just because it's free.

---

### Post by ams_0 on 2010-05-02
> **vyco10 said:**
> This is getting to be very frustrating. Every release it's one thing causing problems... the next release it's yet another. How do they expect the general public to adopt Ubuntu/Linux if this is the best they can do? And don't come at me all offended over the comments I'm making. I understand a lot of hard work has been poured into the Ubuntu project over the years. But some of these problems are ridiculously absurd. Screen resolution is something very fundamental in day-to-day computing. It's not like this is a problem with some out-of-left-field application or configuration setting. This is basic computing problems people are having... problems people were having 4 and 5 years ago that are still cropping up.

I know a lot of the Linux enthusiasts don't like hearing this, but if problems like this can't be dealt with before a distribution's release you can expect to never overtake Microsoft or Apple. _Never_. Laypeople aren't going to use something out-of-box that doesn't work just because it's free.

We have a problem and we are trying to solve it. Don't be too negative. :)

---

### Post by lavinog on 2010-05-02
> **vyco10 said:**
> This is getting to be very frustrating. Every release it's one thing causing problems... the next release it's yet another. How do they expect the general public to adopt Ubuntu/Linux if this is the best they can do? And don't come at me all offended over the comments I'm making. I understand a lot of hard work has been poured into the Ubuntu project over the years. But some of these problems are ridiculously absurd. Screen resolution is something very fundamental in day-to-day computing. It's not like this is a problem with some out-of-left-field application or configuration setting. This is basic computing problems people are having... problems people were having 4 and 5 years ago that are still cropping up.

I know a lot of the Linux enthusiasts don't like hearing this, but if problems like this can't be dealt with before a distribution's release you can expect to never overtake Microsoft or Apple. _Never_. Laypeople aren't going to use something out-of-box that doesn't work just because it's free.

Ubuntu will always be a work in progress.  New technologies are implemented pretty quickly but the implementation sometimes leads to regressions.  Also The bugs that many people are experiencing are due to KMS which is a major milestone for linux...it is a big thing that has potential for many bugs to arise.  KMS just started being implemented during karmic, and it was decided to push to fully implement it in lucid...at some point it needed to be implemented so that progress could be made.
It isn't always easy for developers to anticipate these sort of issues.  They will get fixed, but it will take some time.
These issues are not 4 or 5 years old.
The correct way to resolve this issue is to file a bug report if not already filed.  Developers rarely read the forums.

---

### Post by blackSP on 2010-05-03
> **vyco10 said:**
> This is getting to be very frustrating. Every release it's one thing causing problems... the next release it's yet another. How do they expect the general public to adopt Ubuntu/Linux if this is the best they can do? And don't come at me all offended over the comments I'm making. I understand a lot of hard work has been poured into the Ubuntu project over the years. But some of these problems are ridiculously absurd. Screen resolution is something very fundamental in day-to-day computing. It's not like this is a problem with some out-of-left-field application or configuration setting. This is basic computing problems people are having... problems people were having 4 and 5 years ago that are still cropping up.

I know a lot of the Linux enthusiasts don't like hearing this, but if problems like this can't be dealt with before a distribution's release you can expect to never overtake Microsoft or Apple. _Never_. Laypeople aren't going to use something out-of-box that doesn't work just because it's free.


I love Ubuntu and don't mind countless hours of tweaking after every upgrade. Yes, at the same time it is frustrating if a new distro does not run perfectly 'out of the box'.

I'm sure that all Linux lovers or technically savvy people don't see this as an issue but I agree with **vyco10**. This is not good when trying to acquire a larger footprint...

---

### Post by vyco10 on 2010-05-03
> **blackSP said:**
> I love Ubuntu and don't mind countless hours of tweaking after every upgrade. Yes, at the same time it is frustrating if a new distro does not run perfectly 'out of the box'.

I'm sure that all Linux lovers or technically savvy people don't see this as an issue but I agree with **vyco10**. **This is not good when trying to acquire a larger footprint**...

This was really my point.

I consider myself a Linux enthusiast. I hope to one day be completely and %100 migrated to Linux. I'm fairly familiar with computers and how to navigate the software, but I'm not an expert by anyone's stretch of imagination. I have to scratch and claw at Google to figure out how to solve these issues. IMO, it shouldn't have to be this way. I understand the need to push new technologies forward, but there's also a need to be practical. That should take precedence over trying to push new technologies forward if the endgame is have Linux adopted by as many people as possible.

---

### Post by gAzZa! on 2010-05-20
I had a similar problem when I upgraded Kubuntu to Lucid from Karmic using the Kpackage updates.  My card that was effected was a ATI Radeon 9250, except that it was a little a bit more serious in my instance.  I didn't even get a log-in screen all I got was a blank screen and no disk activity instead.

Luckily I was able to launch via Recovery Mode and then used low graphics mode and was able to log-in I then entered the previously quoted code here which solved the problem :-

```

echo options radeon modeset=0 | sudo tee /etc/modprobe.d/radeon-kms.conf

```then reboot.

I am also a big fan of Ubuntu but this is 3 times I have now upgraded and 3 times that graphics card problems have prevented Ubuntu even booting up properly.

With the amount of similar issues I have seen posted on the net surely this should have been identified during testing??? :confused:

Unlike others I will keep using Ubuntu mainly because I believe there should be serious open-source competition to the Microsoft desktop monopoly that should be supported but I will hope future upgrades will be smoother than this.

---

### Post by Mark Phelps on 2010-05-21
> **gAzZa! said:**
> ... With the amount of similar issues I have seen posted on the net surely this should have been identified during testing???...

Unlike MS, Canonical does not have tens (or hundreds?) of millions of dollars to commit to testing Ubuntu.  So, it's unlikely that a card that ATI relegated to "legacy" status over a year ago is going to be tested.

These kinds of problems are one of the main reasons I believe that beta-testing should be devoted to actual testing -- allowing folks to test the new OS version against their hardware to see what problems arise. 

So, when the next version gets to the testing stage, jump over to the testing forum and test it yourself.  That way, you can give them an early heads-up on any video card related problems -- that may then get fixed prior to release.

---

### Post by arunabhdas on 2010-05-26
Following the following steps should fix the issue - 

1. Start Virtual box and log into Ubuntu.

2. Hit the right ctrl key so you can get your mouse pointer outside the virtual machine.

3.Go to top of virtual window, click on devices then select "Install Guest Additions"
You will see a window pop up inside Ubuntu showing you that there are some new files mounted in a virtual CDROM drive. One of those files should be VBoxLinuxAdditions.run

You must run the file with some admin permissions so do that this way...

4. Click inside the Ubuntu screen again then go to Applications - Accessories then Terminal. The terminal window is where you will run the file from, but first we must navigate to the correct directory.

5. type this... cd /media/cdrom0 (then hit enter, there is a space after cd!)

6. next type... dir (You should see amongst the files displayed VBoxLinuxAdditions.run)

7. now type... sudo sh ./VBoxLinuxAdditions.run (yes, that is a full stop before the slash!)

after you hit enter and it has done its stuff, the files are now accessable from Ubuntu.

8. You now need to reboot the virtual machine or press Ctrl+Alt+backspace.

9. Log onto the Ubuntu desktop and this time go to System - Preferences then Screen Resolution. You should now have more options than the three low res options you had at the beginning of the day!

---

### Post by turbo9 on 2011-01-22
I just had this problem (again) and blamed my ATI card as well. This was with Ubuntu 10.10 running on bare hardware.

It turns out that Ubuntu could not get the right video resolution from my monitor. I see a number of these messages in dmesg


[   12.905074] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 63
[   12.905125] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   12.905166] <3>40 ff ff ff ff ff ff ff 22 64 b3 06 01 08 00 00  @......."d......
[   12.905170] <3>2e 0f 01 03 0a 22 1b 78 ea fd 59 a5 53 4a 9d 24  .....".x..Y.SJ.$
[   12.905173] <3>14 4f 56 bf ef 80 81 80 31 0a 31 ca 01 01 01 01  .OV.....1.1.....
[   12.905176] <3>01 01 01 01 01 01 30 2a 00 98 51 00 2a 40 30 70  ......0*..Q.*@0p
[   12.905179] <3>13 00 52 0e 11 00 00 1e 00 00 00 fd 00 38 4b 1e  ..R..........8K.
[   12.905182] <3>50 0e 00 0a 20 20 20 20 20 20 00 00 00 ff 00 35  P...      .....5
[   12.905185] <3>34 36 44 44 31 4b 43 41 32 30 34 39 00 00 00 fc  46DD1KCA2049....
[   12.905188] <3>00 48 61 6e 6e 53 74 61 72 20 55 31 37 31 00 80  .HannStar U171..

Now, this worked in Ubuntu 10.04, but didn't in 10.10. Then, it magically started working in 10.10 for a few weeks and then the problem came back.

Here is how I fixed it:

You don't need to be root to do this.

Check to see if the video mode exists. 

	xrandr

If the one we want is missing, we need to add it. 
Get the mode line from the desired resolution:

	cvt 1280 1024	

which barfs out something like:

	# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
	Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

Grab the modeline from the second line of output and add it to the known modes:

	xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

Things might shimmy a bit, which you might interpret as a good sign.

Associate this mode with the appropriate video output

	xrandr --addmode VGA-0 1280x1024_60.00

Then use your normal video resolution gui to set it and then make it the default.

This setting does not survive a reboot. You get a bunch of "could not set monitor resolution" messages.
The default setting survives the restart, but the system does not know the mode exists (same problem as before).
So, write a script with the steps above and execute it once you login (put a call to it on the panel). 

	xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
	xrandr --addmode VGA-0 1280x1024_60.00

Things should shimmy and then go to the resolution you set as default before.

This is not a permanent fix - it is a hack, but I can live with it (rather than buying a new monitor).

---

### Post by lavinog on 2011-01-24
> **turbo9 said:**
> I just had this problem (again) and blamed my ATI card as well. This was with Ubuntu 10.10 running on bare hardware.

It turns out that Ubuntu could not get the right video resolution from my monitor. I see a number of these messages in dmesg


This could be caused by the monitor and not the card.
What monitor do you have, and what type of connection are you using (vga/dvi/hdmi/displayport)

---

### Post by lavinog on 2011-01-24
> **turbo9 said:**
> 
[   12.905074] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 63


Actually, this might be caused by noise or a bad connection.  Have you tried using a different cable, or re-routing the cable away from things that can cause interference?

---

### Post by turbo9 on 2011-01-24
> **lavinog said:**
> This could be caused by the monitor and not the card.
What monitor do you have, and what type of connection are you using (vga/dvi/hdmi/displayport)

Thanks for helping, but you should know that I have fixed my resolution problem. 

I'm hoping that you're wanting to address the cause of my problem (which was a varying EDID checksum calculation) for everyone else having a similar "an upgrade to Ubuntu broke my video resolution" problem.

If that's the case, all the data you seek is actually in my post - it's a HannStar U171 on VGA-0 (on at ATI 9200SE video card). Yes, this is old crappy gear which still works great.

---

### Post by turbo9 on 2011-01-24
> **lavinog said:**
> Actually, this might be caused by noise or a bad connection.  Have you tried using a different cable, or re-routing the cable away from things that can cause interference?

No, I have not. I did tighten up the connections.

The fact that it worked great for years, then broke on the upgrade in October, fixed itself in December only to break again in January led me to believe that the problem was not transient like you'd get with a bad cable. The magic fix and subsequent rebreak both happened after up update, so I lean towards this being a software problem.

---

### Post by turbo9 on 2011-03-02
> **turbo9 said:**
> 

The fact that it worked great for years, then broke on the upgrade in October, fixed itself in December only to break again in January led me to believe that the problem was not transient like you'd get with a bad cable. The magic fix and subsequent rebreak both happened after up update, so I lean towards this being a software problem.

Sigh. This again fixed itself in February, only to break again on an update I applied this morning. There was a kernel update as part of this morning's update. I check for updates daily, so this "fix" was not in the repository yesterday.

Luckily, I configured a "startup application" last time, which I never deleted.

---

