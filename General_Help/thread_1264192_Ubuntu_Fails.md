---
title: "Ubuntu Fails"
date: 2009-09-11
forum: General Help
---

### Post by Ring-Ding on 2009-09-11
Hey, I'm dual booting with Vista and Ubuntu (I'm posting this on Vista right now, because Ubuntu is all ****** up) and I tried to run Ubuntu and do some simple config today and Ubuntu couldn't handle it and ****** itself up.

I am (was) running Ubuntu 64 bit, and I have dual monitors. I was trying to configure Ubuntu to properly use my dual monitors (having two desktops, one on each monitor, as opposed to mirroring screens) and I eventually got it to work, kind of. I had it set up but it thought my left monitor was on the right, so I tried to move it over and my main screen went black. Then after waiting for it to fix itself and reset the settings back to normal it crashed. I booted Ubuntu back up and (after waiting for check disk) I tried to fix the monitors again, and the same thing happened. I booted again and (after waiting for check disk again) tried to fix it yet again and it crashed again! So after this time I booted up and check disk failed, then it told me to fix it. Course I don't know how to fix what it screwed up in the first place.

Help?

---

### Post by mbuehl on 2009-09-11
I am very new to ubuntu, found the setup of dual monitors to be very easy. No crashes, easy to follow config. Failing checkdisk (though I really have no idea what that is - I can only assume) would indicate to me probable hardware issues rather than software?

What are you using to configure your desktops?

---

### Post by Ring-Ding on 2009-09-11
Well, I went into settings -> display, then was using the GUI to set up my monitors.

Yeah, failing check disks means that my hard drive is prolly all ****** up now. I'm gonna guess that its pretty likely that ima have to reinstall Ubuntu, but after all the **** its given me I don't really feel like it.

Also I read that you can press esc to skip the check disk but I did and it totally ignored me.

---

### Post by lisati on 2009-09-11
> **Ring-Ding said:**
> Well, I went into settings -> display, then was using the GUI to set up my monitors.

Yeah, failing check disks means that my hard drive is prolly all ****** up now. I'm gonna guess that its pretty likely that ima have to reinstall Ubuntu, but after all the **** its given me I don't really feel like it.

Two questions. 

Did you let the fsck (disk check) run to completion? (This might help avoid your disk being asterisked up)

Have you booted into recovery mode and used the options there to try to fix your settings?

<aside>We appreciate your frustration. Please remember that we try to be a "family friendly" forum, which is why some "colourful" words are usually censored.</aside>

---

### Post by mbuehl on 2009-09-11
> **Ring-Ding said:**
> Well, I went into settings -> display, then was using the GUI to set up my monitors.

Yeah, failing check disks means that my hard drive is prolly all ****** up now. I'm gonna guess that its pretty likely that ima have to reinstall Ubuntu, but after all the **** its given me I don't really feel like it.

If your hard drive is the issue I seriously doubt reinstalling anything will work.

When I ran ubuntu off the boot disk I had the option of having my HD checked for errors, I didn't use it, but you might see if you can navigate back to that.

Bad hard drives dont jive well with any OS, unless you're running knoppix or something else that's ram-driven.

I wasn't able to use the built in GUI to configure my monitors very well, then I got a different driver (Sorry, new... don't really recall where), and that gave me an nVidia-specific settings window, called "X server" Naturally if you're using something non-nVidia for your graphics (ATI, namely), you'll need to figure that out on your own - and I guess since I have no idea how to get the nVidia driver I have... you're on your own there too :D

Sorry for my newishness, just trying to help with the basics anyway.

gl

---

### Post by Ring-Ding on 2009-09-11
I let fsck run as long as it wanted to and it eventually stops at like 80% then says it doesn't know what to do and tells me to fix it.

I tried booting in recovery mode but that wants to run fsck too.

If theres something wrong with my hard drive then Ubuntu caused it, because this is a perfectly working drive and always has been.

I have an ATI card which means I might be able to use ATI's Catalyst Control Center or CCC to configure my monitors (i never thought about doing that, good idea) but first I need to be able to actually boot Ubuntu.

---

### Post by mbuehl on 2009-09-11
Ubuntu also caused the great depression of the 1920s.










I naturally have no logic or reasoning to back this up, but it's gotta be true.

---

### Post by Ring-Ding on 2009-09-11
Hey, I'm posting this now in Ubuntu, I fixed the problem.

I let fsck run to completion, then I surmised from its tricky language that it wanted me to type fsck then hit enter, so I did and fsck ran again. Then it found some errors on the drive, asked me should it fix it so I hit y successively and it eventually fixed itself.

Thanks for the support, i'm now off to try and fix my monitor problem through CCC (thanks mbuehl!)

---

