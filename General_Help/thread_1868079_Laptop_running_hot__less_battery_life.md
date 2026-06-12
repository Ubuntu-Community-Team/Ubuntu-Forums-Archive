---
title: "Laptop running hot / less battery life"
date: 2011-10-23
forum: General Help
---

### Post by OneXero on 2011-10-23
My laptop is running hotter than normal (the heat can be felt through the keyboard) and my battery life is about 2-2.5 hours lower than normal (when running Windows) on Samsung Series 9.

I am loving Gnome 3.2 on Ubuntu 11.10, but this kind of wear and tear on my laptop is gonna send me back to windows if I can't figure it out. I've solved a lot of my other problems, but these two are persistent, and I am hesitant to apply the solutions I've found by searching as they feel relatively hardware specific.

Can anyone lend a hand, or point me in the right direction?

---

### Post by conradin on 2011-10-23
Most of the time I find that there is lint in the heat sink when poeple express similar issues. have you cleaned your heat sink lately?

---

### Post by OneXero on 2011-10-23
Well, I haven't messed with the inside of my laptop at all, but I turn it off for a bit (until it cools) and I use my windows partition and the heat isn't nearly as bad, nor is the fan (which constantly runs on ubuntu) the fan is quiet on this laptop, and usually I can't hear it, but I can when I run ubuntu. Especially when the charger is plugged in. (Not so on windows)

Is Ubuntu specifically lint unfriendly? (haha)

---

### Post by kaldor on 2011-10-23
What graphics card do you have? Which driver do you use?

Also, install the [_Jupiter applet_]("https://launchpad.net/~webupd8team/+archive/jupiter") and set it to "Power saver".

---

