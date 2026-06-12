---
title: "ubuntu 10.04 - Suspend, Hibernate not working"
date: 2010-05-02
forum: General Help
---

### Post by SyAu on 2010-05-02
I have Ubuntu 10.04 installed in my laptop and facing problems with Suspend and Hibernate options, both are not working. Please help me to fix this. For information, I'm dual booting with xp.

---

### Post by P4man on 2010-05-02
is this a wubi install or not?
What hardware?
What happens when you try suspend and when you try hibernate?

---

### Post by Don9307 on 2010-05-02
I'm having the same issue with suspend and hibernate not working on my Presario V5000 laptop.  After suspend, you must shut down the laptop and turn it back on.  After suspend, networking is interrupted as well.  To fix the networking problem, I have to Enable Networking again.

---

### Post by leag on 2010-05-02
me too, i have a compaq cq40 320la

---

### Post by elclanrs on 2010-05-02
me too, I have an Acer Aspire One 150.

---

### Post by dino99 on 2010-05-02
dont forget to look at bios settings

---

### Post by jja on 2010-05-02
After update from Karmic to Lucid my machine stopped doing proper hibernate... Worked with Karmic... Everything looks like with Karmic, but no resume... It seems that the bug [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/499940]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940") still persists. At least with updates from Karmic.

---

### Post by pmos69 on 2010-05-02
here's the bug I filled for my problem with resume from suspend (hibernate works fine)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by jja on 2010-05-02
Strange. It seems that I have more problems with hibernate...

---

### Post by SyAu on 2010-05-03
> **P4man said:**
> is this a wubi install or not?
What hardware?
What happens when you try suspend and when you try hibernate?

No this is not a wubi install. I got HP pavilion dv9000 with Intel Core2 duo and nVIDIA GEFORCE GO 7600.

---

### Post by Taus on 2010-05-03
i'm not completely sure about this - but i think i read somewhere on ubuntu bug list that if u perform a default install u have to make sure that the SWAP partition is AT LEAST the same size as the total ram on your machine. If the swap is smaller than that hipernate/suspend won't work.

Cheers

---

### Post by gmmarcin on 2010-05-03
same for me - did an upgrade from Karmic 9.10 where both hibernation and suspend worked fine on Lenovo X61s

---

### Post by giorsat on 2010-05-03
I have a hppavillion dv7 with nvidia geforce 9600 m gt and both suspend and hibernate don't work both on 64bit version and 32bit one. fresh installs for both.

---

### Post by cecilx22 on 2010-05-03
I can confirm this on the Dell Stuido XPS16 as well...  dang

---

### Post by pmos69 on 2010-05-03
Everyone affected should either fill a new bug report or mark an existing bug as affecting them.
Here's mine: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by DrWig on 2010-05-04
This seems to be exactly the same issue as I'm having:
[http://ubuntuforums.org/showthread.php?t=1464559&highlight=drwig](http://ubuntuforums.org/showthread.php?t=1464559&highlight=drwig) 

I too get the networking issue, but not all the time (after a hardboot after failed resume...)

cheers

DrWig

---

### Post by jferna57 on 2010-05-07
I have the same problem in sony vaio vgn-sr19xn.

My swap space -> 3,1 Gb
My memory space -> 3 Gb

In ubuntu 9.04, 9.10 works fine for me....

---

### Post by DrWig on 2010-05-07
I might test the 9.10 live CD to see if suspend and hibernate works on that, but I'm pretty sure it didn't work for me in 9.04 either......

---

### Post by RiffRaff06078 on 2010-05-08
Same for me: Toshiba Satellite L305D 64-bit.

Worked perfectly fine for me in 9.04. Worked a little less well on 9.10, but still basically worked.  Now, I cannot resume from suspend in 10.04.  I can resume from hibernate without issue.

Any information on differences, if any, between fresh install and upgrade?

---

### Post by P4man on 2010-05-08
you could try booting a livecd and see if suspend works there. If it does, then a fresh install might cure it, but I wouldnt have too high hopes.

---

### Post by StuartN on 2010-05-08
> **P4man said:**
> you could try booting a livecd and see if suspend works there. If it does, then a fresh install might cure it, but I wouldnt have too high hopes.

I went through all the alphas, betas and release candidate with this problem, and have tried ext3 and ext4 with the same result - so no, I don't think a fresh install will work for everyone, but it might for some.

---

### Post by RiffRaff06078 on 2010-05-11
Actually, not only does suspend not work, but when I do a hard reboot after it fails to resume, my gnome panel preferences are fubar'd and I have to reset them from command line.

I'm going back to 9.4.  For an LTS release, I am highly disappointed with Lucid. :(

---

### Post by dnguyen1963 on 2010-05-11
I set the screen saver program to "Blank Screen" and quit Firefox when I need to walk away from the computer.  My Dell Inspiron 2400 can wake up from hibernation without any problem.  However, by leaving Firefox running during hibernation can leave to freezes (not all the time though!).

10.04 LTS, Dell 2400, 512 Mb, Dual-Boot with XP, Integrated Intel Graphic card 82845G/GL.

---

### Post by SyAu on 2010-05-12
I remember, initially it used to work in 9.10, i tried 10.04 beta and then i erased the ubuntu partition and installed again 9.10. This time i faced problems in suspend and hibernate options and this continues in 10.04 also (i upgraded to 10.04 from 9.10 through update manager). 

For information, i have ubuntu installed in 115G and the swap is 4.9G.

---

### Post by dnguyen1963 on 2010-05-12
> **dnguyen1963 said:**
> I set the screen saver program to "Blank Screen" and quit Firefox when I need to walk away from the computer.  My Dell Inspiron 2400 can wake up from hibernation without any problem.  However, by leaving Firefox running during hibernation can leave to freezes (not all the time though!).

10.04 LTS, Dell 2400, 512 Mb, Dual-Boot with XP, Integrated Intel Graphic card 82845G/GL.

Update - I updated my system last night and the computer locked up on me this morning...could not wake up from hibernating.  :(

---

### Post by kerrynmitch on 2010-05-12
> **Taus said:**
> i'm not completely sure about this - but i think i read somewhere on ubuntu bug list that if u perform a default install u have to make sure that the SWAP partition is AT LEAST the same size as the total ram on your machine. If the swap  is smaller than that hipernate/suspend won't work.

Cheers

This is true.  I had a problem before with the suspend and hibernate, but I had quickly installed Ubuntu allowing it to set my hard drive partitions..  It only gave about 500MB for swap and as a result I couldn't suspend/hibernate.  In fact that is the error message that came up.

I reinstalled Ubuntu after fixing my partitions, have the swap a couple GIGS, and now everyone works fine and dandy.  I have 8GB swap but that is alot, I think good rule of thumb is RAM = SWAP as mentioned by Taus.

---

### Post by monkeys on 2010-05-13
Would this SWAP size problem be relevant if you'd upgraded your system? It was working perfectly for me on Karmic, but now suspend just makes the screen freeze black and hibernate puts on the screensaver, AND THEN freezes.

---

### Post by besn0847 on 2010-05-14
Hi all,

I have the same issue regarding suspend/resume on my Thinkpad X40 with 1G RAM and 1.5G SWAP.
I was using 9.04 for a year without any issue and upgraded 3 days ago.

First my laptop screen was going blank after X started and i add to install the following kernel: 2.6.33-02063303-generic. I then managed to re-use X normally.

However suspend/resume does not work any more as after resuming the screen goes blank and no magic key comibnation works (hard reset is needed).

So there seems to be 2 issues; dunno if hey are linked. I also installed 10.04 LTS on my professional laptop (Thinkpad T60p): works perfectly.

Bye

---

### Post by exel0n on 2010-05-18
Same same, updated last night on HP Mini 2140.

Quality releases as always, **** I have to stop updating my system, every time I do it breaks... Good thing they changed some icons though, now my taskbar looks completely inconsistent. Gosh, they removed the system log shortcut *sigh*.

[This thread]("http://ubuntuforums.org/showthread.php?p=9261807") seems to handle a similar issue, getting a ```
PM: Device usb4 failed to suspend: error -16
``` myself, though I haven't tried the workaround yet.

---

### Post by dnguyen1963 on 2010-05-19
> **kerrynmitch said:**
> This is true.  I had a problem before with the suspend and hibernate, but I had quickly installed Ubuntu allowing it to set my hard drive partitions..  It only gave about 500MB for swap and as a result I couldn't suspend/hibernate.  In fact that is the error message that came up.

I reinstalled Ubuntu after fixing my partitions, have the swap a couple GIGS, and now everyone works fine and dandy.  I have 8GB swap but that is alot, I think good rule of thumb is RAM = SWAP as mentioned by Taus.

Not quite that simple...many of us have swap size much larger than the amount of RAM and still experienced freezes.  See other threads in this forum regarding this issue.

---

### Post by SyAu on 2010-05-21
:)     Good news !!!  Now both Suspend and Hibernate are working in my laptop. I installed drivers for the 'Extra' option under 'Change Desktop background' - 'Visual Effects', this is the change i made in Ubuntu apart from regular updates through 'Update Manager'. I usually test suspend and hibernate options atleast once in 2 days and after the above changes it started working. Still not 100% sure if the driver installation fixed the problem, but it's worth trying this.

Please note: After enabling 'Extra' option, I switched back to 'None' option due to occasional screen flickering issue with 'Extra' option.

---

### Post by ak123 on 2010-05-22
I dont know if this is the same issue which everyone else seems to have, but whenever i tell ubuntu to suspend or hibernate, it locks the screen instead. 
the same thing happens when i shut the laptop lid...
However mine isnt freezing up..
I really would like a fix to this because it means i have to shut down every time i wwant to save my battery charge...

Im using a Samsung NC10 by the way..

---

### Post by xinix on 2010-05-25
> **SyAu said:**
> :)     Good news !!!  Now both Suspend and Hibernate are working in my laptop. I installed drivers for the 'Extra' option under 'Change Desktop background' - 'Visual Effects', this is the change i made in Ubuntu apart from regular updates through 'Update Manager'. I usually test suspend and hibernate options atleast once in 2 days and after the above changes it started working. Still not 100% sure if the driver installation fixed the problem, but it's worth trying this.

Please note: After enabling 'Extra' option, I switched back to 'None' option due to occasional screen flickering issue with 'Extra' option.

I had been having trouble with suspend and was getting quite frustrated.  I gave the "Extra" option a shot; it worked!  Suspend failed since my last update but worked after setting this option.  Thanks for the workaround.

---

### Post by zcacogp on 2010-05-26
I have two laptop machines, both running 10.04. One's an IBM x31s, the other a Lenovo X61s2. Neither of them will suspend or hibernate; they both produce a black (but illuminated) screen which can't be then recovered to a usable state. 

Both machines have swap files of 1.7gb. This is more than the 750mb memory on the x31, but less than the 4gb memory on the x61s2. 

I'll watch this thread with interest, as suspend and hibernate are useful functions (and work fine on XP on both machines). 

BUT, in the meantime, can someone give me some more information on the "Extra" upgrade, as mentioned by xinix and SyAu? I can go to System > Preferences > Appearance > Visual Effects and choose "Extra", but this doesn't make any difference (neither does it attempt to install more drivers, which SyAu suggested it would.) Isn't this related to CompizConfig as well? (Which I have installed on both machines.) 


Oli.

---

### Post by dino99 on 2010-05-26
> **zcacogp said:**
> I have two laptop machines, both running 10.04. One's an IBM x31s, the other a Lenovo X61s2. Neither of them will suspend or hibernate; they both produce a black (but illuminated) screen which can't be then recovered to a usable state. 

Both machines have swap files of 1.7gb. This is more than the 750mb memory on the x31, but less than the 4gb memory on the x61s2. 

I'll watch this thread with interest, as suspend and hibernate are useful functions (and work fine on XP on both machines). 

BUT, in the meantime, can someone give me some more information on the "Extra" upgrade, as mentioned by xinix and SyAu? I can go to System > Preferences > Appearance > Visual Effects and choose "Extra", but this doesn't make any difference (neither does it attempt to install more drivers, which SyAu suggested it would.) Isn't this related to CompizConfig as well? (Which I have installed on both machines.) 


Oli.

[COLOR="Blue"]Please note: After enabling 'Extra' option, [COLOR="Red"]I switched back to 'None'[/COLOR] option due to occasional screen flickering issue with 'Extra' option.[/COLOR]

---

### Post by obscurant1st on 2010-05-26
> **SyAu said:**
> :)     Good news !!!  Now both Suspend and Hibernate are working in my laptop. I installed drivers for the 'Extra' option under 'Change Desktop background' - 'Visual Effects', this is the change i made in Ubuntu apart from regular updates through 'Update Manager'. I usually test suspend and hibernate options atleast once in 2 days and after the above changes it started working. Still not 100% sure if the driver installation fixed the problem, but it's worth trying this.

Please note: After enabling 'Extra' option, I switched back to 'None' option due to occasional screen flickering issue with 'Extra' option.


I love you dude.
It worked. :)

---

