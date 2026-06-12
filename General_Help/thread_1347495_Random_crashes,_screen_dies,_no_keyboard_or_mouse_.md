---
title: "Random crashes, screen dies, no keyboard or mouse entry accepted"
date: 2009-12-06
forum: General Help
---

### Post by FionnMc on 2009-12-06
Hi,
First post here :)

My issue is that my screen will randomly die i.e. it will stop displaying whatever was being displayed at that point and go into standby as though it is receiving no signal from the PC. 

Tapping the keyboard or mouse will not "re-awaken" the display. I can still hear the PC whirring away and if any media is playing when these crashes happen then I can still hear it playing through the speakers.

I cannot ssh into the PC when these crashes occurs as any connection attempt just times out.

The only way to regain control of the PC is to switch it off by holding and pressing the hardware power button. Of course this means that any unsaved work is lost :(.

I'm running Xubuntu 9.10 Karmic Koala. This issue originally started to occur when I moved to Xubuntu 9.04. It occurred a lot more frequently in 9.04 i.e. at least twice every three days. It's occurring less frequently in 9.10 i.e. maybe twice a week.

I'm at a loss as to how to go about debugging this problem as it seems so random.
Where can I search for clues as to how to solve this issue?

---

### Post by sgardne on 2009-12-08
I have the same problem Xubuntu 9.10 on a Dell GX 270. I am new to Xubuntu, and I'm not finding the power settings where I can prevent standby from occurring in the first place. Am I looking in the wrong place? Anyone know how to prevent standby in Xubuntu?

---

### Post by FionnMc on 2009-12-11
> **sgardne said:**
> I have the same problem Xubuntu 9.10 on a Dell GX 270. I am new to Xubuntu, and I'm not finding the power settings where I can prevent standby from occurring in the first place. Am I looking in the wrong place? Anyone know how to prevent standby in Xubuntu?

Try Applications->Settings->Xfce-4 Settings Manager->Power Manager

[IMG]http://i48.tinypic.com/20ij91f.png[/IMG]

[IMG]http://i50.tinypic.com/oh4ldh.png[/IMG]

If any tweaks you make there improve things then let us know please :).

---

### Post by joes7 on 2009-12-11
Re-install Xubuntu with a different configuration (using LiveCD). I have been running xubuntu with no problem at all.

---

### Post by FionnMc on 2009-12-12
To be honest if I was going to go the re-install route I'd probably take the opportunity to go for a different distro.

I suspect my issue is probably something to do with my graphics card (ATI Radeon 9550) as the main symptom is loss of display.
It's somewhat frustrating to not be able to debug it any further.

---

### Post by Themotorman on 2009-12-13
> **FionnMc said:**
> Hi,
First post here :)

My issue is that my screen will randomly die i.e. it will stop displaying whatever was being displayed at that point and go into standby as though it is receiving no signal from the PC. 

Tapping the keyboard or mouse will not "re-awaken" the display. I can still hear the PC whirring away and if any media is playing when these crashes happen then I can still hear it playing through the speakers.

I cannot ssh into the PC when these crashes occurs as any connection attempt just times out.

The only way to regain control of the PC is to switch it off by holding and pressing the hardware power button. Of course this means that any unsaved work is lost :(.

I'm running Xubuntu 9.10 Karmic Koala. This issue originally started to occur when I moved to Xubuntu 9.04. It occurred a lot more frequently in 9.04 i.e. at least twice every three days. It's occurring less frequently in 9.10 i.e. maybe twice a week.

I'm at a loss as to how to go about debugging this problem as it seems so random.
Where can I search for clues as to how to solve this issue?
I have new but similar ?? problem , installed Xbunutu on older dell5000, it ran Ok but after updates i have no mouse. Help please

---

### Post by Themotorman on 2009-12-15
> **Themotorman said:**
> I have new but similar ?? problem , installed Xbunutu on older dell5000, it ran Ok but after updates i have no mouse. Help please

Tried a complete re-install and n ow the mouse doesn't work. If I go into the BIOS and change the auto enable for the external mouse to disable then sometimes the built in mouse works. I cannot get an external mouse to work at all.
This is very frustating as it is my friends computer and i told her that Ubuntu was fantastic and she should get rid of win2000.. Now we have nothing!!
HELP PLEASE>>

---

### Post by eacp001 on 2009-12-30
The problem also occurs in Ubuntu 9.10, it has to be something in the background, no in the desktop. Any help please!

---

### Post by FionnMc on 2010-01-02
Well the problem seems to have disappeared for me after doing a re-install.

I decided to go ahead an do a fresh install of Xubuntu.
I downloaded the iso again and burned it to a fresh cd.

I re-installed the OS. This time I didn't accept the "recommended updates" and only applied the security updates.
To prevent nagging by the update manager I've only set the update reminders to notify me of security updates as follows.
Applications->System->Update Manager->Settings->Update Tab->Ubuntu updates

Check **Important Security Updates**
Uncheck the other options under "Ubuntu updates" as per screenshot below.

[IMG]http://i48.tinypic.com/2yvtdmp.png[/IMG]

Since then I haven't had a single random crash where the screen dies or the mouse and keyboard become unresponsive.

I also used to use the Deluge bittorrent client and wondered if it may have been part of the problem.
I now use rtorrent instead. It's probably unrelated but thought it best to mention it in case it helps someone.

---

