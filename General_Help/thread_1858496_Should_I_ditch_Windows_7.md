---
title: "Should I ditch Windows 7"
date: 2011-10-12
forum: General Help
---

### Post by SneakPeak on 2011-10-12
Hi,

I have been an Ubuntu user for several years.  I basically went to Ubuntu first time round because I didn't have a legal version of Windows.  Over time I have upgraded my machine and my version of Ubuntu but I have never bought a new machine that ships with an OS.  Yesterday I bought a new Lenovo B570 that came with Windows 7 Professional.  I really like Ubuntu but I can't decide if I should give up my Windows 7.  Some considerations:

1. My windows 7 is 64bit.  If I go to Ubuntu 64bit I am concerned that I will be limited in respect of the software I will be able to install.  Is most of the Ubuntu software available in 64bit?  (I most often use Gimp, Audacity, Rythmbox, Thunderbird, Firefox and Chrome)

2. If I go to Ubuntu 32bit am I missing out on better performance that I would have got on Windows 7 64bit? 

3. If I go Ubuntu 32bit can I install windows 7 64bit in a VirtualBox on the windows 32bit installation? (I'd have to do this from recovery disks created from the laptop because the machine shipped with Windows pre installed with no disks)

4. I need windows for a few things.  Most importantly Garmin Connect which is not going to support Linux anytime soon.  I don't like a dualboot setup.  I currently have Windows XP in a Virtualbox on my desktop PC and that works quite nicely for me.  If I go Ubuntu I'd like to run Windows 7 in a virtual box so I can access both without a reboot.

I like Ubuntu but I don't subscribe to the view that Windows is rubbish.  The virus threat is a pain in the backside but installing hardware and software is often much easier in Windows.  Also almost all vendors support Windows but not necessarily Linux.  Linux feels more secure and more clever in a way and some of the software is great.  I love Gimp and Audacity and it seems to be something of a hack to get these to run under windows.

I'd appreciate any views - pointers.

Hope I am not posting this in the wrong forum.

Thanks

Cheers

Sneaks.

---

### Post by matt_symes on 2011-10-12
Hi

Personally i would dual boot. After all you have paid for windows and, personally, i think Windows 7 is pretty good.

Clone your hard drive using Clonezilla or some such before you do anything (hard drive and not just partition). That way you can always roll back if things go wrong.

Go for 64 bit Ubuntu if you do decide you want to use it.

Kind regards

---

### Post by SneakPeak on 2011-10-12
Thanks for the reply.

I am not a big fan of dual boot.  I don't like the idea of having to shutdown and restart a different operating system everytime you want to do something that doesn't work in your current one. I like the VirtualBox setup.  It means you have access to both OS's at the same time.  I just wonder how a Windows 7 64 bit will work inside an Ubuntu 32 bit system? 

Cheers

Sneaks

---

### Post by cryptotheslow on 2011-10-12
If you don't like dual-boot per se. Then how about just running Ubuntu in a virtual box within Win7?

That would neatly avoid any possible support nightmares e.g. the typical "please reinstall the original OS sir" helpdesk approachs most manufacturer helpdesks seem to like.

---

### Post by Vaphell on 2011-10-12
you already paid for win7 license, so why not have that native win7 around just in case virtualization is not enough?
have ubuntu and win7 in dual boot.
Yes, you can use VM to use windows inside linux but if you need robust 3d acceleration and such, there is nothing better that running windows on the metal.
Just shrink win7 to let's say 100GB so you can use all those incompatible devices and install all that non-linux software. Ok, you may not need it every day but if there is an emergency that you need something working ASAP with a deadline set to yesterday, i don't think you would be happy to jump through the hoops to force troublesome piece of hardware/software to work in linux/virtual machine.

64bit host can run both 64 and 32bit guests, but not the other way around.

64bit ubuntu is in a very good shape, pretty much everything works perfectly, i don't remember having any trouble caused by bitness of my system. The only thing worth mentioning was manual installation of 64bit flash - but it's easy, you can automate it (there is PPA and firefox plugin for that) and on top of that Oneiric Ocelot has 64bit in standard repositories since Adobe released official 64bit version of flash 11.

---

### Post by airper on 2011-10-12
Why not just dual boot for best of both worlds.

I recently bought a new Toshiba Satellite R830, with W7 pre-installed. In the past I have just wiped the Hard Drive installed Ubuntu, but on this occasion, I thought I'd try a dual boot setup.

Very easy to do, just follow the prompts for a dual installation,  it works excellently.

Grub gives you a boot menu, by default it boots into Ubuntu after a 10 sec delay, or hit return to start the boot immediately, if you select W7 and hit return then you go to a standard W7 boot up. And this is all working fine with 64 bit installations of both W7 and Ubuntu.

I don't use W7 very often, but very very occasionally need to look at a file I can't in Ubuntu, in which case it saves messing about on another machine.

All the applications you mentioned are working fine on my Tosh with the 64 bit version of 11.04.

Hope this helps.

---

### Post by SneakPeak on 2011-10-12
Thanks for all the replies.  Any reason why Ubuntu's download page would have recommended I download the 32bit version and not the 64bit?

---

### Post by snowpine on 2011-10-12
I agree with the recommendations above for dual booting Ubuntu 64-bit and Windows 7. 

Alternately you can run Ubuntu in VirtualBox inside of Windows 7, if you don't like the dual-boot concept.

I am fairly certain your OEM Windows 7 license is not valid for a VirtualBox install; Microsoft can tell you for sure obviously.

---

### Post by Vaphell on 2011-10-12
2 reasons:

- 32bit version will work on both 32 and 64bit machines so if you lack detailed knowledge about your computer, 32bit is a choice guaranteed to work. Also there are many machines that don't have much RAM (big part of 64bit advantage is hassle-free support for greater address space). 4GB is the threshold from the memory point of view so if you have 64bit capable processor but 1GB ram, you will not benefit from 64bit system.

- 3rd party software that doesn't have true 64bit version, or only has some beta (like flash up to recently). Linux community can't do anything about that software that your average user considers crucial. For example 64bit ubuntu by default used 32bit flash wrapped up for 64bit use, but the wrapper added a good deal of instability. Now the problem is gone.

---

### Post by Mark Phelps on 2011-10-12
One wrinkle no one mentioned ...

To run Win7 virtually inside Ubuntu, you will have to completely reinstall Win7 from scratch -- and since your PC came with it preinstalled, it's most likely that you do NOT have the install media to do that.

If you do have a Win7 CD, it's likely a Restore CD and can not be used to install Win7, only to Restore the PC to its original state.

Also, if you can lay your hands on a Win7 DVD, when you reinstall it inside VB, you will have to deal with activation, and you will have to reinstall ALL your apps -- again.

So, basically, setting up dual boot with Ubuntu saves you all of this grief associated with reinstalling Win7, reactivating it, and reinstalling all your Windows apps.

---

### Post by SneakPeak on 2011-10-12
Thanks for all the advice.  I think I'll go dual boot.

---

### Post by JC Cheloven on 2011-10-12
Just to answer the OP:

> **SneakPeak said:**
> 
1. My windows 7 is 64bit.  If I go to Ubuntu 64bit I am concerned that I will be limited in respect of the software I will be able to install.  Is most of the Ubuntu software available in 64bit?  (I most often use Gimp, Audacity, Rythmbox, Thunderbird, Firefox and Chrome)
You'll find in the 64bit-repos all this software. No problem.
> 
2. If I go to Ubuntu 32bit am I missing out on better performance that I would have got on Windows 7 64bit? 
Performance is better in 64 bits only for certain specialized tasks (video editing and such). If you're not in that, you can't tell any difference.

> 
3. (...)

4. (...)
I think you have already solved these points. Just my aditional vote for dual boot, despite your initial disliking. I also thing it's the best solution for you. 

> I like Ubuntu but I don't subscribe to the view that Windows is rubbish.  The virus threat is a pain in the backside but installing hardware and software is often much easier in Windows.  Also almost all vendors support Windows but not necessarily Linux.  Linux feels more secure and more clever in a way and some of the software is great.  I love Gimp and Audacity and it seems to be something of a hack to get these to run under windows. 

Agreed. I'm still wondering why people didn't massively ran away from windows by the times of vista, but with w7 things have changed, I mean from a functional point of view. I still prefer gnu-linux though. 

Best
JC

---

### Post by rjs987 on 2011-10-12
I work desktop support for the state and we are "officially" a MS shop standardizing now on W7. However I thought I would add a few reflections on the VBox option since that is what I personally do at work. I have Ubuntu installed on my machine and use it for some troubleshooting and file recovery/compatibility conversions that cannot be done in W7. For a time I was running Linux as host with a W7 vm in Virtual Box. Lately I've been running things the other way around with W7 as host and Linux in the vm in Virtual Box (due to certain individuals who are brainwashed in favor of MS). Anyway, I found that I had almost the same performance with W7 in a vm on Linux as if it was the only OS on the disk. On the other hand, Linux has definite performance lag issues when run in a vm on W7, or should I say any OS in a vm does. I've determined that W7 does not handle virtual machines as well as Linux. One reason I have this opinion is that I also ran a W7 vm on W7 with the same performance lag issues. At home I also need a Windows presence for that one utility from Garmin (if not for that I would totally abandon windows at home). I very much prefer to run windows as a vm on Linux.

Having said that, I also agree with what Mark Phelps said. It is very unlikely that you will be able to install W7 in a vm from your recovery DVDs that you made since most vendors "fix" those installs to require them to see the hardware. This hardware check cannot make it through the vm so you are most likely stuck with running dual-boot or a Linux vm with that media. The performance lag is really not too bad for me since I am forced to work in Windows only programs that we have for support for most things at work, but I would be able to tolerate it at home since I am in Linux 99.999% of the time (only need to update my Garmin device once per quarter so only run the vm every 3 months for about an hour or two- MS updates and all).

---

### Post by wildmanne39 on 2011-10-12
Hi, I have a dual boot but it has been a year since I booted windows, I am thinking about getting rid of it completely.

I also have windows running in virtualbox and it works good but I do not play any games. Draw back every time there is a little change in virtualbox I have to reactivate windows 7 again.

I have only booted it a few times in the last year.

I run ubuntu 64 bit I have for about five years now, and there is not a problem with having enough applications to run on it.

As Mark Phelps stated it is getting harder to get a copy of windows on a disk that comes with a new computer and the agreement does not allow windows to be ran in a vm if I remember correctly. 
Thank you

---

### Post by SneakPeak on 2011-10-13
Thanks for your views RJS987.  I use Garmin connect virtually everyday because I have one of their fitness devices and I train 6 days a week.  Currently I wake up at 4:20am boot up my Linux box.  Start VirtualBox and go out for a run.  When I come back my Garmin data uploads automatically and once its done I kill the VirtualBox.  That is basically all I use Windows for.  It seems trivial but to shutdown one operating system and boot another and then shutdown again and boot the first sytem again just seems like a pain in the neck.  Anyway. I think people are correct in saying I am going to battle to install from a recovery disk so I'll just go the route of dual boot.

---

### Post by Mark Phelps on 2011-10-13
> **wildmanne39 said:**
> ... Draw back every time there is a little change in virtualbox I have to reactivate windows 7 again.

And, one of these days, the automatic reactivation that works now could possibly NOT work anymore.

And yes, I KNOW that a retail copy is supposed to be allowed to be reactivated an unlimited number of times ... but on the Windows 7 forum, we see post from folks where reactivation has failed.  Seems that MS has stepped up their "anti-piracy" efforts by establishing arbitrary limits on the number of times a copy can be reactivated within a limited timeframe.  Unfortunately, true to form, they won't tell us the limit or the timeframe.

We are left to "discover" this when our version suddenly won't reactivate anymore.

---

### Post by wildmanne39 on 2011-10-13
Hi,
> And, one of these days, the automatic reactivation that works now could possibly NOT work anymore.

I suspected this could happen but it has not happened yet probably because I almost never boot windows, if and when it does I will be done with windows for good.

I do not have any programs that I need it for anymore, I was using magic jack and I do not use it anymore.

I used windows for netflix but now I use a roku box.
Thank you

---

### Post by bobsageek on 2011-10-13
After dual booting for years some of my boxes for years, when I ordered my new Dell 17R I planned to dump Windows as soon as I was sure the laptop was in full working order. So after a few hours of tinkering I ran the recovery disk utility to create a backup install of Win 7(should I decide to sell this laptop sooner than later) and installed 11.04 and haven't looked back. Outside of retail games there really isn't any piece of software I require that I cannot find an equal to on Linux. Of course your needs may vary, but Linux (and specifically Ubuntu) has matured so much as a desktop it's not really a stretch. 

Plus I love not dealing with licensing issues, DRM, etc...:KS

---

### Post by dave2001 on 2011-10-13
> **Mark Phelps said:**
> One wrinkle no one mentioned ...

To run Win7 virtually inside Ubuntu, you will have to completely reinstall Win7 from scratch -- and since your PC came with it preinstalled, it's most likely that you do NOT have the install media to do that.




While this is true, something many people don't realize is that the CONTENTS of the install disc is often somewhere on their hard drive. You can take these files and create an installation disc that works just as well as one you would pay microsoft for (yes they charge for them, even if you didn't receive one originally). I have done this before and can vouch for it's functionality. The trick is to find where the files have been placed, and get them into a usable form. I forget the exact steps, but it's nothing too complicated. I'm sure you can locate a tutorial online without too much trouble. That's how I did it.

