---
title: "New installation on Windows 7 Laptop - Won't Boot"
date: 2010-05-10
forum: General Help
---

### Post by kananesgi on 2010-05-10
Howdy folks,
 
New guy here. I've always wanted to try a linux based OS out but never had the guts. A classmate suggested I try Ubuntu since it has an option to install from within Windows, making it a bit easier to try out. I downloaded the disk ISO torrent and burned it to a DVD. I then ran the DVD and installed Ubuntu using the Windows installer. Upon rebooting, I get the boot menu asking which OS I want to start. I select Ubuntu and it goes to a countdown to hit ESC to select boot options. Once boot starts, I get a bunch of crap on the command lines and then it hangs. The entry it hangs on is something to do with ?child-(several numbers I can't remember right now). I hope that is enough for someone to identify where it's hanging during boot.
 
Any idea what is causing this? The computer is a Toshiba Satallite L505D-S5983. You can look up the specs for that. Processor is an AMD Athlon II M300 2.0Ghz, 32-bit, with 3GB RAM. Video is AMD M860G with ATI Mobility Radeon 4100. Primary OS is Windows 7.
 
I'll see if I can find some paper and a pen to write down the particulars of the error. I usually use my computer for note-taking, but I obviously can't do that here.
 
Thanks in advance for any help.

---

### Post by kananesgi on 2010-05-10
Here is the line where the boot hangs:
 
```
[      0.851281] [<ffffffff810141e0>] ? child_rip+0x0/0x20 
```
 
Is there any kind of boot log that records this stuff? Not sure if that's possible or not.

---

### Post by Mark Phelps on 2010-05-10
It's possible you got a "bad" disk image.  

Ubuntu 10.04 fits on a CD, and it should really be downloaded from one of the official sites.

---

### Post by kananesgi on 2010-05-10
I downloaded it from here, and I put it on a DVD because I don't have any CDs to put it on. I didn't think that would be a problem. Would I simply uninstall it through Windows and try again, perhaps waiting till I can get some CD-Rs?

---

### Post by Apv507 on 2010-05-10
Download Daemon tools Lite and an install the ISO through there. People actually use physical media still? :) Just make sure you have the right ubuntu (desktop vs server or netbook) and the right architecture x86 or 64bit!

---

### Post by kananesgi on 2010-05-11
Now, I did notice that the wubi installer was trying to automatically download the following file:
 
ubuntu-10.04-desktop-amd64.iso
 
This is the version I downloaded with BitTorrent. The windows installer was going to take half a day to download the file, but the torrent downloaded in a little over an hour.
 
My laptop has a 32bit OS, but I don't know what the processor architecture is.
 
How can I tell whether my processor is 32 or 64 bit?

---

### Post by Apv507 on 2010-05-11
If its running a 32bit OS the architecture is more than likely x86 (32bit). While you could run a 32 OS on a 64bit architecture I find it unlikely that would be the case. While I think it IS possible to run a 64bit OS on a 32bit processor, it doesn't really do much for you.

---

### Post by kananesgi on 2010-05-11
Well, I guess this just isn't going to work for me. I downloaded the i386 version of ubuntu from the site, mounted it in daemon tools (figured I needed a physical disk before), and installed it. On the first try, I got a timeout error that I think was due to my poor internet.I unistalled that copy and tried again, with success this time. However, upon reboot into ubuntu, the boot hangs at a different spot now.
 
So, I guess I'll give up on this. This little experiement has definately not left a good impression of linux or ubuntu for me.

---

### Post by Apv507 on 2010-05-11
I understand your frustration, it is often just something simple that gets missed that causes the problem. It's a shame it didn't work for you. When I first heard of ubuntu it was on version 7.04 and I used the liveCD to run my computer b/c HP gave me a WindowsXP recovery disk that didn't have sata hard drive drivers on it, but for a sata hard drive, and running in legacy mode was slow. (Brilliant of them huh?) Anyway I used Ubuntu temporary and thought it was okay, Then came back to it for version 9.04 and fell in love with it. Come back in a version or two down the road and give it another try. 
Thought I don't blame you at all for giving up on it now. IF you really want to use it, at least to get a feel for it true installing virtualbox and mounting the ISO in there and installing it. You need a fair amount of CPU power and Ram to get it to run well but even a slower machine will let you try it out. I use virtual box on Win7 to run XP b/c i had the disk and wasnt going to pay Microsoft for something they should have included anyway. Anyway if you need help with virtualbox tutorials are all over the place and feel free to ask here or me personally.

---

### Post by joosto on 2010-05-11
I had problems with the initial installation of Ubuntu as well. I persisted though and I really love it now. I've been using it for a couple of months and I don't think I'll ever return to Windows.

