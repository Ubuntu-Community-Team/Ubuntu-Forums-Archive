---
title: "I hope I haven't bricked it....."
date: 2011-10-23
forum: General Help
---

### Post by hazmatt86 on 2011-10-23
Hey, thanks for reading.
The problem I have arose when I hard shut down my netbook while it was updating (i had forgot what it was doing). After that, it seemed like the drivers for the keyboard and mouse on the netbook had been lost or something. I would get to the login screen and find that i couldnt use my mouse nor keyboard. What I did find though, was that i could plug in my wireless mouse and move it and click away, but I didnt have access to the admin account because I couldn't type in the password. Also, when I entered a regular user account, the drivers seemed missing for about everything else, like the wireless card, etc.
Thats all moot now, though, because after so much messing around with a mouse, I no longer get a GUI, but a screen that tells me some code and has evidently loaded a program called busybox built-in shell. Any tip you have would be appreciated. Please tell me I haven't lost it all..

---

### Post by finny388 on 2011-10-23
my approach would be to load a usb stick with ubuntu, boot from usb, back up your files, then do a fresh install.

that's just me, others may have suggestions for salvaging the existing installation

good luck

---

### Post by hazmatt86 on 2011-10-23
> **finny388 said:**
> my approach would be to load a usb stick with ubuntu, boot from usb, back up your files, then do a fresh install.

that's just me, others may have suggestions for salvaging the existing installation

good luck
Right, I guess I should have explained that too. I have tried doing a fresh install of both the netbook remix and 11.10, but for some reason, it never boots from the flash drive install. I have changed the boot order in the bios. Also, when I do try to boot from a usb, it takes me to a screen with a colorful Intel logo and a report on what BIos version i'm running. Thanks!

Also, I'm not too concerned about whats on there, if it comes down to losing any info, thats fine, I would just rather not have a large purple paper weight hanging around.

---

### Post by Gawains Green Knight on 2011-10-23
It won't boot from USB? How did you get Ubuntu on there in the first place?

---

### Post by hazmatt86 on 2011-10-23
It booted from the USB fine the when I first put it on there, Only after I screwed it up did it stop booting from the USB.

---

### Post by OneXero on 2011-10-23
> **hazmatt86 said:**
> It booted from the USB fine the when I first put it on there, Only after I screwed it up did it stop booting from the USB.

Have you tried going into the bios menu at the start and setting it to default configuration (commands depend on your bios I think but F10 on mine sets it to default config) ? You might also try using a windows recovery USB (sometimes that would boot for me instead of a linux boot disk) and then format using the windows command line options.

I had a pretty wacky thing going on for a while when I messed up my partition table! Took me forever to repair it.

Do you have a USB optical drive? You could try booting from that with a boot disc.

Have you tried a linux recovery USB? (not just an install)

---

### Post by Rasa1111 on 2011-10-23
Dang, Sorry to hear it.

Probably not bricked for good..
Just have to figure out where the problem is.

I wonder if you've tried removing all power sources from it before booting it?
Unplug it, and remove the battery.
Leave it that way for 15-20 seconds, Then put it back together, plug'er in, (with live USB inserted)
and boot it up.

It may do nothing..
But a handful of times I have found when I was having different booting issues,
Doing what I suggested would fix it every time. lol
It was suggested to me by another member here, and I thought. 'wth is that gonna do?"
but it really helped. Not sure why. But it did.

Hopefully it works for you!
Im not counting on it, but its worth a shot?

There are a lot of very knowledgeable people here though, i'm sure someone can help you get it figured out.   Good luck.

---

### Post by hazmatt86 on 2011-10-23
> **OneXero said:**
> Have you tried going into the bios menu at the start and setting it to default configuration (commands depend on your bios I think but F10 on mine sets it to default config) ? You might also try using a windows recovery USB (sometimes that would boot for me instead of a linux boot disk) and then format using the windows command line options.

