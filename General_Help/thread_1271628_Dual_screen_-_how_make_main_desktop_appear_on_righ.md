---
title: "Dual screen - how make main desktop appear on right side monitor"
date: 2009-09-21
forum: General Help
---

### Post by kjetilbmoe on 2009-09-21
Dear experts,
I have connected an LCD and a CRT monitor to my computer running Ubuntu 9.04. The LCD is located to the right of the CRT - but my main problem is that I want the LCD to be my default one, where the menus and default desktop appears. I have an Intel 965, no fancy Nvidia card I'm afraid - but shouldn't there be a way to set this so that I can use my LCD as "default" monitor? Does the main screen always have to be the VGA one?

---

### Post by Owlman on 2009-10-04
Same problem. I tried using System->Preferences->Display to rearrange them, but that resulted in losing one monitor (it just went black). Putting it back again made them both black. I had to turn off my computer (by holding down the on button) and reboot. Luckily everything came back up again, but I'm not game to fiddle with it any more!

---

### Post by fela on 2009-10-04
If you're using nvidia, go to nvidia settings and change your default monitor from there.

If you just want to move your panels around, just move them around it'll work.

If you're using intel or ATI, sorry I can't help you as I've only ever been with nvidia.

---

### Post by Owlman on 2009-10-04
Radeon X1600 Pro... :(

---

### Post by fela on 2009-10-04
> **Owlman said:**
> Radeon X1600 Pro... :(

There might be an ATI control panel.

---

### Post by kjetilbmoe on 2009-10-04
The rearranging works fine. But it's the thing about not being able to choose a default screen which really annoys me. Somehow my CRT screen is favoured instead of my better LCD-screen. I just cannot see the logic in that the VGA outlet should be equivalent to the "best" screen ...

---

### Post by Sjenitzer on 2009-10-21
I've got the same problem. The left screen is always the main screen, but I like my right screen to be the main screen. My graphics card is an onboard intel.

---

### Post by P4man on 2009-10-21
what is "main" about the main screen?
Just create 2 new panels, drag them to the right screen (one top one bottom) and add all the menu's and notification area's. Then feel free to delete the panels on the left screen if you want. (Note only 1 notification area can be active at a time, so if you make on on the right screen you have to delete it on the left before it shows and works).

---

### Post by kjetilbmoe on 2009-10-22
But what will then happen next time - when I only use the laptop monitor itself, or then reconnect the second monitor - will the settings persist?

---

### Post by P4man on 2009-10-22
good question. I guess the settings will persist, but you dont want to remove everything from your laptop monitor as you'll end up not having any panels without the other screen attached. I guess.  cant tell for sure though, as thankfully I got an nvidia card and its dead easy to configure twinview any way I want.

---

### Post by Sjenitzer on 2009-10-22
Thanks, this is in a very simple, and therefore nice, solution, but when I switch to only the laptop screen and then back to 2 screens the panel are back at the left.


Bart

---

### Post by kjetilbmoe on 2009-10-22
Exactly. There **should** have been an option to choose main screen, not just move panels around randomly ... they don't stay this way obviously.

---

### Post by P4man on 2009-10-22
perhaps one of you can post your xorg.conf? Dont know what it looks like on an intel dual monitor setup. With nvidia you have a "TwinViewXineramaInfoOrder" option where you can specify which is the first screen.

---

### Post by Sjenitzer on 2009-10-22
My xorg.conf is 
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2880 900
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```

But I don't see where I could specify a first screen

---

### Post by P4man on 2009-10-22
Indeed, thats kinda empty lol. Have you tried ```
grandr
``` ? its in the repo's

---

### Post by ptgood on 2009-10-23
I just fix the same issue.

I moved the two original panels from the left monitor to the right one.

When I use only the laptop (the left of the two) everything gets back in place. 
When I reconnect the second screen and restart, the panels are on the right side again!!


Hope it work for you too!


PS. For moving the panels I un-tick expand in their properties, move them and tick again to expand.

---

### Post by Sjenitzer on 2009-10-26
Hmm , my panels jump back after I've booted with a single screen and the grandr only sets my screens to mirror mode. 

But I think I'll wait a week, because the 9.10 version apparently upgrades the intel video driver:
[http://www.ubuntu.com/testing/karmic/beta#New%20Intel%20video%20driver%20architecture%20available%20for%20testing](http://www.ubuntu.com/testing/karmic/beta#New%20Intel%20video%20driver%20architecture%20available%20for%20testing)

See if this solves some problems

---

### Post by Sjenitzer on 2009-11-02
> **Sjenitzer said:**
> Hmm , my panels jump back after I've booted with a single screen and the grandr only sets my screens to mirror mode. 

But I think I'll wait a week, because the 9.10 version apparently upgrades the intel video driver:
[http://www.ubuntu.com/testing/karmic/beta#New%20Intel%20video%20driver%20architecture%20available%20for%20testing](http://www.ubuntu.com/testing/karmic/beta#New%20Intel%20video%20driver%20architecture%20available%20for%20testing)

See if this solves some problems

It worked for me, Ubuntu 9.10 remembers where my panel were on a dual screen mode.

---

### Post by tirthapratim1987 on 2011-02-04
Just go to System->preferences->monitor and set the laptop and external monitor screen with laptop in the left and external monitor in the right. Set the resolutions as adjusted.

By default the laptop will be the primary.

if u want to make the external monitor as ur primary run the command.

xrandr --output HDMI2 --primary

<HDMI2> is ur external monitor here. u willl get the correct o/p for command "xrandr".

---

