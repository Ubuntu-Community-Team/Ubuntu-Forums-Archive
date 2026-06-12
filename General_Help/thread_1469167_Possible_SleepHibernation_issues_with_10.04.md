---
title: "Possible Sleep/Hibernation issues with 10.04?"
date: 2010-05-02
forum: General Help
---

### Post by jaybok on 2010-05-02
Have been using Ubuntu 9.10 since past 2 months and had similar power and screen saver options as I do now after upgrading to 10.04.  ( "sleep" after 1 h, "lock screen" after 10 min, "hibernate" when "close lid" on a Dell 600m laptop)

With Karmic, Never had issues with closing the lid while the laptop was sleeping.  Three times in a row noticed that if the lid is closed while laptop is in sleep mode, opening the lid results in a blank screen, HDD and CD drive spins, fan turns on.  No response to keyboard and/or mouse.  Pressing the power key: no response.

The only solution is to shut-down by holding the power key down for a few seconds and reboot.

Cant imagine why there would be a problem, but wondering if there are others who also see the same thing and if there is fix to this.  Right now, have disabled sleep and will see if problem shows up.

---

### Post by coprolites on 2010-05-02
I'm also having the same problem. Every time I resume from sleep/suspend the PC turns on but only shows a white screen. 
I'm using 10.04 32bit on a dell dimension 8300. ATI Radeon 9800 Pro graphics card, with compiz. Not sure what else could be causing the problem.

---

### Post by pcrat on 2010-05-02
I have a Toshiba Satalite, L305 I put it into Hybernate or sleep ,, shut the lid and later on i come back and the the battery is dead...

no big deal when im at home.. but when im on the road it kinda sucks.. so i have to just shut it down.. thank god it boots up fast...

---

### Post by jaybok on 2010-05-02
So, I am not the only one.  That feels good in a way.  Update:  purposefully put the laptop to sleep and experienced the same problem.
There seems to be some conflict for sure.  Does anybody have a fix other than disabling sleep?  Thanks!

---

### Post by /Michael/ on 2010-05-02
It could be the case that suspend works on my Lenovo S10 since I set an empty password for the login keyring. I was just trying to debug this problem as described in [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) when I realized that resuming works. Everything I changed recently is the empty password!?!

---

### Post by /Michael/ on 2010-05-04
Unfortunately, one day later, things got back to normal: i.e. resume is not working anymore. For further details see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by jaybok on 2010-05-04
Thanks for reporting the problem Michael.  Hopefully, a fix will be on its way!

> **/Michael/ said:**
> Unfortunately, one day later, things got back to normal: i.e. resume is not working anymore. For further details see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

### Post by xinix on 2010-05-06
I'm having the same issue.  It's pretty frustrating when things that used to work just fine no longer work after upgrading.

---

### Post by swappa on 2010-05-07
Same thing here. 
Dell Latitude E6500

---

### Post by blampars on 2010-05-07
Same problem for me on both of my laptops

Dell Inspiron 9100
Dell Inspiron 8600

---

### Post by Sandertje on 2010-05-08
Same prob here with Dell Studio 1745. Hibernate *does* work, but it's very very very slow. rebooting is a lot faster. If I hibernate, resuming the session will result in a black screen for about 1 minute, then a black screen with blinking cursor for about 2 minutes, after which the mouse cursor appears (no movement of it though!). A minute or so later, the login screen finally appears, but laptop remains sluggishly afterwards. (for comparison, booting is about 20 seconds total on my machine).

---

### Post by Scooter_X on 2010-05-08
Same thing here. I don't know if the problems are related, but then my screen resolution went all out of wack, and my sound quit working. Serious. I'm in the process of partitioning my drive all over and starting over. Though I think I may head back to Karmic until I know I won't have that problem again.

---

### Post by mattPiratt on 2010-05-08
Acer TM 4102 - the same here on 10.04

---

### Post by TehWhale on 2010-05-08
Happens here too, Dell Inspirion 1464.

---

