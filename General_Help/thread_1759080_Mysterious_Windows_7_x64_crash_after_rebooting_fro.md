---
title: "Mysterious Windows 7 x64 crash after rebooting from Ubuntu 11.04"
date: 2011-05-15
forum: General Help
---

### Post by Mogster64 on 2011-05-15
I've been dual booting Ubuntu based distros and Windows 7 x64 for a couple of years now, but since installing Ubuntu Natty I've been experiencing a strange problem. Every time I reboot from Ubuntu and load Windows, Windows will always crash and reboot shortly after reaching the desktop. This even happens in Safe Mode, but if you simply reload Windows after the crash it works perfectly. The only error report in the event viewer is a kernel-power one stating that the system shut down unexpectedly. I'm not even getting a BSOD.

This only started happening after installing Ubuntu 11.04, but even so I thought this must have been a coincidence up until now. However, after a lot of testing it really does only happen after rebooting from Ubuntu. If I load Windows from GRUB straight after switching my PC on, it works fine. If I reboot Windows after this and boot straight back into Windows, it works fine. I can only assume that Ubuntu is doing something weird to the Windows hard drive without appearing to mount it.

Has anyone seen anything like this happen before? I'd be grateful for any suggestions, other than removing Windows of course. ;)

---

### Post by Twinnie on 2011-05-16
I just came here looking for a solution to this myself though the difference is I'm using BCD rather than GRUB. I can boot from other OS' just fine but Natty Narwhal always causes it to crash followed by a perfect boot after that.

---

### Post by McNopper on 2011-05-17
I have the same problem since installing Ubuntu 11.04. The previous version 10.10 did run fine besides Windows 7.
My feeling tells me, that it is probably the graphics card driver or some other device, which does not reset properly when doing a reboot - with no power off. If the power was completely off, there is no problem. Just a guess :-)

---

### Post by Mogster64 on 2011-05-17
It was a good guess. For some reason I hadn't thought to test the behaviour after a proper shutdown. It turns out that doing so from Ubuntu results in a crash and reboot during the POST screen, after which Windows loads without any issue. This is slightly less annoying than the crash in Windows itself, so it's a step in the right direction!

It's still totally bizarre though. The Windows crash even happens when booting from the Windows 7 install disk after rebooting from Ubuntu. I would have thought that if it was a problem with a driver not unloading itself properly then surely I shouldn't see any issue after a full shutdown? I still get the POST crash even if after switching the power off at the mains. Anyway, if it helps I've at least managed to record what happens after every shutdown action:

Reboot from Ubuntu back into Ubuntu: No issue.

Reboot from Ubuntu into Windows 7: Crash and reboot after reaching Windows desktop

Shutdown from Ubuntu: Crash and reboot during POST. No issues afterwards in Windows or Ubuntu

Reboot or shutdown from Windows 7: No issues

Oh and just for fun...

Reboot from Ubuntu into Windows 7 install CD: Crash and reboot after loading Windows PE.

It's good to see I'm not alone. :)

---

### Post by McNopper on 2011-05-18
By the way, which graphic card do you have and which driver?
I do have a ATI 5850 with the 11.5 *proprietary* driver from AMD website ... still thinking that this is the problem as - I am not 100% sure - before using this driver, I could reboot with no problem.

---

### Post by Mogster64 on 2011-05-18
I have an NVidia 8800GTX, and I'm using the most recent proprietary driver. I'll try removing it tonight to see if it makes a difference.

EDIT: I installed the driver from the one detected by Ubuntu's "Hardware Drivers" application, rather than from NVidia's site.

---

