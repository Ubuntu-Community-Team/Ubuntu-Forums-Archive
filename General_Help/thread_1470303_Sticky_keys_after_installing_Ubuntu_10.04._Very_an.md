---
title: "Sticky keys after installing Ubuntu 10.04. Very annoying."
date: 2010-05-02
forum: General Help
---

### Post by Redsandro on 2010-05-02
After running 9.10 for half a year, I did a fresh installation of Ubuntu 10.04. It removed **all my files** because I had my drives mounted somewhere in /var, even though the installer said it would only remove conflicting system files.

As usual, I did install ~4GB of packages afterwards.

Now I have at random times, annoyingly often, that the system pretends CTRL, ALT or SHIFT is continuously pressed. Making it impossible to do all sorts of things.

This is so random, I don't know where to begin looking for the problem.

---

### Post by Sparx139 on 2010-05-13
I have the same problem. I had something similar that happened with my gnome session back on hardy (window controls didn't load so I couldn't close anything/move windows around), which fixed itself when I typed "compiz" in the terminal. Perhaps the same approach would work here - to anyone reading who's more *nix-savvy then me, how would one go about reloading the keyboard driver?

I know it's a bit of a gaffer-tape solution, but it if it works it at least saves logging out.

---

### Post by Redsandro on 2010-05-13
Out of curiosity, are you running Synergy+ too?

Sometimes I get the feeling that Synergy+ is joking around, even if you use the computer native keyboard.

Note: I'm not running Compiz or other desktop compositing.

---

### Post by Sparx139 on 2010-05-14
I'm just running a standard Lucid desktop install from a blank hard drive. No added features other than restricted plugins such as flash/LAME etc.

The compiz thing was just to try and explain my suggestion - that reloading the keyboard might act as a hack solution to the problem

---

### Post by digory on 2010-05-28
I am also experiencing sticky keys with Ctrl and Alt (so far). I had no problems under Karmic, only after upgrading to Lucid.

The way I can tell they are sticking is that I can no longer type or use the mouse properly. I figured out which key is sticking by what actions I can do without having to hold that key down.

I was running a synergy process (no gui), but was using the local keyboard. I terminated synergy the last time my key got stuck, and it remained stuck. We will see if it continues to happen without synergy running.

I can unplug the USB keyboard and plugin a different one, and it has the same problem, but both times I have done so, I was able to get it un-stuck in a minute or two (I had tried several minutes with the first keyboard with no luck).

---

### Post by Redsandro on 2010-05-28
Exactly, I also swapped ps/2 keyboards and it had the same problem, proving that it is not the hardware.

Please let us know what you find out.

---

### Post by travisj on 2010-06-01
I get this same problem too (in fact, it just happened as I was trying to reply to this thread). It only began after upgrading to 10.04, and happens on both my desktop and laptop (with very different hardware configurations) at seemingly random intervals.

For me, usually it is the ctrl key, or caps lock key that gets "stuck", and it doesn't happen after pressing either of those keys.

I am only able to "unstick" the keys by some combination of Ctrl-Alt-SysReq-R and switching to tty1 and back.

---

### Post by lunatico on 2010-06-03
Uhm yes I just installed 10.04 on my desktop and same thing. We'll see how finds the solution first.

---

### Post by digory on 2010-06-04
Just happened again. I went a few days in between, during which I had killed the synergy process, but after some updates and a reboot, I forgot that synergy was running again... Does anyone else use synergy and have this sticky key problem?

As travisj suggested, I pressed Ctrl-Alt-SysReq-R and switched to TTY1 and back, and the problem was fixed. (This time, it was Ctrl that stuck.)

I then killed synergy and set it not to start on boot anymore.

Not sure if switching to TTY1 and back did the trick, or the key sequence, or both. Next time I will try it without the key sequence.

---

### Post by Redsandro on 2010-06-04
Still haven't found a fix to this annoying problem, but I noticed that randomly pressing the six buttons (left and right ctrl alt and shift) on the local keyboard for a few seconds (not holding but randomly pressing like typing with six fingers :P) sometimes fixes the problem. For a little while.

