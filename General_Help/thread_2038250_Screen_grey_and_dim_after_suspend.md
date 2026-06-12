---
title: "Screen grey and dim after suspend"
date: 2012-08-06
forum: General Help
---

### Post by Bucky Ball on 2012-08-06
Hi all,

As per the title. When I close the laptop lid, suspends and all is good if only for awhile. If I leave it for a long while, when I open the lid, comes out of suspend okay but I can only just see the desktop enough to get to the Log Out button, log out and log back in, then all is good again. 

Fresh install of Xubuntu 12.04 LTS. After three days of problems, touch wood, this seems like the last. Just ask if more info required.

---

### Post by Toz on 2012-08-06
When this happens, can you increase the brightness using your brightness function keys? Does that make the screen bright again?

Can you run the following command and post back the results? It will query and display information about your backlight interface(s):
```
for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
```

---

### Post by Bucky Ball on 2012-08-06
```
sproinks@tosh:~$ for file in /sys/class/backlight/*; do echo $file; cat $file/actual_brightness; cat $file/max_brightness; cat $file/brightness; done
/sys/class/backlight/acpi_video0
7
7
7
/sys/class/backlight/toshiba
7
7
7

```I haven't tried the brightness (don't have that icon and can't see enough to find it but might try) but doesn't look like a brightness thing. It is like everything is still there but it has a piece of heavy gauze over the screen. Weird.

I'll try the brightness. Cheers.

* Hmmm. Don't seem to have a brightness applet available. I am using a fairly stripped back version of Xubuntu 12.04. ;)

---

### Post by spjackson on 2012-08-06
> **Bucky Ball said:**
> 
* Hmmm. Don't seem to have a brightness applet available. I am using a fairly stripped back version of Xubuntu 12.04. ;)
I don't think Toz was suggesting an applet. Most laptops have function keys on the keyboard that double up for things like changing the volume, adjusting the brightness, perhaps turning wireless on/off. Depending on how the laptop is configured, you may have to hold down a Fn key to use these functions. On the 2 laptops I have to hand, the brightness symbol is like a circle with rays coming out.

---

### Post by Bucky Ball on 2012-08-06
> **spjackson said:**
> I don't think Toz was suggesting an applet. Most laptops have function keys on the keyboard that double up for things like changing the volume, adjusting the brightness, perhaps turning wireless on/off. Depending on how the laptop is configured, you may have to hold down a Fn key to use these functions. On the 2 laptops I have to hand, the brightness symbol is like a circle with rays coming out.

Found that. Makes no difference on my normal desktop screen, though. I see the brightness icon when I hit the key combo but the screen brightness changes not. Am going out later so will try when I get back, just in case. 

Even if this does work, it shouldn't be happening in the first place and I would like to tweak to fix. There must be a config issue somewhere. Will keep digging if I get some time later but 'under the pump' a bit at the moment. ;)

---

### Post by Bucky Ball on 2012-08-09
Any takers? I have noticed that it appears random and the majority of the time it doesn't happen. But annoying as hell when it does (especially when in a hurry!).

At first I thought it was a time thing but over the last couple of days have noticed it's not. I just left the room for five minutes and screen 'gauzed' when I just opened the lid. I left it all day yesterday, opened lid and fine.

---

### Post by brainwash on 2012-08-20
Really annoying bug, most likely related to xscreensaver and/or AMD Radeon cards.

[https://bugs.launchpad.net/bugs/1015297](https://bugs.launchpad.net/bugs/1015297)

---

### Post by Bucky Ball on 2012-08-20
Yea. I have the AMD Radeon. Can't figure it out. I did notice in Power Management, under 'Extended' and 'Set Monitor Sleep Mode' was set to 'Standby'. I have set this to Suspend to see if that makes a difference.

Wild stab in the dark, really. Thanks for the input. ;)

PS: I have posted on the bug report as, although mine is slightly different as it appears random, the poster has given an exact description of what actually happens. The black sheet on top of what's there is it.

---

### Post by brainwash on 2012-08-22
Things to try:

A) Navigate to Settings Manager > Screensaver > Adavnced > Fading and Colormaps and untick *Fade to Black when Blanking*.

B) Disable oder even remove xscreensaver completely.

---

### Post by Bucky Ball on 2012-08-22
@brainwash: I tried A. Will let you know how it goes. Cheers. ;)

---

### Post by brainwash on 2012-08-26
So does this issue still occur? If yes, some log files (dmesg, xorg,..) might contain useful information to find the culprit. However, I really suspect that the fading animation gets interrupted at some point leaving the corresponding overlay screen still visible after resuming the system.

---

### Post by Bucky Ball on 2012-08-26
> **brainwash said:**
> A) Navigate to Settings Manager > Screensaver > Adavnced > Fading and Colormaps and untick *Fade to Black when Blanking*.

I'm using Xubuntu so the wording is slightly different but same idea. I tried this and have been waiting before posting back. Haven't noticed it do it for awhile so I'm almost convinced. Thanks.

---

### Post by brainwash on 2012-09-02
> **Bucky Ball said:**
> Haven't noticed it do it for awhile so I'm almost convinced.
I suppose this thread can be marked as "Solved" then. Moreover, the status of the bug report on launchpad needs to be updated.

---

### Post by Bucky Ball on 2012-09-03
> **brainwash said:**
> I suppose this thread can be marked as "Solved" then. Moreover, the status of the bug report on launchpad needs to be updated.

Hardly used my computer lately and this is not ready to be marked as solved. As mentioned, not convinced. That it should resolve itself with not human intervention is extremely unlikely, but not outside the realms of possibility.

---

### Post by Imvor on 2012-09-30
> Originally Posted by **brainwash**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12188663#post12188663")                 
                 *A) Navigate to Settings Manager > Screensaver > Adavnced > Fading and Colormaps and untick [I]Fade to Black when Blanking*.[/I]
=> This is what resolved this problem for me.

Xubuntu fresh install with Radeon 7750.
Problem occurred only after I installed fglrx-amdcccle package.
This "incomplete fade-in" occurred every time I used xscreensaver, after locking the screen or exiting stand-by mode. All the screen is grey, only the mouse is not affected.
Any change to Settings Manager > Display would restore normal brightness, until the next use of xscreensaver.

As I said, problem is solved for me by disabling the fade-out.

---

### Post by Bucky Ball on 2012-10-01
Sorry all. Forgot about this thread. I have done nothing to fix it but hasn't happened in ages so will take a chance and mark this solved ... by divine intervention?

Cheers ...

@ imvor: Thanks for that and hopefully it can help someone in future ...

---

### Post by kcxzero on 2012-10-04
> **brainwash said:**
> Things to try:

A) Navigate to Settings Manager > Screensaver > Adavnced > Fading and Colormaps and untick *Fade to Black when Blanking*.

Thank you very much, this worked for me too. I've been testing it for about 2 weeks now, has not happened once since I disabled it. Use to occur about every second time after coming out of suspend. My GPU is Radeon 4650.

---

