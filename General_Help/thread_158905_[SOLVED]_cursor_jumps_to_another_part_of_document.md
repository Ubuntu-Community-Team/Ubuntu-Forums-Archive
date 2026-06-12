---
title: "[SOLVED] cursor jumps to another part of document"
date: 2006-04-11
forum: General Help
---

### Post by mdsmedia on 2006-04-11
I use Thunderbird, OpenOffice 2, Firefox, and I've found in all these packages, I'll be typing away (in Firefox it might be in a forum like this) and all of a sudden I find I'm editing the middle of a line 3-4 lines up, or some other place, or it just jumps out of the edit box and I'm not typing anywhere.

Any idea what might be happening and how I might fix this?

---

### Post by moephan on 2006-04-12
Here's a WAG: perhaps you are using a laptop with a touch pad with a "tap to click" feature, and you hit it with the palm of your hand whilst you are typing. If this is the case, you can disable tap to click.

Cheers, Rick

---

### Post by rabidphage on 2006-04-12
yup .........that could be coz the touch pad drivers aren't smart enough at this stage to recognise accidental taps and stuff like that. Hopefully it'll be fixed soon
If u have a short cut key to disable the pad (and if it works:D )use it. its usually the fn key with some combokey or a key atop the pad. It'll be second nature after some time. Or alternatively disable tap.

---

### Post by GoodPanos on 2006-04-12
Yep, the same happens to me too.  And I do have a laptop with a touchpad.  In the Windows version of the Synaptics driver it has an option to disable the touchpad while typing.

Is there perhaps an option like this in the Linux version?

---

### Post by moephan on 2006-04-12
Funny, seems like this has been coming up a bit lately. Here's a link to a related thread: [http://ubuntuforums.org/showthread.php?t=132590](http://ubuntuforums.org/showthread.php?t=132590)

Cheers, Rick

---

### Post by mdsmedia on 2006-04-17
Thanks, that might be what it is. I hadn't even thought of that, because I don't use the touchpad if I can get away with it, but I might just be tapping it accidentally while I'm typing.

I plugged a mouse in for just that reason, that I didn't know how to disable the tapping, and it's far too sensitive.

I'll take more notice and maybe that is what's causing it.

I've also found some touchpad drivers on the web but haven't yet had the courage (or time and inclination) to install them. I'm pretty sure I have them bookmarked on my notebook (using XP desktop at work atm). So I'll post the URL's when I get on my notebook again.

Cheers,

Michael

---

### Post by bliffle on 2007-11-13
Couple months ago I found the solution within these forums (fora?) and applied it with great success, but then it disappeared after I upgraded from feisty to Gutsy (with the alternateCD followed by the usually flurry of internet updates).

---

### Post by bliffle on 2007-11-14
I believe this is the patch I found a few weeks ago, so I applied it to my Gutsy, but I still get that cursor hopping.

in:

/etc/X11/xorg.conf

if req'd add to the Synaptics Touchpad section:
        Option          "MaxTapTime"            "0"

to make sure you have:
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapTime"            "0"
EndSection

---

### Post by Nuafite on 2007-12-19
> **moephan said:**
> Here's a WAG: perhaps you are using a laptop with a touch pad with a "tap to click" feature, and you hit it with the palm of your hand whilst you are typing. If this is the case, you can disable tap to click.

Cheers, Rick

Thanks, Moephan. Disabling "tap to click" saved me from going mad.

---

### Post by tiltus on 2008-07-14
Today was the first time I gave my netbook a good slogout with the typing, and I must have spent a third of the time rearranging after this very problem kept happening to me. 

Did a search and here's a recent solution on how to fix it.
[http://maketecheasier.com/ubuntu-hardy-disable-synaptics-touchpad-when-typing/2008/06/24](http://maketecheasier.com/ubuntu-hardy-disable-synaptics-touchpad-when-typing/2008/06/24) 
:)

---

### Post by mh_pathfinder on 2008-07-17
This is a problem that has, indeed, been plaguing some UBUNTU laptop touchpad users for at least as far back as the Feisty Fawn release of Ubuntu.  None of the configuration fixes worked for my HP Special Edition L2005US laptop touchpad by Synaptics, but simply clicking off the "Enable mouse clicks with touchpad" option on the mouse settings DOES work, at least for my particular laptop.  The left- and right-click buttons being only a fraction of an inch below the touchpad, it is no inconvenience to make the click behavior change for me. 

This particular solution was offered for previous versions, i.e., Feisty Fawn and Gutsy Gibbon, as well as other configuration solutions, but none of them actually worked for my HP Special Edition L2005US, until the current 8.04 Hardy Heron.  Many good fixes in Hardy Heron, the solution to the case of the jumping cursor is one of them.  I know this didn't work for a couple of you and your particular laptops, so I hope you find some alternative solutions.  Thanks to the UBUNTU users who found this one that worked for me.  Amen.  MH

---

### Post by mdsmedia on 2008-07-20
> **mh_pathfinder said:**
> This is a problem that has, indeed, been plaguing some UBUNTU laptop touchpad users for at least as far back as the Feisty Fawn release of Ubuntu.  None of the configuration fixes worked for my HP Special Edition L2005US laptop touchpad by Synaptics, but simply clicking off the "Enable mouse clicks with touchpad" option on the mouse settings DOES work, at least for my particular laptop.  The left- and right-click buttons being only a fraction of an inch below the touchpad, it is no inconvenience to make the click behavior change for me. 

This particular solution was offered for previous versions, i.e., Feisty Fawn and Gutsy Gibbon, as well as other configuration solutions, but none of them actually worked for my HP Special Edition L2005US, until the current 8.04 Hardy Heron.  Many good fixes in Hardy Heron, the solution to the case of the jumping cursor is one of them.  I know this didn't work for a couple of you and your particular laptops, so I hope you find some alternative solutions.  Thanks to the UBUNTU users who found this one that worked for me.  Amen.  MHSince the question predates Feisty, I'm sure that the problem predates Feisty...as did the solution offered. It's easily fixed.

---