### Post by Mogster64 on 2011-05-18
Not much to add today unfortunately, except that removing the graphics driver had no effect. :(

---

### Post by McNopper on 2011-05-18
Hmmm, I am sure, we do both have the same problem when shutting down and rebooting.
Ido have the same results as mentioned in your previous post.
Let's see, if there are any fixes in the next days :-)

---

### Post by wildmanne39 on 2011-05-18
Hi, that all sounds very strange, have you looked to see if there is a bug report on it. I have never heard of ubuntu being the cause of something like this. You could try to file a bug report if there is not one already.

---

### Post by KiwiKiwiNZ on 2011-05-19
Hi there, I have the same problem. 
Apart from the win7 partition, I also have another one with Ubuntu 10.04, and it also crashes at the ubuntu login screen after rebooting from Ubuntu 11.04.
So doesn't seem to be specific to windows.

Maybe it's something related to grub2 (even tho someone is saying it happens with bcd too).
I might try to reinstall it.

graphic card: nvidia 9800 gtx+

---

### Post by FatAngus on 2011-05-23
Hi I am dual booting Windows 7 and Ubuntu 11.04 and I am also experiencing this problem.  My graphics card is also a Nvidia 8800 GTX.

Today I reinstalled Windows 7 and everything in Windows was working okay.  As we know, after installing Windows 7 Grub2 needs to be reinstalled.  Upon completion of reinstalling Grub2 I booted into Ubuntu, restarted the PC and then back into Windows and it crashed again so the problem seems to be either Grub2 or Ubuntu. :confused:

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you wipe the entire drive first before you began this reinstallation of windows 7?

---

### Post by FatAngus on 2011-05-23
@ linuxinstalledfromhdd

I reformatted the Windows 7 partition.  I have Ubuntu installed on a separate hard drive.

---

### Post by linuxinstalledfromhdd on 2011-05-23
yeah, but you didn't wipe the entire disc before you did this..

I'm also thinking that maybe it's a Windows WPI issue where they are checking to see if it's the only system on that disc now.  Windows has been making some changes to the way their OS checks to see that it's the top dog.

---

### Post by FatAngus on 2011-05-23
Thanks for the reply :)

Windows is and always has been the only OS on the first hard disk.  Ubuntu is on the second hard disk as is Grub2. Later I will try installing a different Linux variant and see if the problem is still there.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Sounds like a plan.  You may also want to consider just wiping the whole drive. And installing Windows into Virtualbox 4.  Make things so much simpler:guitar: too.

---

### Post by enimeizoo on 2011-05-23
I'm not sure at all, but I already had a reboot issue. Actually, I couldn't have sound when I rebooted from windows. Booting ubuntu and then rebooting would solve the issue (until next windows reboot..).
It ended up that windows screwed some BIOS settings on shutdown.
Whatever, it was just to say that you could have a look at bios settings.

---

### Post by FatAngus on 2011-05-24
This morning I installed Ubuntu 10.04 as I already had the iso on my hard drive.  After installation I rebooted and used Ubuntu 10.04.  I restarted the computer and booted into Windows.  There were no crashes during boot.  :P

---

### Post by Mogster64 on 2011-05-24
> **linuxinstalledfromhdd said:**
> I'm also thinking that maybe it's a Windows WPI issue where they are checking to see if it's the only system on that disc now.  Windows has been making some changes to the way their OS checks to see that it's the top dog.
That wouldn't explain the POST crash (would it?). 

I'm going to try ripping out the Ubuntu hard drive tonight and installing Mint 10 and GRUB2 on another drive, which is what I was using before. I'll also try disconnecting the Windows drive and see if the POST crash still happens after shutting down from Ubuntu.

At one point in the past by the way I was quadruple booting three Linux distros alongside Windows 7 with no issues like this. I'm not 100% certain yet, but I think it's almost definitely being caused by Ubuntu 11.04 in some way.

EDIT:
> **FatAngus said:**
> This morning I installed Ubuntu 10.04 as I already had the iso on my hard drive.  After installation I rebooted and used Ubuntu 10.04.  I restarted the computer and booted into Windows.  There were no crashes during boot.  :P
I guess I won't bother reinstalling Mint then! Thanks for that. :)

---

### Post by KiwiKiwiNZ on 2011-05-25
It seems clearly related to 11.04.
As I said, I have 3 partitions.
Win7
Ubuntu 10.04
Ubuntu 11.04

After rebooting from 11.04, it crashes for both Win 7 and Ubuntu 10.04.
If I reboot from 10.04 or Win7 to any other OS, everything is fine.
I also have the POST problem after shutting down from 11.04.

I have reinstalled grub2 from Ubuntu 10.04, but that didn't change anything: e.g. not a grub2 problem, but we knew that already.

Someone was suggesting to raise a bug...? :confused:

---

