---
title: "Strange things happen suddenly"
date: 2010-11-24
forum: General Help
---

### Post by DeMus on 2010-11-24
Hi,
Since yesterday I suddenly noticed my lower panel uses other colors, other icons, in other words an other theme. I did not change the theme so something else must have changed it. I am the only user of this computer so no-one else could have done it.
A second strange thing is when I watch a movie, using VLC, the screen turns black after 10 minutes. The led on the front-side starts to blink and I see the icon for Analog/Digital input flashing on screen for a while, then it is totally black.
In the VLC preferences I see the tick-box for "disable screensaver" checked, so that can not be it.
Powermanager does not switch of the screen, well that's what the preferences tell me.
In the monitor itself I also can not find anything relating to 10 minutes (I clocked that).
What can cause these strange things? Is it an update I received, do more people see these, or other, strange things happen?
Who can help me?

---

### Post by sikander3786 on 2010-11-24
Your PC is haunted :lolflag:

Regarding theme, did you change it back to the previous one and see if "something" changes it again to its likings? :P

When the display goes black at VLC and you move your mouse, does your monitor come up again? And do you feel it was the screensaver?

Which version of Ubuntu is this? I am running both 10.10 and 10.04 with all updates till date applied and don't have any issue, whatsoever.

---

### Post by DeMus on 2010-11-25
> **sikander3786 said:**
> Your PC is haunted :lolflag:

Regarding theme, did you change it back to the previous one and see if "something" changes it again to its likings? :P

When the display goes black at VLC and you move your mouse, does your monitor come up again? And do you feel it was the screensaver?

Which version of Ubuntu is this? I am running both 10.10 and 10.04 with all updates till date applied and don't have any issue, whatsoever.

Yes, I did choose the same Theme again, until now no more changes. Strange thing is I have had this before with previous versions of the OS.
At the moment I run LinuxMint Isadora 9, which resembles Lucid.

Yes, when I move the mouse in VLC when the picture is black, it does come up again. The screensaver is set to non, I even set the time to maximum so it can't be that.
I would say I'm afraid it is something in the monitor, strange thing here is it started some days ago. It used to be good, I could watch movies without any problems. Now it just goes black, also without VLC. I can't find it, so if you have some more ideas please share.
Thanks.

---

### Post by sikander3786 on 2010-11-25
If moving the Mouse brings up your display, I believe there is no problem with the monitor itself.

Which graphics card is there? And did you install proprietary drivers for that?

Does that problem seem to affect some other player also besides VLC?

---

### Post by DeMus on 2010-11-25
> **sikander3786 said:**
> If moving the Mouse brings up your display, I believe there is no problem with the monitor itself.

Which graphics card is there? And did you install proprietary drivers for that?

Does that problem seem to affect some other player also besides VLC?

I have the Nvidia GT8500 with driver 260.19.21 coming from a repository I got from a ppa website.
The problem is not only VLC, it's in fact all programs and even when no program is running and I am only watching my 500 pictures alternating on my desktop. In other words it happens all the time.
I have been looking around and found nothing related to 10 minutes.
What can it be? Who can help me with this annoying problem?

---

### Post by matt_symes on 2010-11-25
Hi

What BIOS do you have? Just wondering if it's a BIOS setting?

Kind regards

---

### Post by DeMus on 2010-11-25
> **matt_symes said:**
> Hi

What BIOS do you have? Just wondering if it's a BIOS setting?

Kind regards

I have an AMI BIOS and I will look into it straight away. Never thought about that possibility. Thanks for the idea.

---

### Post by DeMus on 2010-11-25
No, also in the BIOS I could not find anything related to my problem. Thanks anyway for the tip.

---

### Post by matt_symes on 2010-11-25
Hi

What does it say in the logs? and dmesg?

Is it just the monitor powering down or is it going to suspend?

Kind regards

---

### Post by DeMus on 2010-11-25
> **matt_symes said:**
> Hi

What does it say in the logs? and dmesg?

Is it just the monitor powering down or is it going to suspend?

Kind regards

It is only the monitor. The computer just keeps on running.
What should I look for in dmesg? I get a very long list and have no idea what to look for.
The same for the logs. Which log file and what am I looking for?