### Post by nicoeoc on 2010-05-09
I have the same problem, but as far as i experienced this i noted that it happens only when i purposely put the laptop into sleep, otherwise when it shuts to sleep automatically following energy saving settings i can restore the session with no problems...

I have a Dell Inspiron 1750, hope that this will be solved soon, or at least before 10.10 version x )

---

### Post by zcacogp on 2010-05-09
IBM X31s here, and it will neither Hibernate nor Suspend correctly. 

If you try "Suspend", it will (apparently) suspend OK, but when you try and bring it back then it will only get to a black screen. (The screen is working, the illumination is there, but it won't display anything.) Pretty much as described. 

"Hibernate" will apparently work OK as well, but when you re-boot it won't get to Ubuntu. It produces some lines on the screen and freezes at that stage, before you see the log-in screen. 

Both of these are tested with the closing of the lid (having set the desired behaviour appropriately) and forcing it by pressing the power button and choosing from the menu. 


Oli.

---

### Post by christopherbalz on 2010-05-09
I filed a bug at Ubuntu using:

  $ ubuntu-bug hibernate

  [https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/578020](https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/578020)

The 'ubuntu-bug' program automatically collects a bunch of basic information about your system, to assist the developers in fixing the bug.

I am running an IBM ThinkPad R51 laptop w/ ATI Radeon video card.  Suspend was working fine on 9.10 before the upgrade to 10.04.  Comes out of suspend and I can see and move the mouse pointer, but nothing else - the rest is black.  Ctrl-alt-F1 gives a working log-in from a terminal prompt.  'startx' does not immediately work from there as the system says that X is already running.

---

### Post by /Michael/ on 2010-05-10
My laptop resumes now correctly after a "pm-suspend" from console. After the fresh install of 10.04., resume did not work, then, some days later, like a miracle, it did, later again, black screen only but now, perhaps after the kernel update to "2.6.32-22-generic", resume after suspend works again ?! Some of you could perhaps try to boot with the kernel option "nomodeset" in order to see if the problem could be with KMS (kernel mode setting).

---

### Post by barkej on 2010-05-12
I'm glad I'm not the only one with sleep issues. Hibernate luckily seems to work ok for me atm. Sleep refuses to wake up and requires a forced restart.

---

### Post by efflandt on 2010-05-12
Have any of you tried **nomodeset** kernel parameter to use user mode video modules instead of the new default kernel mode (KMS) video driver.

I had trouble with my desktop unable to go into suspend or hibernate.  Suspend would shut off the hard drive, but blank video remained on and power remained on.  Hibernate saved RAM to swap and everything remained on, including blank video and hard drive. In either case I had to manually power off (hold power button for 5 seconds) and cold boot.

Since I have ATI video, either **nomodeset** or **radeon.modeset=0** kernel parameter resolved that, and both suspend and hibernate work (and glxgears is "much" faster).

---

### Post by monkeys on 2010-05-13
I have the same problem. Hibernate and sleep don't work for me - I have to restart my computer, and upon doing so, my network connections are disabled for some odd reason...

---

### Post by pastir on 2010-05-13
I've had this problem with the last two releases of Ubuntu.  I think I upgraded my memory about the same time.  I [read]("https://help.ubuntu.com/community/SwapFaq#Why%20do%20I%20need%20swap?") that your swap partition needs to be at least the size of your RAM in order to hibernate.  I haven't tried it yet, but that could fix the problem.

---

### Post by xboxSlayer on 2010-05-13
Same problem, Dell Inspiron 1525. After I shut it down and restart my network connections are disabled also.

---

### Post by mattPiratt on 2010-05-14
> **pastir said:**
> I've had this problem with the last two releases of Ubuntu.  I think I upgraded my memory about the same time.  I [read]("https://help.ubuntu.com/community/SwapFaq#Why%20do%20I%20need%20swap?") that your swap partition needs to be at least the size of your RAM in order to hibernate.  I haven't tried it yet, but that could fix the problem.

Read the comments, man :( Its not about hibernating, but waking up from hiberantion/sleep.

Are there any people NOT having this issue? What is their CPU,Graphic,Laptop manufacture?

---

### Post by bamuell on 2010-05-14
I have a Toshiba Satellite A205.  Hibernate and Suspend worked for the last year with Ubuntu 9.04 and 9.10 without problems. After upgrading to 10.4 Suspend and Hibernate create a blank screen and no response to keys or mouse. I have to do a hard power off to access my laptop again.

---

### Post by jaybok on 2010-05-15
A lot of folks are having this issue, and it does not seem related to a  particular set of hardware/conditions.  Hopefully a fix will be released  soon, and if Michael is correct, it already is!

Michael, your comment is very interesting.  Can you please provide step-by-step instructions for us to try?  I just tried and am still having "wake-up" issues.  Ubuntu 10.04 is current and updated.  Is this working for everybody?

Thanks!



> **/Michael/ said:**
> My laptop resumes now correctly after a "pm-suspend" from console. After the fresh install of 10.04., resume did not work, then, some days later, like a miracle, it did, later again, black screen only but now, perhaps after the kernel update to "2.6.32-22-generic", resume after suspend works again ?! Some of you could perhaps try to boot with the kernel option "nomodeset" in order to see if the problem could be with KMS (kernel mode setting).

---

### Post by /Michael/ on 2010-05-16
Unfortunately, disabling KMS did not help. You could press SHIFT at startup in order to see the boot loader menu, then edit the command line (ctrl-e I think), add "nomodeset" at the end of the boot entry and boot the system. But as I said, it did not change much on my system. For further details see also the discussion at [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/568711]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711").

What irritates me most is that it seems to me that the Ubuntu boot sequence differs from one boot to another. Sometimes I see a blinking cursor, sometimes a boot image, sometimes a white screen, sometimes not... Booting Ubuntu 10.04 is really fast but I dislike the feeling that I don't know what the system is doing. This morning I (re-)installed good old Lenny.

---

### Post by nikkkko on 2010-05-16
Same for me.  Dell XPS M1130.  Suspend and Hibernate produce blank screen/blinking cursor and require force power off.

---

### Post by lazymangaka on 2010-05-17
I'm experiencing the same problem with an ASUS X83V. Suspend produces a blank, lit screen with no HDD light activity, fans still on, and no system responsiveness. Requires forced restart. Hibernate produces a blinking cursor, no system responsiveness, and also requires a forced restart. These problems only started to occur a few days ago, prior to that suspend was working perfectly and being used frequently.

Did a recent update break it, perhaps?


**POSSIBLE FIX**

I removed the 8GB SDHC card that I had had in the internal card reader and now suspend and hibernate seem to be functioning perfectly. Maybe getting rid of removable media would fix someone else's problem as well.

---

### Post by nsstrunks on 2010-05-17
Same issue here on my Sony Vaio VGN-FW390.

I have noticed that the issue isn't consistent with my laptop.  Going into sleep is never an issue (I don't hibernate), but then about 70% of the time there's an issue coming out of sleep.

Sometimes it takes about 5 minutes to resume, other times it's 20+ minutes.  I haven't played around with it too much to figure out if it's a specific program that's causing the issue, cause that's the only difference that I see with my own machine...

Hopefully I'll have some time later on to play around with it and try sleeping with different things running to see if that has an effect.

---

### Post by a-user on 2010-05-17
there are several different issues with sleep/hibernation and lucid. all or most of them are caused by the kernel 2.6.32 that is used. this problems are not present if you use 2.6.31 or 2.6.33, 2.6.34 kernels from the mainline.

but if you chose mainline kernels you must take care yourself of building and patching for ureadahead and apparmor support.

maybe they will release sometime a fixed 2.6.32 kernel.

p.s. ofocourse there could be the small chance that your specific issue is not related to this kernel, although i doubt it.

---

### Post by nikkkko on 2010-05-17
I found a solution to my suspend/resume problem on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711").

Basically, I unmount my sd card before suspending and everything works fine.  Dell XPS M1330.

---

### Post by Jackson024 on 2010-05-17
I am having the same issue after I updated today.  Before Suspend didn't seem like it was working, it would blank the screen (but not turn off the backlight) but the fans and hard drive clicks never slowed a bit.   After the update it went into suspend and the screen went black (backlights off) and the fans shut off and the system LED was flashing like it should.  So I thought it was fixed and pretty happy... until I came back.  The system LED turned solid again and the fans and all kicked back on, but the video never came back, the backlights did not turn on at all.  I had to reboot using Atl+Prnt Screen + RSEIUB to get it back, tested again and the same thing.  I do not have any mountable media, just a Dell Studio 1537 with 4gb of ram, an Intel proc running 10.4 x64.  ATI video and I am using a ATI proprietary FGLRX driver.        EDIT:  After typing this I removed the ATI driver and rebooted, I can now come out of suspend.

---

### Post by revolver on 2010-05-18
> **/Michael/ said:**
> My laptop resumes now correctly after a "pm-suspend" from console. After the fresh install of 10.04., resume did not work, then, some days later, like a miracle, it did, later again, black screen only but now, perhaps after the kernel update to "2.6.32-22-generic", resume after suspend works again ?! Some of you could perhaps try to boot with the kernel option "nomodeset" in order to see if the problem could be with KMS (kernel mode setting).
"nomodeset" kernel parameter solved sleep/hibernate issue (hardware reboot on wake up) on my IBM X32 laptop with radeon mobility m6 video card 

Thanks for help

---

### Post by harshads on 2010-05-25
I've been having very similar problems.

My laptop will go to sleep just fine - I have it configured to go to sleep only when I press the power button.

However, it doesn't recover properly more often than not. When I press the power button to wake it up, the screen backlight comes on and I can hear the HDD and the GPU fan start spinning. But the screen remains blank and only way I can get my laptop to do anything is to force it off and restart.

I am not able to pinpoint the exact cause of this.  Closing the laptop screen and leaving it in sleep for a while both seem to cause the issue. If I suspend and resume fairly immediately it recovers fine (prompts me for my password and all)

I have used gconf-edit and changed everything relevant I could fing in apps>gnome_power_manager. The system is behaving fine (and in accordance with what I selected) except for this issue. 

I have a Dell studio 14z
It has an nvidia 9400 gpu and I have installed the latest drivers from the nvidia site (this issue persists and existed even before I installed them)
I am running Ubuntu Lucid as my only OS

Any fixes? Suggestions?

Edit: I have /home mounted in its own partition. I don't know how this might affect anything.

---

### Post by dmandn on 2010-06-10
How do you set this nomodeset?

---

### Post by akssps011 on 2010-06-10
Hibernation not working for me at all. It just seem to log of when I Hibernate. When I log in back the task bar looks distorted.
I am not able to work without hibernation as I need to carry on work for days. have to give a fresh start everyday.
**Is there any alternative to hibernation[urgent] **till this bug is fixed ?

btw, my system config is:
compaq presario desktop PC, P4, 1GB RAM.
I updated from kubuntu 9.10 to 10.04 and have all current security patches and updates.

---

### Post by ankanaan on 2010-06-21
same here, (it broke for me a week ago)

Ubuntu 10.04 LTS \n \l

Linux hal 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

I think I made the mistake of doing an update, something I don't do.  Probably while installing some extra stuff it upgraded other stuff.  I hate software involution.

cheers,

Antonio

---

### Post by a-user on 2010-06-21
i recently tested again the 2.6.32  ubuntu kernels and with the latest official one it even cannot shut off the pc. i mean, all is going right, all processes are stopped and so on and the last message ist:
somthing like no powerring off.

that's it. so it is basically the same issue as with suspend and hibernate. the kernel fails at actually powering off.

---

### Post by Atook on 2010-06-27
I'm having the same problem with a Dell Inspiron 8600, and no flash or removable memory in the unit. When sleeping or hibernating the only way to get back into the machine is via the power button.

I'm also running 10.04 on an Asus N61JQ and the unit doesn't suspend properly, the screen shuts off, but the HD and fans are still going, wearing on the battery. It resumes OK, but it's not really suspending

---

### Post by aurous_ on 2010-07-02
Same problem here, on a Toshiba Satellite. Have to hold down the power button to get back any function. Does not resume after sleeping when I close the lid

---

### Post by sa2u on 2010-07-02
I had this problem with Kubuntu 9.10, first installed in April, on my Compaq S6500nx desktop (ASUS motherboard, ATI 9250 video card). In 9.10, the PC could be put in suspend and hibernate OK. Resume from suspend would sometimes work. Resume from hibernate never did. At other times when I tried to resume, the HD and fan would  run furiously while the screen remained blank until I powered off. After some updates, resume from suspend wouldn't work properly at all.

This week I did a fresh install of Kubuntu 10.04. The computer will hibernate or suspend but resume fails every time -- a real nuisance. I hope a fix will be available soon.

---

### Post by domzals1 on 2010-07-03
I'm using a MacBook and although the system eventually goes to sleep, it takes a very long time once the lid is closed.

---

### Post by ankanaan on 2010-07-03
So, how does this work?  Should I change my mind now and install all upgrades I see and hope for the best?  

I was thinking about reinstalling from the CD and choosing no upgrades, as I always do.  I am affraid that as I install new ubuntu software - which I need and won't be installed from the CD - there will be upgrades in working parts of the system and break suspend againg.

Release early release often is great for development, an LTS release is not development and don't get the reason for this upgrade "fever".

cheers,

Antonio

---

### Post by brown12 on 2010-07-05
> **harshads said:**
> I've been having very similar problems.

My laptop will go to sleep just fine - I have it configured to go to sleep only when I press the power button.

However, it doesn't recover properly more often than not. When I press the power button to wake it up, the screen backlight comes on and I can hear the HDD and the GPU fan start spinning. But the screen remains blank and only way I can get my laptop to do anything is to force it off and restart.

I am not able to pinpoint the exact cause of this.  Closing the laptop screen and leaving it in sleep for a while both seem to cause the issue. If I suspend and resume fairly immediately it recovers fine (prompts me for my password and all)

I have used gconf-edit and changed everything relevant I could fing in apps>gnome_power_manager. The system is behaving fine (and in accordance with what I selected) except for this issue. 

I have a Dell studio 14z
It has an nvidia 9400 gpu and I have installed the latest drivers from the nvidia site (this issue persists and existed even before I installed them)
I am running Ubuntu Lucid as my only OS

Any fixes? Suggestions?

Edit: I have /home mounted in its own partition. I don't know how this might affect anything.

Same problem. Thanks for posting. 

Possibly related: this week, the shutdown command has resulted in a reboot loop, unless I removed the NetworkManager.state file that was corrupted by one of the failed resumes.

---

### Post by ankanaan on 2010-07-05
My latitude e6500 is back suspending and hibernating.  I noticed there was a kernel upgrade a few days ago.  I rebooted, still no suspending.  Then yesterday I suspended again and it is working.  No more upgrades in the next couple of years :-)

