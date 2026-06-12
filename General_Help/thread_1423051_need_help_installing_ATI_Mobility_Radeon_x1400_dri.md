---
title: "need help installing ATI Mobility Radeon x1400 driver on ubuntu 9.10"
date: 2010-03-06
forum: General Help
---

### Post by cloudxrocks on 2010-03-06
title says it all. i've been at this for hours and most of the post that i have searched use different graphics cards and all the methods are confusing me. please help.

---

### Post by Intrepid Ibex on 2010-03-06
Hmm.. I found this in just about 4 secconds: [http://ubuntuforums.org/showthread.php?t=390238](http://ubuntuforums.org/showthread.php?t=390238)

---

### Post by MatadorMac on 2010-03-06
> **cloudxrocks said:**
> title says it all. i've been at this for hours and most of the post that i have searched use different graphics cards and all the methods are confusing me. please help.

Good morning.  I am not a Linux expert by any means but I recently spent about 7 hours doing the same thing for my Radeon 2600 card and was eventually successful.

Could you be more specific about which drivers you are trying to install, how you are trying to install them and what errors you are getting if any?

Matadormac

---

### Post by michael37 on 2010-03-06
> **cloudxrocks said:**
> title says it all. i've been at this for hours and most of the post that i have searched use different graphics cards and all the methods are confusing me. please help.

**BASIC:**
Don't install anything.  Whatever you installed (esp ATI "binary" driver aka fglrx), uninstall. Remove /etc/X11/xorg.conf.  

That will default to "ati" (aka radeon) driver which "just works" in 9.10.

**ADVANCED:**
If you want an advanced configuration (Karmic or Lucid only!!!), refer to this page: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting), and follow section "KMS with a Radeon card"

---

