---
title: "Hard Lock up"
date: 2009-12-19
forum: General Help
---

### Post by Tzadok on 2009-12-19
Hey all,

I am a Linux user with some experience, and am having problems with KK Hard Locking on my computer.

I have had this problem for a long time, possibly since before I updated to KK, I don't quite recall. However I had been running some patched wireless drivers for wep and wpa cracking (for personal education and only with permission), and I was running a special Graphics card driver, so I simply figured it was something I had stupidly inserted in the system and resolved to blow it away once I hit break.

I did. Within 15 mins of the first bootup of the fresh install...I hit the same old hard lock.

I have tried the sysrq key to no avail. I checked the md5 of the iso before burning and checked the disc for errors after burning and before install.

My Specs are found [here.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220526")

Any other things you want/need just holler. Been pulling my hair out on this one.

---

### Post by hansdown on 2009-12-19
Hi Tzadok.

This part from the hardware specs may be the problem.

    Cons: not so good its only 32-bit, since ive first had it the video driver has crashed on every game i try even downloading an update driver fails. i believe there is a hardware connection issue.
    Other Thoughts: im not sure if others have had the same problem but if its not do due to improper connection between the video card then asus needs to fix this issue.

---

### Post by Tzadok on 2009-12-20
I had thought that that might be the issue, however the symptomology was slightly different in that I could not force the problem to occur. It simply sometimes would lock up and sometimes not. Also some other things pointed to it not being a hardware issue alone, namely that I used several Live CD's for an extended period of time with no lock ups, even with the highest resolution and such.

Also would this be a driver issue that might be corrected by asus at some point, or would this be a hardware issue that is unresolvable because of the computer I have?

Many Thanks for your response.

---

### Post by hansdown on 2009-12-20
Are you using nvidia 190.53 driver?

[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

---

### Post by Tzadok on 2009-12-20
I had just done a fresh install, and have not installed any video driver. 

I will install that one and check however.

Thanks again for your help.

---

### Post by hansdown on 2009-12-20
If you click system> administratio> hardware drivers, it should search, and find the best driver for you.

---

### Post by Tzadok on 2009-12-20
Hey I installed the driver from Ubuntu's repos and it is 185.

It has not locked up yet, but this is at less than 5mins from startup following the necessary restart.

Also, I would be willing to try installing the latest Nvidia driver, but was wondering if there was a nice way of doing it. The method that I found via google seemed rather inelegant, as I would need to do things every time some of the things were updated via ubuntu.

---

### Post by hansdown on 2009-12-20
The 185 driver is stable.

Try it for now, and see if there is improvement.

---

### Post by Tzadok on 2009-12-20
It locked up within minutes of my last post.

However I found a post on the ubuntu forums somewhere about someone who had lockups due to the same wireless card this thing has. It recommended installing some backport drivers for jaunty(thats when the error was) and installing wicd which apparently worked for two people with that same hardware.

So I tryed it, using the karmic version of the backport, but....for some reason wicd is not in the repos. But at any rate I am trying this and it has not locked up as of yet.

---

### Post by Tzadok on 2009-12-20
Well that was a no go as well :( just locked up and now I am back on w$.

---

### Post by hansdown on 2009-12-21
I'll keep looking.

I'm still guessing the graphics is to blame, given the fixes applied to the latest driver.

[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

---