Antonio

---

### Post by kiMoi on 2010-07-08
Asus Notebook here, ATI graphics card. Had this problem until I unmounted my SD card, now it all works perfectly. Hope this helps someone.

---

### Post by ankanaan on 2010-08-02
hey kiMoi,

actually my problem is the same, it has nothing to do with upgrades, ( and I was bad mouthing the upgrades, sorry upgraders :-) it is the SD card, at least on my machine.  If I have the SD card in, the machine will just hang when I try to sleep.

cheers,

Antonio

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

I have noticed similar problems on a Toshiba Satellite A55-S106 with acpi-support. Suspend & Hibernate lock-up the system and I must reboot. 

Only solution I have found is to not use those features.

---

### Post by rafaelenr on 2010-08-10
I have same problem with Toshiba Satellite Pro U500 with Ubuntu 10.04 (kernel 2.6.32-24-generic), after I try to suspend the screen just locks and nothing is working.
After restart by holding the power button, wired network card not working, this is very annoying since i use it at work and i can only connect to internet through ethernet cable.

Any suggestions?

---

### Post by pablo180 on 2010-08-16
Same problem on Dell Inspiron 1525, and had it since moving to Lucid (Karmic was fine). I can suspend OK and resume OK, that all works fine nine times out of ten, but when I hibernate it seems to hibernate fine, but never resumes, it just boots back up again like a restart.