### Post by Ring-Ding on 2009-09-12
Ok, so i've been trying to get these dual monitors to work for some time now and I haven't had any luck. It seems like my display manager is totally corrupted or bugged or something, because when I try to open it it freezes and slows down my computer like crazy and I have to fully logout then log back in again (effectively closing the frozen display manager) in order to use Ubuntu.

I managed to open CCC with administrative privlages (after searching the internet for the proper command for a while), but I can't completely configure my monitors through there. I have to enable more than one desktop through the display manager first, then I could probably configure it through CCC.

Is there any way that I could enter a command into terminal to enable more than 1 desktop or maybe even some way I could reinstall my display manager or fix it some way?

Thanks.

---

### Post by Ring-Ding on 2009-09-12
So it seems now like its some kind of problem with my driver and Ubuntu. Heres what happened:

At first my ATI driver was disabled and my display properties box worked. Through the display properties I enabled dual desktops and attempted to correctly configure the monitor positions. Once I had them configured the way I wanted I clicked apply and my main monitor screen went black, leaving me with only the secondary monitor working. I used ctrl+alt+del to restart the computer.

When Ubuntu rebooted I had dual desktops but my secondary monitor was on the wrong side (although both were working), so I enabled my ATI driver then restarted Ubuntu. Once it booted up again my previous settings (dual desktops) had been lost and I was back to mirror screens. Now with the ATI driver enabled the display properties freezes.

How do you update drivers in Ubuntu?

I have a Radeon HD4870.

---

### Post by Ring-Ding on 2009-09-12
I FINALLY fixed it. I was searching the internet for a solution and I finally stumbled upon this website: [http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/](http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/)

Aparrantly the driver that Ubuntu automatically installs when you select enable driver from its hardware dialog is incompatable with Ubuntu (go figure), so I had to install the one directly from ATI. I did and it worked. I finally have my displays set up alllmost the way the I want them.

I have 2 monitors, my right monitor is my main one and the one on the left is my secondary. Unfortunately, for whatever reaosn, Ubuntu automatically assumes that the one on the left is your primary, so right now I have the 2 system bars on my secondary monitor instead of my primary. I tried swapping the connections in the back but it still assumes the one on the left is my primary. Any ideas?

---

### Post by P4man on 2009-09-12
I guess Im too late to tell you to fetch new drivers from ATI's website, as they seem needed with your videocard..

Id still tell you this, just for reference, before installing the restricted driver, you had the opensource "ati" driver, and then you can use the "display" app to configure dual monitor. Once you install ATI's drivers, you have to use ATI's control panel.

I wish I could tell you how to change the primary monitor, with the nvidia tool, its just a matter of selecting the monitor and checking "primary display'. I can't imagine there isn't a similar option in ATI's CCC thing?

---

### Post by Ring-Ding on 2009-09-12
Yeah, I've looked and I don't see anything to let me set the primary display =/

---

### Post by P4man on 2009-09-12
does the linux ccc look like this:

[http://images.techtree.com/ttimages/story/95229_displaysmanagerletsyouadjustdisplaysettings.jpg](http://images.techtree.com/ttimages/story/95229_displaysmanagerletsyouadjustdisplaysettings.jpg)

?

If so drag, or right click the monitors under the "main" heading to define your primary (main) monitor.

---

### Post by Ring-Ding on 2009-09-12
Heres a screenshot of my CCC:

[http://img195.imageshack.us/img195/2245/screenshotxg.png](http://img195.imageshack.us/img195/2245/screenshotxg.png)

---

### Post by P4man on 2009-09-12
is there something (useful) behind that tiny down arrow on the biggest 1 screen ? And whats behind multidisplay ? And does right clicking those monitors do anything?

---

### Post by Ring-Ding on 2009-09-12
Ok, I got it. There wasn't a setting for primary monitor, I had to do some weird stuff and play around with things that I have no idea what they mean till I stumbled upon the solution by accident. Thanks!

---

### Post by jobst on 2009-09-12
If your computer crashes and you boot up again you WILL see a chkdsk, this is normal ... just be happy you do not have 10TB to be checked each time you do this.

You need to understand that upon crashing you have a ¨dirty filesystem¨, because while you were using your machine other things happen in the background ... this needs to be fixed upon the next reboot, thats all.

j

---

### Post by Chronon on 2009-09-13
> **Ring-Ding said:**
> Ok, I got it. There wasn't a setting for primary monitor, I had to do some weird stuff and play around with things that I have no idea what they mean till I stumbled upon the solution by accident. Thanks!

If you have an idea of what you did that worked it's worth posting here for others who find this discussion in a search and have the same problem.

---

### Post by Jago6060 on 2009-09-13
> **mbuehl said:**
> Ubuntu also caused the great depression of the 1920s.










I naturally have no logic or reasoning to back this up, but it's gotta be true.
I maintain that Windows did it.  The banks clicked cancel when Windows wanted to shut down...but it did it anyway.  :D

---

