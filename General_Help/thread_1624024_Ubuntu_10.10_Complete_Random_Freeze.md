---
title: "Ubuntu 10.10 Complete Random Freeze"
date: 2010-11-17
forum: General Help
---

### Post by boot_sectorz on 2010-11-17
I have installed 10.10 and experience Random freezing. The freeze is so bad and comes so random it can be 1 min to 2 days of using it. But after the freeze, cold, I can't boot into any of my other OS (XP and Win 7). I can formated the first 4 times, and after reading, dicovered I can recover grub by 
```
fsck /dev/sda5
```
When I live-boot.

I have tried all that I have read and find nothing. I feel ashamed to admit that my windows OS are more reliable that Linux, Ubuntu for that matter.

This is My System:
Dell Latitude D630 Laptop
Nvidia Graphics
4GB Ram with 320GB HDD
Broadcom Crystal HD Card
Broadcom wifi
Ubuntu x64

Any help? It is really a disaster for me to work in windows

---

### Post by boot_sectorz on 2010-11-24
It just got worse. I bootup, run google-chrome. Click on a link and the whole screen turns black, ubuntu shuts down!!

There was a time Ubuntu was not just fun, but it was reliable! You could do anything and know for a fact you be working, unless you run out of battery power. Now I have no idea if I can even type a paragraph without a problem. Not even sure my hard drive is safe with all this cold boots I have done.

What made it reliable made me forget about other OSs. I have not seen that with 10.10, makes me switch back and be amazed that windows works??? That hurts. I have installed all possible updates, googled all possible ideas, and now even the forum gets no reply. I move a step back now, format and install 10.04. Hoping that will still work

---

### Post by gabore on 2010-12-13
10.10 freezes here too, but a restart is enough, it doesnt take grub with it. Usually it happens after a few hours for me.

---

### Post by Linux-Djihad on 2010-12-13
[LEFT]I have the same problem since I have my PC, first with Ubuntu 9.10, then 10.04, and now 10.10. it freezes and reboots by itself, seldom after 10 minutes, but mostly once a day. 
The repair service didn't find anything because they used their own HD with MS Windows on it. Now I have a suspicion:

2 days ago I reinstalled the whole system to have a basic system, without nvidia drivers. I haven't had any freeze yet. Without nvidia drivers one of my fans (GPU or CPU, didn't look yet) runs louder, that means that the nvidia driver always slows the fan down. A decreased fan could overheat the card which could lead to a complete freeze. Months ago there was a bug which causes the fan control to not respond correctly ([http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA)). Maybe still the same issue? 

I will keep the basic nv drivers for the next 2 weeks. If I don't get a freeze then, I know that it's this freaking nvidia driver. And by the way. I ran S.M.A.R.T. HD and memtest RAM checks too, and didn't find errors as they didn't find at the repair service. So I began to narrow it down and I think this is related to the nvidia drivers (for now). When I get a freeze again in the next days, I don't have any clue anymore. 

Do you use nvidia drivers too? 

By the way. It doesn't matter if I use the nouveau drivers or the binary drivers from nvidia. I have the freeze with both of them.

[UPDATE]
I just had a freeze and reboot again, so I don't know what I still should do :(
[/LEFT]

---

### Post by gabore on 2010-12-13
> **Linux-Djihad said:**
> [LEFT]I have the same problem since I have my PC, first with Ubuntu 9.10, then 10.04, and now 10.10. it freezes and reboots by itself, seldom after 10 minutes, but mostly once a day. 
The repair service didn't find anything because they used their own HD with MS Windows on it. Now I have a suspicion:

2 days ago I reinstalled the whole system to have a basic system, without nvidia drivers. I haven't had any freeze yet. Without nvidia drivers one of my fans (GPU or CPU, didn't look yet) runs louder, that means that the nvidia driver always slows the fan down. A decreased fan could overheat the card which could lead to a complete freeze. Months ago there was a bug which causes the fan control to not respond correctly ([http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA)). Maybe still the same issue? 

