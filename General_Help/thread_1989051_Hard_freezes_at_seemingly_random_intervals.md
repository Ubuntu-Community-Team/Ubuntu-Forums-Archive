---
title: "Hard freezes at seemingly random intervals"
date: 2012-05-28
forum: General Help
---

### Post by vectorboson on 2012-05-28
Hello, community. I posted this in another thread, but I now believe it's a separate issue, so I'm floating it separately to see if anyone has any ideas:

My entire system will freeze seemingly at random: sometimes when it's doing something (e.g. compiling, installing things), sometimes when it's just sitting around and I haven't touched it for several minutes - in any case it happens even with suspend and brightness reduction turned off. This has happened with a wide variety of applications open, and it does not seem to have anything to do with any individual programs. The system does not respond to SysRQ commands when it has locked up in this way. The machine is an essentially brand new HP Pavilion dm1-4010us, and it has done this in both a 64-bit installation upgraded from 11.10 and a 32-bit fresh installation of 12.04. I have it dual-booting Windows 7, and have not encountered any issues on Windows.

 System specs are:
 AMD E-450 Processor
 4GB RAM, memtested and it's fine
 Radeon HD 6320 Graphics
 Broadcom BCM4313 Wireless controller, which has given me trouble before on 11.10

 Though I am by no means an expert, I suspect the wireless controller may be related somehow: on 11.10, before I used the driver workaround in the networking support forum, I was getting much more frequent lockups along with unacceptably terrible wi-fi performance. The SysRQ keys DID work for these lockups. Once I did the driver override, wi-fi performance dramatically improved but I continued experiencing these freezes, and SysRQ no longer worked during them. I notice that the wi-fi fix appears to be applied by default in 12.04, as I did not have to do anything to get acceptable performance out of it when I reinstalled.

Two additional points:
-When this happens with audio playing, it stops immediately.
-This has occurred both with open-source video drivers and with flgrx (post-release updates) in use.

 Anyone who has any theories or ideas for additional tests to perform, let me know and I'll try them as I'm able. I use Ubuntu for work and this is really making it hard to get anything done.

---