### Post by Mogster64 on 2011-05-25
> **KiwiKiwiNZ said:**
> Someone was suggesting to raise a bug...? :confused:
I can do so tonight, unless someone else feels like doing so in the meantime? 

Wow. My first bug report.:)

---

### Post by Mogster64 on 2011-05-25
Okay, so maybe I can't submit a bug report. I've just realised that I can't do so without specifying which package contains the bug, and as I don't know what package is causing the problem I can't submit the bug!

---

### Post by KiwiKiwiNZ on 2011-05-26
How do you submit a bug report?

Anyway, 1 more piece of info: if I reboot from U. 11.04 and just stop at grub (I mean, don't trigger the timeout, just don't select any entries and wait), my PC reboots. 

It looks to me that Ubuntu 11.04 issues and stores some kind of command to poweroff the PC after a certain amount of time, and for some reason it triggers even after rebooting.

Mogster64, can you confirm that you experience the same issue?

---

### Post by Mogster64 on 2011-05-26
> **KiwiKiwiNZ said:**
> How do you submit a bug report?
You need to use Ubuntu's built in bug reporting tool. Just bring up a terminal and type in ubuntu-bug [package name] to report about a specific package. if you leave that bit out, it brings up a wizard to help you locate the package, or tells you to sod off if you can't. ;)

I'll see if I get the same reboot from GRUB this evening. I've got a laptop with Natty installed too, so I'll see if I can produce the same error on that.

---

### Post by Mogster64 on 2011-05-26
I can confirm that I get the same reboot in Grub2 after rebooting from Natty. I had to leave it there for about 40 seconds.

---

### Post by KiwiKiwiNZ on 2011-06-01
I have created a bug report. Feel free to add any useful info to it :)
not sure ACPI is the problem, but that was my best guess.

BTW Mogster, do you have an Asus motherboard by any chance?

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089)

---

### Post by Mogster64 on 2011-06-01
> **KiwiKiwiNZ said:**
> I have created a bug report. Feel free to add any useful info to it :)
not sure ACPI is the problem, but that was my best guess.

BTW Mogster, do you have an Asus motherboard by any chance?

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089)

Nice one! That seems to cover pretty much everything. I've just added a comment to say that the reboot seems to happen 40 seconds after doing *anything* other than relaunching Ubuntu 11.04 after rebooting from the OS. It's almost like the system is somehow put on a countdown.

I do have an Asus motherboard as it happens, so I'll post up the model number once I get back. I updated the BIOS to the latest version after the problem started, but it didn't have any effect.

---

### Post by Mogster64 on 2011-06-01
I have an Asus P5N-E SLI motherboard with BIOS revision 1406. I don't suppose you have the same?

---

### Post by FatAngus on 2011-06-01
> **Mogster64 said:**
> I have an Asus P5N-E SLI motherboard with BIOS revision 1406. I don't suppose you have the same?

I also have this motherboard.

---

### Post by KiwiKiwiNZ on 2011-06-01
I have a slightly different one, Asus P5N-T Deluxe. (close enough though :). BIOS ver 1702. It is (nvidia) SLI too although I'm only using 1 graphics card.
The bug has been reassigned to Linux kernel as acpi-support is a deprecated package for handling runtime acpi events...
Maybe you guys can add attachments to the bug report too:
1) cat /proc/version_signature > version.log
2) sudo lspci -vnvn > lspci-vnvn.log

---

### Post by dozycat on 2011-06-01
OMG, too late.

I killed my windows 7 and changed to full ubuntu 11.04 64 bits.
I thought It was a capture card I added.
And my motherboard is an asus P8H67-M pro.
Well I can do everything from ubuntu.

---

### Post by miningold on 2011-06-05
I have the same exact problem. I also have an ASUS motherboard the Striker II Formula.

---

### Post by Arkangyl on 2011-06-13
Same here to all of the rebooting issues to a "t". I've been looking for several days now to no avail till now to find a thread on this subject and how to describe it well which it has been. The rebooting findings and when they happen are the same for me (though I'd add that Windows will reboot from the log in screen if you do not type your password fast enough I believe not just after it hits the desktop after an 11.04 reboot).

Also, Asus P5N32-E SLI MoBo here.