I will keep the basic nv drivers for the next 2 weeks. If I don't get a freeze then, I know that it's this freaking nvidia driver. And by the way. I ran S.M.A.R.T. HD and memtest RAM checks too, and didn't find errors as they didn't find at the repair service. So I began to narrow it down and I think this is related to the nvidia drivers (for now). When I get a freeze again in the next days, I don't have any clue anymore. 

Do you use nvidia drivers too? 

By the way. It doesn't matter if I use the nouveau drivers or the binary drivers from nvidia. I have the freeze with both of them.

[UPDATE]
I just had a freeze and reboot again, so I don't know what I still should do :(
[/LEFT]
Yepp, using NV drivers here, for a mobile 9800m gts. And yes, I had problems with them since 7.04, though this freezing appeared only with 10.10. For me it doesn't restart by itself, it's just that I can move my mouse but no window or any UI responds. So have to restart myself. BTW, what is the soft restart combo? SysRq+Alt?

---

### Post by pveurshout on 2010-12-18
> **Linux-Djihad said:**
> [LEFT]I have the same problem since I have my PC, first with Ubuntu 9.10, then 10.04, and now 10.10. it freezes and reboots by itself, seldom after 10 minutes, but mostly once a day. 
The repair service didn't find anything because they used their own HD with MS Windows on it. Now I have a suspicion:

2 days ago I reinstalled the whole system to have a basic system, without nvidia drivers. I haven't had any freeze yet. Without nvidia drivers one of my fans (GPU or CPU, didn't look yet) runs louder, that means that the nvidia driver always slows the fan down. A decreased fan could overheat the card which could lead to a complete freeze. Months ago there was a bug which causes the fan control to not respond correctly ([http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA0MA)). Maybe still the same issue? 

I will keep the basic nv drivers for the next 2 weeks. If I don't get a freeze then, I know that it's this freaking nvidia driver. And by the way. I ran S.M.A.R.T. HD and memtest RAM checks too, and didn't find errors as they didn't find at the repair service. So I began to narrow it down and I think this is related to the nvidia drivers (for now). When I get a freeze again in the next days, I don't have any clue anymore. 

Do you use nvidia drivers too? 

By the way. It doesn't matter if I use the nouveau drivers or the binary drivers from nvidia. I have the freeze with both of them.

[UPDATE]
I just had a freeze and reboot again, so I don't know what I still should do :(
[/LEFT]

Random freezes & nVidia drivers in use here, too. I'll keep an eye on temperatures - hadn't thought of that yet. Usually I'm getting freezes while using Flash in Chrome/Opera (surprisingly Firefox seems to be doing better) or while playing OpenTTD with a freakishly large game that heats up my CPU to up to 99 degrees Celsius. Usually everything slows down noticeably, though, so I'd assume everything is in order and actual overheating does not occur. Also I'm getting freezes under normal circumstances by just scrolling through an OOorg document, or something. But who knows..!

---

### Post by gabore on 2010-12-18
> **pveurshout said:**
> Random freezes & nVidia drivers in use here, too. I'll keep an eye on temperatures - hadn't thought of that yet. Usually I'm getting freezes while using Flash in Chrome/Opera (surprisingly Firefox seems to be doing better) or while playing OpenTTD with a freakishly large game that heats up my CPU to up to 99 degrees Celsius. Usually everything slows down noticeably, though, so I'd assume everything is in order and actual overheating does not occur. Also I'm getting freezes under normal circumstances by just scrolling through an OOorg document, or something. But who knows..!
Hmm, interesting. The last few times it happened to me was when I actually was writing a few pages in OpenOffice Writer...

---

### Post by pveurshout on 2010-12-18
> **gabore said:**
> Hmm, interesting. The last few times it happened to me was when I actually was writing a few pages in OpenOffice Writer...