### Post by pureblood on 2012-06-02
Look at this post: [http://bit.ly/KH1uJ7](http://bit.ly/KH1uJ7)
It seems a lot of people are experiencing the same exact problem. Have you tried to keep the computer on without the wireless driver on to see if this prevents it from freezing? What wireless card/wireless driver do you use?

---

### Post by pjbroad on 2012-07-03
I have exactly the same freezing issue with my HP DM1-4125sa.  This has the same CPU, Graphics and wifi as your HP dm1-4010us.  The suggested launchpad thread appears to be filled with random freeze problem from many different hardware combinations and with hard and soft freezes too.  My freeze is always hard, requiring a power off reboot.  I cannot switch to a VT or use SysRQ.

I have the same random freeze with Debian Wheezy (testing), Ubuntu 12.04 and Ubuntu 12.10, Unity 2d/3d  and Gnome.  It does not appear to make a difference whether I use the proprietary or open source graphics driver so I'm tending to rule that out.

I've tried inducing the problem by loading the system with cpu, network, and graphics  loads.  Disconnecting/reconnecting wired network, wifi, power, suspend/resume etc but nothing.  The only reliable way to induce the problem is to briefly forget about it.  I must admit it's driving me crazy!  There is never anything of note in the system logs.

---

### Post by vectorboson on 2012-07-03
I believe this problem, or at least my version of it, is caused by a bad disk I/O interaction between the motherboard and the Linux Kernel. I did some further tests, and found the following:

-it happens even with every possible wi-fi driver blacklisted.
-it does *not* happen with no programs running at all and the machine sitting completely idle, disconnected from the internet, even if left up for over 72 hours without suspending.
-it tends to happen quite quickly (within a few minutes) when I initiate a disk usage-heavy task like compiling software in a terminal, though even this is unreliable and it may stay up for over an hour.
-upgrading the Kernel to 3.4.x does not help.
-it happens even on KDE Fedora, so it's not a bug in Gnome, Unity, or Ubuntu.

A friend suggested that it could be a bug in the disk controller or host adapter that the manufacturer worked around for the Windows drivers but has not publicized so Linux can fix it. I'm not sure what else to do; I haven't been able to find any sign that it's a known issue with the Kernel team. I'd prefer not to have to buy another new computer to be able to run Linux, but I can't think of any further possible avenues for a workaround on our ends.

---

### Post by MrArch on 2012-07-08
Interesting, found your post via
[http://ubuntuforums.org/showthread.php?t=1903054&page=2](http://ubuntuforums.org/showthread.php?t=1903054&page=2)

I'm on a dm1-4000sd myself, running Arch Linux 64 bit and experiencing hard lockups too. When you say you blacklisted every Wifi driver iwconfig did not report any wlan0 devices right? (just to be sure).

The only other far fetched guess I could make is that we have a CPU affected by this problem:
[http://it.slashdot.org/story/12/03/06/0136243/amd-confirms-cpu-bug-found-by-dragonfly-bsds-matt-dillon](http://it.slashdot.org/story/12/03/06/0136243/amd-confirms-cpu-bug-found-by-dragonfly-bsds-matt-dillon)

I'm currently running some compiler tests and trying out various HD stress situations to see if I can consistently reproduce the bug.

---

### Post by vectorboson on 2012-07-09
I didn't think to check the wlan0 devices and have since reformatted to a different distro (which also didn't work), but I do remember hitting the wireless switch on the keyboard and having it never go to "on", which seems to me like it would imply that no device was recognized. If it would be useful to investigate beyond that I could blacklist everything again in a few days when I'm back where the computer is.

---

### Post by dino99 on 2012-07-09
2 things to check:


- is the graphic driver well activated ?  ( sudo jockey-gtk )
- is there a process hanging ? (install & use htop )

---

### Post by Oldcanoe on 2012-07-09
Greetings all,
 
A noob to ubuntu here; yesterday full install of 12.04 from verified disc on old xp sp3 machine (Athlon 64 bit, 2 Gb memory). Wireless and network connected ok. Then discovered that after 3~5 minutes mouse and keyboard would freeze and about 1/3 of the time the screen would go black. Reinstalled 12.04 and samey same regardless of activity (web, attempting to play movie, downloading software, idling). Attached to home router by cable, though wireless configured and switched off. 
 
Hard boots are needed to get things moving again. I am new enough to Linux that I do not yet know the appropriate CNTRL-ALT-etc commands.
 
This was starting to happen with xp so it could be a hardware issue. But then found and read parts of a lengthy thread on this forum regarding similar problems with 12.04 that others were having and wondered.... perhaps not hardware after all.
 
Also video software (VLC and the onboard one) will not play commercial dvd's. Says they are encrypted. Do play ok with home made videos. Mainly I want the machine for a dvd player in the living room (also backup desktop) because its monitor is better than the tv's.
 
So far positive and deltas for this ubuntu noob:
 
"+" :D fairly easy download and install; boots faster than xp though not as fast as w7 on the recently new i3 Dell; common software works about same as windows stuff (word processors, spreadsheet, vlc, audacity, etc.)
 
"deltas" :( very frustrating to have a machine that seizes up after only a few minutes.
 
Any leads greatly appreciated. Thanks in advance.
 
p.s. I stuck all this here because it sort of fit and I could not see how to start a new thread.

---

### Post by MrArch on 2012-07-11
Tried to do some harddisk tests by running badblocks in write mode to fill the entire drive with random data, no b43 module loaded. Took about 3.5 hours and finished without problems. After that I reinstallated the system using the latest kernel 3.4 and I noticed it complained about missing microcode fixes from AMD, which wasn't the case with older kernels. So installed the amd microcode update and fully updated the system. Of course, no lockups (yet) but I'm conitinuing testing/playing flash youtube/etc. and let you know the results.

Edit @dino99: there are no processes hanging, the system just lockups completely, SysRQ does not work, mouse hangs, musics stops so definitely not a user space program but something kernel or hardware related.

---

### Post by halfmanhalfpint on 2012-07-12
I have a HP Pavilion dm1-4004sa. I'm running Mint 13.
I have been getting the same freezes, but since updating the
firmware a few weeks ago I haven't had one freeze.
Not sure if this is a coincidence,or if it is actually fixed.

I keep a small Windows 7 partition to do the updates.
Last update was for the BIOS. Downloadable from here if you removed Windows - [http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4062&lc=en&cc=uk&dlc=en&sw_lang=&product=5198195#N475](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4062&lc=en&cc=uk&dlc=en&sw_lang=&product=5198195#N475)

Maybe worth trying out?


Michael

---

### Post by MrArch on 2012-07-12
Thanks for the tip, I'll try to update the bios tonight. But first I have to reinstall windows so I can run the bios update... don't see anything spectacular mentioned in the update documentation though, so I remain sceptical.

---

### Post by MrArch on 2012-07-12
Two interesting updates:
1. Just updated the bios, from version F.01 to version F.16 so there could be a lot of changes. Didn't find any changelog for bios <= F.13 so I'm not sure what changed.
2. Found this very interesing post about users having the same lockup/freeze:
[https://bbs.archlinux.org/viewtopic.php?pid=1053607#p1053607](https://bbs.archlinux.org/viewtopic.php?pid=1053607#p1053607)
I get the same message at boot:
```
SP5100 TCO timer: mmio address 0xb80430 already in use
```So I will try to disable the thermal module like they do and see if that helps.

---

### Post by MrArch on 2012-07-16
Good news, I'm fairly sure I've fixed the lockups. For the last 4 days I haven't had a lockup. This is what I did:
1. Updated the bios from F.01 to F.16
2. Boot the kernel with thermal acpi off, for example:
```
kernel /vmlinuz-linux root=/dev/mapper/root cryptdevice=/dev/sda3:root ro thermal.off=1

```
3. Blacklist the sp5100_tco module
```
blacklist sp5100_tco

```
A big help was this post on the arch linux forum:
[https://bbs.archlinux.org/viewtopic.php?pid=1053607#p1053607](https://bbs.archlinux.org/viewtopic.php?pid=1053607#p1053607)

It seems the instability was caused by the sp5100_tco module and/or the thermal acpi module. I've used the netbook for over 5 hours each day, for the last four days, doing various stress tests, surfing the web, playing youtube, compiling kernels, etc. and it seems finally stable!

---

### Post by Stylebox on 2012-07-19
Glad to hear someone is getting their Dm1-4010us working.  I have the same machine with a similar problem.  Not a complete lock-up ... just keyboard and trackpad stop responding.  Unfortunately, changes with thermal and sp5100_tco don't have any effect.  Thankfully, I can still plug in USB keyboard and mouse.

Some differences -- I'm using the radeon driver and I haven't installed the proprietary wireless drivers (yes, I get horrible wireless at the moment).

Seems like different but related issues.  I agree with the above comments that it appears to be thermal and/or IO related but haven't really been able to find the culprit.  

Graphic performance seems fine with the radeon driver -- video plays well.  Laptop stays cool and is otherwise responsive.

---

### Post by MrArch on 2012-07-20
@Stylebox: although my computer completely freezes the bug is probably related. Take a look at this thread, some people have the same keybaord freezing, these guys have really dived into it:
[http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavilion-DM1-4033ef-linux-freezes-randomly/td-p/1339919/page/2](http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavilion-DM1-4033ef-linux-freezes-randomly/td-p/1339919/page/2)

---

### Post by pjbroad on 2012-07-22
I've been running with the grub option "thermal.off=1" set on my  dm1-4125sa for a few days and, so far, no freezes. The best its been  since the day I bought it.

---

### Post by justinfx on 2012-07-31
Running Asus Laptop R500V, Ubuntu 12.04.

I started out thinking it was video drivers and X, then a kernel bug, also tried the thermal grub option above.  It would still hard freeze - couldn't ever pinpoint what exactly it was.  Nothing ever showed up in the logs.

This post on Arch Linux's forums helped me.  Haven't had a hard freeze in three days.  Was having them at least twice a day before.

[https://bbs.archlinux.org/viewtopic.php?id=145425](https://bbs.archlinux.org/viewtopic.php?id=145425)

---

### Post by RDV on 2012-08-13
I would like to thank "MrArch" for his post #13 in this thread. Following his instructions has eliminated my random system freezes with Ubuntu 12.04 on a HP Pavilion DM1-4010US.

---