### Post by dnguyen1963 on 2010-05-26
> **SyAu said:**
> :)     Good news !!!  Now both Suspend and Hibernate are working in my laptop. I installed drivers for the 'Extra' option under 'Change Desktop background' - 'Visual Effects', this is the change i made in Ubuntu apart from regular updates through 'Update Manager'. I usually test suspend and hibernate options atleast once in 2 days and after the above changes it started working. Still not 100% sure if the driver installation fixed the problem, but it's worth trying this.

Please note: After enabling 'Extra' option, I switched back to 'None' option due to occasional screen flickering issue with 'Extra' option.

Well, you lost me there..."switched back to none" basically disables the "Extra" option.  I'm not sure why it worked for you, but I'll give it a try.

---

### Post by obscurant1st on 2010-05-26
after enabling extra options, i try to update using update-manager, then it showed me some packges to be downloaded n installed. Its updated, and then i tried this resume thing, n it worked with out any problm, then i switchedback that visual thing to normal mode, which i was using before. And still its working!!! :)

---

### Post by Rackstar on 2010-05-26
Very strange! This workaround also worked for me!

Dell Studio 15 ( 1558 )
ATI Radeon HD5470

---

### Post by SyAu on 2010-05-26
> **dnguyen1963 said:**
> Well, you lost me there..."switched back to none" basically disables the "Extra" option.  I'm not sure why it worked for you, but I'll give it a try.

When you install necessary drivers for 'Extra' option, i believe it stays in the system even though you select a different option 'None'.

---

### Post by minibeardeath on 2010-05-26
Is there a list of the drivers installed by enabling the extras option, so that we might be able to identify the "magic" driver?

---

### Post by zcacogp on 2010-05-27
Ditto - what are these drivers? 

When I selected "Extras" (as per my earlier post), I don't believe anything was installed, and it made no difference. 

(Can I confirm that we are talking about System > Preferences > Appearance > Visual Effects and choosing "Extra"?)


Oli.

---

### Post by doko1 on 2010-05-27
> **zcacogp said:**
> Ditto - what are these drivers? 

When I selected "Extras" (as per my earlier post), I don't believe anything was installed, and it made no difference. 

(Can I confirm that we are talking about System > Preferences > Appearance > Visual Effects and choosing "Extra"?)


Oli.


Same here. 

Anyway, this problem has not at all been solved... it's simply a workaround which only works out for some. :(

---

### Post by Anschuz on 2010-05-27
This work around successfully fixed hibernate and suspend on both of my laptops (Dell Inspiron 710m and Compaq/HP TC4400). 

I did have to adjust the settings slightly differently in order to get the "searching for drivers" dialogue window. 

In my case both laptops were originally set to Normal.  Switching to Extra had no effect other than enabling the extra features.  By toggling between None and Normal I was able to invoke the "Searching for drivers" dialogue.  With Normal selected I closed Appearance Preferences and rebooted.  After rebooting both suspend and hibernate are now working.

I was about to revert to 9.04 when I came across this thread.  Thank you very much for this tip!

---

### Post by doko1 on 2010-05-27
Thanks, Anschuz, for this little but important detail. This worked out for me now! :)

[B]So here is how it works (hopefully) for everybody: 
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer[/B]

---

### Post by minibeardeath on 2010-05-27
So how would I go about doing this in, say, Xubuntu where I do not have compiz, or Gnome?

---

### Post by markogts on 2010-05-28
Well I followed the procedure and there is a change. However, if before the standby would not resume, now the standby just locks the screen, but I still hear the fans on, the pc doesn't go to power saving mode.

---

### Post by hufemj on 2010-05-28
> **doko1 said:**
> Thanks, Anschuz, for this little but important detail. This worked out for me now! :)

[B]So here is how it works (hopefully) for everybody: 
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer[/B]


For whatever reason, my Dell Latitude D600 does not give me a dialog box for drivers. When I choose either Normal or Extra, it searches for drivers, seems to try to go to the new setting (normal or extra), then gives me a message that it can't do it and reverts to none all by itself. Suspend still doesn't work. Although, I did notice a brief username/pw dialog box that appeared for a second or so before it went to the backlit black screen with the blinking underline cursor in the upper left. I can ctrl-alt-f5 to a command prompt and reboot. But, that's it.

It's kind of odd that system->admininistration->hardware drivers indicates "no proprietary drivers are in use on the system". Yet, in system->preferences there's an ATI Catalyst Control Center and an ATI Catalyst Control Center (Administrative).

---

### Post by dzajic on 2010-05-28
I have a Dell Studio 1558 that wasn't resuming from suspend and the solution was this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553498/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553498/comments/5)

NOTE: Resuming from hibernation still does not work.

---

### Post by keypox on 2010-05-28
> **doko1 said:**
> Thanks, Anschuz, for this little but important detail. This worked out for me now! :)

[B]So here is how it works (hopefully) for everybody: 
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer[/B]

Since I already installed the video drivers from nvidia I am not given a dialog for drivers.

Also didnt fix suspend for me.  And I used compiz config settings manager wonder if thats causing the problem.

---

### Post by The_Bullfrog on 2010-05-28
I'm also having this problem and the work-around described above did not work for me.

When I place the system into Suspend, it goes through the suspend process and powers off the LCD display but then immediately powers up the LCD again but without any content being displayed on-screen - just a blank, but illuminated, screen.

When I attempt to Resume, the system pulls data from the hard drive but the screen stays blank and illuminated. Soft reset doesn't work and I have to hard reset to get back into the OS.

As with a previous poster I'm also running this on an IBM Thinkpad X31.

I previously abandoned Ubuntu 9.10 due to problems in running it with the X31 graphics chipset, which is a ATI Mobility RADEON M6 LY.

Given the display factors I have described I'm wondering if the 10.04 Suspend problem could be caused by a video driver issue?

Interestingly, I had no problems running CrunchBang based on Ubuntu 9.04.


Oh, a little bit of searching turned up these bug reports:
[https://bugzilla.kernel.org/show_bug.cgi?id=14640](https://bugzilla.kernel.org/show_bug.cgi?id=14640)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/485108](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/485108)

Looks like this problem has been affecting Ubuntu since November2009.

---

### Post by snesreviews on 2010-05-29
Don't know why this has been marked as solved when there are lots of people still having the same issue...

Anyway I found an old thread which had **a** solution to this [http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

So I tried s2disk from the command line and it worked great, but adding them to that script doesn't seem to work (assumingly Ubuntu decided they wanted to ditch that convention). I later discovered that hitting the hibernate button doesn't seem to touch this script - it seems to execute /sbin/pm-hibernate. So big dirty fix was simply to back up your existing script and point it to s2disk instead:

sudo mv /sbin/pm-hibernate /sbin/pm-hibernate.bak
sudo ln -s /sbin/s2disk /sbin/pm-hibernate

And to do the same for suspend (slightly different as it may require --force for some machines)

echo -e '#!/bin/bash\n/sbin/s2ram --force' > ~/s2ram.sh
chmod a+x ~/s2ram.sh
sudo mv ~/s2ram.sh /sbin/
sudo mv /sbin/pm-suspend /sbin/pm-suspend.bak
sudo ln -s /sbin/s2ram.sh /sbin/pm-suspend

And magically it works fine. Wish I just did that instead of the None / Extras fix - went and zapped a lot of my cool compiz settings :(

Anyway just putting it out there in case it's of use to anyone else

---

### Post by zcacogp on 2010-05-29
Thanks snesreviews, 

I found that set of instructions (not there, on the ubuntugeek site, but it's the same instructions.) And, while it suspends nicely (and quickly) with that, my X31s still won't come back from being suspended. 

Good spot otherwise tho', and it may well work for some people on here. 


Oli.

---

### Post by fprintf on 2010-05-30
Sorry to say but I am having identical issues to those posting previously. Mine is an old IBM T30 with an ATI Radeon video card. It took me only a few minutes to get sleep on Jaunty working on it, mostly the removal of scripts that had previously been necessary (from the Thinkpad WIKI as I recall) to be stored in /etc/pm/sleep.d

I am super bummed because this machine stays in sleep in my office except when I need to quickly check the 'Net. Powering it up/off each time is a serious drag. I am wondering if degrading back to Jaunty will be required.

---

### Post by fprintf on 2010-05-30
Ok, I am doing some digging into this and looking at my logs from prior to the install, when the suspend/resume was working and now. It appears that the video quirk handling system is not working. For example, in my old pre-Lucid Lynx pm-suspend.log there is a line:


/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-radeon-off 
success.

This line does not appear in any logs subsequent to the new 10.04 install. Now the question is, how do I fix it so that HAL sends the appropriate quirk?  Help??

---

### Post by hufemj on 2010-05-30
> **fprintf said:**
> Ok, I am doing some digging into this and looking at my logs from prior to the install, when the suspend/resume was working and now. It appears that the video quirk handling system is not working. For example, in my old pre-Lucid Lynx pm-suspend.log there is a line:


/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-radeon-off 
success.

This line does not appear in any logs subsequent to the new 10.04 install. Now the question is, how do I fix it so that HAL sends the appropriate quirk?  Help??

I think therein lies the problem. Lucid did away with HAL, if I'm not mistaken. I think, too, that it might be related to upgrading. There seems to be a major shift in handling video, in addition to HAL. For example, on my Dell D600, I can no longer use the proprietary drivers. Some post, somewhere, mentioned something about ATI focussing all of their attention on supporting the open source drivers. Upgrading from Karmic did not go well with the video drivers, though I think I was able to straighten out the mismatch of old and new such that I'm working off of the open source drivers. But suspend still doesn't work. Given that my laptop still uses the old grub, rather than grub2, I'm wondering just how much other stuff is effected by the changes.

So, sorry to say that I don't have a solution, but my next plan of attack is to back up all my stuff and go with a fresh clean install. Fewer variables to have to deal with.

---

### Post by The_Bullfrog on 2010-05-31
> **hufemj said:**
> So, sorry to say that I don't have a solution, but my next plan of attack is to back up all my stuff and go with a fresh clean install. Fewer variables to have to deal with.

A clean install of Lucid didn't work for me, unfortunately.

I also found, on my X31, that the S2Disk scripts didn't solve the problem - the machine went into suspend/hibernate nicely but on Resuming it just gave me a randomly garbled and unusable display.

The bug reports I posted seem to suggest that this may be a kernel regression :-/

---

### Post by hufemj on 2010-05-31
> **doko1 said:**
> Thanks, Anschuz, for this little but important detail. This worked out for me now! :)

[B]So here is how it works (hopefully) for everybody: 
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer[/B]

I'm glad it worked for you. But it doesn't work for me. The default upgrade on my Dell D600 would not allow selection of the "Extra" or "Normal" drivers. I finally got the ATI driver thing resolved, working with the open source drivers, and now I can select "Normal" or "Extra", and go back to "None", but suspend still doesn't work. It goes to a black back lit screen with a flashing underscore cursor with fans active and that's it.

I was able to get the system to suspend using acpitool from the command line, but then resume just brings me to a black screen.

---

### Post by fprintf on 2010-05-31
I really think this has something to do with HAL or the video quirks not being called correctly. If I copy 98video-quirk-db-handler from /usr/lib/pm-utils/sleep.d over to /etc/pm/sleep.d (the user space settings for suspend/resume I think), the suspend works perfectly. That is, my backlight goes off like it is supposed to.

However the resume does not work properly. I probably need to write a quick 21radeon script that turns the screen on properly on resume. Right now, like so many others, I get either a black screen with the backlight on, or it will come up with my background image but none of the gnome menubars. 

Thanks for any help troubleshooting this. I see lots of bugs are filed over the course of the past few years. I have not filed one yet.

---

### Post by m15hun on 2010-05-31
As someone else has noted this problem **is not solved** could a moderator please change the status of the thread in the hope that it might draw some more interest?

All the above workarounds fall flat on my HP Mini 110c - the computer starts back up (from suspend) but the display isn't backlit - if I hold the screen up to the light I can see the background/ login window (no, the display isn't burnt :) ) but nothing brings it back to life. Hibernate does the self same thing only after a few seconds of non-backlit screen it hangs and reboots.

---

### Post by fprintf on 2010-05-31
> **m15hun said:**
> As someone else has noted this problem **is not solved** could a moderator please change the status of the thread in the hope that it might draw some more interest?

All the above workarounds fall flat on my HP Mini 110c - the computer starts back up (from suspend) but the display isn't backlit - if I hold the screen up to the light I can see the background/ login window (no, the display isn't burnt :) ) but nothing brings it back to life. Hibernate does the self same thing only after a few seconds of non-backlit screen it hangs and reboots.

Maybe if we restart a new thread that would help?  [http://ubuntuforums.org/showthread.php?p=9390739#post9390739](http://ubuntuforums.org/showthread.php?p=9390739#post9390739) is my start, but if you want to pile on so we can get some attention to this issue that would be good!!!

---

### Post by SyAu on 2010-05-31
> **m15hun said:**
> As someone else has noted this problem **is not solved** could a moderator please change the status of the thread in the hope that it might draw some more interest?

All the above workarounds fall flat on my HP Mini 110c - the computer starts back up (from suspend) but the display isn't backlit - if I hold the screen up to the light I can see the background/ login window (no, the display isn't burnt :) ) but nothing brings it back to life. Hibernate does the self same thing only after a few seconds of non-backlit screen it hangs and reboots.

Since many are still facing this problem, i'm marking this as 'unsolved'

---

