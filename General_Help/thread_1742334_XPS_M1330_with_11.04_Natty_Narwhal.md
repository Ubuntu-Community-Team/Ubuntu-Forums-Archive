---
title: "XPS M1330 with 11.04 Natty Narwhal"
date: 2011-04-28
forum: General Help
---

### Post by x C0MMAND0 x on 2011-04-28
Before I upgrade, what are some issues anybody has been having with upgrading/installing 11.04? I currently have Dell XPS M1330 running 64bit 10.10, and will be doing an upgrade as opposed to a clean install.

Any issues for anybody out there? I know it just came out, but I am still curious...

Please post if you:
1. Clean Install vs Upgrade
2. 32bit vs 64bit
3. Any hardware issues after upgrade/install
4. Other comments

I will be upgrading in a week or two here and will post my results, but I want to know how everyone else's experiences go.  Wireless?  Webcam?  Media buttons?

---

### Post by mc4man on 2011-04-28
Been using a 1330 thru the whole dev cycle so many fresh installs, both 32 and 64 bit
Atm on 32
Is about 3 yrs old with 8400m
No issues hardware wise at all, suspend works, don't use hibernation
Both the nvidia and nouveau 3d drivers work, better with the nvidia

May run a few degrees hotter than previously though I think that's more the rise in ambient temp and the so called cooling system degrading over time
Overall performance is better on natty than maverick, the boot may be a few seconds longer, don't care.

(I do lower the sleep time in /etc/init.d/ondemand to 20 secs to get to ondemand from performance quicker
Also I lower the up_threshold for scaling from the default of 95 to 80 for a little better performance

At this point the battery (orig) is pretty shot so don't know about battery life, likely to be lower due to kernel bug

---

### Post by x C0MMAND0 x on 2011-04-28
Kernel bug?  Otherwise glad to hear things are working out for you.

---

### Post by mc4man on 2011-04-28
> Kernel bug?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)
[http://ubuntuforums.org/showthread.php?t=1739770](http://ubuntuforums.org/showthread.php?t=1739770)

---

### Post by geoffm on 2011-04-28
thanks mc4man!
I will be upgrading myself tomorrow. will leave feedback.
by the way, do you guys get that very loud monstruous sound from the dvd drive whenever computer wakes up or boots? Ever find a way to ease the acoustic pain?

---

### Post by mc4man on 2011-04-28
> that very loud monstruous sound from the dvd drive whenever computer wakes up or boots? not really - though if I leave a disk in the drive it tends to run at times when I'm not accessing it (not the quietest.
Had mine replaced once under warranty, don't think those ultra-slims are any better than just ok quality (matshita here

---

### Post by x C0MMAND0 x on 2011-04-28
> **geoffm said:**
> thanks mc4man!
I will be upgrading myself tomorrow. will leave feedback.
by the way, do you guys get that very loud monstruous sound from the dvd drive whenever computer wakes up or boots? Ever find a way to ease the acoustic pain?

They are incredibly loud disc drives on bootup - if there is no disk in it.  I remember when I got the laptop my only two qualms were that 1. It only has 2 USB ports, and 2. The disk drive is loud.  If those are the biggest two problems, then I say it safe to say it's a pretty good computer!

To get around it just leave a disc in the slot at all times.

---

### Post by vdeparday on 2011-04-29
I did an upgrade on Kubuntu 64bit install.

I got one main issue, my wireless did not work any more. 

I think XPS M1330 comes with different chipsets but if you have a Broadcom chipset you will likely hit this bug: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) 

I did the work around from comments #23 or #27 of this bug report (basically downgrading to the previous version of the STA driver) and my wireless is working again.

---

### Post by x C0MMAND0 x on 2011-04-29
> **vdeparday said:**
> I did an upgrade on Kubuntu 64bit install.

I got one main issue, my wireless did not work any more. 

I think XPS M1330 comes with different chipsets but if you have a Broadcom chipset you will likely hit this bug: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677) 

I did the work around from comments #23 or #27 of this bug report (basically downgrading to the previous version of the STA driver) and my wireless is working again.

Excellent, thank you for the information.  I'm sure this will be useful for a lot of people.

---

### Post by x C0MMAND0 x on 2011-05-02
Bump.

Any other issues/reviews from peoples experiences?

---

### Post by morbo84 on 2011-05-04
I upgraded from 10.10 and had some problems with Nvidia drivers... with proprietary drivers the system didn't start. so I formatted and reinstalled 11.04; now I use open drivers and all works fine.

---

### Post by geoffm on 2011-05-04
I switched from maverick 64 to Naughty 64 for 4 days now. Tried unity at first, missing too many important features such as applets and windows list so I'm running gnome2 again ("ubuntu classical"). I haven't experienced any important bugs except an occasionnal "instant logoff" coming from nowhere (happened 2-3 times so far).
My battery is almost dead, I can't tell if it uses more power. I'm not sure if it heats more because computertemp applet doesn't work anymore and I haven't found any other that works (major drawback here!); but I have a feeling it does a little bit.
I would say, unless you really like to have the latest software and all (i know I do), it's not really worth it to upgrade right away.

EDIT: 
forgot to mention, I recently switched from 32 to 64, system has been generally more unstable since, anyway.
Also, I found some gnome-sensors applet that can give me the temperature. seems to be running ok, around 47 with little activity.
upgrade not transferring OpenOffice settings to LibreOffice is kinda disapointing.

---

### Post by Danish989 on 2011-05-07
First of all, I'm so happy to see such a thread exists for other XPS users, will make debugging problems and pinpointing them so much easier and concise. 