Also, if the sticky Ubuntu is the client and Windows 7 is the server, sometimes pressing ctrl+alt+del on the remote keyboard (Win7) also fixes it. Windows sometimes takes over the sticky keys. Only when connected to Ubuntu. Interesting.

---

### Post by lunatico on 2010-06-10
Hi Guys,

I might have found a fix for this. I've been running without the sticky keys for 2 days now.

Basically I was starting synergy by adding the following command to Startup Applications:
```
synergyc <synergy server hostname or ip>
```

But then I changed this and from the Startup Applications I'm calling a script, and the contents of the script are:
```
#!/bin/bash
sleep 2
/usr/bin/synergyc -f --name <hostname of client computer> <hostname or ip of server computer>
```

I hope this helps.

---

### Post by travisj on 2010-06-10
For the record, this problem occurs for me and I don't even have synergy installed, so that can't be the cause of the issue for everyone. The problem happens multiple times every single day.

More specifically, to "unstick" the keys, this works every time (Although is very annoying):

Ctrl-Alt-F1 to jump to tty1
Ctrl-Alt-F7 to jump back
Then press the key that is stuck (Ctrl or Shift)

This works every time, although sometimes a second key turns out to be stuck, requiring the procedure to be repeated a second time.

---

### Post by lunatico on 2010-06-11
> **travisj said:**
> For the record, this problem occurs for me and I don't even have synergy installed

Uhm... I wonder if we're looking at two different problems then....?

Stand-alone sticky and synergy-related sticky.

---

### Post by Titeuf on 2010-06-29
Did anyone find a solution for this?

I have the same issue: at totally random times, it's like the shift key is pressed down and it stays like that for some random time. Really annoying.

Also on 10.04 and i don't have Synergy installed.

---

### Post by lunatico on 2010-06-29
> **Titeuf said:**
> Did anyone find a solution for this?

I have the same issue: at totally random times, it's like the shift key is pressed down and it stays like that for some random time. Really annoying.

Also on 10.04 and i don't have Synergy installed.

Did you try what I posted in #11?

---

### Post by Titeuf on 2010-06-29
> **lunatico said:**
> Did you try what I posted in #11?

I didn't, because I don't have Synergy installed, so I doubt that causes the problem?

Thanks for answering though :)

---

### Post by lunatico on 2010-06-29
> **Titeuf said:**
> I didn't, because I don't have Synergy installed, so I doubt that causes the problem?

Thanks for answering though :)

Oh sorry didn't read your last line....

---

### Post by kryptokatalyst on 2010-07-05
> **lunatico said:**
> Hi Guys,

I might have found a fix for this. I've been running without the sticky keys for 2 days now.

Basically I was starting synergy by adding the following command to Startup Applications:
```
synergyc <synergy server hostname or ip>
```

But then I changed this and from the Startup Applications I'm calling a script, and the contents of the script are:
```
#!/bin/bash
sleep 2
/usr/bin/synergyc -f --name <hostname of client computer> <hostname or ip of server computer>
```

I hope this helps.

This still working?

Does this method start up Synergy Client before logging in?  So that a shared keyboard and mouse can be used for initial login?

Thanks!

---

### Post by lunatico on 2010-07-06
> **kryptokatalyst said:**
> This still working?

Does this method start up Synergy Client before logging in?  So that a shared keyboard and mouse can be used for initial login?

Thanks!

It does work for me and it fixes the sticky keys issues I was having.

This will not start synergy at your login screen, this scripts is to be run at 'Startup Applications'.

I used to have this configured for 9.10 (running synergy at login screen) but after I upgraded to 10.04 the same method stopped working and I haven't bothered to figure it out.

---

### Post by Redsandro on 2010-07-06
Meanwhile, NeatNX is probably the best half-descent alternative.

I have my 'server' in dualscreen mode with one screen running the NeatNX client. At local speed it's very workable, except for games or video.

