---
title: "Oddities after today's automatic update..."
date: 2009-07-29
forum: General Help
---

### Post by norfair on 2009-07-29
After firing up my computer today I found updates ready for me to download and install. I did so, restarted as instructed, but when my system rebooted I was given a message stating that, "HAL failed to initialize." I have no idea what that means. I've checked around here and via Google in general, and it seems HAL involves a number of Ubuntu aspects.

My issues specifically are that my USB devices don't seem to work - as my printer is no longer recognized, and there is "no network connection." Well, the latter is not the case, as I am online. My cable modem is fed to my router which is fed directly to my computer. I also have no trouble connecting via wifi with my DS. So, nothing seems to be wrong with my network. Yet, when I opened Firefox, it loads the "working offline" page. I have to manually uncheck the "work offline" mode. 

I have no idea what's going on. I thought about restarting my computer or doing a full shutdown, but now I'm afraid I'll lose connection for real. Does anyone know what happened to my system? I know it was a result of today's update, as it was working fine before the update, and I have the system set to check for updates daily, and I download any available update daily. 

I would appreciate any and all feedback on this matter. My apologies in advance if I've posted this in the wrong section or if this question of sorts has been exhaustively answered in the past (I couldn't find anything specifically pertaining to my issue). 

Thanks.

---

### Post by UltraZone on 2009-07-29
You're not alone, after today's update my Ubuntu is all kinds of *screwed* [ ;) ] up, not least of which is all my X11 compiz settings.  I hope that Canonical releases an update to correct today's problem, and enforce a slightly better quality control procedure.

---

### Post by norfair on 2009-07-29
> **UltraZone said:**
> You're not alone, after today's update my Ubuntu is all kinds of fuked up, not least of which is all my X11 compiz settings.  I hope that Canonical releases an update to correct today's problem, and enforce a slightly better quality control procedure.

While I'm certainly not happy to hear that you're having issues after today's update, I am happy to hear that I'm not alone. I'm with you in hoping an update to the seemingly botched update is released tomorrow. Thanks for the reply.:D

---

### Post by ericab on 2009-07-29
same here

---

### Post by philcamlin on 2009-07-29
> **UltraZone said:**
> You're not alone, after today's update my Ubuntu is all kinds of fuked up, not least of which is all my X11 compiz settings.  I hope that Canonical releases an update to correct today's problem, and enforce a slightly better quality control procedure.

id edit your post beore you get in trouble :D

**remove the swears**

anyways thats a bumer seeing you have issues with your system 

hope they fix it soon :popcorn:

---

### Post by norfair on 2009-07-29
I don't know if it was logical to do or not, but I just filed a bug report via LaunchPad. There were a bunch of other HAL initialization error bug reports, but none matched what I am experiencing. Hopefully mine was unique enough to warrant a new report. I guess we just have to play the waiting game now to see if/when an update is issued. I know I may not be shutting down my computer tonight... Just in case!

---

### Post by QIII on 2009-07-30
> **UltraZone said:**
>  I hope that Canonical releases an update to correct today's problem, and enforce a slightly better quality control procedure.

There may be people who encountered problems.

The only one I encountered was that the resolution on my splash screen was not what I wanted it to be, so I removed "vga=xxxxx" from the new boot line.

It is easy to think that because you see a few others here having problems that the problem is universal.

Remember.  People do not come to complain on forums when things go right.

Filing a bug report as norfair did is a much more constructive action than using a forum to belittle those who work hard on this project. ...

---

### Post by UltraZone on 2009-07-30
Point well taken.

Earlier I may *or may not* have been under the influence of ethanol, so please take my comments with a pinch of salt.

So far it seems that the only things broken on my end are the NVIDIA drivers, strangely enough including the PowerMizer fix shell, & downstream apps et al.  I will report any fix I may figure out tomorrow.

Cheers. :popcorn:

---

### Post by slymi2005 on 2009-07-30
I can't get firefox or firefox 3.5 to start, it shows up in system monitor as running but I guess it is just running in the background because I don't see it. I'm using Songbird for now but I hope that my issue has something to do with today's update. Anyone else having firefox issues?

Update: It works in safe mode

---

### Post by norfair on 2009-07-30
> **slymi2005 said:**
> I can't get firefox or firefox 3.5 to start, it shows up in system monitor as running but I guess it is just running in the background because I don't see it. I'm using Songbird for now but I hope that my issue has something to do with today's update. Anyone else having firefox issues?

Update: It works in safe mode

Other than Firefox opening in offline mode (but works just fine once I uncheck "work offline"), I have no issues with it. Opera works just fine all around, though. That truly is puzzling why you can't even get it running outside of safe mode. Hopefully it will be a simple fix. Only time will tell, I suppose. Good luck.

---