Second, I've been using Natty ever since it released, and everything has been working absolutely fine.

I think the wireless issue occurred, but I don't remember because it probably wasn't that big a deal - I probably just connected via Ethernet and updated or used the additional hardware GUI.

However, my XPS has been overheating constantly, and it's become a nuisance. Sometimes it just shuts itself down, and I find the bottom panel to be scorching hot - which of course means it's doing that so the whole thing doesn't set on fire.

Also, the Bluetooth doesn't work out of the box, but that was a problem I had in 10.10 as well. (Does anyone have a fix for this, by the way?)

Also - my left speaker is shot and produces no sound, but I think that's a hardware issue, (correct me if I'm wrong.)

That's about it though, Unity is pretty much functional.

---

### Post by Church Punk on 2011-05-08
Hello guys :)

I have been using this build on my M1330 for 5 days now and am extremely happy with it. I, being a new linux user (the only linux experience being creating themes for PalmWebOS), "had" to install Ubuntu using WuBi, which worked like a charm.

Every thing worked right out of the box. The only thing that doesnt work is  the fingerprint reader (which doesnt really bother me), and one thing that bothers me is that the two finger scroll doesnt work at all. I have tried some synaptics downloads with no avail (it does work on vista).

But other than that, as i said, i have everything working; wifi, bluetooth (using BT mouse wihtout problems), nvidia drivers (using Unity), and have had no heating problems. 
I do have to mention that i did the copper mod for the heatsink a year ago, so it might be the reason why the fans are almost never up. Still need to test the HDMI interface, but it probably works too. 
Boot time is about 30 secs and everything opens blazing fast with a SSD. 

So another happy Linux user here :D

EDIT:
Forgot to mention that i screwed my laptop today, but my bro helped me to fix it. Long story short, i messed up the boot file. Had to use a Vista recovery CD to repair my system.
I like to "skin" whatever i can, so i tried to install BURG... So for everybody out there installing Ubuntu using Wubi, dont mess with grub, ever; it doesnt have one i believe ([see here]("http://ubuntuforums.org/showpost.php?p=10244196&postcount=2"))

---

### Post by Danish989 on 2011-05-09
First of all, I'm really drunk right now - so please excuse me if my reply is sloppy.

I think the fingerprint reader works, you just need to get the thingamajig application for it, which makes it work. I can't remember what it's called >__<

The double finger touch thing - I think that can also be enabled, if you go into the mouse preferences. In 10.10 it used to be System >> Preferences >> Mouse. But just searching for 'mouse' should bring it up in Unity....

So, yeah..

---

### Post by Church Punk on 2011-05-09
Thanks for the <drunken> imput :P. I installed thinkfinger and it works as expected! Thanks! The only doubt i have is if im able to change my password and it will recognize the changes.

About the touchpad, i changed the settings in the "mouse" configuration window, under the touchpad tab, but it just doesnt work ("scrolling" - "two-finger scrolling" is checked and it doesnt work, i have to check "edge scrolling" instead). 

Any ideas of why this might be? 

EDIT:
I get the error** "Can't access shared memory area. SHMConfig disabled?"** when i try to run a command on the terminal, like this:
synclient -m 15

---

### Post by age99 on 2011-05-15
Sounds like you guys are having more success than me.  I have a 32-bit XPS M1330, and I've had some major problems with the upgrade to 11.04.  The install crashed initially, but I've sinced tried to upgrade and update everything, and there doesn't seem to be anything missing, although Unity, crashes every time I open a terminal, and I have to reboot through the terminal.

The broadcom wireless is also not working.  

Did anyone have similar experiences?  Any tips/help for me?


Thanks

---

### Post by geoffm on 2011-05-16
I have been experiencing a very annoying bug. When I switch from 2 monitors to the internal monitor only, the display fails. It's all black with only the cursor showing. Doing [Fn] [CRT/LCD] doesn't do a thing, nor do [Ctrl] [Alt] [Del] nor [Ctrl] [Alt] [Backspace]

All I can do is a hard shutdown by holding the power button for several seconds. Of course I loose everything that is opened and have to wait for the whole thing to boot again. 

This is with gnome 2.

---

### Post by Danish989 on 2011-05-16
You might need to do a fresh install - if the installer crashed while trying to update to 11.04 ... that might be a big reason, I suspect.

I think the wireless drivers need to be manually downloaded, and it doesn't work out of the box. Did you try doing that?

---

### Post by Danish989 on 2011-05-16
Aah, I have this horrible problem too!

Correct me if I'm wrong - but this is because you're trying to give each display it's own x-screen? Xinerama might or might not be on.

I have no idea how to fix this, even though it was working fine in 10.10.

I thought it was just Unity up until now, but you are reporting this is with Gnome 2, which is kind of upsetting.

---

### Post by age99 on 2011-05-16
If I remember correctly, the 10.04 install wored immediately, but I can't be sure.  I am hoping not to have to do a complete re-install because I have a lot of programs that take a while to reinstall and configure.  I'm running a dual-boot, which further complicates things.  The wireless I am confident to fix, but the constant restarting Unity is a nightmare.

---

### Post by geoffm on 2011-05-20
> **Danish989 said:**
> Aah, I have this horrible problem too!

Correct me if I'm wrong - but this is because you're trying to give each display it's own x-screen? Xinerama might or might not be on.

I have no idea how to fix this, even though it was working fine in 10.10.

I thought it was just Unity up until now, but you are reporting this is with Gnome 2, which is kind of upsetting.

Damn, it does it with Unity too? I can't find Xinerama in the repos. I tried running Jupiter, to no avail.

---

