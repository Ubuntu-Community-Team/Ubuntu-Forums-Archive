---
title: "Slow Resume From Suspend"
date: 2011-10-27
forum: General Help
---

### Post by dfarrell07 on 2011-10-27
Since upgrading to 11.10, my laptop is taking a very long time to resume from suspend (to RAM). I first thought that resume was broken, but one time I let it sit a bit longer, and noticed that it ended up working. Once it gives me a loggin prompt, everything is perfect, like no error happened at all. During the long pause, I can normally see my mouse on a black but backlit screen. After some portion of the pause, I can even move my mouse around freely, no lag or apparent heavy work.

It seems to me like resume is missing some signal, and then just does nothing until the signal or process is re-broadcast or re-run. 

I am running 11.10 with all the latest updates on a Lenovo W520. I can provide more hardware specs as needed. I should mention that I have a SSD, and made optimizations in 11.04 to better work with it. I added:

> block/sda/queue/scheduler = noop
to 
> /etc/sysfs.conf
and 
> tmpfs /tmp tmpfs nodev,nosuid,mode=1777 0 0
to 
> /etc/fstab

The source of those modifications is: [http://bit.ly/sWeDj7](http://bit.ly/sWeDj7)

The most closely related bug I can find is [http://bit.ly/t5vOao](http://bit.ly/t5vOao). It is a 10.10 bug, and was apparently fixed. However, the symptoms are very similar. I have not found any other threads or bug reports that detail the same issue. Thank you for any help you can provide!

---

### Post by xyzzyman on 2011-10-28
Is it also slow switching between text VT's and VT7?

[http://ubuntuforums.org/showthread.php?t=1867282](http://ubuntuforums.org/showthread.php?t=1867282)

It looks like you have an nVidia card also so I have a feeling these are all related as I have your issue and the stalling with VT1>VT7 switch.

---

### Post by dfarrell07 on 2011-10-28
> **xyzzyman said:**
> Is it also slow switching between text VT's and VT7?

Yes! It is **exactly** the same behavior. Ctrl+alt+f1 takes < 1sec. Ctrl+alt+f7 gives me a black, backlit screen. Initially my cursor is visible but will not move, then about halfway into the pause I can move it with no lag, then after a typical suspend-resume delay all is perfect again.

Good find! Starting to work towards a coherent picture of the bug.. :D

---

### Post by dfarrell07 on 2011-11-02
When resuming from suspend, if music or video was playing when the computer suspended, it resumes nearly right away. The audio starts playing in the amount of time my computer usually takes to resume, although like I described, only a black, backlit screen is shown (no loggin screen).

---

### Post by Craigus on 2011-11-03
I can confirm this behaviour on a Sony Viao with nvidia video.

If AC power is connected however, resume is normal and rapid. On battery power, the above occurs.

---

### Post by dfarrell07 on 2011-11-09
On [http://bit.ly/uCxK3t](http://bit.ly/uCxK3t), effenberg0x0 discusses a similar problem. I also noticed that the same user, effenberg0x0, and I share another glitch ([http://bit.ly/rxwunv](http://bit.ly/rxwunv)). That glitch involves mouse pointers freezing up. I fixed that issue by disabling the 'disable touchpad while typing' option. As not many users are affected by either of these bugs, and at least two are affected by both, it seems plausible that they are related.

Any ideas anyone? Any one else affected? Please, post something if you are.

---

### Post by dfarrell07 on 2011-11-09
> **Craigus said:**
> If AC power is connected however, resume is normal and rapid. On battery power, the above occurs.

The power source doesn't have any relationship to the glitch for me. I'll test more to make sure, but I'm quite confident of this. Thanks for posting to let us know what's up. If you like, subscribe to this thread. I want to get this fixed, lol.

---

### Post by dfarrell07 on 2011-11-09
> **Craigus said:**
> I can confirm this behaviour on a Sony Viao with nvidia video.

If AC power is connected however, resume is normal and rapid. On battery power, the above occurs.

Ohh, also, are you affected by the glitch effenberg0x0 describes? Spicifically, if you > Use CTRL+ALT+F1 to go to VT1 (F2 to VT2, etc) and CTRL+ALT+F7 to go back to X. do you see the same lag glitch?

---

### Post by che--- on 2011-11-10
Hi Folks,

there is already a bug report regarding the reported issue:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/828761]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/828761")

---

### Post by copester on 2011-11-23
I am seeing the exact same problem with my Thinkpad W520 using the nvidia driver for a Quadro 2000M. Using the intel driver this bug does not happen.

> **dfarrell07 said:**
> Yes! It is **exactly** the same behavior. Ctrl+alt+f1 takes < 1sec. Ctrl+alt+f7 gives me a black, backlit screen. Initially my cursor is visible but will not move, then about halfway into the pause I can move it with no lag, then after a typical suspend-resume delay all is perfect again.

Good find! Starting to work towards a coherent picture of the bug.. :D

---

### Post by andersgb1 on 2011-12-01
> **copester said:**
> I am seeing the exact same problem with my Thinkpad W520 using the nvidia driver for a Quadro 2000M. Using the intel driver this bug does not happen.

I have the exact same laptop configuration AND the same problem! No difference between AC plugged or not. In addition, I experience longer boot time and considerably longer login time...

---

### Post by efflandt on 2011-12-01
I have given up on suspend (and don't hibernate with 8 GB RAM and no swap).  Drive or drive settings should not matter much if any, since I think the system just flushes the write cache before putting CPU and RAM into a low power state.  But it can matter for boot.

I boot 64-bit 11.10 on my desktop PC from SSD.  Waking from suspend takes about a full minute to get a login screen.  Then Unity bar is colored snow until I hover over it.

If I do a cold boot, grub menu to login screen is 8 seconds and login to Unity is under 2 seconds.  I have no clue why waking from suspend takes so much longer, so I either idle with screen off or shutdown instead.  But I could see why you would want to suspend or hibernate a laptop to save batteries.

While I have not done other SSD optimizations yet since installing 11.10, I have proper partition alignment and do use **noatime** and **discard** options for mounting it and **tmpfs** for **/tmp** to avoid little writes to /tmp that are erased anyway next boot.  Although, a real /tmp or swap might be needed in certain cases for creating or modifying large iso files.

---

### Post by guakeke on 2011-12-23
Only a workaround, but I installed GDM as detailed here and the slow resume problem disappeared. 

[http://linux-software-news-tutorials.blogspot.com/2011/10/problems-with-lightdm-on-ubuntu-1110.html](http://linux-software-news-tutorials.blogspot.com/2011/10/problems-with-lightdm-on-ubuntu-1110.html)

---

### Post by birdsarah on 2012-01-11
Hi, I was having the exact same issue.

It is now gone after removing the nvidia drivers - as here: [http://ubuntuforums.org/showthread.php?p=11604370#post11604370](http://ubuntuforums.org/showthread.php?p=11604370#post11604370)

(Doing this has also enabled me to use dual monitors again effectively)

---

### Post by cbennett926 on 2012-04-02
Hey all, didn't know if there was a viable solution to this; I have the same configuration and problem!

---

### Post by mrhat1988 on 2012-07-06
Hi,


i also solved the slow resume-from-ram problem by using Gnomde Desktop Manager GDM instead of the new apparently unstable Light Desktop Manager LightDM.

Described here - very easy to switch no problems so far

---