By the way, just noticed your symptoms include 'soft freezes'. Mine are always hard, while the occasional soft freezes are all X-related. Soft reboot combo is AltGr+SysRq+REISUB (though even that doesn't work in my case :(). Make sure to wait a few seconds between each command; especially after E in order to give applications a fair chance to end softly and S to make sure all data is written before the U and B commands follow

---

### Post by Simon_WM on 2010-12-18
A fellow freeze companion, I've had the same.. but thinkit might be my HD playing up...

So i've loaded Windows 7, just to check some files and shizzle, and update the bios, then gonna re-run the diagostics, so see if thats cleared my problem, if not i have a bigger problem to solve !!

---

### Post by adysko on 2010-12-29
I am experiencing the same problem with Dell Latitude D630 (NVidia). This definitely started when I upgraded to Maverick (64-bit). My observations are as follows:
 - it happens rather quickly when I use NVidia drivers (manual or included with the system)
 - It still happens sometimes even if I work with no visual effects.
 - when it happens all is frozen, no response to keyboard or touchpad. Most of the time Caps Lock and Scroll Lock blinking.
 - yesterday I also experienced screen going totally scrambled ("snowy" like loosing reception on an old TV screen)
 - It is much more likely to happen when I browse internet or watch a DVD, but not only.

I somehow believe it must be temperature related, as yesterday I had this "snowy" screen problem and this would prevent the laptop from loading both Ubuntu and Windows systems for a while. The screen would go "snowy" very shortly after logging into the system. The back of the laptop was very warm. After a waited for a while it all went back to normal. I never had this type of problem earlier in windows or in any other Ubuntu versions before Maverick. Quite disappointing, I have to say but I suspect there is no easy fix apart from not using native drivers and hoping for the best or rolling back to 10.04. I would consider going back but it is just too much hassle...

---

### Post by Trapper on 2010-12-29
I am having many freeze ups with a new install of 10.10 i386 too. I have nvidia video but _do not_ use the nvidia 3rd party drivers. I'll bet my boots the difficulty does not relate to nvidia video. I have installs of 9.10 and 10.04 on this box. They both work just fine. I personally think 10.10 has a mysterious sickness affecting a lot of people that needs to be found. I'm not going to waste my time getting it to maybe work. This is someone elses problem. I'll wait.

---

### Post by mnoyes on 2011-01-16
FWIW I've been having the same problem on a Dell mini 10 since I upgraded to 10.04 and then 10.10. The notebook just freezes -- no response to the keyboard, no response to disconnecting the power cord, etc. Just plain frozen and I have to do a hard reboot. I've been working the various threads but there seem to be too many answers that later turn out to work for some and not for others (e.g. disable irqbalance), so I haven't invested time in trying them out one by one. 

I run ubuntu 10.10 on two other machines: a Dell Mini 9 and a Dell M1330. I have not had freezes on either one. Weird.

I have been using Ubuntu since 8 and this is the worst problem yet, in terms of PITA (lost work) and lack of a solution.

---

### Post by gabore on 2011-01-17
Well the issue did not occur for weeks now... All I do differently is not editing documents for long periods of time, only few minutes...

---

### Post by wolfv on 2011-01-24
Let me add my grievances to yours.  My system freezes from time to time and I can't get to the bottom of the problem.  My rig is different from yours (almost all laptops), it's a big desktop that is my main computer (i5-750 with a huge Thermaltake case and water-cooling, running at default values, even without the Turbo Boost on).  Ubuntu 10.10 freezes randomly, mostly when left idling, without a particular task (apart from downloading a file).  This never happened with 10.04 (my uptimes were between 20-40 days at a time) with the same rig.  And, oh, yes, I also have an Nvidia GPU.

I am on the verge of reinstalling Ubuntu, but it will definitely be 10.04 that I'll go back to.

I am very much pissed off by this, I can tell you

---

### Post by dnguyen1963 on 2011-01-24
I rolled all the way back to 8.04.  The last rock stable version of Ubuntu.  I have PCLinuxOS 2010 on my other computer and have no random freezes.  Check out the random freezes thread on this forum...it has gotten over a quarter of a million views and 165+ pages of posts...you are not alone!

---

### Post by gabore on 2011-01-24
Hmm, I just got another freeze, but this time i was only having some pdfs open, and I could restart ubuntu by ctrl + alt + delete, alt+r.

---

### Post by troll1602 on 2011-02-03
Same problem here. I just started getting these crashes this week and have been running 64-bit 10.10 since November. What happens to me is a total crash; no mouse, no keyboard, screen freezes, REISUB doesn't work, just nothing.

A first I thought that I might have some bad RAM, so I tried to run memtest at boot, but got this error:
```
error: too small lower memory (0x99100 > 0x95800)
```

I think this is unrelated though, after reading about [this bug.]("https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/560839")

Tried looking through logs, couldn't find anything. Now just lost :-) Here are a few specs on my computer if anyone is interested:

Comp: Dell Studio XPS
OS: Ubuntu 10.10 (Kernel 2.6.35-25-generic (x86_64))
CPU: Intel Core i7
RAM: 8154MB
Gaphics: Nvidia GeForce GTS 240

---

### Post by gabore on 2011-02-03
Hi. Have you tried the ram test booting from a separate memtest cd?

---

### Post by troll1602 on 2011-02-04
Yep, just ran memtest from a usb drive. I also ran a diagnostic program that Dell had installed on the BIOS. I did one pass for each and both found zero errors. I am running a SMART test on the hard drive just in case, details are [here]("https://help.ubuntu.com/community/Smartmontools"), if anyone else is interested. I will post the results once the test finishes in a couple of hours. 

So, as of now it doesn't look like the CPU or RAM. SMART will tell me if it is the hard drive. If that comes out clean, then I guess this has to be some sort of crazy OS bug.

Thoughts?

---

### Post by troll1602 on 2011-02-04
Still running the SMART test. However, I was checking internal temperatures with lm-sensors and got this:
```

user@computer:~$ sensors
it8720-isa-0a10
Adapter: ISA adapter
in0:         +0.86 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.91 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.15 V
fan1:        732 RPM  (min =    0 RPM)
fan2:        927 RPM  (min =    0 RPM)
temp1:      +127.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +22.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
temp3:       -63.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +0.000 V

```

So, a little google searching told me that "temp1" is the internal temp, "temp2" is the cpu temp, and I don't know for "temp3" but it looks disabled anyway. 22C sounds normal for the CPU, but 127C for the internal temp? I can touch my computer without burning my hand, so it must be a weird error :-)

**EDIT:** SMART test completed with no errors!

---

### Post by beetlejuice321 on 2011-02-09
I have been having the exact same problem.  I am using Ubuntu 64bit 10.10 on a laptop with Nvidia drivers. I also noticed some similar problems with 10.04 however, anyone else?

I dual boot with Windows 7 64bit. No problems at all. Windows always runs great. 

Testing I have done included installing other Linux distros such as Fedora (64bit). Guess what? The exact same problems with locking up occurred, even without using the standard video drivers included with the base install. 

Most research I have done online indicates this is a common error related to the last few versions of the kernel. Before this my laptop wouldn't even boot unless I pressed any key and held it down! That too was error with newer kernel.

Whats happening with Linux anymore? Its like everything keeps breaking more and more with each release. Its not the new software I am talking about (Gnome, or Apps), its the damn kernel updates breaks things all the time lately.

---

### Post by beetlejuice321 on 2011-02-14
I just wiped the partitions again. This time I installed Ubuntu 32bit. System has been running on my laptop for hours, even went in to sleep mode, still no issues! 

I have been using 64bit Linux for years, but there are still so many bugs...what gives? Actually there is probably very little benefit to using 64bit vs 32bit Ubuntu at this point anyways.

Hopefully they get their 64 bit bugs worked out...I mean we have had 64 bit kernel's for nearly 10 years!

---

### Post by afrodeity on 2011-02-15
try downloading the latest Nvidia drivers (if you have a Nvidia card) and installing them manually.

---

### Post by troll1602 on 2011-02-15
> **afrodeity said:**
> try downloading the latest Nvidia drivers (if you have a Nvidia card) and installing them manually.

Aside from installing the latest drivers and waiting to see another crash, is there anyway to test that my current Nvidia drivers are causing the crashes? I would like to reproduce the crash and know exactly whats going wrong :-)