### Post by sourabh21 on 2010-06-01
i also have the same problem, i use dell studio 1555 and i have installed ubuntu 10.04.
when i hibernate my laptop on starting is shows black and white screen and nothing works...
plz help me out......:confused:

---

### Post by m15hun on 2010-06-01
Thanks. It seems to be quite a prevalent problem - maybe it'll be fixed with an update, who knows? All I know is that it makes my netbook a real pain in the backside to use as it shuts down whenever I close it!

---

### Post by sourabh21 on 2010-06-01
hey, i reinstalled ati hardware driver and now black and white screen problem is solved but now when i hibernate my system,it remains ON and when i turn it off by power switch and restart it, then it resumes the hibernated session.

plz suggest me if anyone knows how to make it turn off by hibernating only.:-k

---

### Post by bkann on 2010-06-01
The following is a pretty shabby work-around, but maybe it will give someone some insight into where the problem lies:

If I log out and then choose suspend from the login screen (GDM for me), the computer both goes to sleep and wakes up perfectly.  No problems at all.

I have had the same problem as many others here, and the 'visual preferences' work-around did not solve my problem.  Gateway M255-E with Ubuntu/OpenBox.

Coincidentally, it appears that this sleep problem is affecting startup networking behavior.  If the machine fails to sleep properly, it may not enable networking on boot.  That was the case for me.  When I shut the machine down gracefully, networking is enabled just fine on startup.  [See here: Launchpad: Networking is disabled on boot]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

---

### Post by matt! on 2010-06-04
I'm also suffering form this

---

### Post by StuartN on 2010-06-04
> **bkann said:**
> Coincidentally, it appears that this sleep problem is affecting startup networking behavior.  If the machine fails to sleep properly, it may not enable networking on boot.

I do not know if Bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711) and Bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981) share the same underlying cause, but following the latter thread might be useful.

