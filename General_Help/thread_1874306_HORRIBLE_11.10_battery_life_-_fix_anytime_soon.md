---
title: "HORRIBLE 11.10 battery life - fix anytime soon?"
date: 2011-11-02
forum: General Help
---

### Post by fictivetoast on 2011-11-02
I updated from 11.04 to 11.10 earlier this week, and though I'd heard reports of increased power usage on oneric, this is ***crazy***.

I have a relatively new Lenovo x220 (core i7) with a 9-cell battery.  With screen dimmed a bit and intermittent wifi use under Windows 7 I can easily get 8+ hours (and could push it to 12+ using Lenovo's power-usage tweaks).  On Ubuntu 11.04 I still got a decently respectable 6+ hours.  On Oneric, I'm getting around 4 hours with *wifi turned off* - ***that's a third of the battery life I can get on Windows***.  This is unacceptable. 

What the heck is going on?  I've heard this is somewhat kernel related, but even so, this seems insane to me.  I've been on Ubuntu for six years and hate the prospect of having to turn back to Windows.  I opted for this laptop specifically for the battery life, and the insane power consumption is making 11.10 practically useless for me.  I'm tempted to revert all the way to 10.10 to see if I can at least get 7 hours with gnome2 and an older kernel.

Can we expect a fix anytime soon?  Have the developers publicly commented on this?  Is it even being acknowledged?  Given how much of a mobile emphasis Ubuntu has had in recent years (netbook edition etc), it seems like they're shooting themselves in the foot releasing a distro that throws portability out the window.


(Relatedly, did something change in powertop?  In previous Ubuntu releases, the stock powertop available in the repos would give me a useful realtime power consumption report along with an estimate of how much juice was left - the powertop on 11.10 seems to offer a bunch of confusing separate tabs with very little useful information.)

---

### Post by 3Miro on 2011-11-02
This is what I am using on 11.10 to get extra battery life (it gies me about an hour extra on my 6-cell battery).

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

The kernel related thing is largely a FUD, there are some laptops BIOS chips that don't conform properly to standards and cause some issues. This is not a problem with the kernel.

Your regression is probably due either to a rogue process taking over the CPU or just some settings that need to be adjusted. Double-check Gnome power manager as well, some of the defaults may have changed due to the upgrade to Gnome 3.

---

### Post by fictivetoast on 2011-11-02
> **3Miro said:**
> This is what I am using on 11.10 to get extra battery life (it gies me about an hour extra on my 6-cell battery).

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

The kernel related thing is largely a FUD, there are some laptops BIOS chips that don't conform properly to standards and cause some issues. This is not a problem with the kernel.

Your regression is probably due either to a rogue process taking over the CPU or just some settings that need to be adjusted. Double-check Gnome power manager as well, some of the defaults may have changed due to the upgrade to Gnome 3.

Thanks for the Jupiter tip, but the only function it seems to offer is manually selecting the "power saver" performance mode, which I'd think my computer already hopped into automatically when I unplugged it, no ?  In any event, even with Jupiter my battery gauge is still reading 4:30 remaining when I immediately unplug and have a full charge.

As for "gnome power manager" are you referring to the power manager settings in the control panel?  Cause the only options available there are when to dim the screen, and when to suspend or hibernate the system.

And on runaway processes, in system monitor my current process are currently hovering around :
plugin-container : 32% (ie the flash plugin)
Gnome-System-Monitor : 16%
Firefox : 12%
compiz : 4%
everything below there is at 0%, and in general all 4 of my cpu cores are hovering between 10% and 40%, never above.

---

### Post by 3Miro on 2011-11-02
Jupiter gives you much better "powersave" settings than the default ones.

Stop flash and let FF open with only basic pages (i.e. like Ubuntu forums). Then see how much time you have, you may have to wait a couple of minutes to get an accurate reading. Flash under Linux will eat your battery pretty quickly. The 33% that you are seeing means that one (out of 4) cores is running on full power to keep up with flash.

Another thing that I have noticed is that the battery applet is very sensitive to the instantaneous load of the system. Let the battery indicator show the time on the top bar and let it run for a while to get a better estimate on a long run.

---

### Post by alfefried on 2011-11-03
+1

Well, shut down your computer and see how much battery life you get :D

I noticed such a default on my hp probook 4530, with i5, when installing 11.10.
It looks like it's getting worse and worse at each new version, and i agree, this is not acceptable: poor battery life and unbearable fan noise !

There must be a kernel issue, you can vote for it to promote a fix :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

you should track some threads here, for example:
[http://ubuntuforums.org/showthread.php?t=1822629&page=14](http://ubuntuforums.org/showthread.php?t=1822629&page=14)

on post #23, i used the trick of "**i915.i915_enable_rc6=1"**, that improved a bit the problem.

Did you have better performances using lucid ?

---

### Post by fictivetoast on 2011-11-03
I spoke too soon, Jupiter is indeed helping - I seem to be bumped up to ~6h30m now.  Again though, that's still half what Windows 7 offers.  FYI I've applied [this fix]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") to at least keep my core temps down.

I'll keep my eye on that kernel thread for now I suppose.

---

### Post by techvish81 on 2011-11-03
i installed jupiter eepc support package and jupiter indicator through synaptic, but i cant open it or see its settings, there is some difference in battery consumption but i'm not able to figure out as it is to early to tell, can anyone give me a way to see the settings mentioned in above posts in jupiter.

---

### Post by aeronutt on 2011-11-03
FYI, this significantly decreased power draw on my i3 based laptop.

[http://ubuntuforums.org/showpost.php?p=11385278&postcount=9](http://ubuntuforums.org/showpost.php?p=11385278&postcount=9)

My current draw went from ~1500mA to ~800mA with the following kernel options

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then sudo update-grub

The one that made the majority (nearly all) of the difference was the first.

---

### Post by alfefried on 2011-11-03
yeah,

i was looking for this thread too : 
[http://ubuntuforums.org/showthread.php?t=1865820](http://ubuntuforums.org/showthread.php?t=1865820)

there weren't the i915.lvds_downclock=1 there ...

Does anyone understand what it means ?

:guitar:

edit: found [http://www.lesswatts.org/projects/powertop/faq.php]("http://www.lesswatts.org/projects/powertop/faq.php") , that may be interesting to us.

---

### Post by fictivetoast on 2011-11-03
I've managed to bump it up to an estimated 9+ hours with screen around 70% brightness and wifi/bluetooth both on by adding those additional parameters to my grub conf, which now reads :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

Woohoo!!!

---

### Post by techvish81 on 2011-11-03
> **fictivetoast said:**
> I've managed to bump it up to an estimated 9+ hours with screen around 70% brightness and wifi/bluetooth both on by adding those additional parameters to my grub conf, which now reads :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

Woohoo!!!

your 9+ hr battery life is with Jupiter, powertop and these above additions to grub conf,  or just the additions ?

---

### Post by fictivetoast on 2011-11-04
Jupiter + those grub additions.

I have powertop installed, but haven't been using it.  As I mentioned earlier, I don't really understand the new powertop interface with the version packaged in 11.10, so I haven't even touched it...

---

### Post by frankencat on 2011-12-22
^ new powertop...+1

---

### Post by TBABill on 2011-12-22
With all these changes it'd be interesting to compare Ubuntu's battery life to Fuduntu's battery life since I believe Fewt is the Jupiter dev as well as the Fuduntu lead dev. Wondering if Fuduntu has other tweaks to help on battery life...

---

### Post by BC59 on 2011-12-22
There is the kernel 3.2 RC option....for the ones who dare to do it.

---

### Post by Z06Gal on 2011-12-22
I downgraded to the 2.6.39.3 kernel and it runs so much cooler it isn't funny.  The fan comes on rarely.  I think the fix is supposed to be in the 3.3 kernel when it is released or at least that is what I have read :D


Robin

---

### Post by BC59 on 2011-12-22
> **Z06Gal said:**
> I downgraded to the 2.6.39.3 kernel and it runs so much cooler it isn't funny.  The fan comes on rarely.  I think the fix is supposed to be in the 3.3 kernel when it is released or at least that is what I have read :D


Robin

In this forum there are #54 posts but no coincidence on what kernel is better or worst, on overheating.
[http://ubuntuforums.org/showthread.php?t=1745389](http://ubuntuforums.org/showthread.php?t=1745389)

---

### Post by Z06Gal on 2011-12-22
I understand but that is what works for me.  My laptop runs 15 degrees cooler with the downgraded kernel:D

---

### Post by BC59 on 2011-12-22
As I understand this is the problem and that's why they cannot find a simple solution. The good kernel for some is the disaster for others. It's extremely difficult to satisfy all these diverse structures.

---

### Post by Vidar30 on 2011-12-27
i915.i915_enable_rc6=1 
i915.i915_enable_fbc=1 
i915.lvds_downclock=1

These three options in grub made a huge difference for me. Using ~8W now, cool and quiet.

Toshiba satellite c660

I must say; Unity has really grown on me even though it's sluggish. Make a lightweight version without all the pretty stuff.

Unity is a great idea.

---

### Post by werewolves on 2011-12-27
> **aeronutt said:**
> FYI, this significantly decreased power draw on my i3 based laptop.

[http://ubuntuforums.org/showpost.php?p=11385278&postcount=9](http://ubuntuforums.org/showpost.php?p=11385278&postcount=9)

My current draw went from ~1500mA to ~800mA with the following kernel options

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then sudo update-grub

The one that made the majority (nearly all) of the difference was the first.

Tried it on my i7.  Fingers crossed!

---

### Post by werewolves on 2011-12-28
> **werewolves said:**
> Tried it on my i7.  Fingers crossed!

Ugh, no help.  Still mediocre, even with Jupiter installed.

---

### Post by fuduntu on 2011-12-28
> **werewolves said:**
> Ugh, no help.  Still mediocre, even with Jupiter installed.

Also add:

pcie_aspm=force

to your grub kernel options.

---

### Post by JCoop on 2011-12-28
pcie_aspm=force added to my grub boot menu is what netted me the largest gain. I am running an i5 with intel graphics and kernel 3.1.4. I am going to try a 3.2 kernel later on to see if there is any difference. The other options (i915.i915_enable***, etc.) provided about the same increase in battery life as powertop. Phoronix has a really good article about these and about the different kernels. 

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

### Post by werewolves on 2011-12-29
> **fuduntu said:**
> Also add:

pcie_aspm=force

to your grub kernel options.

OK, I'll try it out.

---

### Post by xyzzyman on 2011-12-29
> **werewolves said:**
> Tried it on my i7.  Fingers crossed!

You may want to try the 3.2 ubuntu kernel (It has the ASPM fix already backported into it). For Oneiric there is a PPA with 3.2 RC7 from Precise already backported for Oneiric if don't want to compile on your own. The final 3.2 kernel should be out shortly and the PPA will be updated. This is the kernel that PP will be shipping with.

[https://launchpad.net/~ptn107/+archive/ppa](https://launchpad.net/~ptn107/+archive/ppa)

---

### Post by aura7 on 2011-12-29
The best option is to wait for next Ubuntu release

[http://www.engadget.com/2011/12/19/ubuntus-precise-pangolin-to-pull-less-power-than-predecessors/](http://www.engadget.com/2011/12/19/ubuntus-precise-pangolin-to-pull-less-power-than-predecessors/)

---

### Post by divergex on 2011-12-29
> **BC59 said:**
> There is the kernel 3.2 RC option....for the ones who dare to do it.

I installed kernel 3.2.0-999 on my Lenovo G570 and so far I have noticed that the fan runs more quietly and that battery life appears to be much better. I have not had any crashes or compatibility issues with this kernel.

---

### Post by mattia.tamellini on 2011-12-29
hi everyone! 

I had the exact same problem as fictivetoast (though I have a dell vostro v131). I edited grub as you were suggesting, and everything seems fine, but I was wondering what kind of problems this may cause, so that I can keep an eye on them. For example, is it possible that this fix cause a slight overheating? I didn't check cpus and hdd temperatures before changing grub, but now using lm-sensors I saw the cpus stay between 47°C and 51°C and hdd around 40°C. Is it normal?

---

### Post by nebula12 on 2011-12-29
hello! i'm not a professional ubuntu user, i have a dell latitude E5420 i5. ubuntu battery life is quite lower than on windows 7. how can i add "those additional parameters to my grub conf"??

---

### Post by zero2xiii on 2011-12-29
> **nebula12 said:**
> hello! i'm not a professional ubuntu user, i have a dell latitude E5420 i5. ubuntu battery life is quite lower than on windows 7. how can i add "those additional parameters to my grub conf"??

Dont even try it. Since you are not experienced enough you can break the system. Easily. So rather stay away for now until a fix is found (if something is broken) and packaged with an update or distro.

---

### Post by xyzzyman on 2011-12-29
> **zero2xiii said:**
> Dont even try it. Since you are not experienced enough you can break the system. Easily. So rather stay away for now until a fix is found (if something is broken) and packaged with an update or distro.

How did most of us become experienced without trying?

---

### Post by aeronutt on 2011-12-29
> **nebula12 said:**
> hello! i'm not a professional ubuntu user, i have a dell latitude E5420 i5. ubuntu battery life is quite lower than on windows 7. how can i add "those additional parameters to my grub conf"??

It's pretty simple....but to insure I tell you exactly right, I'll have to wait until I'm home on a linux machine. :) The basics are...edit one line in one file (/etc/default/grub), run 'sudo update-grub', reboot.

---

### Post by nebula12 on 2011-12-29
ok, i'll wait then.. but if something may be dangerous i don't want to try it now. i installed jupiter.but the options are default for each mode, right? i mean, if i choose power saver i don't know what it does to save power..and i don't see any difference on the display, any dim for example.. but if it really works, allright, then!

---

### Post by aeronutt on 2011-12-29
> **nebula12 said:**
> ok, i'll wait then.. but if something may be dangerous i don't want to try it now. i installed jupiter.but the options are default for each mode, right? i mean, if i choose power saver i don't know what it does to save power..and i don't see any difference on the display, any dim for example.. but if it really works, allright, then!

It's an easy, safe, change to make. Others might chime in and show you the details before I get a chance. You can also try it from the grub command line as a temporary (one time) command line, to see if it works. I didn't see any benefit from Jupiter, so I don't use that.

---

### Post by fuduntu on 2011-12-29
> **nebula12 said:**
> ok, i'll wait then.. but if something may be dangerous i don't want to try it now. i installed jupiter.but the options are default for each mode, right? i mean, if i choose power saver i don't know what it does to save power..and i don't see any difference on the display, any dim for example.. but if it really works, allright, then!

Everything Jupiter does is behind the scenes.  To get the best benefit from it on Sandy Bridge chipsets, you need to mix it with the kernel parameter tweaks.

---

### Post by mattia.tamellini on 2011-12-29
> **nebula12 said:**
> hello! i'm not a professional ubuntu user, i have a dell latitude E5420 i5. ubuntu battery life is quite lower than on windows 7. how can i add "those additional parameters to my grub conf"??

if you want to try, open a terminal, and do:
```
sudo gedit /etc/default/grub
```

then replace the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

with the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_osi=Linux i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=1"
```

save, exit go back to the terminal and do:
```
sudo update-grub
```

and then reboot your system.

---

### Post by nebula12 on 2011-12-29
> **aeronutt said:**
>  You can also try it from the grub command line as a temporary (one time) command line, to see if it works. I didn't see any benefit from Jupiter, so I don't use that. what do you mean by that? it's also safer this way, isn't it?

---

### Post by aeronutt on 2011-12-29
> **nebula12 said:**
> what do you mean by that? it's also safer this way, isn't it?

Do exactly what mattia says and all will be fine. Or, yes, you can do a 'one time' edit by:

At boot, when grub appears with OS boot options (assuming you have multiple boot options), hit 'e' while the OS you're booting to is selected. This will let you edit the kernel options. Move your cursor to the line that starts with 'linux /boot/vm.......'  And add your kernel options to then end of that line. ( The options being "quiet splash pcie_aspm=force acpi_osi=Linux i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=1").  Hit the key as described at the bottom of the screen to boot (I think it's ctl-x).

This is a one time fix.

---

### Post by nebula12 on 2011-12-30
ok, i did it. soon i will see if there is any effect but i think that already my battery signs 4 hours and before rebooting it said 3.. thank you very much.. but if you please explain as far as you can, what was this change that i did in the kernel? it's time for as newbbies to learn something... :p


edit: but, i think the sign of my battery showing how much time remains has gone a little crazy.. from 4.30 went 2.30 and then 3.10... :S   and so on

---

### Post by mattia.tamellini on 2011-12-30
> **nebula12 said:**
> ok, i did it. soon i will see if there is any effect but i think that already my battery signs 4 hours and before rebooting it said 3.. thank you very much.. but if you please explain as far as you can, what was this change that i did in the kernel? it's time for as newbbies to learn something... :p

I'm not an expert either, but this is what I understand :)

[LIST]
[*]- pcie_aspm=force : enables ASPM (i.e. the power manager), even on devices that do not support ASPM (it may be that even if your pc supports ASPM, your BIOS says otherwise, and so you have to force ASPM to be enabled)
[*]- acpi_osi=Linux: by default the kernel responds false when BIOS asks if Linux is running. acpi_osi=Linux tells the kernel to respond true.
[*]- i915.lvds_downclock=1: this option is used to slow down the refresh rate of your monitor
[*]- i915.i915_enable_fbc=1: this option enables the compression of what is going to be displayed on your screen, thus requesting less memory and cpu.
[*]- i915.i915_enable_rc6=1 – this option makes GPU enter the low-consumption mode when idle.
[/LIST]

this should be it, but I will appreciate any feedback from the more-experienced users :)

---

### Post by mattia.tamellini on 2011-12-30
> **nebula12 said:**
> 
edit: but, i think the sign of my battery showing how much time remains has gone a little crazy.. from 4.30 went 2.30 and then 3.10... :S   and so on

this is because it depends on how much the cpu is stressed in that particular moment. The indicator shows the time that remains if the cpu keeps on working at that speed.

---

### Post by aeronutt on 2011-12-30
> **nebula12 said:**
> ok, i did it. soon i will see if there is any effect but i think that already my battery signs 4 hours and before rebooting it said 3.. thank you very much.. but if you please explain as far as you can, what was this change that i did in the kernel? it's time for as newbbies to learn something... :p


edit: but, i think the sign of my battery showing how much time remains has gone a little crazy.. from 4.30 went 2.30 and then 3.10... :S   and so on

Yea, gotta average those results over a bit of time. 5 minutes...or 30 minutes or so, depending on what the workload is. In idle state, mine went from burning 2300mA to around 800 mA, after I did all the changes and removed a handful of applications from auto start. But by far, the biggest for my laptop was the " i915.i915_enable_rc6=1" kernel mod.

---

### Post by nebula12 on 2011-12-30
thank you all for your advice!! :)

---

### Post by xyzzyman on 2011-12-30
There should almost be a sticky with how to do the one-time edit and then the permanent grub option.

---

### Post by Expert Novice on 2012-01-08
I agree about the sticky suggestion. I've been searching around for days to find a posible solution to the overheating and excess power draw issues I've had on my laptop since installing Ubuntu 11.10 (my first experience with Ubuntu/Linux). Hopefully mattia.tamellinis suggestion will help make a difference so I'll give it a go.

One question though, as a total newbie... When using the one time fix option will the kernel options automatically revert to the original configuration after the next shut down and reboot?

---

### Post by Elfy on 2012-01-08
> **mattia.tamellini said:**
> if you want to try, open a terminal, and do:
```
sudo gedit /etc/default/grub
```

then replace the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

with the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_osi=Linux i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=1"
```

save, exit go back to the terminal and do:
```
sudo update-grub
```

and then reboot your system.

> **Expert Novice said:**
> I agree about the sticky suggestion. I've been searching around for days to find a posible solution to the overheating and excess power draw issues I've had on my laptop since installing Ubuntu 11.10 (my first experience with Ubuntu/Linux). Hopefully mattia.tamellinis suggestion will help make a difference so I'll give it a go.

One question though, as a total newbie... When using the one time fix option will the kernel options automatically revert to the original configuration after the next shut down and reboot?

If you are talking about doing this - then no it will not revert. The change is permanent - or at least it will be if you do not edit the line again.

---

### Post by Expert Novice on 2012-01-08
No, this was the post I was meaning but now I re read it perhaps I misunderstood the meaning of 'one time fix'. That is to say is is not saying the fix is temporary (one time, or one boot only) rather that you only have to do it once.

Thanks for clarifying :-)

> **aeronutt said:**
> Do exactly what mattia says and all will be fine. Or, yes, you can do a 'one time' edit by:

At boot, when grub appears with OS boot options (assuming you have multiple boot options), hit 'e' while the OS you're booting to is selected. This will let you edit the kernel options. Move your cursor to the line that starts with 'linux /boot/vm.......'  And add your kernel options to then end of that line. ( The options being "quiet splash pcie_aspm=force acpi_osi=Linux i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.i915_enable_rc6=1").  Hit the key as described at the bottom of the screen to boot (I think it's ctl-x).

This is a one time fix.

---

### Post by aeronutt on 2012-01-08
> **Expert Novice said:**
> No, this was the post I was meaning but now I re read it perhaps I misunderstood the meaning of 'one time fix'. That is to say is is not saying the fix is temporary (one time, or one boot only) rather that you only have to do it once.

Thanks for clarifying :-)

Any changes done in grub at boot up by the method I described as 'one time fix', will not be persestent. At next boot, grub will reload /etc/default/grub (and have not record of what you did previously).

If you want it to be permanent, you must edit /etc/default/grub, and run 'sudo update-grub'.

---

### Post by Expert Novice on 2012-01-08
> **aeronutt said:**
> Any changes done in grub at boot up by the method I described as 'one time fix', will not be persestent. At next boot, grub will reload /etc/default/grub (and have not record of what you did previously).

If you want it to be permanent, you must edit /etc/default/grub, and run 'sudo update-grub'.

Ok, so I had it right thefirst time and no permanent changes are made untill you execute sudo update grub.

Thanks for helping me learn a little more :-)

---

### Post by jfever311 on 2012-02-21
I just did this and it has slowed my Asus K52f BIN6 WAY DOWN!! How do I undo these changes!?! 

I am pretty green to all this, so please be a bit patient. 

_***[SIZE=4]HELP!![/SIZE]***_

---

### Post by jfever311 on 2012-02-21
Okay, I seem to have fixed it. Just had to go through and put the original script back in.

---

### Post by ToshibaLaptoplinux on 2012-02-22
I was doing a search on a similar issue and stumbled upon this thread. Very disheartening to read.

My previous 2 laptops, Dell and Toshiba, both fried my battery running Ubuntu. "Fried" as in all of sudden they stopped taking a charge. It wasn't a coincidence and they were both brand new machines. I bought new batteries and always pulled them out and ran on AC as much a possible. At the time I posted on both the Forums and Launchpad.Why do I give this history?

I have just purchased a new Samsung i7/64bit and when running Win 7 get 7 hours of battery life but when running the live CD get less than 2 hours. I like Ubuntu enough that I can suffer the loss of battery time, but as this Laptop model doesn't have a removable battery, I can't afford to destroy the battery because it can only be replaced at the factory. This could really be a deal breaker for me as much as I like Ubuntu.

Has anyone else heard of or experienced this?Any ideas/advice?

---

### Post by radvinb on 2012-02-28
I have tried to edit the kernel, but this is what I get when I open up the editor.


radvin@radvin-ThinkPad-Edge-E220s:~$ sudo gedit /etc/default/grub
[sudo] password for radvin: 

(gedit:2471): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.D8BAAW': No such file or directory

(gedit:2471): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


Also battery life is horrible, this is why i have been trying this patch (posted on 1st page).

please help!

---

### Post by Mark Phelps on 2012-02-29
> **ToshibaLaptoplinux said:**
> Any ideas/advice?

I've read that this kernel problem has been fixed in 12.04.  You could try downloading 12.04 beta when it comes out, making a bootable USB stick from that, booting from that -- and seeing if that performs better.

---

### Post by aeronutt on 2012-02-29
> **radvinb said:**
> I have tried to edit the kernel, but this is what I get when I open up the editor.


radvin@radvin-ThinkPad-Edge-E220s:~$ sudo gedit /etc/default/grub
[sudo] password for radvin: 

(gedit:2471): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.D8BAAW': No such file or directory

(gedit:2471): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


Also battery life is horrible, this is why i have been trying this patch (posted on 1st page).

please help!

I believe you want to use 
```
gksudo gedit /etc/default/grub
```
If not, try using vi another editor, such as vi: 
```
sudo vi /etc/default/grub
```

---

### Post by radvinb on 2012-02-29
> **aeronutt said:**
> I believe you want to use 
```
gksudo gedit /etc/default/grub
```
If not, try using vi another editor, such as vi: 
```
sudo vi /etc/default/grub
```

Great! the last one went through and showed my settings, but before that i got this message:


E325: ATTENTION
Found a swap file by the name "/etc/default/.grub.swp"
          owned by: root   dated: Wed Feb 29 09:15:32 2012
         file name: /etc/default/grub
          modified: YES
         user name: root   host name: radvin-ThinkPad-Edge-E220s
        process ID: 6697
While opening file "/etc/default/grub"
             dated: Wed Feb 29 09:13:50 2012

(1) Another program may be editing the same file.  If this is the case,
    be careful not to end up with two different instances of the same
    file when making changes.  Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/default/grub"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/default/.grub.swp"
    to avoid this message.
"/etc/default/grub" 35 lines, 1325 characters
Press ENTER or type command to continue

---

