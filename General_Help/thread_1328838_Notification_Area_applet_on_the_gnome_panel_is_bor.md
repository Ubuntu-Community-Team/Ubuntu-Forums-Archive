---
title: "Notification Area applet on the gnome panel is borked!"
date: 2009-11-16
forum: General Help
---

### Post by bshosey on 2009-11-16
I have tried several things. This happens with Karmic i386 & amd64 out of the 4 laptops I have set up. I installed 3 amd64 and 1 i386. All of them almost every time they are booted up and fist loged in. The Notification Area on the gnome panel has to be closed and add by right clicking on the panel and "Add To Panel" then choos Notification Area. This is not the baboon notification this is gnome panel. Why I have to do this is either I get 2 bluetooth icons and no Network Manager Icon or 2 battery icons and no Network Manager Icon. Or a Black Box instead of Network Manager.

I have reinstalled clean install with all the updated and even prereleased updates.

I am getting frustrated please help.

---

### Post by Dark_Stang on 2009-11-16
I had this issue happen on one boot a few weeks ago. Thought it was just a one time glitch.

---

### Post by Velophile on 2009-11-17
I've got the same issue, never boots up with the notification icons working properly.  Usually missing one or two icons and with one duplicated.

Any ideas?

---

### Post by Donalb on 2009-11-18
I am getting Icon problems all over the places since Karmic install. Network Manager icon NEVER displays properly but this time it's gone along with Sound icon.. Right now my Tracker , LCD and a currency shortcut are just grey boxes. Next time I restart it'll be something else. Pain in the **** but I have so many other problems.....

---

### Post by ucal on 2009-11-18
I have this problem as well.  It seems the sound icon is a big bully and likes to push my network icon away >_>.  Which is problematic because ubuntu gets randomly disconnected from my networks all the time.

---

### Post by scouser73 on 2009-11-18
Do you lock your panel icons into place?

---

### Post by akakingess on 2009-11-18
I know this is probably know assistance at all, but I have yet to see the issue at all on a desktop running Karmic x64. Network, volume control, etc. all show up everytime, with no duplicates or anything. I am dual-booting, but wouldn't think that has anything to do with this matter. Let me know it you want to know the specs on my machine to help troubleshoot or anything.

---

### Post by bshosey on 2009-11-18
yes I lock my icons. I uninstaled indicator-applet and indicator-applet-session. This fixed it on 3 computers but not the forth one. when the icons are messed up it is alway network manager icon missing and another icon is duplicated. I am getting really frustrated over this. it seams every time I think I got it. The next reboot does the same thing. It is sad I have never been this frustrated with this kind of stuff. What is really strange is two systems are identicle. Dell Latitude D630 same specs same applications installed. One work the other does not.

I will say this after remove the indicator applets the systems appear to be faster on the GUI side. Also Empathy has not crashed once.

---

### Post by bshosey on 2009-11-19
Ok. I think I may have fixed the notification area. What I did was went to synaptic and marked the already installed ubuntu one stuff for reinstallation. And so far it fixed it on all.

---

### Post by bshosey on 2009-11-20
I guess I did not get it fixed fired up the computer no nework manager. The only difference with this system it is hooked up to an external monitor.

---

### Post by Donalb on 2009-11-21
I generally us an external VGA display connected to a laptop.
After having a screwed up Network Manager icon since install I was working on yet another Karmic problem (external) the other day and this got fixed.
Cycling through the keyboard (Fn+F8) option (5 cycles to get back to where I was) and back on seemed to fix it temporarily. (Until I had a reboot when it went back to screwed, along with other icons).
Cycling the displays seems to work as a temporary fix each time though...

---

### Post by bshosey on 2009-11-21
Well I think there is a problem with ubuntu one and network manager together and Network Manager and multi monitors. I really think there should be more testing on this. Bugs like this can't continue into 10.4. GUI bugs will turn people away. The reason I say that is with GUI bugs you will notice and get the most frustrated with. A GUI is for simplicity of use when you have bugs like this simplicity turns in to annoyance.

Don't get the wrong idea here. I am not insulting ubuntu or OSS. I am here to stay. I love ubuntu and OSS. To me it is more than just software it is a philosophy.

---

### Post by Velophile on 2009-12-02
I finally sorted mine out.  It turned out to be the icon to the right of the notification area, I had mine set up as:

NotificationArea PulseVolControlLauncher Clock IndicatorAppletSession

When I moved the PulseVolControlLauncher away to another part of the panel my notification area started behaving itself.  No issues since, hope it helps.

---

### Post by bshosey on 2009-12-03
Velophile, I was wondering what do you mean by PulseVolControlLauncher? Is that the padevchooser?

---

### Post by Velophile on 2009-12-04
Hi, it's just the icon for the PulseAudio Volume Control applet, I'm not sure if the type of application is relevant to be honest, more that there's an icon between the notification area and the clock.

---

### Post by bshosey on 2009-12-04
> **Velophile said:**
> Hi, it's just the icon for the PulseAudio Volume Control applet, I'm not sure if the type of application is relevant to be honest, more that there's an icon between the notification area and the clock.
O OK. I see what you are saying. I have my Clock right up against the System menu to the top left of the screen. The only thing on the right side of the top screen is Notification-Area-Applet. Well that was not entirely true. I did have a Quick launch icon for Totem in the upper right corner. I removed that. Lets see if that resolves it. I will let you know. Thanks for the input.

---

### Post by Velophile on 2009-12-05
Just for clarity's sake here are a couple of screen shots, I don't think the fact that the icon is for PulseAudio really matters, I think any icon would have the same effect.

In the screen shots the not-working image doesn't display the notification area in it's faulty state, it's just there to show you the position of the icon.

---

### Post by bshosey on 2009-12-05
I only have the notification applet on the upperleft corner of the gnome panel and I still get this at times. Every second or third reboot I will get a duplicate icon with no network manager or a blank space where the network manager should be. The only system that I don't have nitrification area problems are the one that I don't have network manager installed on. So it has to be Network Manager that has the problem.

---

### Post by Velophile on 2009-12-07
The only other thing I can think's effecting it is the applications set to start up at logon.  I've moved some of them into a script that's got a delay in starting:

```

#!/bin/bash

sleep 10
conky -d
/usr/bin/empathy &
/usr/bin/mail-notification --sm-disable &
guake &

```

Not sure if any of these effect the notification area but I have noticed that conky seems to effect drawing (at least with my conky config) if it's not delayed at start up.

---

### Post by Popaul on 2009-12-21
Does that help?
Icons in notification area are linked to the applications / applets starting up automatically at boot.
Go to System / Preferences / Start-Up Applications : there're plenty of little things that can be ticked on or off to load at start-up. If the Volume Control or Network Maanger pr ... is not ticked on, it will of course no show up in the notification area. Tick it on, and it should appear.
And.. check that in the 'option' tab the box is checked also for "automatically remember running applications ..." so that the settings are fixed for the next boots.

---

### Post by RodGer GR on 2009-12-21
There is an open bug for this problem. Maybe you would like to go to [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448) and click the "this bug affects me too" option or even provide any missing information concerning this problem.

---

### Post by ardensdrunk on 2010-03-14
back from the semi dead


just so you guys know ... i right clicked and went to the panel properties ...

checked the "expand" option and everything expanded and now all my icons are good to go ... no more phantom icons

problem might be related to having too many icons and the notification area not automatically expanding?

---

