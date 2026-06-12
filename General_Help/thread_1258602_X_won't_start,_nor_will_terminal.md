---
title: "X won't start, nor will terminal"
date: 2009-09-05
forum: General Help
---

### Post by marc1uk on 2009-09-05
I've recently upgraded a box with a new Ubuntu install, adding a second HD, new (NVidia) gfx card, and some more RAM.  Since then, the loading bar stalls during boot, and when I hit ctrl+alt+del it finishes loading, then gives a blue error message along the lines of:  ```
Could not start the X Server due to some internal error. 
In the meantime this display will be disabled. 
Please restart GDM when the problem is corrected. 
``` It then takes me into CLI. Even undoing the hardware changes, the problem persists. I've looked up a number of threads on similar problems, and made some progress in getting X to start, but as yet no solution. 
For example, I can boot using recovery mode, and if I run fsck I can then resume boot and get taken to the GDM and login normally. However, I can't then run a terminal window, getting the error: 'There was an error creating the child processes for this terminal'. 
I can also start x following the normal boot into CLI, by using: ```
 sudo mount -o remount,rw / 
startx 
``` But again, I can't run a terminal window.   Any help with this would be fantastic, since I can't even boot from the LiveCD to do a fresh reinstall.

---

### Post by Liolikas on 2009-09-05
>Any help with this would be fantastic, since I can't even boot from the LiveCD to do a fresh reinstall.
Why?
You have cdrom right?

---

### Post by marc1uk on 2009-09-05
> **Liolikas said:**
> >Any help with this would be fantastic, since I can't even boot from the LiveCD to do a fresh reinstall.
Why?
You have cdrom right?

Yeah, perhaps I should've added that, but it just stalls on the loading bar too, eventually giving me a blank screen, then:  ```
end_request: I/O error, dev sdc, sector **** 
Buffer I/O error on device sdc, logical block **** 
 