I am using 2.6.32-24-generic, none of the updates seem to have helped.

---

### Post by PetrDymov491 on 2010-08-21
Ìîæåò õîòü çäåñü ìíå êòî íèòü ñìîæåò îáúÿñíèòü êàêîé âèä  ïåðåäà÷è âèäåî ñèãíàëà íà   [ñâåòîäèîäíûé ýêðàí](http://www.ldm-group.ru) ëó÷øå?

---

### Post by pablo180 on 2010-08-22
> **pablo180 said:**
> I can suspend OK and resume OK, that all works fine nine times out of ten, but when I hibernate it seems to hibernate fine, but never resumes, it just boots back up again like a restart.

I fixed my problem, not sure if this will help anyone else but I thought that I should post it, just in case. 

My problem was that the laptop was suspending and resuming fine, but hibernation appeared to work, but always failed to resume from disk. 

Turns out my problem was related to [compcache]("http://code.google.com/p/compcache/"). 

When I typed into the terminal:

```
swapon -s
```

I got back something like:

```
Filename       Type             Size	Used     Priority
/dev/ramzswap0 partition                         100
/dev/sda2      partition	5245212	378256	 -1

```

From what I can gather when coming out of hibernation it must have been trying to load from the highest priority swap, which in this case is the RAM used by compcache. With 4GB of RAM I really didn't need compcache anyway so thought it best to remove, which I did by:

```
sudo swapoff /dev/ramzswap0
```

Then:

```
gksudo nautilus
```

Then I navigated to the folder: 

```
/usr/share/initramfs-tools/conf.d/
```

and deleted the file, compcache. 

Then.
```

sudo update-initramfs -u 
```

And reboot and hibernation is now working fine! A check of swapon -s now gives:

```
Filename       Type             Size	Used     Priority
/dev/sda2      partition	5245212	378256	 -1

```


So if you have a hibernation problem with Lucid, it may well be worth removing compcache, I don't think it is much use when you have a decent amount of RAM anyway. 

I've tried hibernating a few times and everything seems to work perfectly! So just four months after installing Lucid I have a proper laptop again!

If that doesn't work though, you can re-add compcache again by editing the initramfs.conf file:

```
gksudo gedit /etc/initramfs-tools/initramfs.conf

```

OR

```
gksudo nautilus
```

And then navigate to the folder gksudo gedit /etc/initramfs-tools and edit the file initramfs.conf

About half way down is the compcache section, just add a value in between the quotation marks for COMPCACHE_SIZE, e.g.

```
COMPCACHE_SIZE="20%"
```

Examples are in the file for other values such as kilobytes, MB, GB. 

Then enter the following into a terminal:

```
sudo update-initramfs -u
```

And reboot. 

You can check to see if it is working by putting

```
swapon -s
``` 

Into a terminal. You should see something like:
```

Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	823076	0	100
/dev/sda2                               partition	5245212	0	-1
```

---

### Post by jfgauthier on 2010-09-02
I got the same issue here!
System information report, generated by Sysinfo: 02/09/2010 05:38:09
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
    GNOME: 2.30.2 (Ubuntu 2010-06-25)
    Kernel version: 2.6.32-24-generic (#42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010)
    GCC: 4.4.3 (x86_64-linux-gnu)
    Xorg: unknown (21 July 2010  01:03:39PM) (21 July 2010  01:03:39PM)
    Hostname: jean-francois-laptop
    Uptime: 0 days 0 h 29 min

CPU INFORMATION
    GenuineIntel, Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
    Number of CPUs: 2
    CPU clock currently at 2000.000 MHz with 2048 KB cache
    Numbering: family(6) model(15) stepping(13)
    Bogomips: 3990.22
    Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm

MEMORY INFORMATION
    Total memory: 3010 MB
    Total swap: 6236 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  HL-DT-ST 
        Model:  DVD+-RW GSA-T21N 
    SCSI device -  scsi2
        Vendor:  ATA      
        Model:  ST9160310AS      

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Dell Device 022f
    PCI bridge(s)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
        Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
        Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
        Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01)
    USB controller(s)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
        Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    ISA bridge
        Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
        Subsystem: Dell Device 022f
    IDE interface
        Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 022f

GRAPHIC CARD
    VGA controller
        Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
        Subsystem: Dell Device 022f

SOUND CARD
    Multimedia controller
        Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 022f

NETWORK
    Network controller
        Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Device 000a
    Ethernet controller
        Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
        Subsystem: Dell Device 022f

---

### Post by audiofreq on 2010-10-11
Yup extremely frustrating.  Worked for a week then despite changing nothing on my setup, no updates, no new software, no new configs, etc and i get this problem.  Charge my battery, close the lid (or manual suspend/hibernate), put laptop in bag, 30 mins later go to pull laptop out bag and it's roasting and the battery shows signs of excessive use.  Even more frustrating is if left longer it will consume until the battery is dead. I know this isn't a constructive comment but are Ubuntu going to pay for a new battery? Losing faith in ubuntu.  On another laptop random sound issues too. Upgrading to me should imply inherited stability.

---

### Post by pehden on 2010-10-11
This is happening with 10.10 on my laptop Toshiba Satellite, it was with 10.04 but its even worse now, it was working 8/10 times with out out this issue but now it fails 4/10.


This is bad.

---

### Post by Aitaix on 2010-11-01
same issue

Dell Latitude E6510

Ubuntu 10.10

---

### Post by pablo180 on 2010-11-02
Aitaix, Pehden, have either of you tried removing [Compcache]("http://code.google.com/p/compcache/")? It solved all my problems to do with hibernation and also sleep, it now works ten times out of ten. Haven't had a problem in months either when hibernating or coming back from sleep.

[There are instructions above on how to do it above]("http://ubuntuforums.org/showpost.php?p=9753023&postcount=53"), it is pretty simple, and if it doesn't work, you can always put the file back.

---

### Post by jaybok on 2010-11-02
Hi Pablo,
Can you please instruct on how to put it back?  I will try it and get back to the group; am skeptical without knowing how to put it back - just in case I really need it!  Thanks.

> **pablo180 said:**
> Aitaix, Pehden, have either of you tried removing [Compcache]("http://code.google.com/p/compcache/")? It solved all my problems to do with hibernation and also sleep, it now works ten times out of ten. Haven't had a problem in months either when hibernating or coming back from sleep.

[There are instructions above on how to do it above]("http://ubuntuforums.org/showpost.php?p=9753023&postcount=53"), it is pretty simple, and if it doesn't work, you can always put the file back.

---

### Post by pablo180 on 2010-11-02
> **jaybok said:**
> Hi Pablo,
Can you please instruct on how to put it back?  I will try it and get back to the group; am skeptical without knowing how to put it back - just in case I really need it!  Thanks.

No problem, [I have added how to put it back again to the original instructions]("http://ubuntuforums.org/showpost.php?p=9753023&postcount=53").

---

### Post by jaybok on 2010-11-04
> **pablo180 said:**
> No problem, [I have added how to put it back again to the original instructions]("http://ubuntuforums.org/showpost.php?p=9753023&postcount=53").

Thanks Pablo.  Will report to the group how this goes after some testing.

---

### Post by pablo180 on 2011-05-05
Started having the same problems again. For some reason hibernation, which I seldom use, hasn't been working and I only recently noticed.

I checked, and somehow compcache has installed itself again. [I removed this again following the instructions]("http://ubuntuforums.org/showpost.php?p=9753023&postcount=53") and hibernation works flawlessly again. 

Presumably some update or other has added it again? It's annoying and took me several days to realise what was causing it. So if anyone has already removed compcache, and hibernation has once again begun playing up, looks like you'll have to remove it again.

---