It's all set to defaults, 'cept for the boot order. I pressed the default key any way (for me F9), then restarted, got the same screen about the program it had loaded.


> Do you have a USB optical drive? You could try booting from that with a boot disc.

Have you tried a linux recovery USB? (not just an install)This one doesn't have an optical drive, which makes things just that much more tedious, in my opinion. I haven't tried either of those recovery USB's you're talking about, any good tutorials online?

---

### Post by hazmatt86 on 2011-10-23
> **Rasa1111 said:**
> 
I wonder if you've tried removing all power sources from it before booting it?
Unplug it, and remove the battery.
Leave it that way for 15-20 seconds, Then put it back together, plug'er in, (with live USB inserted)
and boot it up.

Sadly, not the quick fix. Thanks for all the help,guys, keep it coming!

---

### Post by OneXero on 2011-10-23
> **hazmatt86 said:**
> It's all set to defaults, 'cept for the boot order. I pressed the default key any way (for me F9), then restarted, got the same screen about the program it had loaded.


This one doesn't have an optical drive, which makes things just that much more tedious, in my opinion. I haven't tried either of those recovery USB's you're talking about, any good tutorials online?

Well, I think you need to have a legitimate copy of windows to get a recovery disk. I think there are some sources for just the recovery options. Then you have to use a program to make a USB bootable out of it, like pendrive. I didn't use a tutorial, so I don't know. Just figured out what I needed to do and looked up the commands. For the windows recovery, you just bypass the part about selecting a windows installation and use diskpart to format the drives. 

I think if you google linux recovery disk: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Something like that may help.

What I was saying about the USB optical is there are some optical drives that plug in via the usb for laptops like yours and mine that have no CD/DVD/BR drive.

Another option could be removing the hard drive completely, booting up with another computer with it attached and dealing with the hard disk that way....

You could also try to make a windows install usb and see if it boots...I had great success using linux to fix windows problems and windows recovery to fix linux problems. Lol.

---

### Post by hazmatt86 on 2011-10-23
> **OneXero said:**
> Well, I think you need to have a legitimate copy of windows to get a recovery disk. I think there are some sources for just the recovery options. Then you have to use a program to make a USB bootable out of it, like pendrive. I didn't use a tutorial, so I don't know. Just figured out what I needed to do and looked up the commands. For the windows recovery, you just bypass the part about selecting a windows installation and use diskpart to format the drives. 
I'm working off of an illegitimate copy of windows right now.... I'll google those recovery sources.

> I think if you google linux recovery disk: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Something like that may help.

What I was saying about the USB optical is there are some optical drives that plug in via the usb for laptops like yours and mine that have no CD/DVD/BR drive.I'm working on the gparted suggestion right now, will post results. I was dense on the optical drive thing, but, nope, wouldn't have one of those either.

Gparted wouldn't boot either, just goes to the flashy Intel screen, as mentioned above.

---

### Post by OneXero on 2011-10-23
> **hazmatt86 said:**
> I'm working off of an illegitimate copy of windows right now.... I'll google those recovery sources.

I'm working on the gparted suggestion right now, will post results. I was dense on the optical drive thing, but, nope, wouldn't have one of those either.

Maybe being a little dense on the legitimate part too. I just don't recommend pirated software. On forums.

---

### Post by OneXero on 2011-10-23
What laptop is it, anyways? (Model number, brand...etc)

---

### Post by hazmatt86 on 2011-10-23
Its an Acer Aspire 1, Model No. NAV50
Is there anything I can do BIOS-wise, such as flashing it, that might reset anything?
Forgive me if I'm wrong, I'm just a beginner at this whole thing.

---

### Post by oldtimer7777 on 2011-10-23
> **hazmatt86 said:**
> Its an Acer Aspire 1, Model No. NAV50
Is there anything I can do BIOS-wise, such as flashing it, that might reset anything?
Forgive me if I'm wrong, I'm just a beginner at this whole thing.

You only need to apply BIOS updates if they are warranted by the manufacturer's web site.