---

### Post by alphaamanitin on 2011-10-13
You can find legal versions of windows 7 operating disks on the pirate bay.  I say legal because these are not cracked and you have to have your license key to install.  Keep in mind that you have an OEM install and so you need an OEM version of the operating system install dvd.

AlphaA

---

### Post by egkeat on 2011-10-13
No. I'm thankful to have a dual boot after what happened to me today in 11.10. You have to know more than a few things before attempting to use Ubuntu on a regular basis. Learn Ubuntu-Linux well first, then dump Windows. Otherwise, keep both.

---

### Post by viperdvman on 2011-10-13
I have a netbook that came with Windows 7 Starter pre-installed. I am dual-booting my Ubuntu 11.04 alongside Win7. What I did was shrink the Data partition (the easier one to do at the time) and installed Ubuntu to it. And I installed the GRUB bootloader on the same partition as Ubuntu (not in the MBR). I also downloaded EasyBCD so I could tweak the Win7 bootloader to add Ubuntu to the boot list. It was much easier than dual-booting with Windows XP using **its** bootloader.

The best reason to use the Windows bootloader to chainload GRUB is that when Windows comes out with new service packs, they usually overwrite the MBR. And if you have GRUB in there, then you can no longer boot Ubuntu and have to restore it from the Ubuntu LiveCD's restore console. Using the Windows bootloader to chainload GRUB and thus Ubuntu is more complex to set up (especially for WinXP), but it saves you a lot of drama when Windows Service Packs come out, or you need to reinstall Windows for any reason.

Oh, and to answer your question... you paid for Windows 7 and the key along with your laptop. So I wouldn't ditch it. You may still have a use or two for it, so get your money's worth :) Good luck with your dual-boot.

---

### Post by TroN-0074 on 2011-10-13
I dont know if the size of your hard drive is an issue but you can reduce the W7 partition perhaps 100GB (More than enough for windows), install Linux in the remaining chunk of HD and run XP in VB inside Linux.
For what you said you are already running XP in Ubuntu so you can do a similar set up in your Linux partition (you can DD your old hard drive into the linux partition on your new hard drive) at the same time you are keeping W7 which you already paid for it when you purchased your computer.
That is my Two Cents to this entry Good Luck to you.

---