(See [http://www.iol.ie/~stuartneilson/Bootup_fsck.html](http://www.iol.ie/~stuartneilson/Bootup_fsck.html) for symptoms, workarounds and bug-list)

---

### Post by fprintf on 2010-06-04
There was an update distributed yesterday (at least on my system) that included a new Kernel. Now my system is sleeping and waking just fine. I need to experiment and take the scripts I had installed into /etc/pm/sleep.d/ out, but for now I just don't want to screw around with it.

For the record I copied a script there that turned my backlight off (called 21radeon), and also 98video-quirk-db-handler.

---

### Post by pjgingras on 2010-06-04
Greetings,

I am novice with Linux.

I have Ubuntu 10.04 installed on a Toshiba Satellite A40 with the same suspend and hibernate problems. Tried the appearance preferences/visual effects workaround, but can't change the option to either Normal or Extra. When I try to do so, first the 'Searching for available drivers...' message is displayed, then the screen flashes a few times and finally, the message 'Desktop effects could not be enabled' is displayed. Any idea on how to fix this?

Is there a way to know whether a fix will come out anytime soon for the suspend/hibernate problem in Ubuntu 10.04?

Thank you,

Philippe

---

### Post by bkann on 2010-06-04
For what it's worth, I installed the new updates mentioned by fprintf above and all is right with the world again.  I had not been using any custom scripts (as fprintf seemed to indicate s/he did).

Thanks for the heads-up, fprintf!  I hope everyone else's luck is as good.

---

### Post by m15hun on 2010-06-04
Thanks for the info folks.

Even with the new updades all is still bobbins with my HP Mini though.

---

### Post by The_Bullfrog on 2010-06-04
Unfortunately the updates haven't changed anything for me. Still having this problem with the Thinkpad X31.

---

### Post by fprintf on 2010-06-05
I hate to say this, but the update that came out yesterday for me screwed my system up again. Again it was a kernel update. So I had about 24 hours of a properly working system!

---

### Post by hufemj on 2010-06-05
> **pjgingras said:**
> Greetings,

I am novice with Linux.

I have Ubuntu 10.04 installed on a Toshiba Satellite A40 with the same suspend and hibernate problems. Tried the appearance preferences/visual effects workaround, but can't change the option to either Normal or Extra. When I try to do so, first the 'Searching for available drivers...' message is displayed, then the screen flashes a few times and finally, the message 'Desktop effects could not be enabled' is displayed. Any idea on how to fix this?

Is there a way to know whether a fix will come out anytime soon for the suspend/hibernate problem in Ubuntu 10.04?

Thank you,

Philippe

Good news/bad news. I had the same problem with my Dell D600 laptop, which uses ATI graphics. With Linux, getting the video right can be tricky. There are open source video drivers for the major chip manufacturers, which in the past have been a bit limited. ATI provided proprietary drivers that could be optionally installed via System->Admin->Hardware. That's what I used with the previous release of Ubuntu and everything worked fine. I read somewhere that ATI has shifted focus to support of the open source drivers. When I upgraded to Lucid, the proprietary drivers were still in place, but apparently broken. Nothing showed up in System->Admin->Hardware and the ATI Control Center and ATI Control Center Admin both showed up in System->Preferences. I had the same problems as you when trying to switch to "Extra" or even "Normal" in for screen appearance. When I tried ATI Control Center a message popped up that either there was no video adapter found or the driver was faulty.

I found an Ubuntu help page that provided directions for installing the open source drivers and removing the proprietary drivers. That sort of worked. ATI Control Center and ATI Control Center Admin no longer showed up in System->preferences. I was able to switch appearance to either Normal or Extra. However, the video became garbled in parts of the screen. I ran the update, but still experienced suspend problems. But then again, my suspend problems start with suspend. That is, the system doesn't fully suspend in the first place. I get a black back lit screen with a flashing underline cursor in the upper left.

Check to see if ATI Control Center and ATI Control Center Admin show up in System->Preferences. If so, you have proprietary drivers in place and you probably want to switch to the open source drivers. I forget where it is, but there's an Ubuntu help page with good directions.

So, the good news is there's a solution to not being able to switch to Normal or Extra. The bad news is that it may not fix the suspend problem, anyway.

I'm waiting for the resume-from-suspend to be fixed and then I'll try a fresh install to see if it solves the suspend problem.

---

### Post by Eyeless Blond on 2010-06-05
> **hufemj said:**
> I'm waiting for the resume-from-suspend to be fixed and then I'll try a fresh install to see if it solves the suspend problem.
Well I'm having the same problem as you: I can't get my system to suspend properly, even after a fresh install, and no matter if I use the open radeon drivers or the closed fglrx drivers. I'm getting roughly the same problem as you: the system doesn't even suspend; it just goes to a blank screen and then hangs. I can't even use the Alt-SysRq trick to reboot from there; I have to hit the reboot button. Afterwards, I have to re-enable networking manually (I'm pretty sure this is because suspend disables networking before suspending, and since it never resumes it never comes back).

Even worse, I can't even get the system to shut down/reboot correctly with the closed drivers. There it hangs during the splash screen. Even so I'm still tempted to keep the closed drivers, as compiz performance really bites using the open drivers (though I guess I should be glad it works at all; it didn't used to).

Oh, and note: I'm **not** on a laptop, unlike seemingly everyone else on this list. I'm on a desktop:

Processor: Athlon x4 620
MB: MSI DKA790GX
Video Card: Radeon 4670

---

### Post by hashky on 2010-06-05
I tried everything on the last 8 pages.  I can now Suspend and Hibernate.  BUT when I resume,

1.  There is no mouse cursor.
2.  The screen is very dim.
3.  The network does not reconnect.

The only thing I know to do is reboot, which defeats the purpose of Suspend and Hibernate.

Both Suspend and Hibernate worked much better under 9.10.  

Ron Spruell

---

### Post by Scarfy on 2010-06-06
Suspending my Dell XPS 1530 used to work perfectly in 9.10 (okay, there would be a 1% chance something might go wrong, but otherwise...)

Now, I can only suspend once. The second time around, it appears that something crashes, as the screen doesn't switch off and I can't wake it up any more.

Someone mentioned that they think it might be the kernel doing it, but I have no idea.

I hope they fix it soon, since I much prefer suspend / resume, to shutting down.

---

### Post by The_Bullfrog on 2010-06-06
> **fprintf said:**
> I hate to say this, but the update that came out yesterday for me screwed my system up again. Again it was a kernel update. So I had about 24 hours of a properly working system!

Did you happen to notice which kernel you had when it was working for you?

It didn't work for me on kernel 2.6.32-21 nor on update 2.6.32-22.

---

### Post by efflandt on 2010-06-06
Apparently so many different systems have many different issues.

Suspend/hibernate worked fine on my old Athlon64 (2004) desktop with default modules for X1300 video in 64-bit 9.10, but failed in 10.04.  Fixed with **nomodeset** kernel option (apparently does not like the new kernel mode setting driver).

Compaq Presario V2000 with ATI 200M video would not resume from suspend/hibernate at all in 9.10 (dark screen with no backlight), but suspend works perfectly in 10.04.  I use **nomodeset** for it, but not sure if that is essential.  Have not tried hibernate because it has other issues attempting to power up.  If off for awhile, I have to remove all power (remove battery, disconnect AC) before it can be powered up.

Old Dell Inspiron 8200 w/nVidia NV17 [GeForce4 440 Go] (rev a3) I only had occasionally to fix failed and corrupted Windows hard drive.  So I do not recall if suspend/hibernate worked before.  But in 10.04 whether using standard drivers or nvidia (96) with or without nomodeset, it starts to go through the motions, backlight goes off for an instant then comes back on with blank screen, and it wakes up in 20 seconds (according to pm-suspend.log) to gui login.  Switching to Extra effects and/or then back to None had no effect.  At least it does not lock up or crash.

After installing uswsusp and setting things up for nVidia (adding **Option "NvAGP" "1"** to Device section of xorg.conf and blacklisting intel_agp module), that did not work either, but was enlightening about the 20 second pause before waking.  It brought up messages on the 1st console:

end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
Freezing of tasks failed after 20.00 seconds (1 tasks refusing to freeze):
udisks-daemon

Then kept occasionally spitting out the I/O errors about the non-existing floppy drive.  So maybe I just need to figure out how to have the kernel ignore fd0 which does not exist (unless inserted in a modular bay which is currently DVD).

Update:
- Commented out fd0 mount in /etc/fstab
- Added to /etc/modprobe.d/blacklist.conf: **blacklist floppy**
- Did: **sudo update-initramfs -u**
- After reboot, can now successfully suspend/resume from standard Gnome menu

---

### Post by fprintf on 2010-06-06
> **The_Bullfrog said:**
> Did you happen to notice which kernel you had when it was working for you?

It didn't work for me on kernel 2.6.32-21 nor on update 2.6.32-22.

Since my system is current 2.6.32-22-generic, I would assume it was -21-generic that worked. However I think it may have been a fluke. Now my system will occasionally fail, perhaps 1 of every 4 suspend/resume attempts will end in a blank screen, backlight on, if I bring my mouse over where the login dialog is, the pointer will turn to a "text entry" pointer where I can log-in... sometimes with the result being I will get my background image but no other Gnome features. 

So apparently, on a 25% chance I get the blank screen, the system is up, not hanging, just something about X or Gnome isn't kicking in correctly. I wish I knew how to restart X from a terminal by going to Ctrl-Alt-F2, logging in as a new user - (proving that my system is not "hung") and then gracefully restarting my X session.

---

### Post by nnahler on 2010-06-06
I have three systems all running 10.04 and NONE of them work with Suspend and Resume:

Dell Studio 1557 (Ubuntu 64bit, network comes on after restart)
Thinkpad X61S (Kubuntu 32bit, network comes on after restart)
Dell Mini 9 (Ubuntu 32bit, network does not come on after restart)

All three suspend but do not resume (black screen, no mouse). Only a forced restart gets them back to live. The last kernel update 21 to 22 did not change this either. - I never used hibernate.

Oh, all three systems worked fine with 9.10. As somebody else previously said: 1% fail on resume.

This is really a major inconvenience for any laptop user and I look forward to a fix to this problem.

---

### Post by Eyeless Blond on 2010-06-06
How does this "nomodeset" thing work? I've heard elsewhere about people having success with it. I've tried looking it up, but the results confuse the heck out of me; is there a good step-by-step guide for disabling it?

---

### Post by utnubuuser on 2010-06-06
I haven't read the entire thread so if someone has mentioned this already... a thousand pardons....

there is a suspend/hibernate thread that suggests using bind...> [http://ubuntuforums.org/showthread.php?t=1498523&highlight=suspend%2Fhibernate+bind]("http://ubuntuforums.org/showthread.php?t=1498523&highlight=suspend%2Fhibernate+bind")

---

### Post by efflandt on 2010-06-08
> **Eyeless Blond said:**
> How does this "nomodeset" thing work? I've heard elsewhere about people having success with it. I've tried looking it up, but the results confuse the heck out of me; is there a good step-by-step guide for disabling it?

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by Bogle on 2010-06-08
On a Sony Vaio VGN-TX3XP the Suspend is working now I've unmounted the 2GB SD card. HTH.

---

### Post by Scarfy on 2010-06-08
Doesn't work for me, sadly.

Following the instructions, I updated my /boot/grub/menu.lst to the following:

# kopt=root=UUID=fd2daad1-a3f9-4bc6-8113-fecf26a34475 ro nomodeset

as then run

sudo update-grub

not sure if I've actually do that right (should the # still remain there?). Anyone else tried and failed or passed?

---

### Post by janie70 on 2010-06-08
ugh, mine too...

---

### Post by jeffrey2009 on 2010-06-08
I also have this problem. It has been plaguing me since Karmic.  I hope they fix the bug soon.  Does anyone know if there is any work around for the disable networking issue that is mentioned in this thread?

---

### Post by Manuwash on 2010-06-08
I have 9.10 and still suspend wont come back when I press a key, I have to do a hard reboot. kinda sucks, i havent found any solutions anywhere, my swap file is 2gb.

---

### Post by jrdm on 2010-06-11
Hello everyone!
well, my suspend works with some problems:
It Suspends and resumes fine at the first time, but at the second time i suspend, it will not resume! The screen remains totally black (it seems like the screen isnt turn on!).. So i have to force shutdown and when reboot the network is disabled!

Does anyone know how to fix this? i've searched a lot but find no answers.
Thanks

---

### Post by martintremblay on 2010-06-11
I have the same issue - HP Laptop. 

It was caused by changes made in Kernel 2.6.32-22-generic
this load has completely screwed up my Suspend and Hybernate funtions

If I select an earlier Kernel/Image from GRUB when booting I have no problems, all suspend and hibernate functions work perfectly.

I have tried hours of troubleshooting... the Nomode change does not help  and updating system files in 2.6.32-22-generic to align with older Kernels/images does not help

To date I have had zero success

Why has this worked perfectly until now? and what in 2.6.32-22-generic has caused this problem!!! For now I guess I boot into older Kernels until an appropriately updated and tested Kernel is available!

---

### Post by martintremblay on 2010-06-11
The most difficult issue with this problem is SOOOOOO many of us have similar issues that thousands of posts can be found in hundreds of forums, unfortunately none with any feasible solutions. 

My biggest concern is many people possibly don't even know they have this problem. My system previously suspended with no issues at all. I just realized recently that it was burning hot in the AM. 

This means many people out there running Ubuntu could be unknowingly damaging fans, hard drives, processors and other heat sensitive components!

How did this work fine in earlier Ubuntu versions yet become such a huge bug in an LTS release!

---

### Post by makash on 2010-06-12
I got hibernate working on my Thinkpad T410i by making the following changes

[LIST=1]
[*]/etc/default/grub
[*]Added resume=/dev/sd8 [ My swap partition ]
[*]Then I did update-grub
[/LIST]

---

### Post by zcacogp on 2010-06-13
> **makash said:**
> I got hibernate working on my Thinkpad T410i by making the following changes

[LIST=1]
[*]/etc/default/grub
[*]Added resume=/dev/sd8 [ My swap partition ]
[*]Then I did update-grub
[/LIST]

Sounds promising ... can you explain those steps in a little more detail please Makash? Thanks. 


Oli.

---

### Post by The_Bullfrog on 2010-06-13
> **zcacogp said:**
> Originally Posted by makash  
I got hibernate working on my Thinkpad T410i by making the following changes
/etc/default/grub
Added resume=/dev/sd8 [ My swap partition ]
Then I did update-grub

Sounds promising ... can you explain those steps in a little more detail please Makash? Thanks. 
Oli.


This didn't work on my Thinkpad X31 but if you want to give it a try these are the steps to follow:

1. Go to the System Menu, then Administration and click on the Disk Utility application.

2. Identify the Volume which holds your Swap volume. If you did a clean install of Ubuntu 10.04 then your Swap space is likely to be on Logical Partition sda5. Make a note of this partition number.

3. Open a Terminal by going to the Applications menu, then Accessories and click on Terminal.

4. In the Terminal window type sudo nautilus and enter your password when prompted, this will open the file browser with Super User privileges.

5. Browse to the folder /etc/default and open the file named grub.

6. The first 2 lines are comments which start with a hash character (#). After these 2 lines enter the following:
resume=/dev/sda5. Then save the file and close the Nautilus file browser.

7. Go back to the Terminal and press CTRL-C to terminate the call to Nautilus. You then need to update the Grub settings by typing sudo update-grub and then entering your password. This will regenerate Grub.

8. Reboot and try the suspend/hibernate features.

9. Come back here and tell us whether or not this worked for you and what hardware you are using.

As I say, this solution did not work for me on a Thinkpad X31 and I'm not really sure why it worked for Makash as the RESUME line is already included in /etc/intramfs-tools/conf.d but you may as well give it a shot - at this stage I'd be happy to try anything.

The Bullfrog.

---

### Post by silverbirch on 2010-06-14
thanks Bullfrog

didnt work for my PC ( athlonXP2600,) :D:(

but i appreciated the lesson on editing etc. thank you :-)

---

### Post by leonardo_neo on 2010-06-15
Thanks Bullfrog,

But this tutorial didn't work on my ACER ASPIRE laptop either.

Before it was working properly until I updated to the latest kernel (2.6.32-22) around 10 days ago.

I wish if the fix is updated soon.

---

### Post by martintremblay on 2010-06-15
I highly suggest trying out earlier linu/kernel versions to see if it helps your system

Everything worked on my hp nc6400 in 10.04 Lucid kernel 2.6.31.20 or earlier. (I also went back to Karmic 9.10 and 9.04 and found zero issues-EVERYTHING WORKS!)

2.6.32-22 has caused the suspend and hibernate to "break" for me
2.6.32-23 did not make any difference, still broken

Is there a location where we can find the list of changes made to 2.6.32-22 or if we can contact the developers directly and determine what changes they made caused this?

---

### Post by StuartN on 2010-06-15
> **martintremblay said:**
> Is there a location where we can find the list of changes made to 2.6.32-22 or if we can contact the developers directly and determine what changes they made caused this?

Yes, locate the package, e.g. [http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic](http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic) and look for link to the changelog [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.32-22.36/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.32-22.36/changelog)

---

### Post by martintremblay on 2010-06-15
> **leonardo_neo said:**
> Thanks Bullfrog,

But this tutorial didn't work on my ACER ASPIRE laptop either.

Before it was working properly until I updated to the latest kernel (2.6.32-22) around 10 days ago.

I wish if the fix is updated soon.

you can try 2.6.32-23 and see if it makes any difference (it's available.. but didn't help me) 
I think we need to dig into changes made into 2.6.32-22 to determine what the developer(s) did to cause this issue. for now I'll report as specific bug

---

### Post by martintremblay on 2010-06-15
> **StuartN said:**
> Yes, locate the package, e.g. [http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic](http://packages.ubuntu.com/lucid/linux-image-2.6.32-22-generic) and look for link to the changelog [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.32-22.36/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.32-22.36/changelog)

Thanks! - looks like many changes in 2.6.32-22 could have caused this. 

I have submitted a bug report for now against kernel 2.6.32-22

---

### Post by spotted zebra on 2010-06-16
> **martintremblay said:**
> you can try 2.6.32-23 and see if it makes any difference (it's available.. but didn't help me) 
I think we need to dig into changes made into 2.6.32-22 to determine what the developer(s) did to cause this issue. for now I'll report as specific bug

where is 2.6.32-23? i looked for it via terminal and didn't find anything.

also are we trying to figure out the changes between 2.6.32-20 or is it another kernel? i would love to get this to work it is d*mn annoying to have to shut down every time.

for reference:
i am running an acer aspire one D250

my hibernate function works perfectly. it will correctly hibernate and resume.

the suspend function on the other hand will suspend the netbook correctly but when i try to resume the hard drive loads, i assume the hdd light comes on for a second, then i get the backlite black screen. i have to hard restart the computer and re-enable the networking when it comes back up.

i would much rather edit the grub/kernel that have some shotty work around.

i will be keeping an eye on this thread and maybe trying a few things when i have time. i will be sure to report my findings. i personally think it is something to do with the driver support of the graphics cards.

i also tried a couple of fixes list here. the drivers from the change to 'extra' and back didn't work. i also tried adding the resume=/dev/etc/sda5 also didn't work. last i tried

---

### Post by martintremblay on 2010-06-17
[I]    "where is 2.6.32-23? i looked for it via terminal and didn't find   anything."
[/I]Currently 2.6.32-23 is a pre-release, and you can only get by adding  "Pre-release updates (Lucid Proposed)"  in Synaptic Package Manager

I am in agreement with you Spotted... workarounds should not be the solution to this problem. Preferably whatever was broken in kernel 2.6.32-22 should be fixed. Any workaround could simply be defeated by proper updates in a future release.

---

### Post by martintremblay on 2010-06-17
If you have this same problem, I suggest going into launchpad and  indicating this bug 594787 also affects you.  

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/594787](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/594787)

---

### Post by mahboop on 2010-06-17
> **makash said:**
> I got hibernate working on my Thinkpad T410i by making the following changes

[LIST=1]
[*]/etc/default/grub
[*]Added resume=/dev/sd8 [ My swap partition ]
[*]Then I did update-grub
[/LIST]

[SIZE="3"][COLOR="Blue"]This works for me perfectly[/COLOR][/SIZE]
suspend/hibernate and resuming from them is OK now

My laptop is [COLOR="Green"]HP Pavilion dv6[/COLOR]

Thanks makash for the idea
Thanks The_Bullfrog for the explanation 

Regards,
Saudi Arabia

---

### Post by spotted zebra on 2010-06-18
> **martintremblay said:**
> If you have this same problem, I suggest going into launchpad and  indicating this bug 594787 also affects you.  

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/594787](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/594787)


i think the title of the bug should be more descriptive because you can change what your laptop does when you close it. 

i think by default it is suspend but to make it easier for the developers to pin point the problem i would consider changing it to only "[SIZE=2]**2.6.32-22 causes  suspend hibernate to not work**[SIZE=1]" and leave out the lid closing.

i will say i am having this problem too.
[/SIZE]

[/SIZE]

---

### Post by spotted zebra on 2010-06-18
> **martintremblay said:**
> [I]    "where is 2.6.32-23? i looked for it via terminal and didn't find   anything."
[/I]Currently 2.6.32-23 is a pre-release, and you can only get by adding  "Pre-release updates (Lucid Proposed)"  in Synaptic Package Manager

I am in agreement with you Spotted... workarounds should not be the solution to this problem. Preferably whatever was broken in kernel 2.6.32-22 should be fixed. Any workaround could simply be defeated by proper updates in a future release.

sorry for the double post.

where can one find the source code for say 2.6.32-20 and 22 so one could compare them? i think we could go through them and test some things out; maybe figure out what is going on and how to fix it. 

i think i am just going to stay at the 22 build if the 23 build doesn't fix it anyway.

---

### Post by martintremblay on 2010-06-18
Title changed!

> **spotted zebra said:**
> i think the title of the bug should be more descriptive because you can change what your laptop does when you close it. 

i think by default it is suspend but to make it easier for the developers to pin point the problem i would consider changing it to only "[SIZE=2]**2.6.32-22 causes  suspend hibernate to not work**[SIZE=1]" and leave out the lid closing.

i will say i am having this problem too.
[/SIZE][/SIZE]

---

### Post by zcacogp on 2010-06-18
> **The_Bullfrog said:**
> This didn't work on my Thinkpad X31 but if you want to give it a try these are the steps to follow:

1. Go to the System Menu, then Administration and click on the Disk Utility application.

2. Identify the Volume which holds your Swap volume. If you did a clean install of Ubuntu 10.04 then your Swap space is likely to be on Logical Partition sda5. Make a note of this partition number.

3. Open a Terminal by going to the Applications menu, then Accessories and click on Terminal.

4. In the Terminal window type sudo nautilus and enter your password when prompted, this will open the file browser with Super User privileges.

5. Browse to the folder /etc/default and open the file named grub.

6. The first 2 lines are comments which start with a hash character (#). After these 2 lines enter the following:
resume=/dev/sda5. Then save the file and close the Nautilus file browser.

7. Go back to the Terminal and press CTRL-C to terminate the call to Nautilus. You then need to update the Grub settings by typing sudo update-grub and then entering your password. This will regenerate Grub.

8. Reboot and try the suspend/hibernate features.

9. Come back here and tell us whether or not this worked for you and what hardware you are using.

As I say, this solution did not work for me on a Thinkpad X31 and I'm not really sure why it worked for Makash as the RESUME line is already included in /etc/intramfs-tools/conf.d but you may as well give it a shot - at this stage I'd be happy to try anything.

The Bullfrog.
Thanks Bullfrog. I tried it on my X31 and X61s and it didn't work on either of them ... thanks for the instructions all the same. 


Oli.

---

### Post by spotted zebra on 2010-06-18
i am really hoping some other people are actively working to solve this besides the devs.

i have found [this]("https://wiki.ubuntu.com/KernelTeam/SuspendResume") after some googling. i am in the process of deciphering everything that is here but two heads are better than so jump in.

i am not some amazing ubuntu freak i just want this problem solved and willing to try some stuff to get it fixed.

---

### Post by Fathead_on_linux on 2010-06-19
My hibernate works fine......but the backlight on my laptop doesn't completely come back when it comes out of hibernate! I'm on a HP pavilion dv9000 with ubuntu 10.04

---

### Post by DarkArmada on 2010-06-20
Suffering the same issues, Toshi A100, NVIDIA prop graphics drivers, suspend or hibernate goes to illuminated black screen with no way of resuming without hard reset. Also of note, when I reboot, Networking is disabled. Made sure SWAP > RAM, have tried the None/Std/Extra fix with no joy.

Am willing to try anything at this point, I use sleep / suspend all the time in Windows. I'm an Ubuntu noob and absolutely loving it, but this is a thorn in my side I'd love to rip out. :D

Thx in advance to the tireless millions working on my issue lol

~DA

---

### Post by keithmcc on 2010-06-20
> **hashky said:**
> BUT when I resume,

1.  There is no mouse cursor.

Workaround: try <CTRL><ALT><LEFT ARROW> or <CTRL><ALT><RIGHT ARROW> (changes workspace).

---

### Post by fprintf on 2010-06-21
Interesting to see all the developments. I added the 'nomodeset' to my grub a few weeks ago and it worked perfectly. My IBM T30 is sleeping and resuming just fine as far as the backlight goes.

Now I am hoping a kernel update doesn't wipe out this good thing!

---

### Post by Scarfy on 2010-06-21
> **fprintf said:**
> Interesting to see all the developments. I added the 'nomodeset' to my grub a few weeks ago and it worked perfectly. My IBM T30 is sleeping and resuming just fine as far as the backlight goes.

Now I am hoping a kernel update doesn't wipe out this good thing!

Where did you add the nomodeset? Could you past the lines from your GRUB? I tried this and it didn't work for me.

Steve

---

### Post by dnguyen1963 on 2010-06-21
> **DarkArmada said:**
> Suffering the same issues, Toshi A100, NVIDIA prop graphics drivers, suspend or hibernate goes to illuminated black screen with no way of resuming without hard reset. Also of note, when I reboot, Networking is disabled. Made sure SWAP > RAM, have tried the None/Std/Extra fix with no joy.

Am willing to try anything at this point, I use sleep / suspend all the time in Windows. I'm an Ubuntu noob and absolutely loving it, but this is a thorn in my side I'd love to rip out. :D

Thx in advance to the tireless millions working on my issue lol

~DA

Try rolling back to kernel 2.6.32.21-generic.  It has been working well for me.

---

### Post by martintremblay on 2010-06-21
Some good news and some bad news...

First the Good News:
I have isolated the causes of my suspend hibernate issues, and by reverting to an earlier kernel eliminated the problem.

I removed all kernels released after 2.6.31-20, and have now reverted back to using ONLY Linux Ubuntu Lucid 10.04 kernel 2.6.31-20-generic.  I did this by:

A-First I determined which kernels were broken by selecting them from my GRUB menu at boot up and testing out suspend and hibernate.  (2.6.32 and all later kernel variants did not work for me) the latest kernel I could find that still worked is 2.6.31.20

B - Perform a search in System-Admin-Synaptic for 2.6.32 and select to _completely remove_ any related installs (right click and select completely remove all, this will even remove it from your GRUB menu) 

Now I boot only into 2.6.31.20 and have zero issues 


Now the Bad News:

I cannot determine what is causing the issue in the newer kernels and...
I was asked by the developers to move my bug report
(2.6.32-22 causes suspend hibernate to not work [https://bugs.launchpad.net/bugs/594787](https://bugs.launchpad.net/bugs/594787)) into  ubuntu-bug linux . suspend resume . issues are caused by the kernel

Unfortunately, another bug prevents me from doing this!!! (when I attempt to register the bug the bug collection reporting system incorrectly indicates I am not using an official Ubuntu installation. (even though I have only installed and upgraded from the official Ubuntu site... sigh) 

I will continue to attempt to log this bug until successful, to ensure this gets corrected in future kernels for anyone else who is suffering!

---

### Post by fprintf on 2010-06-22
> **Scarfy said:**
> Where did you add the nomodeset? Could you past the lines from your GRUB? I tried this and it didn't work for me.

Steve

Hey Steve, I added my nomodeset according to the brief instructions at [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

For the record I have Grub 1, so had to follow the instructions for that option. I saw your earlier response that it didn't work for you, which is actually why I never tried it before for myself.

My grub line is:

# kopt=root=UUID=854aa3fb-079f-4868-a548-43bc783f4b1d ro nomodeset

---

### Post by DarkArmada on 2010-06-22
> **dnguyen1963 said:**
> Try rolling back to kernel 2.6.32.21-generic.  It has been working well for me.
Damn, I would but the latest Kernel I am running is allowing my Belkin N1 Express Card to work natively (which wouldn't work at all in the previous kernels I've run and seems to be a pain point only just recitifed)

If it's not one thing it's another lol

---

### Post by arseny1991 on 2010-06-22
Good news !

Just freshly reinstalled 10.04 (64-bit). In software sources chose Pre-released updates and installed all the updates. New kernel 2.6.32-23-generic also present. 
Tried to hibernate, took a bit of time, like 20 seconds but it worked great. Also woke up from hibernation too ! No problem here, only the backlight was at the dimmest setting, Network was working.

Suspend, FINALLY suspended fully ! In about 7 seconds and woke up with no blank screens and freezes ! BUT ! i have a flickering image problem, how can i fix that ?
From what i saw through flickering, my WiFi was connected and the brightness was as i left it before the suspend.

I use an Acer Aspire 5100

Turion x2 64
2.5 GB ram, swap set to 2.8 GB
ATI Radeon Xpress 1100 ( also known as 200M) - all the desktop effects work great right out of the box.

Everything else works great too, except Microphone, it has some noise and TOOOO quiet, impossible to use. (tried playing around with alsamixer, no help)

Please help get rid of the flickering image ! I want to change over from Win to Ubuntu and in every single version there is something that always keeps me from doing so :(

---

### Post by martintremblay on 2010-06-22
Another link to assist in debugging hibernate suspend issues.
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)
(did not help me, but maybe someone else out there can benefit!)

For my specific issue I have transfered my bug report from to here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597347](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597347) 
as requested by developers. If your issue is caused by changes made in kernel 2.6.32 please go to the above link and select "this bug affects me"

---

### Post by hufemj on 2010-06-24
Somebody somewhere in this thread suggested changing the settings in the update manager to include pre-releases. I tried this on my Dell laptop D600, but it did not fix the suspend problem. However, I tried hibernate and it seems to work. "Seems to" in that a "failed to thaw" message appears a few seconds before the system goes into hibernation. But the system does hibernate and appears to properly resume as well. 

Not sure if the pre-releases solved the hibernate problem because I had not been testing hibernate with the other fixes - only suspend.

When suspend fails, I get a black back lit display with a flashing cursor in the upper left. Also, an authentication dialog box appears for a few seconds, but not long enough for me to enter a password.

Thanks to whoever it was that suggested updating with pre-releases. At least now when my wife closes the cover on my laptop it will actually turn off.

---

### Post by Scarfy on 2010-06-24
I think I've found a cause of the suspend issue on my laptop.

After reading another thread, one user recommended removing their SD cards which they always had plugged in. I did the same and now I am suddenly able to suspend again.

Apparently, it has something to do with the kernel attempting to mount or unmount the card during the hibernate process.

Anyway, I have taken out my card and now my laptop is happily hibernating and resuming. Well, it has done so far - hopefully it'll continue. The screen still takes a little longer to turn off that it probably should, but it's okay.

So, in short - Try removing your external drives or SD cards! If it has something to do with attempting to mount drives, then I have no idea if this will work with dual-boot systems.

I'll update with... er... updates on my progress.

---

### Post by DarkArmada on 2010-06-24
> **Scarfy said:**
> I think I've found a cause of the suspend issue on my laptop.

After reading another thread, one user recommended removing their SD cards which they always had plugged in. I did the same and now I am suddenly able to suspend again.

Apparently, it has something to do with the kernel attempting to mount or unmount the card during the hibernate process.

Anyway, I have taken out my card and now my laptop is happily hibernating and resuming. Well, it has done so far - hopefully it'll continue. The screen still takes a little longer to turn off that it probably should, but it's okay.

So, in short - Try removing your external drives or SD cards! If it has something to do with attempting to mount drives, then I have no idea if this will work with dual-boot systems.

I'll update with... er... updates on my progress.
Wowow - ok so removing the SD card I had in my lappy allows me to suspend and wake! My only problem is once I've come back from suspend, my Bluetooth Mouse is no longer working. Most likely a completely seperate issue.

Thanks again to all that helped and to Scarfy with the above solution!

---

### Post by fligen on 2010-06-24
On my Nokia booklet 3g I have found if closing the lid and opening will result in a black screen, however if press the power button 1 time this will bring the laptop out of suspend.

It is annoying for this not to work automatically but having to press the power button 1 time to have a working suspend is worth the annoyance for now.

(I have not tried any other fix in this forum and have a clean install of 10.04)

hope this helps someone

---

### Post by fedoraboy on 2010-06-25
I believe there are multiple causes and multiple solutions here... but, for those of you running ATI, maybe this will help.

I went through every possible solution in this thread.  Then, like an idiot, I finally actually looked at the wiki for the folks that make the fglrx driver... and there it was:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Suspend.2FHibernation](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Suspend.2FHibernation)

It works for me...  Your mileage may vary.

---

### Post by tonywhipps on 2010-06-27
> **DarkArmada said:**
> Wowow - ok so removing the SD card I had in my lappy allows me to suspend and wake! My only problem is once I've come back from suspend, my Bluetooth Mouse is no longer working. Most likely a completely seperate issue.

Thanks again to all that helped and to Scarfy with the above solution!

This worked for me too!  I searched all over and it was only the SD card.  The hibernate did take a while both ways though.

---

### Post by filip007 on 2010-06-27
13 pages of that problem sounds serious...

My best guess is:
Use only default partitioning
Check BIOS for S3 Power Management option working

Remember that Swap partition is needed for suspend/hibernation and any changes to that will probably brake S3 to working properly.

If still not working then hardware is not supported.

---

### Post by arseny1991 on 2010-06-27
anyone knows how i can get rid of the flickering problem which only comes up after suspend ? Im on Ati Radeon x1100 (aka 200M).

Hibernate works, tried fglrx, would hang with black lit screen to suspend.

---

### Post by Scarfy on 2010-06-30
All,

I can confirm that the removal of the SD card from my laptop when suspending and removing has fixed this issue for me.

The only further problem I had was when I took my laptop out of suspend whilst it was working off the battery. In that case, the screen simply began to go white (best described as looking as though it was icing over). I was forced to power off.

Other than that, it's all working okay.

---

### Post by jappie on 2010-07-01
> **elclanrs said:**
> me too, I have an Acer Aspire One 150.
I have the same system  but have 10.04 netbook remix installed and with me (and I am sure with anybody else!) suspend / hybernation is working fine...it the **resume function** that does not work. I have tried all options in the app/power managment/... via de gconf-editor but still no resume with any button/mouse. etc....just only hard reboot.

I did notice that every time after I need to do a hard reboot when I tried testing the suspend function is that my  enable (wifi) network funtion is turned off!
When I restart/turn on my system normally, the networking works fine...

a BIG OEPS! I completely missed the SD card that I stuck in my storage expansion a while ago and never put anything on. Anyway, After removal the suspend works fine!
Any hope for a fix of this?

---

### Post by utnubuuser on 2010-07-01
Anybody know anything about using the laptop's BIOS to Suspend/Hibernate instead of power-manager?

Is it possible to remove  sleep/suspend/hibernate functions from the OS and have the BIOS handle it?

Thanks

---

### Post by sourabh21 on 2010-07-02
I had the following problem but now these are solved \\:D/

1.Hibernation was not working
2.desktop visual effect not working

i dont know how exactly it worked but i did following steps...


1. Go to synaptic package manager >> Preferences 
 then tick the option of pre-released updates. now go to update manager u will get many new updates install them all.

one of them will be a hardware driver update in my laptop it was ##"fglrx"(this driver was already installed but it was not working but after installing pre released updates it worked)

2. now go to option HARDWARE DRIVER and then activate driver and restart your computer(if your driver is already active then inactive it and restart and then activate it).

now try to activate ur visual effects and also hibernate ur system.

it ll be working. In my system this worked hope that your ll also work!!!! 
Best of luck ;)

---

### Post by sourabh21 on 2010-07-02
I had the following problem but now these are solved \\:D/

1.Hibernation was not working
2.desktop visual effect not working

i dont know how exactly it worked but i did following steps...


1. Go to synaptic package manager >> Preferences 
 then tick the option of pre-released updates. now go to update manager u will get many new updates install them all.

one of them will be a hardware driver update in my laptop it was ##"fglrx"(this driver was already installed but it was not working but after installing pre released updates it worked)

2. now go to option HARDWARE DRIVER and then activate driver and restart your computer(if your driver is already active then inactive it and restart and then activate it).

now try to activate ur visual effects and also hibernate ur system.

it ll be working. In my system this worked hope that your ll also work!!!! 
Best of luck ;)

---

### Post by acs236 on 2010-07-07
I have 10.04 installed on two systems:  my Asus 1000HE netbook (Intel 950 graphics) and my custom-built desktop (nvidia 260).  

Suspend/hibernate works fine on the netbook, but I'm having the same issues as everyone else with the desktop.  I've tried all the "fixes" I could find online, and none work.  Hopefully this gets fixed soon.

---

### Post by martintremblay on 2010-07-07
sourabh21, do you know which kernel you are using?
I'm wondering if a newer release has caused improvements
(open terminal and type uname -r to find out which release you are using)

10.04 Lucid pre-release updates have caused hibernate and suspend to fail on my system. 

As long as I remain rolled back to 2.6.31-20-generic, my system functions properly, with any pre-release updates installed (including 2.6.32-22 and 2.6.32-23) my suspend and hibernate fail.

---

### Post by mikhairu on 2010-07-07
I'm also having problems with Suspend on my laptop.

I have HP Pavilion dv6 laptop: AMD Dual Core x64 (I'm running 32-bit Ubuntu 10.04), 4GB RAM, ATI Mobility Radeon HD 4650. 

Hibernation works fine but 'suspend' does not. 
I can put computer to sleep via 'suspend', but it wouldn't wake up - I get a blank black screen when I try to bring computer out of suspend. I have to resort to powering off my machine (holding power button), and when computer restarts my networks (wireless) are disabled.  My wireless adapter is Atheros AR5009 WiFi Adapter.

I tried using [FONT=Courier New]s2ram --force[/FONT], it puts machine into suspend without problems, but still I can't bring it out of suspend - the same blank screen appears.

It seems that a lot of people are having this problem, so hopefully someone comes out with a solution : ) *keeping my fingers crossed*.

---

### Post by clarencetso on 2010-07-09
> **Scarfy said:**
> All,

I can confirm that the removal of the SD card from my laptop when suspending and removing has fixed this issue for me.

The only further problem I had was when I took my laptop out of suspend whilst it was working off the battery. In that case, the screen simply began to go white (best described as looking as though it was icing over). I was forced to power off.

Other than that, it's all working okay.

Just wanted to add that the SD card fix works for me as well, whether on AC or battery power. Toshiba Satellite U200. 

Thanks to those who have confirmed this fix so far, this problem's been making me bang heads for awhile.

---

### Post by palgan on 2010-07-10
Hi,

Just wanted to add that both problems (suspending & hibernating) are solved on Dell D430 with Ubuntu 10.04 by prior removing of SD card. Screen and wifi resume without any problems.

Many thanks to all for the efforts!

P.

---

### Post by foutes on 2010-07-10
> **doko1 said:**
> Thanks, Anschuz, for this little but important detail. This worked out for me now! :)

[B]So here is how it works (hopefully) for everybody: 
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects" 
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer[/B]


I tried this and it worked even though extra could not enable and reverted back to none.I had 2 instances of Firefox running and my HTC Hero connected by usb and hibernate worked like a charm.I will try again when I get home and see how wireless works after hibernate.Thank you for posting this info.

Laptop specs are as follows.
Toshiba A105-s1416 2 gig ram
ATI 200m graphics with open source driver
Ubuntu 10.04 fresh install with 4 gig swap partition
Internet connection is a HTC Hero Android 2.1 tethered cause I am at work.

---

### Post by foutes on 2010-07-10
I am home now and tried hibernate again and it still works,wireless auto connects,no artifacts in menus or desktop.However Suspend does not work.My laptop will not boot after Suspend,I have to pull the battery out and unplug power adapter then plug power and battery back in go get it to boot.Suspend not working is not a big deal but it would be nice to have it working.

---

### Post by scytherswings on 2010-07-14
I have an IBM ThinkPad T21 from 2001, and even though it didn't install any extra drivers with that method, for some reason it worked! Thanks guys!

---

### Post by pboerr on 2010-07-14
I had the same problem and get solved after removing the SD card. Thanks!!!

---

### Post by billsbrother on 2010-07-26
I have an internal card reader, not holding a card. None of the solutions worked for me, so I disabled the card reader in the BIOS. 

It's a workaround that works.

---

### Post by utnubuuser on 2010-07-26
> I had the same problem and get solved after removing the SD card. Thanks!!!The fact that some of these issues are resolved simply by removing an sd card is probably an indicator of where to look.  Now we just need to figure out what it all means...

---

### Post by crisponions on 2010-07-26
> **utnubuuser said:**
> The fact that some of these issues are resolved simply by removing an sd card is probably an indicator of where to look.  Now we just need to figure out what it all means...

Just stumbled across this thread.  Removing the SD card worked for me too.  

Dell e1705
ATI x1400 (open source driver)
intel 3945abg

---

### Post by mhampson on 2010-07-30
On my Acer Aspire One, to get suspend to work 
**I don't have to remove the SD card, just unmount it.**

Even better, 
**it automatically re-mounts on resume**.

What I would love to do now is make the keyboard shortcut (Fn-F4 on the laptop itself, the sleep button on an external keyboard), or some other keyboard shortcut, or a menu item or panel button, both unmount the SD card (umount /dev/mmcblk0p1) and suspend (pm-suspend), ideally (but not necessarily) without requiring my sudo password. Anyone know how to set up any of these options?

EDIT: the best I have come up with so far is the following in an executable text file -

gnome-screensaver-command --lock
umount /dev/mmcblk0p1
sudo pm-suspend
gnome-screensaver-command --poke

...which I could link to a menu item or panel button (aka Launcher).

Anyone know how to link the script to a keyboard shortcut?

Anyone know a method that doesn't require the sudo password?

---

### Post by utnubuuser on 2010-07-31
My best fix for ATI M6 Ly in a thinkpad x31 so far:> In System>>Appearance select no effect, add nomodeset as boot paramater, then switch compositing on with Alt+F2, gconf-editor, apps, metacity, general, compositing-managerI get suspend/hibernate(?), performance is snappy, and good visual effects, ( transparent terminal etc).> brad@brad-laptop:~$ glxgears
957 frames in 5.0 seconds
1088 frames in 5.0 seconds
1138 frames in 5.0 seconds
1139 frames in 5.0 seconds
1137 frames in 5.0 seconds


Install Klipper in Ubuntu-Gnome [http://sazeit.com/articles/klipper-in-ubuntu-gnome]("http://sazeit.com/articles/klipper-in-ubuntu-gnome")

---

### Post by mhampson on 2010-08-01
> **utnubuuser said:**
> My best fix for ATI M6 Ly in a thinkpad x31 so far:I get suspend/hibernate(?), performance is snappy, and good visual effects, ( transparent terminal etc).

To what problem was that a solution?

---

### Post by Vimmander on 2010-08-01
I have an Inspiron 1501 running Lucid, and the only way I can put my machine into a low power state is by suspending with Fn+Esc.  Anything other method of suspending or hibernating, including closing the lid, requires a hard reboot to get going again.

The truth is that there are just too many machines out there with too many different configurations (software AND hardware).  Even buying a Dell 15n wouldn't work, because upgrading from 9.10 to 10.04 would break stuff.  There will never be a unified solution for simple and frequently used functions like suspend and hibernate in any distribution of linux, and a workaround that works for some people just isn't going to work for others with the same hardware configuration.  It's baffling, confusing, and a turn off.

That being said, I still use Ubuntu because what else am I going to do with the remaining 51 GB on my hard drive?  That, and Windows costs money to run because commercial AV software works better than free stuff...and believe me, I've tried the free stuff.  It's crap.

---

### Post by jondodson on 2010-08-01
Removing SD card worked for me - dell inspiron 6000.

---

### Post by Vimmander on 2010-08-02
> **jondodson said:**
> Removing SD card worked for me - dell inspiron 6000.

I have an SD slot?  (Leans over and checks)  Oh!  I do!  That's cool.

Seriously, I hardly use that thing.  It's empty unless I'm logged into Windows for pictures, videos, or syncing my Sansa Fuze with my library.

---

### Post by frogo on 2010-08-07
Hi, 

I have resume from suspend/hibernate troubles too. Looks like the video just doesn't resume. 

The machine is Latitude e4310. i5 core with integrated Intel graphics with 4GB RAM. I've got a generous swap partition (~ 10 GB). I have a dual install with one of Windows on it (can't recall which). 

Things I've tried following this thread:

1. Remove dummy SD card from reader. 
Result: Problem persists.

2. Add: 
resume=/dev/[SWAP Partition] to /etc/default/grub (then sudo update-grub) 
(I found the SWAP partition using the disk utility.)
Result: Problem persists.

Not sure: Does it matter where I place this line?

3. Add "nomodeset" to GRUB_CMDLINE_LINUX in /etc/default/grub (then sudo update-grub) 
Result: Problem persists
+ a very bad idea overall! I then lost video on reboot. I had to use my install USB, mount my system under media and clean /boot/grub/grub.cfg to remove 'nomodeset' for at least one system. Then I could boot into my machine revert /etc/default/grub to as before and run update-grub. (I could edit /etc/default/grub when booting from USB but not run update-grub as it wouldn't find some paths..)

I've been following too many different threads since I installed 10.04 afresh on that machine and couldn't rely on suspend/hibernate. 

I'm a newbie and I just don't get it. Am I missing something? Like a wiki page addressing this apparently pervasive and persistent issue or a thread that collects all relevant threads? 

thanks for any input

---

### Post by Vimmander on 2010-08-08
I just tried it again, and resuming from suspend to RAM causes a partial crash of X (some programs open as white screens, like the Terminal), and a reboot causes a kernel panic.  Therefore, full shutdowns are my only option.  I wonder if shutting down and restarting put more wear and tear on a drive than sleeping...

---

### Post by texla on 2010-08-09
> **jondodson said:**
> Removing SD card worked for me - dell inspiron 6000.
This worked for me, too!  Thanks - Asus x83 - now I just have to reconnect to the internet after suspend but that's a lot better than having to reboot...

---

### Post by zbeckerd on 2010-08-10
This really is beyond annoying.  I have been using nix for 2 decades and ubuntu since 5.xx. I have filed a bug report and followed the threads' trying all of the fixes.  Even loaded to a new partition so I could start fresh after all of the hacks I have tried.

There is more to this than meets the eye as I have tried puppy, dream, and mint.  No suspend or resume on those either.  So it looks more like a kernel issue.

I am at this moment doing the unthinkable and loading win7 as the primary OS as I need my laptop to suspend (and resume).  For several years I have only used win$ for customer support, running it in virtualbox.  Thank goodness my desktop does not need to suspend.

Hibernate does work but it is faster to boot fresh than to reload from hibernate.

Hmmmmm looks like sleep is ghosted in windows as well.  Nope it works after updating ati driver.  So now to load ubuntu inside win on my usb.

---

### Post by blur xc on 2010-08-13
> **snesreviews said:**
> Don't know why this has been marked as solved when there are lots of people still having the same issue...

Anyway I found an old thread which had **a** solution to this [http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

So I tried s2disk from the command line and it worked great, but adding them to that script doesn't seem to work (assumingly Ubuntu decided they wanted to ditch that convention). I later discovered that hitting the hibernate button doesn't seem to touch this script - it seems to execute /sbin/pm-hibernate. So big dirty fix was simply to back up your existing script and point it to s2disk instead:

sudo mv /sbin/pm-hibernate /sbin/pm-hibernate.bak
sudo ln -s /sbin/s2disk /sbin/pm-hibernate

And to do the same for suspend (slightly different as it may require --force for some machines)

echo -e '#!/bin/bash\n/sbin/s2ram --force' > ~/s2ram.sh
chmod a+x ~/s2ram.sh
sudo mv ~/s2ram.sh /sbin/
sudo mv /sbin/pm-suspend /sbin/pm-suspend.bak
sudo ln -s /sbin/s2ram.sh /sbin/pm-suspend

And magically it works fine. Wish I just did that instead of the None / Extras fix - went and zapped a lot of my cool compiz settings :(

Anyway just putting it out there in case it's of use to anyone else

Thanks!  You are a genius!  So far (knock on wood) this is working for me.  I've been going round and round with this little netbook for two weeks now (for this and other problems) but this makes it finally usable.  Thanks again...

And for those w/ 10.04, the hal scrips have been replaced with dbus (so I've been told), so the new scripts are located in /etc/acpi folder, there's a sleep.sh and a hibernate.sh.  I made new ones to call s2ram but it would not work from the gnome menus or when closing the lid, but this fix works like a charm.

BM

---

### Post by blur xc on 2010-08-13
> **blur xc said:**
> Thanks!  You are a genius!  So far (knock on wood) this is working for me.  I've been going round and round with this little netbook for two weeks now (for this and other problems) but this makes it finally usable.  Thanks again...

And for those w/ 10.04, the hal scrips have been replaced with dbus (so I've been told), so the new scripts are located in /etc/acpi folder, there's a sleep.sh and a hibernate.sh.  I made new ones to call s2ram but it would not work from the gnome menus or when closing the lid, but this fix works like a charm.

BM

I have only one minor, minor, issue- when resuming form suspend or hibernate, its as if the screen gets locks and needs the user to enter the password, which is weird, because when I rung s2ram or s2disk from the command line, when it resumes it doesn't ask for a password..  I'd like to disable that if at all possible.  I'm sure it has something to do with the way Ubuntu or Gnome handle resuming...

Anyway, thanks again-
BM

---

### Post by nic4m on 2010-08-15
> **snesreviews said:**
> Don't know why this has been marked as solved when there are lots of people still having the same issue...

Anyway I found an old thread which had **a** solution to this [http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

So I tried s2disk from the command line and it worked great, but adding them to that script doesn't seem to work (assumingly Ubuntu decided they wanted to ditch that convention). I later discovered that hitting the hibernate button doesn't seem to touch this script - it seems to execute /sbin/pm-hibernate. So big dirty fix was simply to back up your existing script and point it to s2disk instead:

sudo mv /sbin/pm-hibernate /sbin/pm-hibernate.bak
sudo ln -s /sbin/s2disk /sbin/pm-hibernate

And to do the same for suspend (slightly different as it may require --force for some machines)

echo -e '#!/bin/bash\n/sbin/s2ram --force' > ~/s2ram.sh
chmod a+x ~/s2ram.sh
sudo mv ~/s2ram.sh /sbin/
sudo mv /sbin/pm-suspend /sbin/pm-suspend.bak
sudo ln -s /sbin/s2ram.sh /sbin/pm-suspend

And magically it works fine. Wish I just did that instead of the None / Extras fix - went and zapped a lot of my cool compiz settings :(

Anyway just putting it out there in case it's of use to anyone else

had to change the paths to /usr/sbin to make it work on 10.04

---

### Post by oleink on 2010-08-15
> **GrogTheDreamer said:**
> I have an SD slot?  (Leans over and checks)  Oh!  I do!  That's cool.

Seriously, I hardly use that thing.  It's empty unless I'm logged into Windows for pictures, videos, or syncing my Sansa Fuze with my library.

wow i do all that on linux

---

### Post by minibeardeath on 2010-08-16
So is there a consistent solution to this issue yet? Or perhaps a fix to the source of the problem in the kernel?

---

### Post by matik on 2010-08-22
> **The_Bullfrog said:**
> 
...

5. Browse to the folder /etc/default and open the file named grub.

6. The first 2 lines are comments which start with a hash character (#). After these 2 lines enter the following:
resume=/dev/sda5. Then save the file and close the Nautilus file browser.

...


is there really RESUME keyword in /etc/default/grub ?

i did following modification, changed the line
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="resume=/dev/sda1"
```
(sda1 is my swap partition)

and hibernation/resume seems to work now, no other changes

---

### Post by billsbrother on 2010-08-23
After my kernel update yesterday my hibernate/suspend is no longer working (it used to after my workaround : sd slot disabling in the BIOS)

could be grub, the boot menu was changed, grub now tried to boot into the mem test.

---

### Post by billsbrother on 2010-08-23
> **matik said:**
> is there really RESUME keyword in /etc/default/grub ?

i did following modification, changed the line
```
GRUB_CMDLINE_LINUX=""
```to
```
GRUB_CMDLINE_LINUX="resume=/dev/sda1"
```(sda1 is my swap partition)

and hibernation/resume seems to work now, no other changes

Tried that (where I presume it needs to be the swap partition, sda7 on my laptop), it didnt help.
Booted into the previous kernel and that doesnt resume anymore either.

This pisses me off. It worked until the kernel update. How to undo the kernel update?

---

### Post by Tibco on 2010-08-28
I have this problem as well. Its not every suspend, and occurs very infrequently but it is still annoying. Would be nice to be able to reliably put my computer to sleep. I dont think its the floppy drive issue on my laptop because i dont have a "fb0" in my fstab. Any help would be great. 

PS also tried removing SD card

---

### Post by bravebear on 2010-09-06
Same issue here on a Toshiba Satellite R25-S3503 tablet running Lucid 10.04 WITH SD CARD MOUNTED. Suspend and Hibernate did not finish, got stuck on some screen, either in Desktop/GDM or in Console. After Hard reset, computer would start with wireless disabled, had to click on "Enable Network" or something. Used pm-utils, which comes with Ubuntu standard, it seems. Tuxonice and USWSP and stuff did not give me any other results.
After removing SD card suspend and hibernate worked.
I found these "fixes"/scripts, they are actually the same but written slightly different and work for my machine, no more issues with suspend and hibernate whatsoever:

1) [https://help.ubuntu.com/community/AspireOne/Ubuntu9.10]("https://help.ubuntu.com/community/AspireOne/Ubuntu9.10")
Look for *_Suspend Mode with SD cards mounted_* a few paragraphs down.

2) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384")
The solution is in comment [31]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384/comments/31")

And here it is from reference 2):

1 - open the text editor/gedit found in Accessories(? I think, don't have the Aspire in front of me), copy/paste the following:

# Drop to: /etc/pm/sleep.d
# Use this script to prevent data loss on mounted MMC/SD
# cards. It syncs data and umounts all mmcblk devices prior to
# suspend, and cancels suspend if umounting was not possible
# (i.e: something locks a file)
case "${1}" in
    hibernate|suspend)
        /bin/sync
        for drive in $( /bin/ls /dev/mmcblk?p* ); do
        /bin/umount ${drive} > /dev/null
        # If umount failed: abort suspend
        if [ $? -gt 0 ]; then
        # Test if device keeps mounted. Previous command could fail
        # (i.e device was not mounted) with a non-stopper
        # problem for the suspend process.
        /bin/mount | /bin/grep ${drive}
        if [ $? -eq 0 ]; then
            exit 1
        fi
        fi
    done
    ;;
# resume|thaw)
## Do nothing. All devices will be automatically mounted again.
# ;;
esac


2 - Save as *010_unmount_SD.sh* in your Home folder

3 - Open the Terminal (under Accessories)

4 - Use the following command to copy the file to the correct location (you will be prompted for the Admin password when you hit Enter):

*sudo cp 010_unmount_SD.sh /usr/lib/pm-utils/sleep.d/010_unmount_SD.sh*

5 - Set the proper permissions with this command (you will again be prompted for the Admin password):

*sudo chmod 755 /usr/lib/pm-utils/sleep.d/010_unmount_SD.sh*

This script will unmount a SD card present and let your machine hibernate/suspend, IF the SD card is the issue. But like some reported, this is not the case for all.

---

### Post by texla on 2010-09-07
> **bravebear said:**
> 
2) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384)
The solution is in comment [31]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560384/comments/31")


Thanx - now I have a permanent fix for my sd card bug!  Works on my asus x83vb.

---

### Post by Cfhs_1 on 2010-09-10
Hey Guys, I WAS having the exact problem as everyone else in ubuntu 10.04. Hibernation/suspend just refused to work anymore. I soon decided to see if hibernation/suspend was still working in an older kernel version (2.6.32-23) and it worked perfectly! It seems that kernel version (2.6.32-24) will kill hibernation/suspend functions on some Dell Laptops. Instead of uninstalling the newer kernel, I simply commented it out of my grub config. now kernel (2.6.32-23) is my default choice and suspend/hibernation is once again working. I hope this helps someone else, because it sure saved me. Hibernation is a very necessary function on a laptop to me.

Cheers, Cole Brown

---

### Post by shahnweb on 2010-09-13
I'm on Toshiba Qosmio laptop.

Neither suspend or hybernate works.

It makes the screen black, but you cannot go back to original state by mouse movement or clicking the power botton on the laptop. It hangs and need another hard reboot.

Some site suggests to use 's2ram'.  When I installed and used it, I got the following error.
Since so many people reported the similar issue, I wonder if this not machine specific problem but Ubuntu in general.

$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "TOSHIBA"
    sys_product  = "Qosmio X505"
    sys_version  = "PQX33U-02T01R"
    bios_version = "V2.60   "
See [http://suspend.sf.net/s2ram-support.html](http://suspend.sf.net/s2ram-support.html) for details.

---

### Post by imota on 2010-09-13
I am using an ACER ASPIRE 5553G, Ubuntu 10.04 64bit and my computer will suspend but not come back to life. Suspend does everything right (LCD goes blank (backlight off), HD off and power LED off, Little blinking light bulb flashing to indicate computer in standby)

Hibernate locks the computer up, backlight still on.

Try to come back from suspend, lights temporarily flash, LCD lights up but stays blank. No keyboard, nothing. 

Hard reset, come back, network disabled.

In short, very similar to everyone else's problems.

I've tried tinkering with my ATI graphics card (Mobility Radeon HD4200), using the Open src one and the proprietary one, tried disabling power play on the proprietary one, tried the visual effects trick, nothing.

Anyone else has an Acer Aspire with this problem?

I'll give the nomodeset a try, but not very hopeful...

No SD cards (Although I have an SD slot, nothing mounted there).

---

### Post by imota on 2010-09-14
I tried all the solutions on this thread, none worked. Even tried upstream linux kernels, didn't work...

I reported the bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/637712](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/637712)

Please, if anyone with an Acer Aspire has the same symptoms or found a solution post it here!

Thanks

---

### Post by juppy999 on 2010-09-18
Similar issue with Ubuntu 10.04 on Lenovo Ideapad S10e. Suspend and Hibernate were working **just fine** until an update about 3 days ago. Machine *will* now suspend OK, but cannot resume; starts up but no display and backlight remains off. Forced shutdown required to recover. When machine restarts after shutdown, networking is disabled. 

Hibernate option is still working though, so getting by with this instead. Anyone any idea about the suspend problem? (A 'system restore' facility in case of a bad update is looking like a useful thing to have, I reckon)

Just made an update (21 Sep) and suddenly suspend is working properly again!  There were only three packages affected by the update (bzip & dpkg & libbz2, I think), none seemed to have any connection with this problem - but anyway, it fixed it.  Thank you to whoever was working away in the background on this and knew how to repair it - much appreciated :)

---

### Post by Nines on 2010-09-29
New to Ubuntu

Using : 
Lenovo/IBM T60
Ubuntu 10.04

[ranty] I've spent several hours getting Ubuntu to play nice with wireless, video and VPN.  I wasn't expecting it to work 100% out of the box, but 'suspend' and 'hibernate' being jacked is pushing it a bit far [/ranty]

Suspend : Suspends, but can't resume [HDD spools up but nothing happens]
Hibernate : Can't hibernate [backlight remains on,etc]
-- Both features work in W7 (had to be said...)

Being new to GNU/Linux in general I would prefer not to have to mess with recompiling the Kernel, etc.

Has the cause of this issue been confirmed?

edit : attempting more fixes discussed in this thread.

---

### Post by MazM on 2010-10-06
Hello,

I am new to linux and after my computer suspends a few times and i log back in, my internet doesn't work and it says "Device not ready" and it won't work until i restart my computer. Please help.

Maz

---

### Post by SyAu on 2010-10-06
> **MazM said:**
> Hello,

I am new to linux and after my computer suspends a few times and i log back in, my internet doesn't work and it says "Device not ready" and it won't work until i restart my computer. Please help.

Maz

Try this, right click on the 'Up and down arrow' in the task bar and click 'Enable Networking' ...

---

### Post by leonardo_neo on 2010-10-07
After trying many fixes mentioned in this thread, I finally gave up, as nothing helped.

So I tried Ubuntu 10.10 RC.

Hibernate/Suspend working perfectly. (I hope the next kernel updated doesn't spoil it again, like it did in 10.04)

---

### Post by lots_of_entropy on 2010-10-07
Intersting ... also installed 10.10 ... still does not resume. Laptop: Thinkpad x200

---

### Post by hexplor on 2010-10-11
Installed 10.10
[http://www.amazon.com/Sony-VGN-NW350F-Notebook-Blu-ray-Microsoft/dp/tech-data/B003340VTK/ref=de_a_smtd](http://www.amazon.com/Sony-VGN-NW350F-Notebook-Blu-ray-Microsoft/dp/tech-data/B003340VTK/ref=de_a_smtd)

Doesn't resume. Worked perfectly on all earlier releases including 10.04...

---

### Post by billsbrother on 2010-10-12
whoa, now I feel like a dumbass. Did some regular updates to see if this would fix my hybernation issues, that once were gone but came back again. I noticed a very dim logon screen in the blackness. All I had to do now was to use the hardware buttons on my keyboard to get the backlight on again. 

I cant remember if I had tried this before but this sure is entry level trouble shooting. Still dont understand why this wasnt needed when it worked, maybe a setting in auto adjustment that was changed.

---

### Post by acs236 on 2010-10-14
10.10 solves the resume problem for me.  I'm running a desktop with nvidia graphics.

---

### Post by rafaelenr on 2010-10-17
> **MazM said:**
> Hello,

I am new to linux and after my computer suspends a few times and i log back in, my internet doesn't work and it says "Device not ready" and it won't work until i restart my computer. Please help.

Maz

This worked for me: 

[http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html)

It worked to solve the network problem after hard reboot, but it is actually easier to right click and enable network back.

I still cannot solve the suspend/hibernation issue (I have a toshiba satellite pro u500 -1e5

---

### Post by Cclips on 2010-11-04
Weiiird. Anyway I'm still using 10.04,and up until a day or so ago had suspend/resume working fine. Then tonight it wasn't working at all and would require a hard reboot after trying to suspend. I was about to revert to an older kernel when I noticed I still had an SD card inserted. I removed the card and now it suspends/resumes fine once again. 

Something in a recent kernel apparently broke suspend/resume while an SD card is mounted...Give that a try if you are still having problems.

---

### Post by geezerone on 2010-11-04
Would also like to report two separate 10.10 fresh installations not properly suspending/hibernating (PC stays on and monitor has blank screen). Only recover by hard reboot.

---

### Post by bablakely on 2010-11-07
Confirming this problem on a Lenovo X200 with updated 10.10 x86_64.  Occasionally suspend works, but most of the time the screen goes blank and the sleep LED just flashes until I hard power off.

---

### Post by koenr on 2010-11-08
> **Bogle said:**
> On a Sony Vaio VGN-TX3XP the Suspend is working now I've unmounted the 2GB SD card. HTH.

I'm using a Lenovo R500
I upgraded from GRUB 1.5 to GRUB 2 without succes
I tried some of the other suggestions (extra, [https://bugs.launchpad.net/bugs/370935](https://bugs.launchpad.net/bugs/370935),)

Eventually, removing my always inserted 2 GB SD card solved the problem. Thanks a lot for that!

---

### Post by vaibhavmahimkar on 2010-11-12
Confirming the issue.

Issue:
Hibernate not working after updating to release 10.10
-screen goes black with backlight on and cursor blinking
-only way out is Hard powerdown.

Used to work upto 10.04.


Hardware: Dell Studio 15 laptop.

---

### Post by qmmr on 2010-11-24
Ubuntu 10.10 same problem here, suspend / hibernate does not work, blank screen shows up with just a blinking cursor. Power button on the chasis turns system back (as if from sleep or hibernate) but you can see / hear the computer working all the time. Really weird. I have ATI Radeon HD4850.

---

### Post by hukkettoso on 2010-11-25
> **Cclips said:**
> Weiiird. Anyway I'm still using 10.04,and up until a day or so ago had suspend/resume working fine. Then tonight it wasn't working at all and would require a hard reboot after trying to suspend. I was about to revert to an older kernel when I noticed I still had an SD card inserted. I removed the card and now it suspends/resumes fine once again. 

Something in a recent kernel apparently broke suspend/resume while an SD card is mounted...Give that a try if you are still having problems.

[SOLVED]

Thanks @Cclips, your solution worked fine for me. I forgot an SD card mounted for weeks and when removed suspend mode turn back working fine.
Still wonder why an SD can break the suspension.. 
i tried kernels from 2.6.32-21 to 2.6.32-25 ..and I had the same issue

---

### Post by bablakely on 2010-11-25
[NOT SOLVED]

I do not have an SD card mounted and still have the problem, as described in my post above.

---

### Post by bybirius on 2010-11-27
I was having this same problem. I'm running 10.04 on a toshiba netbook NB205. I read through all of these posts and tried some of the suggestions and nothing worked for me. For some reason I went into login screen and changed the setting to "Automatically login to "myusername" and that fixed the problem. It's been working for a couple of weeks now. It's worth a shot.

---

### Post by juppy999 on 2010-12-01
Lenovo S10e & Ubuntu 10.10 - suspend/resume working, not working, update fixes it, next update kills it, even using an external monitor had an effect (bad one) on suspend :(  Then I tried installing 'hibernate' package found in Synaptic - suggestion from another thread - and it actually seems to work properly! Worth a try, guys!

---

### Post by bablakely on 2010-12-08
FYI: Installing hibernate seems to have done the trick for me.  Perhaps this should be installed by default?

---

### Post by Sunflower1970 on 2010-12-09
> **utnubuuser said:**
> My best fix for ATI M6 Ly in a thinkpad x31 so far:
Quote:
In System>>Appearance select no effect, add nomodeset as boot paramater, then switch compositing on with Alt+F2, gconf-editor--> apps--> metacity--> general --> compositing-manager
I get suspend/hibernate(?), performance is snappy, and good visual effects, ( transparent terminal etc).

Yes, suspend works with this workaround, but one cannot run any higher visual effects like Compiz. I've tried and it's painful to say the least. If the nomodset is removed then Compiz effects can be run quickly and smoothly (This is on a Thinkpad R40)

---

### Post by Rick B. on 2010-12-10
I have an IBM Thinkpad R51 and just last week upgraded to 10.04. Suspend/Hibernate does not work. Why hasn't this bug been fixed yet? Is there a fix? 

Installing Hibernate from Synaptic Manager did NOT work. Thanks.

---

### Post by tamashumi on 2011-02-16
Hi,

My case is as follows:

VAIO VGN-SZ650N with Ubuntu 10.04 x64.

Hibernate/suspend doesn't work. Screen goes black, three keyboard leds flashes and than nothing... at least that what I thought (always did hard reset).
Just by the coincidence I figured out if I wait long enough laptop suspends (haven't checked with hibernate yet). It takes like 5 minutes or more. It seems something "holds" it against going sleep.

**I'm attaching lspci.txt, pm-suspend.log.txt and syslog.txt with logs from only one suspend try - successful but definitively after too long time. Maybe someone could please point if anything suspicious can be found inside.**

Just to mention hibernate/suspend had been working for this laptop just fine with 9.04, 10.04 (before) or 10.04 booted from live CD even now.
Another thing worth of mentioning is fact I upgraded from 4 to 8 GB RAM, but I increased swap enough too and tried to remove 1 RAM stick back to 4GB but this didn't helped.

[COLOR="DarkRed"]Maybe someone from above posts had similar case but haven't waited long enough to see that his laptop does suspend.[/COLOR]

---

### Post by hufemj on 2011-03-03
> **Rick B. said:**
> I have an IBM Thinkpad R51 and just last week upgraded to 10.04. Suspend/Hibernate does not work. Why hasn't this bug been fixed yet? Is there a fix? 

Installing Hibernate from Synaptic Manager did NOT work. Thanks.

You might want to check out this thread:

[http://ubuntuforums.org/showthread.php?p=10516577#post10516577](http://ubuntuforums.org/showthread.php?p=10516577#post10516577)

I have a Toshiba Satellite C655 and ACPI wasn't working. I upgraded the BIOS and changed ACPI to 

GRUB_CMDLINE_LINUX="acpi=copy_dsdt"

in grub and it's now working perfectly.

---

### Post by ssulaco on 2011-03-16
Just installed Lucid on Dell Dimension 4600 (dual boot XP).......couldnt resume from Suspend,
used this procedure,working good so far
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by siretfel on 2011-03-21
[I][SIZE="1"]Quote:
Originally Posted by doko1 View Post
Thanks, Anschuz, for this little but important detail. This worked out for me now!

So here is how it works (hopefully) for everybody:
1. Go to System -> Preferences -> Appearance
2. Choose Tab "Visual Effects"
3. Make sure option "None" is chosen, if not choose it
4. Change to "Extra", this makes the system searching for drivers automatically
5. Change back to the configuration you prefer
[/SIZE][/I]


The above solution worked perfectly for me.I can hibernate and resume without ANY problem so far.
Thanks:popcorn:

---

### Post by Martin Hecht on 2011-03-29
I have worked through all solutions proposed in this thread and NONE of them worked for me.
I have a Thinkpad x31 with Ubuntu 10.04.2 LTS (xubuntu) Kernel  2.6.32-30-generic. After a suspend or Hibernate the final picture is a pattern of vertical lines with different widths. After a suspend to disk I can follow the messages until the disk image is uncompressed, after a suspend to ram the screen is blank and then turns to this pattern.
No keys at all, not even Ctrl+Alt+Del/Backspace/F1...F8 work (Only pressing the power button for a long time). 
This only proposal which seems to help is adding nomodeset to grub, however, this has the side effect that the computer sometimes freezes in the middle of working, without any notable reason.
I also tried to disable the suspend-action connected to the action of closing the lid - but it seems that editing /etc/acpi/events/lidbtn or the scripts called from there has no effect, even after reboot.

---

### Post by oldguysrule on 2011-04-07
Sorry if this has already been brought up but here is what worked for me. None of the suggestions on most of the pages I tried worked so I went into my BIOS and in power management noted the ACPI power state was set to S2 (cpu powered off). I set it to S1 & S3 (third option in my choice list). This solved the problem for me. Again if this has already been suggested I apologize I didn't have time to check every page. :popcorn:

Gateway GT5426E - AMD Athlon 64x2 at 5200 running Lucid

---

### Post by geezerone on 2011-04-08
Tried S1 (was S3 only choice) still the same.

I see there is a message (two lines) regarding usb devices stopping suspend/hibernate (copied part below from dmesg):

> [   64.630097] PM: **Entering standby sleep**
[   64.630110] Suspending console(s) (use no_console_suspend to debug)
[B][   64.630404] pm_op(): usb_dev_suspend+0x0/0x20 returns -32
[   64.630413] PM: Device 8-4 failed to suspend async: error -32[/B]
[   64.650698] PM: Some devices failed to suspend
[   64.712245] PM: resume of devices complete after 61.540 msecs
[   64.712381] PM: resume devices took 0.060 seconds
[   64.712397] PM: Finishing wakeup.
[   64.712398] Restarting tasks ... done.
[   64.802409] r8169 0000:06:00.0: eth0: link up
[   65.351790] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   75.410055] eth0: no IPv6 routers present
[   77.003720] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   78.925952] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[   78.925956] PM: Marking nosave pages: 00000000cfdf0000 - 0000000100000000
[   78.926420] PM: Marking nosave pages: 0000000020000000 - 0000000024000000
[   78.926622] PM: Basic memory bitmaps created
[   78.926623] PM: Syncing filesystems ... done.
[   78.927030] Freezing user space processes ... (elapsed 0.01 seconds) done.
[   78.940099] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[   78.960106] PM: Preallocating image memory... done (allocated 895771 pages)
[   79.808785] PM: Allocated 3583084 kbytes in 0.84 seconds (4265.57 MB/s)
[B][   79.808787] Suspending console(s) (use no_console_suspend to debug)
[   79.809147] pm_op(): usb_dev_freeze+0x0/0x20 returns -2
[   79.809149] PM: Device usb8 failed to freeze async: error -2[/B]
[   79.837392] PM: restore of devices complete after 0.528 msecs


---

### Post by doru001 on 2011-04-30
In my case, I can not ENTER hibernate after a few days of use. 

Also, the desktop theme is not applied after a clean restart until I do System > ... > Keyboard Shortcuts. 

Ubuntu 10.04 Desktop LTS

---

### Post by rrice on 2011-04-30
I installed 10.10 on my ZT laptop and have applied updates as they have been issued but - the power management is a bit faulty.  When I hibernate, I get a gray screen with lots of vertical lines and it will not resume.  Sleep also does not "un-sleep", though the "sleep" indicator on my computer says it is sleeping.

When the power chord is unplugged, even if there is a 50% charge, it will suddenly think the battery is critically low and sometimes it will sleep (as I asked it to when critically low).

So, there seem to be some battery/power management issues in 10.10 even with all the updates applied.

---

### Post by baobab33 on 2011-05-22
Good news though as there is a simple fix to this bug for 10.10, documented in the [Ubuntu 10.10 Maverick Meerkat release notes]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes").

this "might" work with 10.04 (i did not try)

When the XHCI module is loaded for USB 3.0 operation the system cannot suspend. Manually unloading XHCI will allow suspend to complete normally. To avoid future suspend problems, the workaround is to add [FONT="Courier New"]SUSPEND_MODULES="xhci-hcd"[/FONT] to [FONT="Courier New"]/etc/pm/config.d/unload_module[/FONT] then the system can suspend normally. ( 522998 )

_Please note_: this fix only seems to work when using the closed source nVidia drivers.  Using the open source nouveau drivers gives a black screen when awoke from suspend or hibernate.


Implementing the fix - create a new configuration file

1. Open at terminal window Applications > Accessories > Terminal

2. Enter the following command into the terminal window:

[FONT="Courier New"]gksudo gedit /etc/pm/config.d/unload_module[/FONT]

3. In the editor window that pops up, paste the following text and save the new file. 

[FONT="Courier New"]SUSPEND_MODULES="xhci-hcd" 
[/FONT]

That's it ! Suspend and hibernate should now work as normal for some people.  Good luck.


[SIZE="1"]copied from here : [http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html](http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html)[/SIZE]

---

### Post by Rick B. on 2011-05-23
I am currently using 10.10 and now have a newer IBM Thinkpad. Suspend now works like a charm. Thanks.

---

### Post by kirovs on 2011-10-26
If you have HDMI external monitor try to disconnect it and see if now your suspend works.
If you have ATI Catalyst driver add vga=0 to the kernel entry in your menu.lst:
See this:
[https://wiki.archlinux.org/index.php/ATI_Catalyst#Video_fails_to_resume_from_suspend2ram](https://wiki.archlinux.org/index.php/ATI_Catalyst#Video_fails_to_resume_from_suspend2ram)

---

### Post by wmichaelb on 2011-10-30
I have the same problem with an Asus motherboard & Intel dual core. It worked fine after the original install, but one of the recent updates changed that. Mine will neither hibernate nor suspend; it only shuts down.

---

### Post by wmichaelb on 2011-10-30
Thank  you, Baobab33; your solution works on 10.04 as well!:D

---

### Post by bonjovi123 on 2012-02-07
I'm in 11.04 version of Ubuntu. 

My laptop is Thinkpad L412

This works for me & a bunch of other people (well, as I see in the comments)

Pretty easy & worth a shot:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by MrTadeKK on 2013-02-03
My computer either didn't work with suspend. Then I tried push  some buttons. F4 or F5 wake up system :p I'm using Dell Inspiron N5010 with original ATI drivers.

---

