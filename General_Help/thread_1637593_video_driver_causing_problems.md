---
title: "video driver causing problems?"
date: 2010-12-04
forum: General Help
---

### Post by daweefolk on 2010-12-04
I'm actually running slackware but I've had good experiences here so I'm asking here for help. 
When I ran ubuntu I could play games such as supertux, tuxracer, and nexuiz easily. My computer took a crap and on the new laptop I installed slackware. Now my cpu tops at near 100 percent when I'm even playing some online flash games. 
I ran an lspci -v and found out my video driver is intelfb. 
my kernel is 2.6.27.7
Would there be any updates or patches available to help with the cpu problem? Do you think it's because of the video driver, or would a kernel update possibly help?

---

### Post by lovinglinux on 2010-12-05
See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by daweefolk on 2010-12-05
it's not flash that i'm really worried about, i'm just wondering whether my video driver or kernel version is causing the 100% peaks in cpu all the time. it happens with almost every game i have on my computer, including the default kde ones.

---

### Post by lovinglinux on 2010-12-05
> **daweefolk said:**
> it's not flash that i'm really worried about, i'm just wondering whether my video driver or kernel version is causing the 100% peaks in cpu all the time. it happens with almost every game i have on my computer, including the default kde ones.

If it happens with other applications, not only flash, then is probably the video driver.

---

### Post by daweefolk on 2010-12-05
> **lovinglinux said:**
> If it happens with other applications, not only flash, then is probably the video driver.
General question: is there a place i can find an update or patch? not specifically mine, but is that normally possible?

---

### Post by lovinglinux on 2010-12-05
> **daweefolk said:**
> General question: is there a place i can find an update or patch? not specifically mine, but is that normally possible?

Update or patch for what? You can get from the repositories or using a [ppa from Launchpad]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories"). You will need to find a [ppa]("https://launchpad.net/ubuntu") for the application you want to upgrade. Keep in mind I don't recommend installing random ppa repositories. Try to find threads in the forum that suggests a ppa for your particular issue.

---

### Post by daweefolk on 2010-12-05
> **lovinglinux said:**
> Update or patch for what? You can get from the repositories or using a [ppa from Launchpad]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories"). You will need to find a [ppa]("https://launchpad.net/ubuntu") for the application you want to upgrade. Keep in mind I don't recommend installing random ppa repositories. Try to find threads in the forum that suggests a ppa for your particular issue.

an update/patch for my video driver. if that's the problem, wouldn't there be a way to fix it?

---

### Post by lovinglinux on 2010-12-05
> **daweefolk said:**
> an update/patch for my video driver. if that's the problem, wouldn't there be a way to fix it?

I use a ppa for nvidia driver, but I don't know anything about yours. Sometimes the driver isn't supported, but I don't know if that is the case. Try looking [here]("http://www.google.com/search?q=intelfb+site%3Aubuntuforums.org&hl=en").

---

