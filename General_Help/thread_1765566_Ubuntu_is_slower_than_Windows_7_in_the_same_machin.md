---
title: "Ubuntu is slower than Windows 7 in the same machine"
date: 2011-05-23
forum: General Help
---

### Post by vugh on 2011-05-23
I just recently migrated to Ubuntu 11.4, from being a Windows user. I've dabbled with Ubuntu many times before, since 6.xx, but have always been on dual boot. It's just now that I'm going full Ubuntu, yey :)

My "problem" though is that Windows 7 (and even Windows XP) seemed faster and more "polished". By that I mean:

1. startup time. it takes around 30 - 45 seconds in ubuntu. when i was on windows, it was only about 20 seconds. i didn't have any startup programs so i was able to work immediately when it loaded.

2. loading of programs like chrome, netbeans, eclipse, and even the simplest - the terminal, gedit, calculator. everything was just faster-loading in windows 7. and small programs like notepad and calculator loaded instantly.

3. i dont know how to call this, but let's just say the "painting" of the windows, especially when loading programs or switching between windows, sometimes it takes time to "paint windows" in ubuntu. i understand this also happens to windows programs, but the ubuntu programs are just a bit more clunky.

4. loading of folders with svn (i use rabbitcvs). it can take about 30 - 45 seconds to open a folder. while in windows (tortoise svn), everything opened instantly

I really had no problems with the speed of my laptop when I was on Windows. But now I feel like I need to upgrade already. it really lessens my productivity :( 

Any ideas?

Here are my specs.. don't laugh.. this lappy's a bit old :)

Laptop

Ubuntu 11.04 (natty)
GNOME 2.32.1
Kernel 2.6.38-8-generic

Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
Frequency 1867.000 MHz
L2 Cache 1024 KB

Video: Intel Corporation Mobile GM965/GL960 Integrated Grahics Controller