Also, in the last week I have only seen one crash as apposed to the 2 crashes a day when I first started posting. Not sure if I really changed anything.

---

### Post by dokter on 2011-02-21
Hi guys... 

I've been running on those freezing problems since last week... Have 10.10 64bits installed since december on my laptop (Dell E6500)running without freezing problems... 

I've found the solution... There might be a bug with the nVidia driver and the 64bit distro.. I've did the solution provided in the this link and it worked for me:

[http://www.nvnews.net/vbulletin/showthread.php?t=158729]("http://www.nvnews.net/vbulletin/showthread.php?t=158729")

Hope this help!

---

### Post by troll1602 on 2011-02-28
> **dokter said:**
> Hi guys... 

I've been running on those freezing problems since last week... Have 10.10 64bits installed since december on my laptop (Dell E6500)running without freezing problems... 

I've found the solution... There might be a bug with the nVidia driver and the 64bit distro.. I've did the solution provided in the this link and it worked for me:

[http://www.nvnews.net/vbulletin/showthread.php?t=158729]("http://www.nvnews.net/vbulletin/showthread.php?t=158729")

Hope this help!

Tried this solution, but I still got a crash. The original poster from the link provided actually posted that it didn't work for him either.

I also tried reinstalling the 64bit Nvidia drivers manually. This didn't work either :-( Very strange, I will go 5-6 days and not see a single crash and then suddenly see two crashes in the same day.

Thanks for advice to those who have given it!

---

### Post by afrodeity on 2011-03-02
try deleting ~/home/user/.compiz

If that doesn't work, then try reinstalling compiz

```

sudo apt-get install --reinstall compiz

```

---

### Post by troll1602 on 2011-03-03
> **afrodeity said:**
> try deleting ~/home/user/.compiz

If that doesn't work, then try reinstalling compiz

```

sudo apt-get install --reinstall compiz

```

I deleted and then reinstalled compiz and then rebooted. However, it only booted to the first terminal and when I ctrl+alt+F7'ed to the GUI it looked frozen on the normal ubuntu boot screen.

So, I reinstalled nvidia drivers again and then everything booted normally. So far no crashes! I will post back in a few days to give an update.

I'm still curious as to the cause, though. If compiz is the culprit, could someone avoid the crash by setting the Visual Effects in Appearance Preferences to 'None'?

---

### Post by xdmx123 on 2011-03-05
I'm having the same problem under kubuntu 10.10... so it's not a compiz problem.. with closed nvidia drivers (both from repo and last from nvidia.com) after some time everything just go so slow that i have to reboot... using open drivers I get random freeze (at least 1-2 during everyday)... This problem showed up just since 10.10, with 10.04, 9.10, 9.04 it always worked great  Latitude e6500 with nvidia G98M [Quadro NVS 160M]

---

### Post by afrodeity on 2011-03-05
If none of the above solutions work, try moving to the xswat repos.

nVidia:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

```


ati

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx

```

---

### Post by ZigBlazer on 2011-03-05
I'm one of the new users of Ubuntu, I just installed Ubuntu 10.10 along side of Windows XP on my ThinkPad.  I'm not having any problems with XP, just getting sick of it slowing down, and taking 5 min to turn on, etc.

I hate how closed off, and unmodifiable iCraps are so I did a little research and Ubuntu looked like a perfect fit.

I installed it, and it appeared to work great, for an hour or 2.  It then froze.  No ctrl-alt-del reset or anything.  I had to hold the power button for 10 sec and just power off.  It then wouldn't restart, so I started XP, which worked great.  So I tried Ubuntu again, and it worked.  So I've been using it about a week, and it has froze about 15 times now, at completely random times, regardless of what I'm doing, or not doing.  It has froze once where the mouse would still move, but nothing else worked.  It has froze after leaving it on overnight with the cover shut.

This morning it refused to connect to the internet.  I tried all the tricks I knew usually worked with windows, none worked.  It kept finding the network, but wouldn't connect.  It asked for the network password, several times over, then gave up.

I figured I would just keep watching the forums for a way to fix the freezing, but now without the internet, it could get difficult.  I restarted in XP and internet connection works great.

Is Ubuntu always this problematic?

Any suggestions?  I will try the NVidia driver thing if I can figure it out.

---

### Post by Maxiejoe on 2011-03-05
I have the same problems running 10.04 but I also have the same problem when I run XP on this machine.  Is it possible it could be keyboard /mouse related?  I am using a Logitech wireless keyboard and mouse but they do not supply driver support,  just a question as I have spent many hours on this problem of freezes.

---

### Post by troll1602 on 2011-03-10
> **ZigBlazer said:**
> I'm one of the new users of Ubuntu, I just installed Ubuntu 10.10 along side of Windows XP on my ThinkPad.  I'm not having any problems with XP, just getting sick of it slowing down, and taking 5 min to turn on, etc.

I hate how closed off, and unmodifiable iCraps are so I did a little research and Ubuntu looked like a perfect fit.

...

Any suggestions?  I will try the NVidia driver thing if I can figure it out.

Could we get a few more details on your hardware setup? Also, take a look at the log files after a crash. A easy way to do this is through System > Administration > Log File Viewer . I usually look at these files: messages, debug, kern.log, and Xorg.0.log. Note the time of the crash and look around that time in the log. If you see anything *strange* or anything that says 'error' post that section of the log in the forum, maybe someone will know what to do.

---

### Post by troll1602 on 2011-03-10
> **Maxiejoe said:**
> I have the same problems running 10.04 but I also have the same problem when I run XP on this machine.  Is it possible it could be keyboard /mouse related?  I am using a Logitech wireless keyboard and mouse but they do not supply driver support,  just a question as I have spent many hours on this problem of freezes.

Having the same crashes/freezes regardless of operating system sounds a lot like a hardware problem, probably related to the RAM. Try a few hardware tests. There is more info in the Ubuntu Documentation, [Faulty Hardware]("https://help.ubuntu.com/community/FaultyHardware").

---

### Post by troll1602 on 2011-03-10
So, it has been almost a week since I tried afrodeity's solution of deleting/reinstalling compiz and I have not seen a single crash.

I will post back if I run into any more problems, but for me at least, compiz seems to be the source of the crashes.

---

### Post by ZigBlazer on 2011-03-11
I've run pc-doctor on everything and only come up with one error.  The one ubuntu gparted partition software said was there, but wouldn't look for, find or fix.  It is bad sectors in the free space of my XP partition.  Windows chkdsk couldn't find any errors.  I decided to format and reload windows xp, and lost everything on the drive, and found my XP disk is bad.  So I've been working on getting everything back up and going.

I'll let you know when I get it back up and going, and whether or not it still has freezing issues.

I've installed ubuntu on my wife's laptop and haven't had it freeze up yet.  So I don't know what's going on.

Thanks for the help.

---

### Post by killabee44 on 2011-03-12
Same issues here guys. This machine freezes up and is unresponsive. The only way to get it back is to do a hard reboot. Im running 10.10 here as well on  a desktop. It's an old Compaq machine that just runs on integrated graphics.  

I can't find an answer.

I hope something is found soon..

---

### Post by tk189 on 2011-03-12
There is a massive thread (it began with 10.04) regarding the sudden freezing issue here: [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

The most noticeable thing in my case was just prior to the freeze my whole file system would go read-only. I only noticed this while editing atext doc and when i went to save it, I was unable to do so, it had gone read-only. Within seconds none of the launchers would work, open windows where just grey blanks and a hard reset was all i could do until i discovered ctrl alt sysrq reisub

Without going over all my findings that i shared in the thread mentioned above my issues seemed to diminsih, to the point of my system running totally stable for weeks at a time by the following:

Blu tacked my hard drive sata cable to the drive (very loose connection, sata cables suck)
Altered the cpu fan setting in my bios - I forget now to what, check the other thread.
Stopped using the very pretty but fairly pointless compiz special effects.

---

### Post by killabee44 on 2011-03-12
Thanks for your reply...

This machine is fairly old and does not get hot at all. 

I checked the Sata cables and they are on there tight.

I do not use Compiz at all.


One thing I noticed is that it seemed to lock up right after the updates notification appeared. I will be more attentive next time to make sure. Other times I used it with the updates notification there without a problem, so it might just be coincidence.

---

### Post by The End of The World on 2011-03-12
I get freezes too, yet my laptop hasn't got nvidia graphics chips - any ideas?

---

### Post by kalliba on 2011-03-12
I solved my freeze problems by modifying grub, adding "acpi_skip_timer_override" as follows:

sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_skip_timer_override**"

sudo update-grub

no more interrupts on boot, no more freezes after periods of inactivity, no problems resuming from sleep/hibernate; sometimes you need to hit Enter or Spacebar a couple times, that's all

this is the only thing that has worked for me on my Toshiba a205-s4607 satellite laptop. Note: running 32bit version

---

### Post by killabee44 on 2011-03-12
Kalliba,

What exactly does that do? 

I noticed that I can get mine to freeze pretty regularly when I drag a window. Im also getting some issues with lines (really thin lines) that flash on the left side of my monitor for a fraction of a second. 

That leads me to believe it is a video driver issue. This machine has minimal specs though. It only has:

*SiS Mirage2  Integrated with up to Up to 128MB allocated video memory*

I tried looking for drivers to no avail.  

> **kalliba said:**
> I solved my freeze problems by modifying grub, adding "acpi_skip_timer_override" as follows:

sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_skip_timer_override**"

sudo update-grub

no more interrupts on boot, no more freezes after periods of inactivity, no problems resuming from sleep/hibernate; sometimes you need to hit Enter or Spacebar a couple times, that's all

this is the only thing that has worked for me on my Toshiba a205-s4607 satellite laptop. Note: running 32bit version

---

### Post by ZigBlazer on 2011-03-16
> **troll1602 said:**
> Could we get a few more details on your hardware setup? Also, take a look at the log files after a crash. A easy way to do this is through System > Administration > Log File Viewer . I usually look at these files: messages, debug, kern.log, and Xorg.0.log. Note the time of the crash and look around that time in the log. If you see anything *strange* or anything that says 'error' post that section of the log in the forum, maybe someone will know what to do.

I have an IBM ThinkPad R51e 1844-69U
Build Date: Apr06
Processor: 1.4GHz Intel Celeron M
Ram: 1Gb, 874Mib System Usable
Hard Drive: 250Gb WD HDD
Main System: Windows XP Home 32bit
Main Partition Size: 139Gb
Ubuntu System: 10.10 Maverick
                           Kernel Linux 2.6.35-27-Generic
                           Gnome 2.32.0
Ubuntu Partition Size: 100Gb
Ubuntu Free Space: 81Gb

I tried all of the recommendations including;
Mem test - 4 different ways - No problems found
Nvidia Driver update - No change
Grub Update - No change
Disk Check through Windows - No problems found
PC Doctor complete HDD check - Found bad sectors in XP partition Free Space

I formatted the entire HDD erasing XP, Ubuntu, and IBM Service Recovery Partitions - 3 times until no bad sectors were found.

I reinstalled XP, IBM service, and Ubuntu to the partition sizes above.

Rechecked Mem and HDD, No problems found

XP is running perfectly, all used programs reinstalled, system backup done before installing Ubuntu

Installed Ubuntu, and encountered many more problems than the first time.  It took 12 times of restarting and using ubuntu recovery to update every part for ubuntu to load correctly.

I have run every update, and re-done all of the recommended things on this thread, finishing yesterday.

Today it has frozen 4 times.  Once after being idle for an hour, only program open was firefox.  Once while using Software Center to install Mount Manager.  Once as soon as it was loaded, before anything was open.  Once while trying to redo the Nvidia drive install from page 3, because I couldn't tell if it worked the first time.

Each time it freezes I can move the mouse, make the screen un-dim, but nothing else.  I don't know what the normal reset buttons are for ubuntu, but I've tried ctrl-alt-del, alt-r, alt-4, alt-f4, ctrl-esc.  Nothing works.  I have to hold the power button in for 5 sec.  Half of the time when restarting ubuntu freezes before it finishes loading, and I have to try again.

I forgot to look at the exact time it froze to check the logs, and couldn't find anything special looking through them, so I'll wait until it happens again.

Thanks for the help, and if anyone has any ideas please let me know.

By the way, I installed Ubuntu on my Wifes Lenovo that is a year newer, with a duo core processor, 2gb ram, and 160 gb HDD, and it has not frozen once in Ubuntu.  But it has Windows Vista as the primary system, which freezes regularly.

---

### Post by troll1602 on 2011-03-16
> **ZigBlazer said:**
> I have an IBM ThinkPad R51e 1844-69U
Build Date: Apr06
Processor: 1.4GHz Intel Celeron M
Ram: 1Gb, 874Mib System Usable
Hard Drive: 250Gb WD HDD
Main System: Windows XP Home 32bit
Main Partition Size: 139Gb
Ubuntu System: 10.10 Maverick
                           Kernel Linux 2.6.35-27-Generic
                           Gnome 2.32.0
Ubuntu Partition Size: 100Gb
Ubuntu Free Space: 81Gb

....

By the way, I installed Ubuntu on my Wifes Lenovo that is a year newer, with a duo core processor, 2gb ram, and 160 gb HDD, and it has not frozen once in Ubuntu.  But it has Windows Vista as the primary system, which freezes regularly.

Might sound like a stupid question, but are you running 32bit or 64bit Ubuntu? If you are running 32 bit, then your problem might be completely unrelated to the problem that everyone else in this thread is having, because this thread is specific to 64 bit.

A few things tips for any crash though:
1)Try to restart X server. The hotkey for this was disabled after 9.10, but to enable it go to "System > Preferences > Keyboard", and then under the Layout tab click "Options". Select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.

2) If X server restart doesn't work, the try "Alt + SysRq + k". This will kill all running processes. This is a type of [Magic SysRq Key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") and on some laptops you need to hold down "Fn" as well.

3) Finally, the last resort is to try the sequence: "Alt + SysRq + R,E,I,S,U,B". So, you hold down "Alt + SysRq" and then one at a time press "R E I S U B". This will do a several tasks (you can read about them in the wiki) and then finally reboot. Basically it is just a safer way to reboot instead of holding down the power button.