``` that happens whether i try to enter a live session or install.

---

### Post by Liolikas on 2009-09-05
90% that you have:
1)bad disk
2)bad (wrong connection) cdrom

---

### Post by marc1uk on 2009-09-05
A little more info: even when entering recovery mode, loading still stalls, this time at about 5 repeated lines of:
```
codec_read: codec 0 is not valid
```or some such. Again, hitting ctrl+alt+del completes the loading and takes me into the recovery mode options menu.  

Also just found that, having left it for about 10 minutes on those I/O buffer errors, the CD install option has eventually given me the installation menu. Perhaps I should just proceed with this, if it's not an easy fix?

---

### Post by marc1uk on 2009-09-05
> **Liolikas said:**
> 90% that you have:
1)bad disk
2)bad (wrong connection) cdrom

Hrmmm. Well, I've got two DVD drives, and the LiveCD won't run on either. Plus, given that this is a problem both with the installed version and the Live, I'd suspect the drives are fine. The disk's also been verified, and has provided several successful installs prior to this one. 
The HD install is also very new (literally a few days) and was working fine until the upgrades, which makes me think the HD's fine, and some settings have just gone awry.

---

### Post by marc1uk on 2009-09-05
Well, I attempted a reinstall, but got an error saying that Grub could not be installed on hd0, and sent to a live session instead. Restarting shows the situation's unchanged. 

I think my best lead at the moment is the success of sudo mount -o remount,rw /. If i try startx from CLI before running that, i get a spate of errors about the system being read-only, so that necessary temporary files can't be made. Doing this seems to make it writeable.  
Other than that, does anyone have any ideas about not being able to start terminal?

---

### Post by marc1uk on 2009-09-05
In other news, whenever I'm in CLI or at the recovery options menu, I get continual messages saying  
```
usb 1-8: reset high speed USB device using ehci_hcd and address 3
usb 1-8: reset high speed USB device using ehci_hcd and address 3
usb 1-8: reset high speed USB device using ehci_hcd and address 3
usb 1-8: reset high speed USB device using ehci_hcd and address 3
[sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
```interspersed with the occasional: 
```
end_request: I/O error, dev sdc, sector *** 
Buffer I/O error on device sdc, logical block ****
```That's even when I don't have the LiveCD in the tray.   Ho hum. Maybe this might trigger something someone's encountered before perhaps.

---

### Post by marc1uk on 2009-09-06
Well i tried another reinstall, but the same issue still happens. It does seem that if i leave the loading bar for long enough (about 10 minutes) it does finally load, and i can run terminal too. But, this isn't really practical.   I suspect a permissions issue, because of the read-only filesystem errors, and the partial success of mount -o remount,rw /. But I don't know enough to follow this up.   Any help appreciated.

---

### Post by ckonestroh on 2009-09-06
Wait, wait, wait....

Something doesn't fly with this setup....


Are these IDE drives or Sata drives...

If IDE drives 

1. are they on the same ribbon cable??
2. One is master other slave???? Jumpers
3. What is the bios saying???? Does the bios recognize both drives??
4. does the bios support this hard drive size?????


Sometimes with two drives on the same ribbon cable this causes a slow down... Not sure if this would cause a crash?????


This is not an Operating System problem???? 

please give the size of hard drive and type....


What type of computer is this model and brand?????

---

### Post by ckonestroh on 2009-09-06
wait, does this ram module get recognized???

Do you here any beeps at post????

What type of Nvidia card is this????

Starting to sound like a video card out of rage possibly ,but doesn't answer drive issue???????

---

### Post by marc1uk on 2009-09-06
Hurrah, some interest. :)  > **ckonestroh said:**
>  Are these IDE drives or Sata drives...
IDE drives, both. 

If IDE drives:
1. are they on the same ribbon cable??
Yep.

2. One is master other slave???? Jumpers
Jumper settings are fine, they're on master & slave, also tried swapping and using CSEL.

3. What is the bios saying???? Does the bios recognize both drives??
Yep, and they both appear fine in the OS too when I eventually boot. If I boot from normal mode then start X, I can mount them, although not if I boot from recovery mode.

4. does the bios support this hard drive size?????
Should do. The drive it came with was an 80GB Seagate. I had a working Ubuntu install on that before this. I then added a 160GB Maxtor. But as mentioned, the problem's persisting even when I revert back to just the Seagate. 

5. Sometimes with two drives on the same ribbon cable this causes a slow down... Not sure if this would cause a crash?????
Still happens with just the one drive.

6. This is not an Operating System problem????
Oh?

7. What type of computer is this model and brand?????wait, does this ram module get recognized???
The PC's a prebuilt Fujitsu Scaleo 600. The RAM modules get recognised by BIOS, and OS when I eventually boot.

8. Do you here any beeps at post????
No.

9. What type of Nvidia card is this????
BFG GeForce 6600GT. I've also tried reverting back to the old card, which worked in Ubuntu before I tried to update (an NVidia FX 5600XT) with no luck. The new gfx card is also from another machine which was working fine in Ubuntu, so both should be compatible.

10. Starting to sound like a video card out of rage possibly ,but doesn't answer drive issue???????
Out of range??  Thanks for the time, hopefully this info will help, although to me it all seems very inconclusive.

---

### Post by ckonestroh on 2009-09-06
Thanks for the info will get back to shortly....


I never heard of a Fujitso running in Linux.... I seen Fujitso Laptops having trouble with Linux not a desktop....

Well looks like you did your homework.... I going to punch around google for a minute to get an idea about this system... Should take no more then 30 minutes for an answer....


Be back...

Sorry I work nights so I was up all night running movies and talking tech will be up all night to night as well....

---

### Post by ckonestroh on 2009-09-06
Well I did research on this system...

Seems that this computer is well supported in Europe for Windows XP...

I seen it expressed this system works with Linux.... Since I live in the States I've seen this computer 2 or 3 times... 

We started to have problems with this system when we updated Windows XP to service package 2.... It gave us problems with Nortons server side Anti Virus... 


Being that this computer uses a ATA 100 drive... Was another sore spot in the IT field when they jumped from ATA 100 TO ATA 133... US makers were having trouble running both ATA 100 and ATA 133 on the same system. Microsoft resolved the problem 2 to 3 months later and was able to run both drives together....


Now linux had no problems recognizing either ATA 100 or ATA 133.... What I have seen in the linux world is some people with older hardware revert
 back to older linux versions...

I wondering were you running Ubuntu 9.04 or Ubuntu 8.10????

I would also suggest going with a different Linux distro..  In your case I've seen a lot of hits and misses with this system on OpenSuse, Mandravia and Ubuntu...

 
Of course I will get a lot of users in this forum saying... oh No i run the latest OS from Ubuntu with no problems.... 

Head over to linuxquestions.org.... you'll see this computer is posted in numerous posts and you'll find a great deal of users using other distro's on your hardware....

Most people in the States will not have this system so there is no way for me or most users to say for 100% on how to tackle this issue????



good luck....

---

### Post by marc1uk on 2009-09-07
> **ckonestroh said:**
> Well I did research on this system...

Seems that this computer is well supported in Europe for Windows XP...

I seen it expressed this system works with Linux.... Since I live in the States I've seen this computer 2 or 3 times... 

We started to have problems with this system when we updated Windows XP to service package 2.... It gave us problems with Nortons server side Anti Virus... 


Being that this computer uses a ATA 100 drive... Was another sore spot in the IT field when they jumped from ATA 100 TO ATA 133... US makers were having trouble running both ATA 100 and ATA 133 on the same system. Microsoft resolved the problem 2 to 3 months later and was able to run both drives together....


Now linux had no problems recognizing either ATA 100 or ATA 133.... What I have seen in the linux world is some people with older hardware revert
 back to older linux versions...

I wondering were you running Ubuntu 9.04 or Ubuntu 8.10????

I would also suggest going with a different Linux distro..  In your case I've seen a lot of hits and misses with this system on OpenSuse, Mandravia and Ubuntu...

 
Of course I will get a lot of users in this forum saying... oh No i run the latest OS from Ubuntu with no problems.... 

Head over to linuxquestions.org.... you'll see this computer is posted in numerous posts and you'll find a great deal of users using other distro's on your hardware....

Most people in the States will not have this system so there is no way for me or most users to say for 100% on how to tackle this issue????



good luck....

Thanks for coming back, and for doing that research. I'll hit up linuxquestions in a moment, and see what I can find there.
Tbh i wouldn't have expected a hardware issue, given that I had no issues installing Ubuntu on this PC originally, and the imported hardware also came from a box that was running Ubunutu; both 9.04. Still, maybe it's the combination, so I'll keep an open mind, of course. 

As for XP, I've left space for a dual boot, but haven't got round to giving that a go yet. One step at a time eh? I know what MS installs can be like... (half the reason I switched to linux). The PC originally had XP on it when I got it, though not sure what SP. Maybe if i do try to do a dual boot I'll try a streamlined pack with SP2/3 already on it, just in case. Won't worry about the Norton issue, I tend to use freeware antivirus' like Avast! anyway.

Trying another distro is a possibility, but as a linux newb I've had the most success with Ubuntu so far, very keen on the user friendliness, so I'd like to stick with it if i could. (So far I've tried this, Slackware and Fedora Core, and of course XP; 4 OS' is quite enough for me!)

For the moment, I've just been letting it take its sweet time and eventually it boots without any problems (it pauses at 'codec_read: codec 0 is not valid' for about 4 mins, but searches for that seem to be mostly concerned with sound problems.) In trying to pinpoint the problem I've installed Bootchart, so I'll post the results of that here in case it helps.

p.s. in case it matters, this'd be a european version yep, in the UK.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127697&stc=1&thumb=1&d=1252271261[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=127697&d=1252271261")

---

### Post by P4man on 2009-09-07
Thats a lot of errors and problem seemingly unrelated to each other for one machine. Some semi random thoughts:
- problem with the cd/dvd drive (firmware issue). could you try booting from an USB stick? Try a 9.04 stick while you're at it
- powersupply problem.  you added a drive, and upgraded the videocard.. perhaps the psu is no longer up to the task?
- IRQ conflict. Though rare, it still happens. Check your bios if you can change any settings related to IRQ assignments. And/or try disabling ACPI see if that resolves it.

---

### Post by marc1uk on 2009-09-07
> **P4man said:**
> Thats a lot of errors and problem seemingly unrelated to each other for one machine. Some semi random thoughts:
Story of my life with computers really.
> **P4man said:**
> 
- problem with the cd/dvd drive (firmware issue). could you try booting from an USB stick? Try a 9.04 stick while you're at it
- powersupply problem.  you added a drive, and upgraded the videocard.. perhaps the psu is no longer up to the task?
- IRQ conflict. Though rare, it still happens. Check your bios if you can change any settings related to IRQ assignments. And/or try disabling ACPI see if that resolves it.

Very random few ideas indeed. Take it the I/O buffer errors are the DVD firmware issue? I'll try making a USB key, though I haven't booted from one before, so will have to see how I can enable that in my BIOS. 
PSU IS very low power, i must admit, but I've tried removing the new components and no luck. It also all works when it boots eventually too, so I'd rather not have to fork out £70 odd on a new PSU just in case... =\ 
I shall check out IRQ and ACPI and get back. 
Edit: disabling ACPI as a boot option didn't work, and can't see any options in the BIOS relating to IRQ that might've been changed. 

Thanks for the tips, all leads are somewhere to look.  :)

---

### Post by marc1uk on 2009-09-08
'Fraid I'm just reporting back to say thanks to the guys who offered their time and help - the problem seems to have solved itself! Honestly, I don't know what to say. Kinda leaves a feeling of unfinished business, leaving the problem as a mystery, but ... all's well that ends well i guess? 
I needed to do some stuff on my old PC, so swapped all the new hardware back. Didn't touch the PC, left it off and uplugged the whole time, but upon swapping it all back again and booting up again, ... it fired up in seconds. Bizarre. 
I'll add a bootchart, just in case there's something in it that'll help shed any light if others with the same problem later. It certainly seems to show a lot more activity this time round, though I'm not familiar enough with the boot process to make any sense of it. 
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127917&stc=1&thumb=1&d=1252439090[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=127917&d=1252439090")

Thanks again to all those who offered help. It really is appreciated; I feel a little bad that I can't say it's what lead to the solution. Well, it stopped my formatting my drive and going back to Windows anyway. :) Gold stars all round for the effort. :KS:KS:KS:KS:KS

---

### Post by ckonestroh on 2009-09-08
Well,

After rereading this post .....  Came to conclusion I beat the ram was not seated correctly.....

Or the bios really wasn't recognizing hardware...


This known as a hiccup in computer world... it happens rare...

That is usually why I take my time when installing new equipment or upgrading... I usually let a machine sit for about 1 day make sure I secured all video cards, hard drives and ram modules... I double check all connections....


Usually in an upgrade I wouldn't install all items at one time... I would install hard drive and memory together... wait a couple hours check logs,bios, run hard drive checks and other utilities before proceeding with video card....


This was a great learning experience for you.... :)


Glad to see computer is running....



later


PS for future reference take a can air clean the inside before install... dust is a big problem with computers...

---

### Post by P4man on 2009-09-08
> **marc1uk said:**
> 
I needed to do some stuff on my old PC, so swapped all the new hardware back. Didn't touch the PC, left it off and uplugged the whole time, but upon swapping it all back again and booting up again, ... it fired up in seconds. Bizarre. 

I gues its good it works now, but I dont like problems that disappear without having actually solved them. They tend to come back :) I'd risk another guess by blaming a bad IDE cable?

---

### Post by marc1uk on 2009-09-09
> **ckonestroh said:**
> Well,

After rereading this post .....  Came to conclusion I beat the ram was not seated correctly.....

Or the bios really wasn't recognizing hardware...


This known as a hiccup in computer world... it happens rare...

That is usually why I take my time when installing new equipment or upgrading... I usually let a machine sit for about 1 day make sure I secured all video cards, hard drives and ram modules... I double check all connections....


Usually in an upgrade I wouldn't install all items at one time... I would install hard drive and memory together... wait a couple hours check logs,bios, run hard drive checks and other utilities before proceeding with video card....


This was a great learning experience for you.... :)


Glad to see computer is running....



later


PS for future reference take a can air clean the inside before install... dust is a big problem with computers...

H'mmm, it could've been, I've made that mistake before though (with disastrous consequences - it shorted out and destroyed the RAM. >_< Lucky it didn't kill the mobo too), so I'm wary of it. Having swapped components in and out trying to see what was the source of the problem, I'm not sure that'd have been it, but it's possible. Also always clean out any new PC when i get it. It's crazy how much dust gets in there huh? Amazing they still run. 

Still, it's helped me learn a little more about BIOS, hardware settings and bootup problems, so that's all good. Even passed on a few tips to other unsolved threads while i was searching, but I've still got a long way to go before I really know what I'm talking about. Much to learn...

---

### Post by marc1uk on 2009-09-09
> **P4man said:**
> I gues its good it works now, but I dont like problems that disappear without having actually solved them. They tend to come back :)  
DON'T TEMPT FATE! 
> **P4man said:**
> I'd risk another guess by blaming a bad IDE cable?
Possibly, possibly. Who can tell. Intermittent faults are a pain in the ***. If it comes back, *touch wood*, it'll be one of the first things I check.

---

### Post by ckonestroh on 2009-09-09
> **marc1uk said:**
> 
Still, it's helped me learn a little more about BIOS, hardware settings and bootup problems, so that's all good. Even passed on a few tips to other unsolved threads while i was searching, but I've still got a long way to go before I really know what I'm talking about. Much to learn...

After working on 2000+ computers there is not really much to learn about BIOS.... BIOS just identifies what devices or hardware are connected...  The BAD some BIOS'S suck.... 

The Rule of Thumb is--- usually the more your board costs the better the BIOS.... 

Funny I remember once playing with my home computer I done something stupid deleted a .dll file in windows 2000 pro it crashed the system.. So it was about 2 or 3 am got the idea of rewinding my BIOS system clock....  Funny the system clock controls the date, year and time of where it reads from the hard drive.. So the OS came back couldn't remember all the software I loaded so about every 2 or 3 weeks... I would get these programs to just magically popup... Cool no install, no reboot system, new wallpaper, files and folders just re-appearing ...  LOL



Well I hope your system will be fine!!!


later...

---