### Post by MatadorMac on 2010-03-06
I just checked out that previous URL    [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

It appears to be pretty much what I did and was successful with my system only I used other resources.

I found that I had to fight through all the steps to a successful conclusion or my system was stuck in a low res limping configuration that I couldn't do anything about so stick with it and good luck.

Matadormac

---

### Post by michael37 on 2010-03-06
> **MatadorMac said:**
> I just checked out that previous URL    [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

It appears to be pretty much what I did and was successful with my system only I used other resources.

I found that I had to fight through all the steps to a successful conclusion or my system was stuck in a low res limping configuration that I couldn't do anything about so stick with it and good luck.

Matadormac

Good example of WHAT NOT TO DO.  This guide is way outdated by nearly 3 years.  Karmic 9.10 works in a very different way.  Notably, the drivers mentioned in this guide WILL NOT WORK with ATI Mobility Radeon X1400 due to changes with AMD/ATI proprietary driver.

---

### Post by cloudxrocks on 2010-03-06
> **Intrepid Ibex said:**
> Hmm.. I found this in just about 4 secconds: [http://ubuntuforums.org/showthread.php?t=390238](http://ubuntuforums.org/showthread.php?t=390238)
 i've been on that post tried the methods and still not able to get it working.

---

### Post by michael37 on 2010-03-06
> **cloudxrocks said:**
> i've been on that post tried the methods and still not able to get it working.

Same comment as previuos: the post is from 2007.  Today is 2010.  ATI as a company existed in 2007, it doesn't anymore (acquired by AMD).  The driver support is all different now.  FGLRX driver DOES NOT WORK for X1400 family in Ubuntu Karmic 9.10.

---

### Post by michael37 on 2010-03-06
General request: do not reply here unless you have experience with recent ATI hardware and drivers.  The outdated info is ... outdated.

[thread="1238129"]This (long) thread[/thread] has the most updated information, but the summary is in my comment #4.

---

### Post by cloudxrocks on 2010-03-07
> **michael37 said:**
> General request: do not reply here unless you have experience with recent ATI hardware and drivers.  The outdated info is ... outdated.

[thread="1238129"]This (long) thread[/thread] has the most updated information, but the summary is in my comment #4.

so what do u suggest i do?

---

### Post by michael37 on 2010-03-08
> **cloudxrocks said:**
> so what do u suggest i do?

read my comment #4 above.

---

### Post by pingu1 on 2010-03-08
I have an ATI Radeon x300 card - and got it working 100% - even compiz works flawlessly.
I followed this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by pingu1 on 2010-03-08
although I see your card is not listed in any of the lists on the page linked above - it may work even though... I'm no expert...

---

### Post by Mark Phelps on 2010-03-08
If you're getting a graphical desktop, you already have the open source driver installed.

If you download and attempt to install any other drivers, you will only hose up your display big time, have to then remove those drivers, and end up reinstalling the same open source drivers you already have.

Sorry, but ATI dropped Linux support for your card a long time ago.  There are no ATI drivers that will work with your card and any recent Ubuntu versions.

---

### Post by michael37 on 2010-03-08
> **Mark Phelps said:**
> If you're getting a graphical desktop, you already have the open source driver installed.

If you download and attempt to install any other drivers, you will only hose up your display big time, have to then remove those drivers, and end up reinstalling the same open source drivers you already have.

Sorry, but ATI dropped Linux support for your card a long time ago.  There are no ATI drivers that will work with your card and any recent Ubuntu versions.

Clarification: **X1400 card is fully supported in Ubuntu 9.10.**

"ATI driver" above refers to a proprietary AMD (formerly ATI) driver.  It's not needed nor recommended for X1400 chipset.  The best option is to use free open source "radeon" driver mentioned previously: 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Open source driver works particularly well when KMS/DRI2 is enabled per my previous comment #4. 

This driver is packaged with all versions of Ubuntu and Kubuntu and is provided by package xorg-xserver-video-ati

---

### Post by cloudxrocks on 2010-03-09
> **michael37 said:**
> Clarification: **X1400 card is fully supported in Ubuntu 9.10.**

Open source driver works particularly well when KMS/DRI2 is enabled per my previous comment #4. 


im having a problem with this. after i modify the bootoptions and run update-grub the options remain the same. am i doing something wrong?

---

### Post by michael37 on 2010-03-10
> **cloudxrocks said:**
> im having a problem with this. after i modify the bootoptions and run update-grub the options remain the same. am i doing something wrong?

Probably.  Try reading up this page:  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I assume you are using Grub2, not older Grub; that's a case when you fresh-install Ubuntu 9.10.

If this doesn't resolve, please start another thread to address Grub issue to avoid thread contamination.

---

### Post by rawlins02 on 2010-03-12
On a related note, I'd like to know if I'll be able to run flightgear flight simulator, which requires, I believe 3d acceleration. I have an ATI Radeon X1400 card (Thinkpad T60), and just yesterday installed Ubuntu 9.10.  Although glxgears shows good frame rate, I suspect flightgear needs FGLRX driver to run properly. A couple years ago when running Gutsy Gibon I used the Restricted Drivers Manager to install the proprietary ATI driver from Ubuntu repositories.

---

### Post by michael37 on 2010-03-13
> **rawlins02 said:**
> On a related note, I'd like to know if I'll be able to run flightgear flight simulator, which requires, I believe 3d acceleration. I have an ATI Radeon X1400 card (Thinkpad T60), and just yesterday installed Ubuntu 9.10.  Although glxgears shows good frame rate, I suspect flightgear needs FGLRX driver to run properly. A couple years ago when running Gutsy Gibon I used the Restricted Drivers Manager to install the proprietary ATI driver from Ubuntu repositories.

ATI Catalyst driver (former fglrx) discontinued support for X1400 using fglrx driver last year.

[http://en.wikipedia.org/wiki/Radeon#Linux](http://en.wikipedia.org/wiki/Radeon#Linux)

ATI Mobility X1400 is powered by R500 family chip.

Try the instructions for Kernel Mode Settings.  Even though current KMS reduces the speed of glxgears, it supposedly increases speed of complex full screen 3D ops. For performance, you may also choose to go with Lucid pre-release.

---

### Post by rawlins02 on 2010-03-13
Thanks. The more I read about newer versions of linux, older ATI cards, and drivers, I'm probably lucky that I got a working display when I installed 9.10. Most apps like all my Firefox plugins work fine. I'll have to try your suggestions the next chance I get.

---

### Post by michael37 on 2010-03-14
> **rawlins02 said:**
> Thanks. The more I read about newer versions of linux, older ATI cards, and drivers, I'm probably lucky that I got a working display when I installed 9.10. Most apps like all my Firefox plugins work fine. I'll have to try your suggestions the next chance I get.

Nah, radeon driver works extremely well in 9.10 out of the box.  It's just that adding 3D appearance, games, movie playing and etc will not run that hot.  That's what requires newer stuff.  Overall, anyone should have better experience by the time 10.04 comes up next month.

---

### Post by Mark Phelps on 2010-03-15
> **michael37 said:**
> Overall, anyone should have better experience by the time 10.04 comes up next month.

Based on what information?  

Where does it say that the 10.04 Ubuntu version of the open source driver is going to be any better for "legacy" cards than the current version?  I'm asking because I'm running one of the "legacy" cards and would like to see this information first hand.

---

### Post by aarteaga on 2010-03-16
Hi!
After hot-plugging and unplugging a beamer, 1680x1050 resolution is no longer displayed in the Display Preferences dialog. I tried installing propietary driver to solve the problem, but my card is a radeaon x1400. So, after failling with the installation, my graphic desktop only starts in low graphic mode. After reading some posts, I think all I need is to reinstall radeon driver, but I don't know how to do it.
Thanks in advance!

---

### Post by aarteaga on 2010-03-16
Ok, I tried the basic suggestion of #4. And now my graphic desktop is running again. But, in the Display Preferences does not display the 1680x1050 resolution yet.
Any idea? I was happy with my graphic performance before the beamer incident, so I don't wanna try advanced options unless totally needed.

---

### Post by michael37 on 2010-03-16
> **Mark Phelps said:**
> Based on what information?  

Where does it say that the 10.04 Ubuntu version of the open source driver is going to be any better for "legacy" cards than the current version?  I'm asking because I'm running one of the "legacy" cards and would like to see this information first hand.

In fact, yes, support for older cards, esp R300, R400 and R500 families, will be better in Lucid.  Read [http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon) in reference to the 2.6.32 kernel (to be used in Lucid).

---

### Post by michael37 on 2010-03-16
> **aarteaga said:**
> Ok, I tried the basic suggestion of #4. And now my graphic desktop is running again. But, in the Display Preferences does not display the 1680x1050 resolution yet.
Any idea? I was happy with my graphic performance before the beamer incident, so I don't wanna try advanced options unless totally needed.

Glad something is working for you.

You probably want to follow the cleanup guide after an attempt to use (non-working) proprietary driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

After that, please provide some kind of troubleshooting to help you diagnose your program.  As you realize, "it doesn't work" isn't particularly helpful.

---

### Post by aarteaga on 2010-03-25
Ok.
I followed the instructions of section "Problem: Need to fully remove -fglrx and reinstall -ati from scratch" in the #26's link. Evertything seems to work normally, with exception of the still missing resolution. I really don't know what troubleshoot information to provide or where to post my problem.
Thanks in advance.

---

### Post by Mark Phelps on 2010-03-25
One of the goals of Karmic was to avoid having to hack the Xorg.conf file to establish resolutions but to set the resolution using the Display applet from the Settings menu.  

Can you not do that on your system?

---

### Post by aarteaga on 2010-03-25
Yes, I can use the Display applet from the preferences menu. But, after using a beamer as extended desktop, 1680x1050 resolution is no longer displayed.

---

### Post by landman 1560 on 2010-04-15
I have a similar issue as far as resolutions go to the above post.  I just bought a 23" Hannspree monitor that has a 1920 x 1200 resolution and I can only get the GUI to let me have 1280 x 720.

I'm running the monitor as an extended on a Dell E1505 with an X1400 vid card.  I would really like to be able to run this at a higher resolution for work reasons.

I have tried it in Vista and I can get the higher resolution so I know the vid card will push it.  However 9.10 just doesn't seem to recognize the resolutions the monitor will use.

Any help would be great.  Also, if this might be fixed in 10.04 I'll just wait. :)

---

### Post by Mark Phelps on 2010-04-15
> **landman 1560 said:**
> I have a similar issue as far as resolutions go to the above post.  I just bought a 23" Hannspree monitor that has a 1920 x 1200 resolution and I can only get the GUI to let me have 1280 x 720.

I'm running the monitor as an extended on a Dell E1505 with an X1400 vid card.  I would really like to be able to run this at a higher resolution for work reasons.

I have tried it in Vista and I can get the higher resolution so I know the vid card will push it. 
And ... you probably installed the ATI video drivers in Vista, right?  Problem is there are no ATI Linux drivers that will work in 9.10. 

>  Also, if this might be fixed in 10.04 I'll just wait. :)

Anything is possible, but you should go to the 10.04 beta testing forum and look around for ATI video-related posts -- you may find an answer to your question there: Development & Programming, Lucid Lynx Testing.

---

### Post by clhsharky on 2010-04-15
HI

Newer OSS drivers "open source stack" default video drivers can be be found at this PPA.

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Please read the whole page, before installing.

They are stable for me, your hardware may very. Hope they may be of some help to you.

Sharky

---

### Post by michael37 on 2010-04-15
> **landman 1560 said:**
> I have a similar issue as far as resolutions go to the above post.  I just bought a 23" Hannspree monitor that has a 1920 x 1200 resolution and I can only get the GUI to let me have 1280 x 720.

I'm running the monitor as an extended on a Dell E1505 with an X1400 vid card.  I would really like to be able to run this at a higher resolution for work reasons.

I have tried it in Vista and I can get the higher resolution so I know the vid card will push it.  However 9.10 just doesn't seem to recognize the resolutions the monitor will use.

Any help would be great.  Also, if this might be fixed in 10.04 I'll just wait. :)

1. Do you have xorg.conf, and if yes, why?  Sometimes a malformed or old xorg.conf may mess you up.

2. Are you using kernel mode-setting?  If not, try it.  It's notably better in picking up resolutions.

---

### Post by david.burlingame on 2010-06-01
Thanks :)
I had the same problem x1400 radeon on 9.10 and the advanced steps listed in reply #4 worked for me.  

Cheers,
-Dave

---