---

### Post by DeMus on 2010-11-25
This is my dmesg output. (see attachment)

---

### Post by matt_symes on 2010-11-25
Hi

BTW: What is the value of 'Regard the computer as idle after ...' value on your screen saver preferences dialog?

Kind regards

---

### Post by Gunman1982 on 2010-11-25
Did you already check or energy saving properties? The little powerplug icon or under 'System->Properties->Energy...' (menu just a guess since I don't use the english language for my system). Check there if you set something like turning off the screen after x minutes.

Normally it shouldn't trigger if you watch a movie (at least it doesn't when you use totem I think) but maybe vlc doesn't announce that its running to the system so the system thinks you are not doing anything and triggers the energy saving settings.

---

### Post by matt_symes on 2010-11-25
Hi

Open a terminal and type

xset q

Post the results back here. Part of the result will tell us about you dpms setup.

EDIT: If dpms is enabled at a terminal type

xset -dpms

and see if your monitor suspends.

If it does not suspend the monitor, add the command to your ~/. bashrc file and ensure the file is executable chmod +x .bashrc

Kind regards

---

### Post by DeMus on 2010-11-25
> **matt_symes said:**
> Hi

Open a terminal and type

xset q

Post the results back here. Part of the result will tell us about you dpms setup.

EDIT: If dpms is enabled at a terminal type

xset -dpms

and see if your monitor suspends.

If it does not suspend the monitor, add the command to your ~/. bashrc file and ensure the file is executable chmod +x .bashrc

Kind regards

matt_symes, Thank you so very much. O boy am I stupid. Call me blond if you like.
I always had the screensaver program installed and had it set to no screensaver, I even set the time to maximum to not be badly surprised should it still work.
I must have deleted the program, I can not remember it, but it was no longer installed.
When I typed the xset -q in a terminal I saw the 600 seconds for the timeout and the standby:

```
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600

DPMS (Energy Star):
  Standby: 600    Suspend: 600    Off: 600
```

I installed it again and switched off the screensaver immediately. Now I get:

```
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 14400
```

I tested it and the monitor stays on now, just as I want it.
Thank you so very much, you have made my day.

DeMus

---

### Post by matt_symes on 2010-11-25
Hi

> Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 14400
[FONT=monospace]
[/FONT]It will still suspend mind you (if that is what is what you want)

Kind regards

---

### Post by DeMus on 2010-11-25
> **matt_symes said:**
> Hi

[FONT=monospace]
[/FONT]It will still suspend mind you (if that is what is what you want)

Kind regards

How to change that? I have been trying to find where I can change this but can't find it. Please help.

---

### Post by matt_symes on 2010-11-26
Hi

Good morning DeMus

```
EDIT: If dpms is enabled at a terminal type

xset -dpms

and see if your monitor suspends.

If it does not suspend the monitor, add the command to your ~/.bashrc file and ensure the file is executable chmod +x .bashrc
```Try this. I have not had your problem so i am relying on the man pages....

Kind regards

---

### Post by DeMus on 2010-11-27
> **matt_symes said:**
> Hi

Good morning DeMus

```
EDIT: If dpms is enabled at a terminal type

xset -dpms

and see if your monitor suspends.

If it does not suspend the monitor, add the command to your ~/.bashrc file and ensure the file is executable chmod +x .bashrc
```Try this. I have not had your problem so i am relying on the man pages....

Kind regards

Hi matt_symes, thanks for sticking with me.
I used the xset -dpms and when watching a movie the screen does not go blank anymore. But when I am just looking at my desktop, after 10 minutes it does go blank.
Any idea where I can find the 10 minutes (or 600sec) so I can change that? I must have looked everywhere but can't find it.
Another thing I found is this:
Typing xset -q gives me this:

```
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled

```
I then used "xset s noblank" and "prefer blanking yes" has changed to no. I'll test it and see if this is what caused the blanking.
Thanks so much for your help.

Edit: I waited 15 minutes in front of my monitor and saw many wonderful hi-res pictures passing by **WITHOUT** the screen go blank. So, I think this problem, well annoyance, is solved.
Thanks to all who helped me.

---

