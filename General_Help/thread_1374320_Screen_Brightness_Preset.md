---
title: "Screen Brightness Preset?"
date: 2010-01-06
forum: General Help
---

### Post by underthestars on 2010-01-06
Hello all, I'm a new user of Ubuntu after becoming fed up with Vista and Windows in general. I have a question about screen brightness/contrast. On my Vista computer I was able to make several &quot;schemes&quot; for brightness from dim to brighter depending on whether I'm using the computer in general or watching a movie. I am one of those people whose eyes hurt if the screen is too bright. I have used the setting in CompizConfig where I can set keyboard shortcuts to dim and brighten the screen, but it only works for one screen at a time and leaves other pieces like the taskbar, firefox bookmarks, drop down menus, etc too bright. Is there another way I can dim the screen without having to go to all that trouble? The default setting for ubuntu is far too bright for my eyes. I have my monitor set to 0 brightness and contrast, but it's not enough. The screen is far too bright still. Please help! I'm enjoying Ubuntu, but this is definitely a problem for me. 

Here's some specs for my computer:
HP/Compaq SR5633WM
Intel Pentium Dual CPU E2200 @ 2.20GHz
Compaq Monitor WF1907
OS: Ubuntu 9.10 Karmic / Vista Home Premium

---

### Post by mikewhatever on 2010-01-06
There should be a slider for screen brightness under System->Preferences->Power-Management. I guess the default is 100%, so try lowering it to a more comfortable level.

---

### Post by underthestars on 2010-01-06
> **mikewhatever said:**
> There should be a slider for screen brightness under System->Preferences->Power-Management. I guess the default is 100%, so try lowering it to a more comfortable level.

Only thing in my power management menu is the following:
- On AC Power: actions and display for computer and monitor to sleep.
- General: actions for power and suspend buttons.
Notification Area: icon, battery power, charging.

---

### Post by mikewhatever on 2010-01-06
I see, Gnome guys are notorious for hiding useful tools away. You can still change the default brightness with **gconf-editor**. Just run that in a terminal, navigate to apps/gnome-power-manager/backlight, and click on brightness_ac to change the value.

---

### Post by underthestars on 2010-01-06
> **mikewhatever said:**
> I see, Gnome guys are notorious for hiding useful tools away. You can still change the default brightness with **gconf-editor**. Just run that in a terminal, navigate to apps/gnome-power-manager/backlight, and click on brightness_ac to change the value.

I changed the setting like you said, but nothing has changed and my desktop is still as bright as ever.

I included an example of how I have one of my presets on Vista and to show you that I did change the value for brightness in the config, but it's still bright. Hasn't changed at all. I should also mention that I am on a Desktop not a laptop.

---

### Post by mikewhatever on 2010-01-07
If that doesn't work, perhaps you monitor has adjustable brightness. It's likely, since you seem to be using a desktop, if the specs in post #1 are to go by.

---

### Post by underthestars on 2010-01-07
> **mikewhatever said:**
> If that doesn't work, perhaps you monitor has adjustable brightness. It's likely, since you seem to be using a desktop, if the specs in post #1 are to go by.

 It does, but I always keep it on 0 for brightness and contrast. Yet, UBU is still completely way too bright. I'm back on my Vista side of the drive and am now looking at a nice dim screen. But every time I boot up in UBU the screen is super bright. And yes I did check my monitor's settings when I was on UBU. Still said 0 for both brightness and contrast. Even when I'm on Vista I still have to dim the system by going to the Intel Graphic Properties I posted in my last post. The settings directly from the monitor don't do much. My monitor is a Compaq WF1907. 

I realize this is an entirely different system than Windows, but it still should come with an interface for brightness and contrast. That way you had me go in and edit the value didn't do a thing and I even restarted to see if it would. Whenever I'm on UBU my eyes feel like their gonna start bleeding from how bright it is.

---

### Post by underthestars on 2010-01-07
Anyone? Is there some package I can download for my Intel G33/G31 Express Chipset Family for my monitor so I can fix the brightness/contrast in color correction like I do on Windows? Please! There's got to be a way to fix this. :(

---

### Post by mikewhatever on 2010-01-07
I have to admit, this is a tough one. With neither gnome-power-manager, nor the on-screen tools working, I only hope someone has exactly the same setup and had it solved before. Meanwhile, it wouldn't hurt trying gddccontrol from the repositories.

---

### Post by underthestars on 2010-01-07
> **mikewhatever said:**
> I have to admit, this is a tough one. With neither gnome-power-manager, nor the on-screen tools working, I only hope someone has exactly the same setup and had it solved before. Meanwhile, it wouldn't hurt trying gddccontrol from the repositories.


Edit: never mind I found it in the software center. I installed it but nothing comes up. I don't have a third-party graphics card. My graphics card came with the computer. It's an "Intel G33/G31 Express Chipset Family". Or at least that's what it said in the devices tab through Windows.

Also got this info from the terminal:

>   *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0

---

### Post by underthestars on 2010-01-08
I wanted to let you know that I'm giving up and overwriting the entire drive with Vista. I appreciate your help but there's obviously nothing that can be done. I like UBU but like I said before I can't use it with this backlighting problem. Too many headaches have resulted from it. Maybe if this issue gets sorted out I'll try it again. That and I really do not understand linux and all the commands. But I digress, thanks for trying.

---

