---
title: "Could use some assistance please :)"
date: 2011-05-05
forum: General Help
---

### Post by SL1DEmemphis on 2011-05-05
I have been having issues getting to Ubuntu as of late.  I can't even get to the login screen.  The screen goes black and says "Killed"  and when I run in recovery mode i get the same thing with a lot of code and something that says its unable to find the root device.

I have ruled out that the SSD is not at fault, I put it in another computer and got to ubuntu just fine.

So next I reset the CMOS to see if that helped.  Nope, I lost Asus Express gate and still no luck getting to the OS.  I can't even use a bootable CD to reinstall ubuntu, but as I said the SSD and OS aren't at fault.

Next I tried to reinstall the bios via USB stick, my next error is BOOTMGR is missing, press CTRL + ALT + Del to restart" or some thing like that.

Can anyone help me troubleshoot please?

Thanks,
Andrew

---

### Post by SL1DEmemphis on 2011-05-06
le bump

---

### Post by 4Orbs on 2011-05-06
Have you tried first disabling Express Gate in the BIOS before attempting to boot to Ubuntu?

---

### Post by SL1DEmemphis on 2011-05-06
oh yeah, speaking of that.  somehow express gate has been removed from the motherboard?  It says Installation failed when the board boots up. :-\

---

### Post by 4Orbs on 2011-05-06
And the option to enable/disable Express Gate doesn't show up anymore in your BIOS? Express Gate, if the options still exist, will probably work again if you disable, reboot, enable and reboot again. It's almost indestructible. But I think it should be disabled before trying to boot into Ubuntu with the grub bootloader (maybe because the 10 second timer keeps going even though you are in Express Gate?).

---

### Post by SL1DEmemphis on 2011-05-06
ill give this a try

---

### Post by SL1DEmemphis on 2011-05-06
ok tried that, disabled restarted, enabled, restarted.  Express gate installation incomplete.  Should I get a new board?