### Post by JohannesJo on 2011-10-23
[FONT=monospace]I got a similar problem ([http://askubuntu.com/questions/71196/what-can-i-do-to-prevent-ubuntu-from-overheating-my-notebook](http://askubuntu.com/questions/71196/what-can-i-do-to-prevent-ubuntu-from-overheating-my-notebook)) and even with just Firefox (2 Tabs) and Thunderbird running sensors shows me around 90° for cpu and gpu (maybe there is a connection to the graphics-driver?). 

Unfortunately it seems there is no solution yet, despite ppl. telling you to clean your vault or update your bios, which doesnt seem to be even necessary while running windows. 

In worst cast its a kernel problem and nothing you can do about it until its next release.

Does it also seem that you fan doesn't raise to its maximum performance (considering its noise)?
[/FONT]

---

### Post by Linuxisfast on 2011-10-23
Driver is very important to prevent heat build up, compared to the older kernel in Natty, the newer one in Oneiric makes my laptop and netbook run cooler.

---

### Post by OneXero on 2011-10-23
> **kaldor said:**
> What graphics card do you have? Which driver do you use?

Also, install the [_Jupiter applet_]("https://launchpad.net/%7Ewebupd8team/+archive/jupiter") and set it to "Power saver".

Intel® HD Graphics 3000

I'll try the Jupiter Applet. Does power saver mode have any additional effects to my computer though? In windows if I choose the power saving mode, the wireless capabilities on my laptop drop dramatically, (loading times, download speeds, etc).

---

### Post by OneXero on 2011-10-23
> **JohannesJo said:**
> [FONT=monospace]I got a similar problem ([http://askubuntu.com/questions/71196/what-can-i-do-to-prevent-ubuntu-from-overheating-my-notebook](http://askubuntu.com/questions/71196/what-can-i-do-to-prevent-ubuntu-from-overheating-my-notebook)) and even with just Firefox (2 Tabs) and Thunderbird running sensors shows me around 90° for cpu and gpu (maybe there is a connection to the graphics-driver?). 

Unfortunately it seems there is no solution yet, despite ppl. telling you to clean your vault or update your bios, which doesnt seem to be even necessary while running windows. 

In worst cast its a kernel problem and nothing you can do about it until its next release.

Does it also seem that you fan doesn't raise to its maximum performance (considering its noise)?
[/FONT]

The majority of the problem is when I have my laptop plugged in, I don't know technical terminology about computers, but to me, it feels like the laptop is always charging, and then overcharging, and by that I mean - the computer is super hot - like it doesn't know how to handle running straight from the AC without constantly cycling between battery and AC.

The fan cannot keep up with charging aspect at all! I just unplugged the charger and the fan and temperature drop dramatically. But this problem does not exist on windows.

---

### Post by aeronutt on 2011-10-23
My current draw went from ~1500mA to ~800mA with the following kernel options

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then sudo update-grub

The one that made the majority (nearly all) of the difference was the first.

---

### Post by kaldor on 2011-10-23
> **OneXero said:**
> Intel® HD Graphics 3000

I'll try the Jupiter Applet. Does power saver mode have any additional effects to my computer though? In windows if I choose the power saving mode, the wireless capabilities on my laptop drop dramatically, (loading times, download speeds, etc).

The applet shouldn't cause any issues. I know of a lot of people who use it, and nobody has ever complained. You can always remove it anyway :)

There are no additional drivers for Intel cards so that's out of the picture. Right now, just give Jupiter a shot to see if that helps.

---

### Post by OneXero on 2011-10-23
> **kaldor said:**
> The applet shouldn't cause any issues. I know of a lot of people who use it, and nobody has ever complained. You can always remove it anyway :)

There are no additional drivers for Intel cards so that's out of the picture. Right now, just give Jupiter a shot to see if that helps.

So I installed it, and I clicked on it using the search, but no window popped up, so I am not sure how to change it's settings. I'll look into it further, not sure what I did wrong.

---

### Post by JohannesJo on 2011-10-23
Maybe its related to this:
[http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/)

---

### Post by OneXero on 2011-10-23
> **aeronutt said:**
> My current draw went from ~1500mA to ~800mA with the following kernel options

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then sudo update-grub

The one that made the majority (nearly all) of the difference was the first.

How do I check my current draw?

---

### Post by kaldor on 2011-10-23
> **OneXero said:**
> So I installed it, and I clicked on it using the search, but no window popped up, so I am not sure how to change it's settings. I'll look into it further, not sure what I did wrong.

It should be in the notification area. Is there nothing showing up?

---

### Post by OneXero on 2011-10-23
> **kaldor said:**
> It should be in the notification area. Is there nothing showing up?

Not that I can see. I am using gnome shell if that matters.

---

### Post by kaldor on 2011-10-23
> **OneXero said:**
> Not that I can see. I am using gnome shell if that matters.

Me too, and it's in the bottom right corner for me. Try a relogin? Kinda odd that it's not working.

---

### Post by aeronutt on 2011-10-23
> **OneXero said:**
> How do I check my current draw?

Unplug the charger, and in a terminal

```
more /proc/acpi/battery/BAT0/state 
```

You should get something like:

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            802 mA
remaining capacity:      4315 mAh
present voltage:         12287 mV

---

### Post by OneXero on 2011-10-23
> **kaldor said:**
> Me too, and it's in the bottom right corner for me. Try a relogin? Kinda odd that it's not working.

Hah! There is no icon for me, for some reason, but when I plugged in my charger I got a "maximum performance mode" pop up with the Jupiter thunderbolt symbol.... Trying relogin.

---

### Post by OneXero on 2011-10-23
> **aeronutt said:**
> Unplug the charger, and in a terminal

```
more /proc/acpi/battery/BAT0/state 
```You should get something like:

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            802 mA
remaining capacity:      4315 mAh
present voltage:         12287 mV

No such directory...:(

---

### Post by kaldor on 2011-10-23
> **OneXero said:**
> Hah! There is no icon for me, for some reason, but when I plugged in my charger I got a "maximum performance mode" pop up with the Jupiter thunderbolt symbol.... Trying relogin.

That's odd :confused:

That applet really helps, though. Take a look [_here_]("http://ubuntuforums.org/showthread.php?t=1854019"). :)

---

### Post by OneXero on 2011-10-23
Interesting, I reinstalled ubuntu completely now that it's fixed and used my entire ssd instead of having windows partitioned...that was the last issues that needed fixing - now that I've done this, jupiter should have been uninstalled, and I still can't see the icon or anything...but the effect is still there - increased battery life, no fan spinning - the same results I got from installing it...

Does jupiter persist even after a complete format and reinstall? I am curious as to how...

---

### Post by JohannesJo on 2011-10-24
I dont know how reinstalling works exactly. When I did it once the error with unity leading to this step was still persistent. Due to this and regarding the much higher speed of the installation I suppose that lots of data is just kept as it is on the hard disk. As the problem relates to the kernel I would suppose that the changes made by Juniper (despite it being not installed/uninstalled) are made to the kernel and thus are not gone.

Just speculation though.

---

### Post by OneXero on 2011-10-24
I reinstalled Jupiter and I still have no Jupiter icon!! Anyone know what's up with this?

---

### Post by aeronutt on 2011-10-24
> **OneXero said:**
> No such directory...:(

No /proc/acpi directory?

Still, you should try adding the kernel options I posted.

---