Keep trying! :D

---

### Post by DomesDKG on 2010-05-11
In his first post he mentions he does have a 32 bit processor, and 64 bit operating systems won't run on 32 bit processors, thus the initial error. (though 32 will run on 64)

I wouldn't recommend using the windows installer, though I'm sure it works.  It seems more practical to me to just shrink your windows partition in the management console in windows, and then just install ubuntu into the empty space after booting to the disk.

---

### Post by DomesDKG on 2010-05-11
Also, if your friend is trying to talk you into using Ubuntu, why don't you get him to fix it for you :P  You'd think if he wants you to use it he' be more than happy to help you get it running.

---

### Post by kananesgi on 2010-05-11
> **DomesDKG said:**
> Also, if your friend is trying to talk you into using Ubuntu, why don't you get him to fix it for you :P You'd think if he wants you to use it he' be more than happy to help you get it running.
 
He's not really a friend, he's a classmate in my online college, and he just started with it a couple months ago. I mentioned to him in a chat that I had wanted to try linux for some time and he suggested I try ubuntu.
 
I guess I'll try shrinking the partition and installing it from the disk. Will that work from a DVD? I just don't want to screw up the Windows installation and loose it as I need this computer for my school work. I may start experimenting on my brother's netbook to see if I can get it working there.
 
Also, I thought I did have 64-bit processor, but I know it's a 32-bit OS now, so it's probably 32-bit processor. I initially chose the 64-bit Ubuntu because that was what the windows installer was trying to download and install, so I figured it had identified the system as 64-bit hardware.

---

### Post by kananesgi on 2010-05-12
Well, the problem has something to do with the hardware of this laptop I think. I downloaded Knoppix and put it on a USB stick. Tried to boot off it and had the same problem. It locked up during boot, this time with a pair of linux penguins in the top left corner of the screen. I also tried booting from a ubuntu LiveUSB setup and boot hung at the same spot as with the Windows based installation. I tried booting my brother's eeepc netbook with the Knoppix USB drive and had no trouble at all. Figured my way through all the boot options and was running linux for the first time in my life. I just wish I could get it working on my laptop as the netbook isn't much of a test. Unfortunately, I've got no real idea what's causing the problem on the laptop.

---

### Post by Mark Phelps on 2010-05-12
> **kananesgi said:**
> ... I then ran the DVD and installed Ubuntu using the Windows installer. Upon rebooting, I get the boot menu asking which OS I want to start. I select Ubuntu and it goes to a countdown to hit ESC to select boot options. Once boot starts, ...

Wubi installation??

Don't use it myself but have noticed that in the Testing Wubi 10.04 thread, there are LOTS of problems with this version.  It's more likely a Wubi-related problem than an Ubuntu-specific problem -- but I can understand your reluctance to mess with partitioning just to try it out.

Suggest you come back in a couple of months when (maybe) the Wubi problems have been solved and try again with a fresh download.

---

### Post by kananesgi on 2010-05-12
I don't think the problem is related to Ubuntu actually. As I mentioned in my previous post, I've now tried several different distributions of linux and all of them crash in one way or another during bootup. I've now tried Knoppix (in LiveUSB mode) on a netbook and my mother's WinXP system and both worked flawlessly. I've also managed to load Ubuntu 10.04 Netbook Remix on the netbook with good results. I'm now installing it on the netbook as I type to see how well it works in reality (running very slowly from the USB). If the netbook crashes, I'm not that upset since we don't really use it very much.
 
The problem with my Toshiba laptop seems to be with Linux in general, not with Ubuntu. Is there anywhere that I might be able to get some help with general Linux issues like this? Support that isn't targeted specifically at a certain distribution? I would really like to see how well linux would run on the laptop. There are a few programs that I want to try that need the power of the laptop (FlightGear flight sim mainly).

---

### Post by colinwhipple on 2010-05-12
> **kananesgi said:**
> I don't think the problem is related to Ubuntu actually. As I mentioned in my previous post, I've now tried several different distributions of linux and all of them crash in one way or another during bootup. I've now tried Knoppix (in LiveUSB mode) on a netbook and my mother's WinXP system and both worked flawlessly. I've also managed to load Ubuntu 10.04 Netbook Remix on the netbook with good results. I'm now installing it on the netbook as I type to see how well it works in reality (running very slowly from the USB). If the netbook crashes, I'm not that upset since we don't really use it very much.
 
The problem with my Toshiba laptop seems to be with Linux in general, not with Ubuntu. Is there anywhere that I might be able to get some help with general Linux issues like this? Support that isn't targeted specifically at a certain distribution? I would really like to see how well linux would run on the laptop. There are a few programs that I want to try that need the power of the laptop (FlightGear flight sim mainly).