edit: screen goes black after the installation incomplete message comes up.  My brain has been hurting for a little over a week over this stuff.  :(

---

### Post by 4Orbs on 2011-05-06
I don't think you need a new board. Does your ssd have Windows on it in addition to Ubuntu?

---

### Post by SL1DEmemphis on 2011-05-06
oh, and excuse my ignorance, but what is the grub bootloader? I am coming from windoze here.

---

### Post by SL1DEmemphis on 2011-05-06
> **4Orbs said:**
> I don't think you need a new board. Does your ssd have Windows on it in addition to Ubuntu?

No, it doesn't, just ubuntu alone.

---

### Post by 4Orbs on 2011-05-06
Grub is the black screen that allows you to switch between booting Windows or Ubuntu. The Grub bootloader replaces the Windows bootloader, and that could be where your main problem (at the moment) is.

---

### Post by SL1DEmemphis on 2011-05-06
> **4Orbs said:**
> Grub is the black screen that allows you to switch between booting Windows or Ubuntu. The Grub bootloader replaces the Windows bootloader, and that could be where your main problem (at the moment) is.

I see, so since I don't have windows, how should I go about diagnosing the problem?

---

### Post by 4Orbs on 2011-05-06
If Ubuntu is the only system on your ssd, then you would probably never see grub.

I think if you disable Express Gate for now... then reboot... if it still doesn't boot into Ubuntu, maybe it will boot into the livecd.

---

### Post by SL1DEmemphis on 2011-05-06
> **4Orbs said:**
> If Ubuntu is the only system on your ssd, then you would probably never see grub.

I think if you disable Express Gate for now... then reboot... if it still doesn't boot into Ubuntu, maybe it will boot into the livecd.

So, disable Express Gate, and boot from the ubuntu CD. ill give it a shot.

---

### Post by SL1DEmemphis on 2011-05-06
Ok, that didn't work, but something different happened.  I took pictures.  I'll try an upload them now.

---

### Post by 4Orbs on 2011-05-06
A puddle of melted plastic?

---

### Post by SL1DEmemphis on 2011-05-06
HAHAHA not so glorious.

[IMG]http://a6.sphotos.ak.fbcdn.net/hphotos-ak-snc6/225581_1698385268655_1508580008_31310678_1023940_n.jpg[/IMG]

then...

[IMG]http://a4.sphotos.ak.fbcdn.net/hphotos-ak-ash4/227504_1698388748742_1508580008_31310679_4970621_n.jpg[/IMG]

---

### Post by 4Orbs on 2011-05-06
That's curious. Before your troubles began, had you configured Express Gate to save some websites and login passwords?

---

### Post by SL1DEmemphis on 2011-05-06
Nope, I hardly ever used express gate, actually could care less to use the feature.  I used to boot to the OS in a matter of 12-15 seconds

---

### Post by SL1DEmemphis on 2011-05-06
Ill give you a bit of history.  I had win7 64bit on the computer (I think it was a bootleg, as I got it from a friend who says it was genuine)  anyway it started acting up and blue screening.  It just went kaput so I formatted and installed ubuntu, 24hrs later while watching a youtube video, the sounds begins looping and the screen freezes.  I try restarting and this begins.

---

### Post by 4Orbs on 2011-05-06
Remove the live cd and reboot. If the Ubuntu installation on the ssd is still intact, you should be able to access the grub screen by hitting the "Esc" key after your ASUS BIOS splashscreen fades out. If that works, on the grub screen choose the option to boot into recovery mode.

---

### Post by SL1DEmemphis on 2011-05-06
got a new error after leaving the pc on since the previous pictures.

[IMG]http://a8.sphotos.ak.fbcdn.net/hphotos-ak-snc6/228649_1698413469360_1508580008_31310691_3209508_n.jpg[/IMG]

Also, here is what I get in ubuntu recovery mode.

[IMG]http://a8.sphotos.ak.fbcdn.net/hphotos-ak-ash4/217692_1679559638026_1508580008_31284745_1786349_n.jpg[/IMG]

and

[IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-snc6/222465_1679558397995_1508580008_31284742_5739400_n.jpg[/IMG]

---

### Post by SL1DEmemphis on 2011-05-06
just fyi, the last 2 pictures were from a few days ago.

Just ran recovery mode again and its doing something else.  ill try to take pictures :-\

---

### Post by SL1DEmemphis on 2011-05-06
more! sadly
[IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-snc6/222170_1698425349657_1508580008_31310695_4813484_n.jpg[/IMG]

[IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-snc6/223357_1698426349682_1508580008_31310696_5210849_n.jpg[/IMG]

---

### Post by 4Orbs on 2011-05-06
After googling the error, I see that a number of people fixed their problem by making sure the sata cables and power connections were good. But others were worried that it might be due to an incorrect RAID setup. This stuff is over my head, but I think you'll get some help if you wait awhile for one of the linux pros to come along. You can bump your post once a day.

Still, it seems odd that the livecd wouldn't boot to the live desktop.

---

### Post by SL1DEmemphis on 2011-05-06
Yeah, I have tried replugging the sata cables, switching to different ports, etc. even tried a raid setup. nothing helped.  I appreciate you taking the time to help me though. ill just continue to bump.

---

### Post by 4Orbs on 2011-05-06
I'll keep watching the thread, really want to know the outcome. Best of luck.

---

### Post by 4Orbs on 2011-05-06
One more thought. If you are no longer in a RAID setup, you might check your BIOS and make sure the hard drive is set to IDE mode or whichever setting is preferred for a ssd.

---

### Post by SL1DEmemphis on 2011-05-06
> **4Orbs said:**
> One more thought. If you are no longer in a RAID setup, you might check your BIOS and make sure the hard drive is set to IDE mode or whichever setting is preferred for a ssd.

Yeah, I did that.  Will have to come back and start working on this mess again after work today.

---

### Post by GreatKeyHunter on 2011-05-06
I have an Asus mobo that gave me a similar problem after messing around with it.  What i did was that i disconnected it from a power source, removed the ram, and the battery.  I waited about 5 minutes enjoying a cup of coffee and put everything back together with my fingers crossed.  Boom, it booted fine.

---

### Post by SL1DEmemphis on 2011-05-06
> **GreatKeyHunter said:**
> I have an Asus mobo that gave me a similar problem after messing around with it.  What i did was that i disconnected it from a power source, removed the ram, and the battery.  I waited about 5 minutes enjoying a cup of coffee and put everything back together with my fingers crossed.  Boom, it booted fine.

ok, pulled the plug, ram, and battery. we'll see what happens next!

---

### Post by SL1DEmemphis on 2011-05-06
No luck :( thanks though

---

### Post by SL1DEmemphis on 2011-05-07
Man, this is giving me a headache.  I think I may just get a new board.

---

### Post by Duncan Williams on 2011-05-07
I am sorta having similar issues...
[ubuntuforums.org/showthread.php?t=1748855]("ubuntuforums.org/showthread.php?t=1748855")

---

### Post by SL1DEmemphis on 2011-05-07
> **Duncan Williams said:**
> I am sorta having similar issues...
[ubuntuforums.org/showthread.php?t=1748855]("ubuntuforums.org/showthread.php?t=1748855")

just read your thread. sounds like you are able to get a little further than i am.  I can't even get to any menus on the LiveCD. :(

---

### Post by Duncan Williams on 2011-05-07
Just worked my problem out and it is all running as it should again. check my thread in 10 mins............ D

---

### Post by SL1DEmemphis on 2011-05-07
> **Duncan Williams said:**
> Just worked my problem out and it is all running as it should again. check my thread in 10 mins............ D
will do

---

### Post by SL1DEmemphis on 2011-05-07
that solution won't work for me unfortunately.

---