Actually, my wife's computer is near identical to mine minus a couple drives and hers does the exact same thing. It started for both of us after our 11.04 upgrades. I did try fixing the MBR and GRUB as well as a Windows /fixboot and all sorts of other "fix attempts" on both OSes.

I wish I could help more . . . if you need me to, please be specific what I need to do, and here's to hoping this gets found and fixed. If there is another or better thread that I have missed, please point the way to that one so I can keep tabs on this bizarre problem. Thanks.

---

### Post by Mogster64 on 2011-06-13
I believe this is the only thread, but there is also a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/791089)

The reboot seems to occur roughly fourty seconds after rebooting from Natty (or one of its derivatives) and doing anything but reloading Natty. Windows itself doesn't seem to have anything to do with it, it just happens that 40 seconds is just enough time to get to the Windows desktop (or indeed the login screen). It will also happen if you just hand around in GRUB, or boot any other non-Natty OS.

It's an odd one!

---

### Post by Arkangyl on 2011-06-13
I managed to find this thread [here]("http://ubuntuforums.org/showthread.php?t=1714550"). His problem appears to have been solved with Win7 which is odd since that is what many posting here are also using in their multi-boots. If it is a bios setting that is now suddenly "wrong" (as in it was fine with every previous version of Ubuntu, and several other Linux distros I run for testing and fun), I am at a loss for what it is. I'd say it might have had to do with upgrading to 11.04 but some have tested a fresh install with the same odd results. I've looked over my bios but see nothing that appears off or appears it would affect this. I'll look again though soon after some sleep for a fresher eye. It's just a wee bit frustrating as it is going to trash something at some point in the file system or win bitmap (actually already has but was able to repair it). I sadly need 7 too for gaming, heheh.

---

### Post by Mogster64 on 2011-06-13
> **Arkangyl said:**
> It's just a wee bit frustrating as it is going to trash something at some point in the file system or win bitmap (actually already has but was able to repair it). I sadly need 7 too for gaming, heheh.

You can sort of get around it by shutting down from Natty instead of rebooting. This way it'll reboot during POST instead of after the usual fourty seconds, after which you can boot into Windows without issue.

EDIT: Mine was a fresh install incidentally. The problem still happens in Linux Mint 11, and even from the Natty Live CD.

---

### Post by Arkangyl on 2011-06-13
I believe this may have also happened with PCLOS (KDE) that I run dual with XP on another HDD that is on a switch so is not active when my Ubuntu-7 HDD is. I will have to test that since I don't actually "use" PCLOS from its HDD install but use it to maintain an up to date Live USB that I can use as needed so never really swap between the two.

Is it possible for the bios to get hosed by rebooting in the middle of a post? I know it is ticked afterwards and prompts me to check my settings at an F1 - del prompt before continuing to load. At least one person I read between all the links I have been following said that they eventually had their computer completely die and only bring up a black screen prompt with no post (of course that could be something else like bad RAM).

So is the general consensus that this is most likely a kernel, or a major library / driver that is kernel related, issue with something in the bios or on the MoBo? I know I saw a few threads here and there that seemed similar but were citing issues with Ubuntu version 10.04 and 10.10 and were older threads. Could it be something that gets fixed then breaks again perhaps?

---