The L505d series of Toshiba laptops has a problem with linux.  I have an L505D-S5983 myself.

Do a top-level search of these forums on "L505D" and you will find lots of discussion.

Also look here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

Colin

---

### Post by hardwired112 on 2010-05-13
> **kananesgi said:**
> Well, I guess this just isn't going to work for me. I downloaded the i386 version of ubuntu from the site, mounted it in daemon tools (figured I needed a physical disk before), and installed it. On the first try, I got a timeout error that I think was due to my poor internet.I unistalled that copy and tried again, with success this time. However, upon reboot into ubuntu, the boot hangs at a different spot now.
 
So, I guess I'll give up on this. This little experiement has definately not left a good impression of linux or ubuntu for me.

I have an L505D-S5983, I'm wondering if this is some sort of hardware issue. I tried booting the live cd, and it hangs right near where you mentioned yours did. I'm going to continue to do research on this, I'll let you know if I find anything.

---

### Post by kananesgi on 2010-05-13
> **hardwired112 said:**
> I have an L505D-S5983, I'm wondering if this is some sort of hardware issue. I tried booting the live cd, and it hangs right near where you mentioned yours did. I'm going to continue to do research on this, I'll let you know if I find anything.
 
Do as Colin mentioned and search the forum for "L505D" and you'll find several threads dealing with this. It's a problem in Toshiba's BIOS I think, from what I'm reading. There are some workarounds, but I'm still researching it to figure out how to fix the problem. I'm now having another problem with my netbook that I installed UNR on earlier.

---

### Post by Apv507 on 2010-05-14
> **DomesDKG said:**
> In his first post he mentions he does have a 32 bit processor, and 64 bit operating systems won't run on 32 bit processors, thus the initial error. (though 32 will run on 64)

I wouldn't recommend using the windows installer, though I'm sure it works.  It seems more practical to me to just shrink your windows partition in the management console in windows, and then just install ubuntu into the empty space after booting to the disk.

Wubi is the way to go if your HDD is over 120 gigs. If you have ever tried to use gparted on a 640 gig hard drive you know what I mean. No one wants to wait a week to use their computer while it resizes such a massive drive. I used to be almost a snob when it came to ubuntu having its own partition, but after using wubi I feel it is the way to go. if you doubt the speed of NTFS + Linux Don't. Ive got a 17 second boot time for Ubuntu and a 20 second boot time for Win7 on the same drive. And as for system performance once it is up and running, I can't tell a difference. The greatest thing is I can still get to my Ubuntu files on windows without having to download some ext4 reader or using a virtual PC. 

As for the windows management console, its new to me, So I'm not sure how that works.

---

### Post by hardwired112 on 2010-05-14
> **kananesgi said:**
> Do as Colin mentioned and search the forum for "L505D" and you'll find several threads dealing with this. It's a problem in Toshiba's BIOS I think, from what I'm reading. There are some workarounds, but I'm still researching it to figure out how to fix the problem. I'm now having another problem with my netbook that I installed UNR on earlier.

disabling acpi worked for me as well. im still looking into a more permanent fix, i would like battery management and everything else that acpi provides. other than that i am loving ubuntu learning linux is extremely entertaining also, things are taking me a while to learn but the satisfaction of getting acquainted with this new os, as well as getting away from windows are both awesome feelings.

---

### Post by kananesgi on 2010-05-16
> **hardwired112 said:**
> disabling acpi worked for me as well. im still looking into a more permanent fix, i would like battery management and everything else that acpi provides. other than that i am loving ubuntu learning linux is extremely entertaining also, things are taking me a while to learn but the satisfaction of getting acquainted with this new os, as well as getting away from windows are both awesome feelings.
 
There looks to be a more permanent solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d&page=9"). I haven't been able to try it yet because I can't seem to figure out how to turn ACPI off, but it does look promising. I started [another thread]("http://ubuntuforums.org/showthread.php?t=1484727") looking for help on how to disable ACPI if anyone wants to help with that.

---

### Post by _rex on 2010-07-25
I have been able to install and boot Lucid by disabling acpi, first with the F6 menu on install, and then by editing the commands in grub... but when I use grub for this (pressing "e", adding "acpi=off" after "ro") the change isn't persistent. I don't want to have to do this every time I boot, and before I undertake a more complex solution, I'm wondering if there's a way to make the change permanent in grub, so acpi is disabled by default. 

This is possible, right? Clearly I'm not too savvy at this; some help would be greatly appreciated.

---

### Post by Seankn on 2010-10-10
Sweet I'll Try this out. I plan on having the Toshibal L505D S983 as my ubuntu laptop...

---