Memory Total: 3009 MiB
Swap Total: 12622 MiB (why is this so huge? :P because when migrating to linux, i found that it was an unused space when i was on windows, and since i didn't think it was enough to be a storage space, i just decided to make the whole thing swap)

scsi0: ATA WDC WD1600BEVT-2
scsi1: Optiarc DVD RW AD-7650A

```

Partition   FS          Mount                Size     Used      Unused   Flags
/dev/sda1   ext4        /                     19.53G    6.66G   12.87G   boot
/dev/sda2   extended                         129.52G  ---       ---      lba
/dev/sda5   ntfs        /media/something...  117.19G  108.17G    9.00G
/dev/sda6   linux-swap                        12.33G  ---       ---

```

By the way, what's that "lba" in my partitions? It's so huge.. I don't remember creating that partition when i installed ubuntu :P

---

### Post by mmsmc on 2011-05-23
you are using 11.4, which  is brand new and of course not as great as older versions, this problem should stop after newer updates, if it is truly to bothersome you can downgrade to 10.10, or just use windows for the time being until 11.4 gets better over time

---

### Post by ivanovnegro on 2011-05-23
Ubuntu 11.04 is a mainstream OS that needs enough resources and it is actually for very recent hardware.
Your hardware seems to have enough power but its an older system.
Yes, you are right, Ubuntu became a little bit more "bloated" in the sense that now it needs really better specs to run perfectly, but thats even ok with today hardware.
On my system it runs without glitches but I realized that I dont need effects and it needs too many resources for things I dont need really, so I settled to a more lightweight distro like Xubuntu.
One of my reasons to use Ubuntu or Linux was to be faster and more efficient, the new release of Ubuntu is the opposite for me, Xubuntu gave me what I wanted from Linux back.
Its personal preference.
So, if you prefer really more speed and less eyecandy, maybe try Xubuntu or Lubuntu (this one will run like XP and better).
In general Ubuntu 11.04 is comparable in speed with Windows 7, XP is definiteley lighter as all the new Ubuntu releases because its an almost outdated OS that runs perfectly on single core systems.

---

### Post by HermanAB on 2011-05-23
Howdy,

Run top and see what junk is running in the background and stop it.
Disable useless services.
Verify that the all DNS are active and that your router doesn't hand out a lame DNS address.

Other than that, with all that swap space, why do you reboot all the time?  If you want to save power, suspend the machine and it will come back to where you left off in a few seconds.

---

### Post by 3Miro on 2011-05-23
All symptoms described by the OP suggest a graphics issue. GM965/GL960 had some issues in the past and apparently they still do.

A later update to the kernel or Xorg may fix the issue, but int he mean time you can try to play around with the graphical settings.

First try to logout and login in Ubuntu Classic. If Ubuntu Classic works well, you can install CCSM (compizconfig-settings-manager) and try to enable disable effects in standard Unity to see if they fix the issue.

If Ubuntu Classic doesn't work well either, then you can try Ubuntu Classic No Effects. This one should be blazing fast (although not as pretty).

---

### Post by davesalyers on 2011-05-23
Just a note - if you are using Ubuntu 11.04 then you are probably not using GNOME 2.32 as 11.04 defaults to Unity or GNOME 3 which are more resource dependent.

My recommendation given your specs (and actually my recommendation for the vast majority of Linux users who tend to be interesting in lengthening the life of their hardware useability) is to switch their distro to either Xubuntu which uses the XFCE desktop environment or Lubuntu which uses the LXDE desktop environment as both of these are less resource intensive. Ubuntu 11.04 is really going the way of trying to eventually appeal to "mainstream" I-Pad users (by 11.10) rather than the traditional Linux audience. Ubuntu 11.04 is really for the experimental users who insist on "eye candy" on their desktop. 

Xubuntu and Lubuntu are more directed towards the traditional Linux population who want to extend the life of their hardware without having to upgrade all the time to meet the needs of increasingly bloated software requirements. You will find an increase in speed using either of these (FYI - Lubuntu is lighter than Xubuntu).

You also might consider going to the 10.04 LTS (Long Term Support) release of either Xubuntu or Lubuntu while the bugs are being worked out of 11.04.

Fortunately 11.04 has prompted a renewed interest in the XFCE and LXDE desktop environments as alternatives to Unity, GNOME 3, and KDE4.

---

### Post by 3Miro on 2011-05-23
> **davesalyers said:**
> Just a note - if you are using Ubuntu 11.04 then you are probably not using GNOME 2.32 as 11.04 defaults to Unity or GNOME 3 which are more resource dependent.

My recommendation given your specs (and actually my recommendation for the vast majority of Linux users who tend to be interesting in lengthening the life of their hardware useability) is to switch their distro to either Xubuntu which uses the XFCE desktop environment or Lubuntu which uses the LXDE desktop environment as both of these are less resource intensive. Ubuntu 11.04 is really going the way of trying to eventually appeal to "mainstream" I-Pad users (by 11.10) rather than the traditional Linux audience. Ubuntu 11.04 is really for the experimental users who insist on "eye candy" on their desktop. 

Xubuntu and Lubuntu are more directed towards the traditional Linux population who want to extend the life of their hardware without having to upgrade all the time to meet the needs of increasingly bloated software requirements. You will find an increase in speed using either of these (FYI - Lubuntu is lighter than Xubuntu).

You also might consider going to the 10.04 LTS (Long Term Support) release of either Xubuntu or Lubuntu while the bugs are being worked out of 11.04.

Fortunately 11.04 has prompted a renewed interest in the XFCE and LXDE desktop environments as alternatives to Unity, GNOME 3, and KDE4.

- Ubuntu 11.04 comes with Gnome 2.32. Ubuntu 11.10 (coming in 6 months will come with Gnome 3). Unity is an interface for Gnome not a separate Desktop Environment. However, it is true that the Unity interface tends to be more resource hungry than the classic one.

- Xubuntu is a great distribution. One can try out XFCE (the DE for Xubuntu) by installing xfce4 from the Software Center, then logout/login (i.e. you don't have to reinstall Ubuntu to get Xubuntu).

- LXDE is also a good DE, but it is somewhat new and still suffers from quite a few bugs. It also has fewer features. LXDE tends to be lighter than XFCE.

- 10.04 will probably have many issues with GM965/GL960 as it came out before Intel released the hardware and drivers.

---

### Post by Jerry N on 2011-05-23
In my experience various versions of Ubuntu boot a bit faster than Windows 7 but certainly don't seem to run any faster.  I haven't found any way in Linux to run high definition .mts movie files downloaded from a Canon camcorder without dropping frames while Win 7 does it with no problem at all.

Have you turned off all the desktop "effects"?  People claim that these effects don't make the machine slower but they sure make it seem slower.  I turn off all that stuff in Windows too.

Jerry

---

### Post by 3Miro on 2011-05-23
> **Jerry N said:**
> In my experience various versions of Ubuntu boot a bit faster than Windows 7 but certainly don't seem to run any faster.  I haven't found any way in Linux to run high definition .mts movie files downloaded from a Canon camcorder without dropping frames while Win 7 does it with no problem at all.

Have you turned off all the desktop "effects"?  People claim that these effects don't make the machine slower but they sure make it seem slower.  I turn off all that stuff in Windows too.

Jerry

This depends on your video cards. Only some Nvidia cards curently have drivers as good as the Windows ones. Some of the Intel cards are close and AMD is getting there, but they are not there yet.

Desktop effects can dramatically slow down your machine. It depends on how many/what effects you are running, what is your video card and how good is the driver. I can get similar performance on with desktop effects or even video games with Nvidia. However, couple of years ago desktop effects would break an older ATI that I had (newer drivers were fine).

---

### Post by davesalyers on 2011-05-23
> **3Miro said:**
> - Ubuntu 11.04 comes with Gnome 2.32. Ubuntu 11.10 (coming in 6 months will come with Gnome 3). Unity is an interface for Gnome not a separate Desktop Environment. However, it is true that the Unity interface tends to be more resource hungry than the classic one.

Ooohh.. ouch.. well, I got that one wrong, BUT that means that folks get to look forward to an OS (11.10) that may be even slower and more bloated than 11.04 if they do not purchase the most up to date hardware to run it??

That sounds a lot like the M$ Windows philosophy... :confused:

---

### Post by 3Miro on 2011-05-23
> **davesalyers said:**
> Ooohh.. ouch.. well, I got that one wrong, BUT that means that folks get to look forward to an OS (11.10) that may be even slower and more bloated than 11.04 if they do not purchase the most up to date hardware to run it??

That sounds a lot like the M$ Windows philosophy... :confused:

New features always take more resources. Visual effects and such are demanding. You can either build a system that lacks visual effects or you can build a shiny one. In Linux, you have the choice between Ubuntu and Xubuntu (also Ubuntu 10.04 which is good for another two years).

Also note that Unity doesn't have so much requirements on the hardware as it does for good hardware drivers. If you have proper drivers for your video card, then it really doesn't slow things down at all. On my Nvidia desktop, 11.04 is no slower than 10.04 and only a tiny bit slower than XFCE.

The problem with Windows is that it wastes a lot of resources. For the features that it provides, there is no reason to have Windows 7 taking almost a 1GB of RAM just to run (goes above 1GB if you just open Firefox). You will not see that in Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I'm running Ubuntu 10.10 right now. It the fastest version of Ubuntu I have ever used yet, next to a minimal install of debian and openbox.  This is so fast!  Most of these people that are complaining are using the cutting edge version of 11.04. And to those users I say - what are you thinking? They might as well be volunteering themselves to be beta testers by using 11.04. Unless that is something you enjoy, try something more stable like the previous release from now on? Just a suggestion.

---

### Post by davesalyers on 2011-05-23
> **3Miro said:**
> New features always take more resources. Visual effects and such are demanding. You can either build a system that lacks visual effects or you can build a shiny one. In Linux, you have the choice between Ubuntu and Xubuntu (also Ubuntu 10.04 which is good for another two years

I guess I don't quite get the point of "visual effects" (aka "eye candy") on the desktop. It sounds like a waste of resources for the kiddies that would be better applied to increasing productivity for work-related tasks for adults instead. 

I want "eye candy" on my games for the few minutes that I play them - not on my desktop, just "because".

---

### Post by 3Miro on 2011-05-23
> **davesalyers said:**
> I guess I don't quite get the point of "visual effects" (aka "eye candy") on the desktop. It sounds like a waste of resources for the kiddies that would be better applied to increasing productivity for work-related tasks for adults instead. 

I want "eye candy" on my games for the few minutes that I play them - not on my desktop, just "because".

Eye candy is entirely a matter of personal preference. I use XFCE as my main DE, but every now and then I do turn comiz on, just to see some nice effects.

---

### Post by ivanovnegro on 2011-05-23
> **3Miro said:**
> New features always take more resources. Visual effects and such are demanding. You can either build a system that lacks visual effects or you can build a shiny one. In Linux, you have the choice between Ubuntu and Xubuntu (also Ubuntu 10.04 which is good for another two years).

Also note that Unity doesn't have so much requirements on the hardware as it does for good hardware drivers. If you have proper drivers for your video card, then it really doesn't slow things down at all. On my Nvidia desktop, 11.04 is no slower than 10.04 and only a tiny bit slower than XFCE.

The problem with Windows is that it wastes a lot of resources. For the features that it provides, there is no reason to have Windows 7 taking almost a 1GB of RAM just to run (goes above 1GB if you just open Firefox). You will not see that in Ubuntu.

It seems to me really difficult to believe that your 11.04 install is faster as 10.04 or 10.10 but its ok, if you say it I will take your word. For many people its just slower even if it runs well, it runs good on my system but it is definiteley slower, look at the boot times and compared to Xubuntu, it is slow and not just a bit slower. But ok, thats only my experience but I know Im not the only one.
Dont get me wrong, Unity is and can run almost fine but I have the feeling that it is a fact, that this release is slower and its funny because every new release we wanted faster boot times and this time it was a step backward. Im aware that this is due to the new and young UI Unity and I know it will improve.

---

### Post by 3Miro on 2011-05-23
> **ivanovnegro said:**
> It seems to me really difficult to believe that your 11.04 install is faster as 10.04 or 10.10 but its ok, if you say it I will take your word. For many people its just slower even if it runs well, it runs good on my system but it is definiteley slower, look at the boot times and compared to Xubuntu, it is slow and not just a bit slower. But ok, thats only my experience but I know Im not the only one.
Dont get me wrong, Unity is and can run almost fine but I have the feeling that it is a fact, that this release is slower and its funny because every new release we wanted faster boot times and this time it was a step backward. Im aware that this is due to the new and young UI Unity and I know it will improve.

Unity is now faster, but it is not slower either. On pure boot time, Unity should make little difference as there are many other things happening that are taking up the bulk of the resources. Unity is just a plugin for compiz, so unless you run into some driver issue it will not be notably slower, than regular compiz (i.e. 10.10).

Next release would be a big change too as things would be moving to Gnome 3. Only then we will have a good picture of what to expect for the next LTS.

---

### Post by vugh on 2011-05-24
Thank you, all, for your insights. They are all very helpful! :)

---

### Post by FormatSeize on 2011-05-24
> **ivanovnegro said:**
> Ubuntu 11.04 is a mainstream OS that needs enough resources and it is actually for very recent hardware.
Your hardware seems to have enough power but its an older system.
Yes, you are right, Ubuntu became a little bit more "bloated" in the sense that now it needs really better specs to run perfectly, but thats even ok with today hardware.
Really? How new of hardware are we talking here? I was running 11.04 (Beta1) not too long ago, and that system was pretty old, as it was my first try at building a computer and I didn't want to risk "wasting" a lot of money if I screwed up. It didn't seem to run that bad, but again, I ran it for a short time.

That build slowly began to deteriorate, so I got a new(er) motherboard, and a couple optical disk drives and a new box and everything seems to be running great on 10.04 and Fedora. I'll give 11.04 another try when I get home today, but my my hardware is circa 2006 (3 PCI ports and an AGP port where the graphics card sits, no PCI Express 2gig RAM DDR1, PATA), but I don't forsee having that many problems with speed or anything. But I could eat these words tonight.
 
> **ivanovnegro said:**
> One of my reasons to use Ubuntu or Linux was to be faster and more efficient, the new release of Ubuntu is the opposite for me, Xubuntu gave me what I wanted from Linux back.
I haven't tried Xubuntu, but maybe I should. I originally switched to Linux specifically for speed, and it worked for me, and I haven't gone back after all these years. At work, I use Windows 7 (I have to), and I don't particularly like it. It also makes me feel that what people are calling "polish" is the same thing that I call "extraneous". But like you said, ultimately, its a matter of personal preference.

---

### Post by ivanovnegro on 2011-05-24
> **FormatSeize said:**
> Really? How new of hardware are we talking here? I was running 11.04 (Beta1) not too long ago, and that system was pretty old, as it was my first try at building a computer and I didn't want to risk "wasting" a lot of money if I screwed up. It didn't seem to run that bad, but again, I ran it for a short time.

That build slowly began to deteriorate, so I got a new(er) motherboard, and a couple optical disk drives and a new box and everything seems to be running great on 10.04 and Fedora. I'll give 11.04 another try when I get home today, but my my hardware is circa 2006 (3 PCI ports and an AGP port where the graphics card sits, no PCI Express 2gig RAM DDR1, PATA), but I don't forsee having that many problems with speed or anything. But I could eat these words tonight.
 

I haven't tried Xubuntu, but maybe I should. I originally switched to Linux specifically for speed, and it worked for me, and I haven't gone back after all these years. At work, I use Windows 7 (I have to), and I don't particularly like it. It also makes me feel that what people are calling "polish" is the same thing that I call "extraneous". But like you said, ultimately, its a matter of personal preference.

11.04 can run perfectly on older systems, I wanted only to say that there are alternatives that will run even better on older systems. My machine is a little bit older as two years and Unity is running normally but I have this feel of extrabloat that I dont need anymore, its just my preference. On Unity for me there is running too much in the background what I dont use. 

Im using Ubuntu/Linux exclusiveley and right now I prefer the speed of a lighter system, I know my machine is getting older and older and I dont want to waste resources, especially the battery power is getting lower and lower for me with each new release of Ubuntu.

---

### Post by nerdy_kid on 2011-05-24
The "painting" lagginess is most likely because you have an older graphics card.

---

### Post by honkanen on 2011-07-10
I'm running into all the same issues as the OP.  I'm also dual booting Ubuntu 11.04 with Win7.  My hardware is a bit different as I'm running a Dell Dimension 5150 desktop with the following specs:
Intel P4 2.8Ghz CPU
4GB RAM
250GB HDD
ATI Radeon X300/X550/X1050 Series

I can't stand that most of the windows I open in Ubuntu are pretty much blank. (the window's contents such as fields, buttons, text will not display)  Sometimes I need to move my mouse over the open window for the contents to gradually display partially.

I have additional issues too such as a HDD clicking noise ONLY in Ubuntu and not present in Windows.  I'll try some of your suggestions.

---

### Post by wildmanne39 on 2011-07-10
> **honkanen said:**
> I'm running into all the same issues as the OP.  I'm also dual booting Ubuntu 11.04 with Win7.  My hardware is a bit different as I'm running a Dell Dimension 5150 desktop with the following specs:
Intel P4 2.8Ghz CPU
4GB RAM
250GB HDD
ATI Radeon X300/X550/X1050 Series

I can't stand that most of the windows I open in Ubuntu are pretty much blank. (the window's contents such as fields, buttons, text will not display)  Sometimes I need to move my mouse over the open window for the contents to gradually display partially.

I have additional issues too such as a HDD clicking noise ONLY in Ubuntu and not present in Windows.  I'll try some of your suggestions.
Hi, it is probably your video card driver, have a look here. Fglrx Interferes With Radeon Driver.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Marky FAQ on 2011-07-10
Try installing BleachBit

---

### Post by honkanen on 2011-07-10
Thanks for the replies. I"ll check out your link regarding fglrx.  I'll also check out BleachBit but I'm not sure how a disk cleaning program could resolve video issues.

---