Hopefully that helps! And don't forget to check the logs :-)

---

### Post by ZigBlazer on 2011-03-16
> **troll1602 said:**
> Might sound like a stupid question, but are you running 32bit or 64bit Ubuntu? If you are running 32 bit, then your problem might be completely unrelated to the problem that everyone else in this thread is having, because this thread is specific to 64 bit.

A few things tips for any crash though:
1)Try to restart X server. The hotkey for this was disabled after 9.10, but to enable it go to "System > Preferences > Keyboard", and then under the Layout tab click "Options". Select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.

2) If X server restart doesn't work, the try "Alt + SysRq + k". This will kill all running processes. This is a type of [Magic SysRq Key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") and on some laptops you need to hold down "Fn" as well.

3) Finally, the last resort is to try the sequence: "Alt + SysRq + R,E,I,S,U,B". So, you hold down "Alt + SysRq" and then one at a time press "R E I S U B". This will do a several tasks (you can read about them in the wiki) and then finally reboot. Basically it is just a safer way to reboot instead of holding down the power button.

Hopefully that helps! And don't forget to check the logs :-)

Not at all a stupid question.  One I didn't know the answer to.  After searching to figure out what I had, I found I am using the 32 bit version.  I did start my own thread, without any answers yet either, but I didn't know if it would be unique to the 64 bit or 32 bit version.  Since both versions are having the same problem.  I did restart the X server and have those keys written down for when it freezes again.

Surprisingly it hasn't froze for the last 5 hours.  Longest span yet.

---

### Post by ZigBlazer on 2011-03-20
This appears to have worked.  It hasn't froze again yet;

sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_skip_timer_override**"

sudo update-grub

I don't know what it does, but no freeze problems since I did it.

Still having wireless issues, but thank you for the help.

---

### Post by afrodeity on 2011-03-21
> **ZigBlazer said:**
> This appears to have worked.  It hasn't froze again yet;

sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_skip_timer_override**"

sudo update-grub

I don't know what it does, but no freeze problems since I did it.

Still having wireless issues, but thank you for the help.

from [http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re81.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re81.html)

"Allow the ACPI layer to recognize and ignore IRQ0/pin2 Interrupt Override issues for broken nForce2 BIOSes that result in the XT-PIC timer acting up."

---