### Post by KiwiKiwiNZ on 2011-06-15
Hi, personally I don't think this problem is related to windows at all, since it happens even when I reboot into a different version of Ubuntu.
The common denominator seems to be that we all have Asus motherboards... and that it is annoying! :(

Just one thing, if you are affected by this bug, make sure you click on the "this bug affects me" link in launchpad. I think the more people it affects the more priority it will have....

---

### Post by Mogster64 on 2011-06-15
> **KiwiKiwiNZ said:**
> Hi, personally I don't think this problem is related to windows at all, since it happens even when I reboot into a different version of Ubuntu.
The common denominator seems to be that we all have Asus motherboards... and that it is annoying! :(

Just one thing, if you are affected by this bug, make sure you click on the "this bug affects me" link in launchpad. I think the more people it affects the more priority it will have....
Oh yeah, everyone do this! It's supposedly only affecting three people so far.

And yes, it's definitely not Windows. I've even tried disconnecting my Windows hard drive and letting the PC wait in the boot device selection screen. The reboot always happens about 40 seconds after rebooting from Natty and doing anything other than reloading Natty.

---

### Post by Arkangyl on 2011-06-15
^ I added that this bug affects me. Thanks for the heads up on that as I missed it. I also noted that it appears to affect ASUS MoBo users (our boards I believe are also very, very similar boards made around the same time frame). I posted my MoBo there. Everyone here might also want to do the same in case the pattern of boards sparks something regarding this glitch (surprised there are not more people posting on this since our boards we've posted were pretty popular boards).

Since the bug has hardly blipped on anyone's radar, I agree that everyone with this issue needs to at least flag the "this bug affects me" tag. Please. :D

---

### Post by triv on 2011-06-21
Another me too reply. Using a Asus P5N32-E SLI board. This was driving me crazy! For a while I thought it was some sort of Windows driver issue until I realized it happened even while I was in the BIOS setup after rebooting from Ubuntu.

Added my "This bug affects me too" vote to the bug report in LaunchPad.

---

### Post by KiwiKiwiNZ on 2011-06-22
Welcome to the asusbuntu frustrated users club Triv.
Unfortunately no light at the end of the tunnel yet.

---

### Post by Arkangyl on 2011-07-13
Updated to 2.6.38.10 kernel today (and all other updates that have been coming out of course) and no change. Issue is unchanged which stinks as I thought a kernel update might have this fixed. Kinda stinks that this hasn't gotten any attention yet really. :\

Just wanted to post that the newest Ubuntu Linux kernel does not solve the issue (for me anyway).

---

### Post by haresear on 2011-07-13
I've had a similar rebooting problem with Ubuntu 11.04 from first install, but the symptoms are a bit different. Whenever I try to reboot from 11.04 back into 11.04, it will fail every time with a kernel panic. However, I can reboot from 11.04 to either Ubuntu 10.10 or Windows 7 with no problem. I can also reboot from 10.10 or Win7 into 11.04 without a problem. This problem is on a Toshiba laptop with an Intel MB. I tried various acpi boot parameters, but nothing changed this behavior, so I've given up trying to fix it. Now I always just shutdown from Natty.

I have Xubuntu 11.04 on a different desktop machine with an Asrock MB, and it has no rebooting problems.

---

### Post by Mogster64 on 2011-07-14
It sounds like you've somehow developed the issue in reverse, haresear! Bizarre. 

Anyway, I'm not sure if I can be much more use here. I jumped ship to Linux Mint Debian Edition last week,which is thankfully free of any such issues on my PC.

---

### Post by KiwiKiwiNZ on 2011-07-26
Mogster64, it's a shame to have to move to another distro due to a bug like this, but I'm starting to get really fed up with this NO POST issue.
Might start thinking about moving away from Ubuntu, which is disappointing after so many years using it.

BTW, one of my hard drives is starting to fail. Could it be caused by the continues crashes?

---

### Post by Mogster64 on 2011-07-26
> **KiwiKiwiNZ said:**
> Mogster64, it's a shame to have to move to another distro due to a bug like this, but I'm starting to get really fed up with this NO POST issue.
Might start thinking about moving away from Ubuntu, which is disappointing after so many years using it.

BTW, one of my hard drives is starting to fail. Could it be caused by the continues crashes?
I'm not sure, although they can't be healthy either way. That's partly why I switched, as I was worried the problem could be having some kind of harmful effect as well as being annoying. Best not to risk it!

Anyway, Debian isn't too far removed from Ubuntu. At least it's staying in the family!

---

### Post by Arkangyl on 2011-07-26
Actually, it is not just Ubuntu afaik. I have a second hard drive on a power switch in my system that has XP and PCLOS dual booting on it (and the other is 7 and Ubuntu). My PCLOS install does the exact same thing. I know that does not help per se, but this issue goes beyond just Ubuntu I believe sadly . . . :( And yeah, I think it is taking a toll on my system somewhat. At least the reported bug has been finally updated to New but last I looked it has not been assigned yet / is not directly being worked on yet but progress has been made at least.

---

### Post by danom1te on 2011-07-26
I have had the same problem since the 11.04 update with an Asus P5N-D motherboard. I actually stopped using it for a while as it was so irritating but Ubuntu is my favourite OS for work so I hope there is a solution soon. Might have to switch to another distro if they don't. :(

---

### Post by Arkangyl on 2011-08-07
Small update on this that might alleviate (a small amount) of frustration. It may also help as a clue to what might be happening to those in the know.

If you have a PSU that has its own on-off switch, you can power it off (only if not in sleep-hibernate mode of course) completely after shutting down and then power it back on. When you next reboot your computer, it will not do the double bios post crash requiring hitting F1 to resume the post and boot cycle.

Of course if your PSU does not have its own on-off switch, you could also I guess unplug the PSU or flip the switch to off if on a surge protector or battery backup.

---

### Post by KiwiKiwiNZ on 2011-08-10
Maybe a work around!!

[INDENT] gksudo gedit /etc/modprobe.d/blacklist.conf
[/INDENT] 
add
 
[INDENT] blacklist nv_tco
[/INDENT] 
Have a look here for details :D

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/791089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/791089)

Please test and let us know if it works for you!

---

### Post by Arkangyl on 2011-08-10
OK, I read everything over there and may post my question there too in case it gets missed here.

One, does blacklisting this module cause any system changes, other issues, missing *anything*, etc. I need to be aware of as I would hate to "solve" (work around) one problem only to add some other issue or oddity.

Two, assuming this gets fixed wherever it needs to be fixed, I also assume I would want to un-blacklist this module at that point. How would I go about doing that, or is it as simple as just going into the .conf file and deleting the line that added the module?

Three, the work around for the module getting blacklisted, would this approach also apply to other distros that are having the same issue?

Thanks and great find!

---

### Post by fegavazza on 2011-08-16
My problem seems to be similar to this, so I dont think I should create another topic.

I tried everything above but I still cant fix.

When I choose to boot windows 7 at grub screen (even rebooting from ubuntu 11.04 or just after turning on the pc), windows animation during boot goes fine, but after that it crashes on a black screen (right before showing the logon screen) and the cpu cooler goes much faster. 
It happened after I made a clean installation of ubuntu 11.04. I can boot under safe mode, but regular mode seems to be impossible.

Any ideas?
Tnx

btw, its a hp dv7t quad with NV 230M GT

---

### Post by Mogster64 on 2011-08-16
Hmm. Are you able to get into Windows 7 successfully at all? The issue we were having only happens if you reboot or shut down from Ubuntu first, or apparently any distro with the bugged kernel using certain motherboards, and after that the PC just forces a reboot if you don't reload the problematic OS.

If you're unable to successfully boot into Windows 7 at all, it sounds like you have a different issue with either Windows 7 itself, or possibly GRUB I suppose. If you can get into Safe Mode though then it might just be a problem with one of your drivers. Check the event log in safe mode and look for any error reports, which may well pinpoint the problem. If you can't find anything obvious there, then run msconfig in safe mode, chose "Diagnostic Startup", reboot and see if you can get into Windows properly. If you can, then you can try re-enabling stuff in msconfig one by one, after which you should eventually find the item that's causing the issue when it fails to boot again. It can be a bit laborious though!

---

### Post by danom1te on 2011-08-16
I don't know if this helps but maybe it's not ubuntu specific. I removed ubuntu from my system and wanted to try fedora. I have 64bit so loaded it on the live cd from boot. When I restarted the same crash occured that has been happening with Ubuntu. I am going to try lxde fedora 64 bit to see if it is gnome related and if I still get the crash I will try a 32 bit version.

---

### Post by Arkangyl on 2011-08-16
^

No, it is not Ubuntu specific I don't think. What it probably is has been discovered as noted a few above and over on the bug report for it. Now, after two months, I would just love to see it fixed. :D Pretty please with sugar on top. Anyway, it happens to me with Linux Mint as well as PCLinuxOS. However, it hits me hardest with Ubuntu since that is my main OS for most things. IF you find a distro that does not cause this, please let us know as that mioght help narrow down how to fix the issue permanently.

---

### Post by danom1te on 2011-08-16
It is strange though that it didn't happen until natty. Burning Fedora lxde now but will report back tomorrow though as I want to go to bed :P

---

### Post by danom1te on 2011-08-17
Ok I have tried with Fedora LXDE 64 bit and Mint Gnome 32 bit (off the live cds) and it crashed with both upon rebooting back into windows.

Is this problem exclusive to dual booting off the same hard drive or does it occur when dual booting off separate drives because I am considering getting another drive if that is the only way to fix it. Alternatively a new motherboard lol

---

### Post by Mogster64 on 2011-08-17
> **danom1te said:**
> Ok I have tried with Fedora LXDE 64 bit and Mint Gnome 32 bit (off the live cds) and it crashed with both upon rebooting back into windows.

Is this problem exclusive to dual booting off the same hard drive or does it occur when dual booting off separate drives because I am considering getting another drive if that is the only way to fix it. Alternatively a new motherboard lol

It definitely has the same effect with two hard drives, so that won't fix it. Have you tried the blacklisting workaround?

---

### Post by KiwiKiwiNZ on 2011-08-17
Not sure why you guys are still looking for root cause since everything is pointing out to be a problem with the nv_tco module, and the good news is that a patch is being worked at, I believe.


[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=6b01d30eef64456ad9e261d2173266a3244da8e1](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=6b01d30eef64456ad9e261d2173266a3244da8e1)

---

### Post by Arkangyl on 2011-08-17
^ Yay!

Good find and thanks for sharing. I was afraid they had not even started on this bug yet. I just hope the fix is out soon(ish) and actually integrated into the distro.

Oh, and yikes, I was searching about for more info. on this module in general, and it has been the bane of a lot of people's existences on a number of levels for years. many years. It seems to regularly cause problems with various things.

---

### Post by danom1te on 2011-08-18
> **Mogster64 said:**
> It definitely has the same effect with two hard drives, so that won't fix it. Have you tried the blacklisting workaround?

I'm relatively new to linux so I don't know enough to tell if that would mess anything else up, since nobody above answered that question I haven't tried it yet, does that fix affect anything else from working? For me the workaround that worked was turning the psu off and on but that is quite annoying and you have to remember to shutdown instead of reboot.

I see now it's a kernel problem so hopefully the patch will be out soon!

---

### Post by Arkangyl on 2011-08-18
So far everyone who has tried the blacklisting is reporting it to work fine. I finally took the leap and did it after waffling for a week whether to do it (plus I was busy migrating two computers with 6 OSes between them to new HDDs). It appears to be working for three different distros. I did see a thread on blacklisting where they said you need to run gksudo initramfs -u to apply something after adding to a blacklist file though am not sure. I did that for the Big U as well as LinMint. That finction does not work with PCLOS. It will require a reboot where the first one will still do the double post crash. After that it appears to work fine.

As for concerns, I was / am too. However, I will note that looking at various distro blacklists, there are a variety of modules that can be considered important, including another watchdog module under PCLOS, that are blacklisted so this is not an uncommon thing per se. This module has also been recommended for blacklisting in the past when it has caused similar bugs, and bugs much, much worse than this one. Frankly, this module has been the bane of many hackers over the years looks like.

As for its importance, it does not appear to be as critical a module for desktop users as it does server and enterprise users (unless you do heavy gaming maybe on the OS). Frankly, my Nvidia card is a cooker, and I like it cool, so I run "nvclock -fF auto" on startup up so the fan ramps up more and runs it about 20&#730;C cooler than the standard bios fan speed does so am not worried about it overheating. My MB worries me more about overheating since it is passive cooling and gets a weee bit warm.



TL;DR: I'd recommend blacklisting the module till it is fixed if it works for you. If you leave your computer on all the time and unattended, then I would not.



Here is my cheat sheet since I had to do it so many times:

Run:
gksudo gedit /etc/modprobe.d/blacklist.conf
 
Add this to end of file: 
# This module is causing the BIOS to Post a second time on boot. Temporary till bug fixed
blacklist nv_tco

Run: 
gksudo update-initramfs -u

---

### Post by danom1te on 2011-10-22
I have been developing in c# now professionally so haven't had to use linux for a while. I am considering installing it again at home if this bug has been fixed, does anybody know if it has?

---

### Post by FatAngus on 2012-01-28
@ danom1te

I have just reinstalled Ubuntu 11.10 and I am able to restart Ubuntu without the computer restarting during boot.

However, I still have the problem restarting the computer from Ubuntu and booting into Windows.

---