---

### Post by digory on 2010-09-08
FWIW, I'm still having the sticky key problem. It only affects Ctrl or Alt for me recently. 

I am no longer running synergy, but it still happens -- probably once a week.

---

### Post by Redsandro on 2011-02-12
I was without Synergy+ for a while because it's unworkable, but I saw the new website so recently I tried the new **1.3.6** version of **Synergy+** and the **1.5.0 beta (r905)** version. After installation, the sticky key problem was back with a vengeance.

So maybe some people experience this without Synergy+. I don't. For me Synergy definitely increases the probability with [sigma]%.

I've created a ticket here:
[http://synergy-foss.org/pm/issues/2866](http://synergy-foss.org/pm/issues/2866)

So if you have the same problem, and it is really really important to you, consider signing up to the bugtracker and upvote the issue.

---

### Post by mr E on 2011-02-17
Same problem... Without Synergy + Ubuntu 10.04.2 LTS + using remote access to this (via remmina, VNC, etc) + KVM (share keyboard, video, mouse with other windows xp box).

Some sequence of numbers active the sticky keys for me.
Sometimes I can workaround this when I need to enter numeric data, for this, I need to enter twice the first number that I need to enter.
By example if i need to enter "6753" :
I need to enter "66753" to make it work. 
But if I enter "6753" I end with "753" and the sticky keys turned on (very annoying).

I wonder if this issue is related with the use of KVM (keyboard,video,mouse), this ubuntu box is using a cheap KVM(usb) to share keyboard + mouse + monitor. I don't have this issue in other ubuntu boxes but without KVM.

BTW, I remove ORCA + assistive technologies and all the related accessibility stuff, but the "sticky keys are back with a vengeance" (painfully funny words)

Regards

---

### Post by oODeanOo on 2011-03-17
Same here, Dell Studio 17 laptop.

Main culprits I've narrowed down to so far appear to be Skype with video calls and YouTube so no doubt Flash related for YouTube as Flash is known to be resource hungry and buggy and Skype with it's Beta status no doubt, so I believe this fits in with the medium CPU load.

I'm afraid things like this and the awful Synaptics Touchpad support in 10.04 and the resetting themes issue on 10.10 will mean that Ubuntu will never be taken seriously when the fix is to upgrade the whole system and hope something else doesn't break, which is a shame as generally I'm a big fan generally. 

Let's hope 11.04 fixes these issues but I've already read that Compiz Cube doesn't work with Unity.

---

### Post by Redsandro on 2011-03-17
I hope any fix will be backported into LTS at least because many people (including me) stick with LTS releases. The fact is: **Not even LTS releases are completely stable, but non-LTS are worse**.

My philosophy for production environment:
**Debian**: Annoyingly **stable**, possibly outdated but proven concepts.
**Ubuntu LTS**: Cutting edge, more or less **stable-ish**.
**Ubuntu non-LTS**: Bleeding edge, **non-stable**; too many quirks.

Anyway, the issue dates back from 2009 iirc, so **I think Synergy+ devs are not using Linux/Ubuntu and Ubuntu devs are not using Synergy+**, because I've heard that there is a 'bug' in Gnome that causes this, and neither the Synergy team works around it nor the Gnome team fixes it.

I cannot find back where I read that, but **I am curious if indeed _K_ubuntu users have no problems.**

Also, in the [bug report]("http://synergy-foss.org/pm/issues/2866") someone mentioned to try this on Ubuntu as a workaround:
*System -> Preferences -> Keyboard: Keyboard Delay = Long*

I can not try this out because I ditched Synergy+ for now and rearranged my workspace as this bug is no minor inconvenience but instead making the setup completely useless. So if someone still has the two systems lined up and willing to try it out, please let us know if it works! :)

---

### Post by tas97459 on 2011-03-17
:D I got GOOD results with

[http://www.howtoforge.com/linux_multimedia_keyboard](http://www.howtoforge.com/linux_multimedia_keyboard)

---

