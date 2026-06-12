---
title: "Log-outs??"
date: 2010-02-15
forum: General Help
---

### Post by style23 on 2010-02-15
Can anyone tell me what message means, I receive it after I get unexpectedly logged out.
Feb 15 13:22:27 lee-desktop pulseaudio[4246]: pid.c: Stale PID file, overwriting.
Feb 15 13:22:28 lee-desktop pulseaudio[4246]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Feb 15 13:22:28 lee-desktop pulseaudio[4246]: alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Feb 15 13:22:28 lee-desktop pulseaudio[4246]: alsa-sink.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Feb 15 13:22:28 lee-desktop pulseaudio[4246]: alsa-source.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.

My Graphics card is a 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) and i'm not using comiz? Distibution Ubuntu 9.10

Can anyone tell me why the unexpected log-outs.

---

### Post by bodhi.zazen on 2010-02-15
My guess would be that those messages are not related to your problem, they are related to sound, but I do not know for sure.

You can try a google search :

[http://www.google.com/search?q=alsa-sink.c%3A+Disabling+timer-based+scheduling+because+high-resolution+timers+are+not+available+from+the+kernel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=alsa-sink.c%3A+Disabling+timer-based+scheduling+because+high-resolution+timers+are+not+available+from+the+kernel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

I saw bug reports, but no solution, but then again I did not read through all the links either.

---

### Post by style23 on 2010-02-15
> **bodhi.zazen said:**
> My guess would be that those messages are not related to your problem, they are related to sound, but I do not know for sure.

You can try a google search :

[http://www.google.com/search?q=alsa-sink.c%3A+Disabling+timer-based+scheduling+because+high-resolution+timers+are+not+available+from+the+kernel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=alsa-sink.c%3A+Disabling+timer-based+scheduling+because+high-resolution+timers+are+not+available+from+the+kernel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

I saw bug reports, but no solution, but then again I did not read through all the links either.

Would the log show what is related to the problem?

---

### Post by bodhi.zazen on 2010-02-15
> **style23 said:**
> Would the log show what is related to the problem?

Depends on the problem, some problems will log an error, others will not.

Perhaps if you described your problem in more detail. What are you doing when it happens ?

---

### Post by style23 on 2010-02-15
> **bodhi.zazen said:**
> Depends on the problem, some problems will log an error, others will not.

Perhaps if you described your problem in more detail. What are you doing when it happens ?

Well it seems like when i'm using fireFox its happening. Having multiple tabs open and then i'll click a link in one of the tabs and then it will just log me out and send me to the login screen. Once I log back in i'll click Firefox and goto a site and then click a tab and open up google, put something in the search and then click search and it will log me out. But that doesn't happen every time. Its like I can't just make it happen. I'm using the chrome web browser right now and everything seems to be working good, and I have multiple tabs open. Since I did a fresh install(last week) I don't think it happen to me without having  firefox open.
I'm going to try and make it happen in the chrome web browser and i'll report back

---

### Post by style23 on 2010-02-15
> **style23 said:**
> Well it seems like when i'm using fireFox its happening. Having multiple tabs open and then i'll click a link in one of the tabs and then it will just log me out and send me to the login screen. Once I log back in i'll click Firefox and goto a site and then click a tab and open up google, put something in the search and then click search and it will log me out. But that doesn't happen every time. Its like I can't just make it happen. I'm using the chrome web browser right now and everything seems to be working good, and I have multiple tabs open. Since I did a fresh install(last week) I don't think it happen to me without having  firefox open.
I'm going to try and make it happen in the chrome web browser and i'll report back

Well I get logged out and I was in chrome maybe its a browser issue. I had two chrome browsers open, and multiple tabs open in both browser. I just finished playing a video in one browser went to click another link the computer wasn't doing anything and then it logged me out. I don't know what it could be, but it seems to only happen while i'm in a browser.

---

### Post by bodhi.zazen on 2010-02-15
Try running your browser from the command line and watch for errors.

---

### Post by style23 on 2010-02-15
> **bodhi.zazen said:**
> Try running your browser from the command line and watch for errors.

Thanks for your help. But my hardware is pretty old and I decided to fall back on the previous LTS. Things weren't running that smooth anyway. In 9.04 I wasn't having that issue but I wasn't able to run compiz in the newer releases but in Hardy Heron things work like a charm. So thank you again. When I get a new comp I will just install the next LTS.

---

### Post by JohnJackson on 2010-02-16
There is definitely a problem with log outs, I experience it on one of my Ubuntu machines, but not all. There are also many posts in the forum about this, such as:

[http://ubuntuforums.org/showthread.php?t=1338378](http://ubuntuforums.org/showthread.php?t=1338378)
[http://ubuntuforums.org/showthread.php?t=1377071](http://ubuntuforums.org/showthread.php?t=1377071)
[http://ubuntuforums.org/showthread.php?t=1390922](http://ubuntuforums.org/showthread.php?t=1390922)
[http://ubuntuforums.org/showthread.php?t=1371906](http://ubuntuforums.org/showthread.php?t=1371906)
[http://ubuntuforums.org/showthread.php?t=1339264](http://ubuntuforums.org/showthread.php?t=1339264)
[http://ubuntuforums.org/showthread.php?t=1334360](http://ubuntuforums.org/showthread.php?t=1334360)

I shall try to look for any relevant bug reports. I was rather hopeful that a solution had been found when I saw this was marked with solved, perhaps it should be changed?

---

### Post by bodhi.zazen on 2010-02-16
> **JohnJackson said:**
> I shall try to look for any relevant bug reports. I was rather hopeful that a solution had been found when I saw this was marked with solved, perhaps it should be changed?

The "problem" ie logouts is a symptom and can be caused by many things, in general these are problems with the X server, so the solutions will be varied and likely hardware dependent (Nvidia, ATI, etc).

In terms as "solved" , the thread is solved to the OP satisfaction, so it is appropriately marked ("Solved" does not mean solved to your satisfaction or that the solution will work for all users, sorry).

---

### Post by JohnJackson on 2010-02-16
Ah, OK thanks for clearing up the "solved" tag. It just seems like downgrading isn't a particularly satisfactory solution, but I guess that is just my opinion.

One thing I have noticed is that each time it logs me out I have the "pid.c: Stale PID file, overwriting." error in the logs, which is related to pulseaudio. It might be this bug [https://bugs.launchpad.net/ubuntu/+bug/407488](https://bugs.launchpad.net/ubuntu/+bug/407488) but I am not sure.

---

### Post by style23 on 2010-02-16
> **JohnJackson said:**
> Ah, OK thanks for clearing up the "solved" tag. It just seems like downgrading isn't a particularly satisfactory solution, but I guess that is just my opinion.

One thing I have noticed is that each time it logs me out I have the "pid.c: Stale PID file, overwriting." error in the logs, which is related to pulseaudio. It might be this bug [https://bugs.launchpad.net/ubuntu/+bug/407488](https://bugs.launchpad.net/ubuntu/+bug/407488) but I am not sure.

I unmarked it solved you were right about it being solved, and wouldn't want to mislead anyone. Like someone told me if a previous version worked before just go back to it. But my computer is old and I was trying to upgrade each time a new version was available. Still the computer didn't run smooth once I started getting into the later versions. Especially my video; for some reason when I tried to stream a video from [www.gametrailers.com](www.gametrailers.com) and click in the bonus round section my CPU would be at 100% and the video would barely play. In 8.04 its better(not the best) but everything else just runs so much smoother. I don't know how old your machine is but in my case an older distro just took a load off of my CPU. Also I don't really know of a major disadvantage if you were to use an earlier distro especially if its still in its LTS life span. Do you have a new machine and this keeps happening to you?

---

### Post by JohnJackson on 2010-02-17
> **style23 said:**
> I unmarked it solved you were right about it being solved, and wouldn't want to mislead anyone. Like someone told me if a previous version worked before just go back to it. But my computer is old and I was trying to upgrade each time a new version was available. Still the computer didn't run smooth once I started getting into the later versions. Especially my video; for some reason when I tried to stream a video from [www.gametrailers.com](www.gametrailers.com) and click in the bonus round section my CPU would be at 100% and the video would barely play. In 8.04 its better(not the best) but everything else just runs so much smoother. I don't know how old your machine is but in my case an older distro just took a load off of my CPU. Also I don't really know of a major disadvantage if you were to use an earlier distro especially if its still in its LTS life span. Do you have a new machine and this keeps happening to you?

It's reasonably old now I guess, single core Athlon (possibly Athlon 64 3000+), it also has some nVidia card, although I can't check right now as it's at work. I have also installed karmic on a couple of old laptops (6 years+ old) and do not experience this problem, although with intel graphics. 

However, I don't think this problem is simply because the machines are old, there is usually a reason. If downgrading works for you and you are satisfied though that's fine. I just don't like giving up ;)

You should know that flash even on a fast computer on Linux will use up a lot of CPU. Flash simply does not run very well on Linux, unfortunately.

---

### Post by style23 on 2010-02-17
> **JohnJackson said:**
> It's reasonably old now I guess, single core Athlon (possibly Athlon 64 3000+), it also has some nVidia card, although I can't check right now as it's at work. I have also installed karmic on a couple of old laptops (6 years+ old) and do not experience this problem, although with intel graphics. 

However, I don't think this problem is simply because the machines are old, there is usually a reason. If downgrading works for you and you are satisfied though that's fine. I just don't like giving up ;)

You should know that flash even on a fast computer on Linux will use up a lot of CPU. Flash simply does not run very well on Linux, unfortunately.

You know I just upgraded back to Karmic Kola because I couldn't bare the denial of not trying to figure this one out as well. Post back if you get any updates. Since I did a fresh install as of right now after all the updates everything seems to be working fine, but will see. I'm not giving up either ;)

---

### Post by style23 on 2010-02-21
> **style23 said:**
> You know I just upgraded back to Karmic Kola because I couldn't bare the denial of not trying to figure this one out as well. Post back if you get any updates. Since I did a fresh install as of right now after all the updates everything seems to be working fine, but will see. I'm not giving up either ;)

Well this seemed to work for me. Things are moving alot quicker, its just overall better now. Still Compiz doesn't work at all in 9.10 but it did in 8.04. I found this in launchpad Bug error # 502055. Here's the website to the solution
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")
John I don't know if this will help you since your using Nvidia, but i'm pretty sure there is a workaround and i'll continue to look for you. Let me know even if your still having this issue. But for others with integrated intel this should work.

---

