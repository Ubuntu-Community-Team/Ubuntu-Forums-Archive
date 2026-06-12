---
title: "visual effects lost on reboot"
date: 2009-09-01
forum: General Help
---

### Post by Big Gaz on 2009-09-01
Hi all,

I have just started using Ubuntu and I have encountered a problem with 9.04 and the visual effects. When I reboot my machine i loss the effects and have to reselect them.

More importantly I also loss the title bar for any open windows.

Reselecting either normal or extra, returns my title bars

What am i doing wrong and how can I reset the visual effects to normal and have it retained on reboot

Thx

Garry

---

### Post by earthpigg on 2009-09-01
on a fresh boot with no effects, press alt+f2 and type this:
> compiz --replace
does that bring back your effects?

to undo it:
> metacity --replace

to make "compiz --replace" run at startup:

system -> preferences -> startup applications -> add

use 'compiz --replace' for the command, and name/describe it however you like.

the part about compiz/metacity --replace is also handy because compiz does not play nice with certain games and applications. when that happens, you can simply use metacity while the game/app is running, and put compiz back in the driver's seat afterwards.

---

### Post by Big Gaz on 2009-09-01
Thx Earthpigg,

I didn't need to do the above as for whatever reason, and i have no idea the problem has gone away.

I had a small problem with my desktop icons (trash etc) going away and a program link i had added to the task bar also.

These seem to have cured themselves as well

Coming from a windows background all these random artifacts are hard to handle

---

### Post by Big Gaz on 2009-09-03
I take everything back.

Today I have just booted up and I have lost resolution.... i'm now running at low resolution.

Is there away of resetting Ubuntu 9.04 to the default screen settings as per the first install?

Also getting a message about a file called $home/.dmrc not owned by me and should have 644 permissions?

---

### Post by Big Gaz on 2009-09-03
white flag....

i'm not having much fun with linux and all this trouble i'm having is not making me much of a convert.

I'm by far not stupid and I just wonder how the average linux user gets on.

I have never has a graphic issue on any version of windows from way back or any problem on my mac.

This is the third and final time I try and move over to linux.... it's just not user friendly!

Great when it's working, but doesn't stay that way for long!

So far I have: -

an error message on boot up about permissions.

a screen resolution of about 640x400

my serial ports can be seen but will not open, permissions issues again

All I have done is install Ubuntu 9.04 from fresh and add some software, nothing complicated

---

### Post by Roasted on 2009-09-03
To each his own. I use Mac, XP, Vista, and Linux, and I find Linux to be the most practically set up and logical in terms of functionality. I've ran into more issues with Windows than I ever have in Linux, and believe me I've had my fair share of Linux issues too.

Nonetheless, did you try reinstalling your graphics card driver? Did it come up under restricted drivers under the hardware manager in system - admin - hardware drivers?

---

### Post by Big Gaz on 2009-09-03
I have reloaded the nvida drivers and I still have the same problem. On boot up the screen tells me it can't see my screen. But it used to. So what has changed?

---

### Post by Big Gaz on 2009-09-04
Sorted, well almost.

My installation has been running fine and then it started to act up, first with compiz and the then linux not seeing my monitor.

The problem appears to be the KVM switch I have between the linux and windows machines i have.

Just as a last resort i plugged the monitor into the PC direct and up came the GUI at full res.

Now all I have to do is sort out the KVM!

I thought all KVM switches where OS independent?

I will post a new tread on this subject.

Sorry for throwing my dummy out the pram!

---

### Post by Roasted on 2009-09-04
Glad to hear you got a lead on the issue man!

---

### Post by Big Gaz on 2009-09-04
Thx,

just need to get my head around the KVM and how I can stop Linux trying to read monitor type through the KVM and lock the monitor settings.

---