Have you contacted tech support for the make and model laptop/netbook yet?  Most web sites allow you to redownload drivers, and occasionally they will list BIOS updates that are available. It is always a good idea to check for BIOS updates every few months after buying a new computer.

---

### Post by OneXero on 2011-10-23
> **hazmatt86 said:**
> Its an Acer Aspire 1, Model No. NAV50
Is there anything I can do BIOS-wise, such as flashing it, that might reset anything?
Forgive me if I'm wrong, I'm just a beginner at this whole thing.

I am a beginner too, very much so. I just have a bit of experience in royally messing up my computer messing with linux (because of the beginner thing).

I don't know about the bios thing. 

I found some youtube video of a smart kid talking about the aspire one bios if you want to give it a try...[http://www.youtube.com/watch?v=l6GRhsvP-og](http://www.youtube.com/watch?v=l6GRhsvP-og)

---

### Post by ironclaw on 2011-10-23
> **hazmatt86 said:**
> It's all set to defaults, 'cept for the boot order. I pressed the default key any way (for me F9), then restarted, got the same screen about the program it had loaded

Can you manually rearrange the boot order so that the USB flash drive has the highest priority? On many BIOSes, resetting to defaults does not include resetting the boot order.

> **hazmatt86 said:**
> Thats all moot now, though, because after so much messing around with a mouse, I no longer get a GUI, but a screen that tells me some code and has evidently loaded a program called busybox built-in shell. Any tip you have would be appreciated. Please tell me I haven't lost it all..
GRUB falls back to a BusyBox shell when it can't boot. This has nothing to do with bricking your netbook.

---

### Post by hazmatt86 on 2011-10-23
> **ironclaw said:**
> Can you manually rearrange the boot order so that the USB flash drive has the highest priority? On many BIOSes, resetting to defaults does not include resetting the boot order.


GRUB falls back to a BusyBox shell when it can't boot. This has nothing to do with bricking your netbook.
I have been setting the flash drive to the first boot position. I've also been moving the hard drive to the bottom position. When the flash drive is in, loaded with either Gparted, or Ubuntu, it goes to the colorful Intel screen,.. and thats it. 
When the flash drive is out, it first tries the whole network boot, because that has that option, then tries to boot ubuntu, but of course, ends on the busybox program.

You've given me a ray of hope.

I'm also backing down on the whole BIOS area, acer seems to have discontinued support for this laptop, and I can't find any new BIOS software for that model, I'm afraid to use any other model's BIOS.

---

### Post by oldtimer7777 on 2011-10-23
> **hazmatt86 said:**
> I have been setting the flash drive to the first boot position. I've also been moving the hard drive to the bottom position. When the flash drive is in, loaded with either Gparted, or Ubuntu, it goes to the colorful Intel screen,.. and thats it. 
When the flash drive is out, it first tries the whole network boot, because that has that option, then tries to boot ubuntu, but of course, ends on the busybox program.

You've given me a ray of hope.

I'm also backing down on the whole BIOS area, acer seems to have discontinued support for this laptop, and I can't find any new BIOS software for that model, I'm afraid to use any other model's BIOS.


Acer usually supports BIOS updates for 2 years...  That means whatever you are running is pretty ancient by now. Ubuntu should have the drivers for it in the Kernel by now, I would imagine..  Sounds like a hardware issue to me.  Maybe because it is old. What was the previous system you had installed on that machine?

---

### Post by ironclaw on 2011-10-23
> **hazmatt86 said:**
> I have been setting the flash drive to the first boot position. I've also been moving the hard drive to the bottom position. When the flash drive is in, loaded with either Gparted, or Ubuntu, it goes to the colorful Intel screen,.. and thats it.

For some reason, it is failing to boot from the USB flash drive. Can you try using a different flash drive?

I would not recommend updating the BIOS right now.

---

### Post by hazmatt86 on 2011-10-23
> **oldtimer7777 said:**
> Acer usually supports BIOS updates for 2 years...  That means whatever you are running is pretty ancient by now. Ubuntu should have the drivers for it in the Kernel by now, I would imagine..  Sounds like a hardware issue to me.  Maybe because it is old. What was the previous system you had installed on that machine?
It might be exactly 2 years old. I, personally, have only had it a little over a year. It was Windows 7 32 bit. Ran that and Ubuntu great, never had any performance problems out of it. If I just hadn't shut it down while updating, I'd say it'd still be running fine today.

---

### Post by hazmatt86 on 2011-10-23
> **ironclaw said:**
> For some reason, it is failing to boot from the USB flash drive. Can you try using a different flash drive?


Used a separate flash drive loaded with 11.10, same results as with the first one.

---

### Post by ironclaw on 2011-10-23
> **hazmatt86 said:**
> Used a separate flash drive loaded with 11.10, same results as with the first one.

Can you upload an image of the Intel screen that appears?

Also, you might want to try booting the flash drives on another laptop or desktop to make sure that they work.

---

### Post by hazmatt86 on 2011-10-23
[IMG]http://www.flickr.com/photos/69015556@N04/6275405372/[/IMG]> **ironclaw said:**
> Can you upload an image of the Intel screen that appears?

Also, you might want to try booting the flash drives on another laptop or desktop to make sure that they work.
Yeah, but it'll have to be a picture of the screen, cheesy right? Also, flickr was the first photo sharing site I could think of.

[http://www.flickr.com/photos/69015556@N04/6275405372/](http://www.flickr.com/photos/69015556@N04/6275405372/)

Oh, and I checked the drives on my other laptop, both working fine, almost installed Ubuntu again.

---

### Post by OneXero on 2011-10-24
Do you know anything about laptop hardware? Like are you knowledgeable enough to remove your laptop hard drive without destroying things? You could try swapping it into the other laptop. Then you could definitely check if it was a BIOS problem.

---

### Post by ironclaw on 2011-10-24
> **hazmatt86 said:**
> Yeah, but it'll have to be a picture of the screen, cheesy right? Also, flickr was the first photo sharing site I could think of.

[http://www.flickr.com/photos/69015556@N04/6275405372/](http://www.flickr.com/photos/69015556@N04/6275405372/)

Oh, and I checked the drives on my other laptop, both working fine, almost installed Ubuntu again.

I'm stumped; I don't know why the USB flash drives are not booting on the netbook. You've probably already tried using different USB slots on the netbook? If you have a USB optical drive or an external hard drive, you can try booting from those.

As a last resort, you can transfer the hard drive in the netbook to another laptop, then boot from a USB flash drive, and create a small partition in the netbook's hard drive to install a live Ubuntu system there (by the same method that you are creating the live USBs). Afterwards, put the hard drive back into the netbook, and it should boot successfully into a live system. Then you can install Ubuntu as you normally would, with the caveat that you cannot overwrite or move the partition where it is booting from (which is why you should make this small). However, you can always wipe this partition after you have Ubuntu installed.

What I've outlined above is rather annoying to carry out, though, so you probably want to look out for other suggestions first.

---

### Post by oldtimer7777 on 2011-10-24
> **OneXero said:**
> Do you know anything about laptop hardware? Like are you knowledgeable enough to remove your laptop hard drive without destroying things? You could try swapping it into the other laptop. Then you could definitely check if it was a BIOS problem.

Hopefully you have access to another computer where you can create a fresh stick of Ubuntu live to boot from.  Perhaps there is something wrong with your USB stick? Did you power off your system while the live USB stick was booted and running Ubuntu? That will sometimes prevent your USB stick from functioning anymore after a hard power cycle.

---

### Post by hazmatt86 on 2011-10-24
> **OneXero said:**
> Do you know anything about laptop hardware? Like are you knowledgeable enough to remove your laptop hard drive without destroying things? You could try swapping it into the other laptop. Then you could definitely check if it was a BIOS problem.
I know my way around the hardware of the other laptop, I'm sure I could swap out the drives, but is there software I'd have to be aware of when switching those drives? Isn't there a bit of drivers specific to certain laptops with certain Hard drives? Like would  the Toshiba drive in the Netbook still be compatible with the other laptop?
Sorry for all these questions, I just wouldn't wanna have two laptops down.

---

### Post by oldtimer7777 on 2011-10-24
> **hazmatt86 said:**
> I know my way around the hardware of the other laptop, I'm sure I could swap out the drives, but is there software I'd have to be aware of when switching those drives? Isn't there a bit of drivers specific to certain laptops with certain Hard drives? Like would  the Toshiba drive in the Netbook still be compatible with the other laptop?
Sorry for all these questions, I just wouldn't wanna have two laptops down.

You can purchase a IDE/SATA to USB connector from most computer stores. Fry's Electronics is a place that has them for around 20 US Dollars.  You just remove the hard drive. Hook the IDE/SATA and power cable to the USB adapter and you can boot from that USB on another computer.

Perhaps there is something only wrong with your Flash Drive? I would try another Flash Drive (a new one) first before taking apart a working system.

---

### Post by hazmatt86 on 2011-10-24
> **oldtimer7777 said:**
> Hopefully you have access to another computer where you can create a fresh stick of Ubuntu live to boot from.  Perhaps there is something wrong with your USB stick? Did you power off your system while the live USB stick was booted and running Ubuntu? That will sometimes prevent your USB stick from functioning anymore after a hard power cycle.
Both were functioning earlier, when Ironclaw asked me to try and boot them from another laptop. Ubuntu loaded and was ready to install. 
[QUOTE=ironclaw] As a last resort, you can transfer the hard drive in the netbook to  another laptop, then boot from a USB flash drive, and create a small  partition in the netbook's hard drive to install a live Ubuntu system  there (by the same method that you are creating the live USBs).  Afterwards, put the hard drive back into the netbook, and it should boot  successfully into a live system. Then you can install Ubuntu as you  normally would, with the caveat that you cannot overwrite or move the  partition where it is booting from (which is why you should make this  small). However, you can always wipe this partition after you have  Ubuntu installed.[/QUOTE]
Sounds like what I may end up doing, as long nothing else stops it.

---

### Post by OneXero on 2011-10-24
> **hazmatt86 said:**
> I know my way around the hardware of the other laptop, I'm sure I could swap out the drives, but is there software I'd have to be aware of when switching those drives? Isn't there a bit of drivers specific to certain laptops with certain Hard drives? Like would  the Toshiba drive in the Netbook still be compatible with the other laptop?
Sorry for all these questions, I just wouldn't wanna have two laptops down.

Well, if you used a linux boot disk wouldn't the kernel have the drivers? I know I've completely wiped my drive and restarted with a linux disc, in that case - where were the drivers? (honest question! I could be confused!)

---

### Post by hazmatt86 on 2011-10-24
> **OneXero said:**
> Well, if you used a linux boot disk wouldn't the kernel have the drivers? I know I've completely wiped my drive and restarted with a linux disc, in that case - where were the drivers? (honest question! I could be confused!)
Drivers probably aren't the word for it. I was speaking from an experience I had helping my roommate fix his girlfriends laptop. Part of that was switching his and her's hard drives. She was using an acer and when he popped in her hard drive, It wouldnt let him boot anything and had an acer logo with a description of the problem. I understand that could have been laptop specific, but I still wanna make sure things go right if/when I switch drives.

---

### Post by ironclaw on 2011-10-24
I think there may be some confusion in this thread. Hazmatt86's problem is unlikely to be related to a corrupted BIOS or to drivers. The BIOS is probably undamaged - it is very difficult to accidentally corrupt the BIOS by power cycling, unless there are serious implementation issues in the firmware. Drivers are not important here because Hazmatt86 is not able to boot into an OS - drivers operate on the OS level.

However, the problem *is* related to the BIOS in the sense that USB flash drives are not booting successfully.


> **hazmatt86 said:**
> I know my way around the hardware of the other laptop, I'm sure I could swap out the drives, but is there software I'd have to be aware of when switching those drives? Isn't there a bit of drivers specific to certain laptops with certain Hard drives? Like would  the Toshiba drive in the Netbook still be compatible with the other laptop?
Sorry for all these questions, I just wouldn't wanna have two laptops down.

As long as the form factors (i.e., dimensions) and the interfaces of the hard drives are the same, you can switch them successfully. Most consumer laptops in the past few years have 2.5 inch SATA hard drives. However, you will generally not be able to boot from installed OSes after a switch, because they will load drivers that are intended for the original laptop.

---

### Post by OneXero on 2011-10-24
> **ironclaw said:**
> I think there may be some confusion in this thread. Hazmatt86's problem is unlikely to be related to a corrupted BIOS or to drivers. The BIOS is probably undamaged - it is very difficult to accidentally corrupt the BIOS by power cycling, unless there are serious implementation issues in the firmware. Drivers are not important here because Hazmatt86 is not able to boot into an OS - drivers operate on the OS level.

However, the problem *is* related to the BIOS in the sense that USB flash drives are not booting successfully.




As long as the form factors (i.e., dimensions) and the interfaces of the hard drives are the same, you can switch them successfully. Most consumer laptops in the past few years have 2.5 inch SATA hard drives. However, you will generally not be able to boot from installed OSes after a switch, because they will load drivers that are intended for the original laptop.

I think I was trying to say something like this in a non-assuming way. I am still new to the technical aspects of computing, but I have a lot of background in logical troubleshooting. 

It's interesting. I had a similar experience with my laptop, and what ended up fixing it was reinstalling grub (one time) and the other manually repairing the MBR for windows 7. It wasn't recognizing any kind of boots, period! And it wasn't related to the bios. So it could be what *I assume* was latent files being loaded and used incorrectly, regardless of it actually booting into the operating system.

---

### Post by egalvan on 2011-10-24
> **ironclaw said:**
> However, [B]you will generally not be able to boot from installed OSes after a switch, 
because they will load drivers that are intended for the original laptop[/B].

True for Microsoft, as it locks the install to the hardware,
but NOT true for Linux.
Installing Linux on one machine, then moving the drive to another, 
is a common way to solve boot problems, such as lack of  optical drives, no USB boot, etc.

---

### Post by Rasa1111 on 2011-10-24
Wonder if this would help? 
[B] [Acer Aspire One BIOS Recovery]("http://www.qrpcw.com/2009/01/acer-aspire-one-bios-recovery.html")

[/B]Found it through this link..[http://en.kioskea.net/forum/affich-46702-aspire-one-wont-boot-even-the-bios-dont-show](http://en.kioskea.net/forum/affich-46702-aspire-one-wont-boot-even-the-bios-dont-show)

---

### Post by hazmatt86 on 2011-10-24
Thanks for everything so far, guys. I will work on switching the hard drives, but results may be late, (work trumps fixing a laptop for me right now).

---

### Post by hazmatt86 on 2011-10-26
Sorry gents, for the late reply, but it was a successful hard drive switch-a-roo. After I replaced the hard drive, it booted up 11.10, and is now updating. Keyboard and mouse are working perfectly.

It still worries me though, that it won't load anything from USB. If I were to royally screw it over again, I guess I'll know what I have to do.

Thanks everybody for the help! That had plagued me for over 3 months, I'm glad its over.

---

### Post by Rasa1111 on 2011-10-26
good news!
glad to hear it, man.

I wonder if once you're all installed and updated..
if USB will start working again?

I had to go do a reinstall on my dads shop PC about a month ago, (ubuntu 10.10)
as no USB devices were being recognized/opened when plugged in.

Couldnt figure it out, So did a reinstall,
and once reinstalled.. USB and everything worked like new again. 

Hope that same happens for you! 

good luck man. :)

---

