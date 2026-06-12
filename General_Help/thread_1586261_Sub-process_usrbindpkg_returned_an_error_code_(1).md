---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-10-01
forum: General Help
---

### Post by konsta82 on 2010-10-01
I just installed maverick and whatever I install,from terminal,software center or synaptic , I get messages like this :


E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Broadcom driver is in use and working so I have no idea what is this about ???

---

### Post by pamepros on 2010-10-16
I have the same problem, could someone figure it out?

It appears every time I install something throught the terminal with apt-get

Thanks

Pam

---

### Post by drs305 on 2010-10-16
> **pamepros said:**
> I have the same problem, could someone figure it out?

It appears every time I install something throught the terminal with apt-get

Is it the same error message? Post the exact error message and we can give you a command to rename or hide the script that is causing the problem.

---

### Post by SlimShelly on 2010-10-19
I have the same error message:
> E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

It happens every time I try to install something. I also get multiple lines of a (different) error code upon startup. It happens so fast I'm not sure what it says, but it still lets me log on. 

I don't know if the two are related.

---

### Post by bilalsana on 2010-10-25
i am having the same issue! help!!

---

### Post by binarycortex on 2010-10-27
I had the same issue. But I fixed it by uninstalling firmware-b43-installer. What happened to me is that I tried to install the b43 broadcom driver and it failed. Then I installed Broadcom STA driver and that worked. However from then on everything I installed from the software center said that it failed even though it worked. At the bottom of the log it said it couldn't configure firmware-b43-installer. So I opened Synaptic package manager, searched for it and completely removed it. Now everything works normally. Hope this helps you guys too.

Cheers,

Ian

---

### Post by shadowgodd on 2010-11-10
E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

i have like a few other b43 things in here should i completely remove them all?...there's; firmware-b43legacy-installer | firmware-b43-lpphy-installer | b43-fwcutter

---

### Post by sikander3786 on 2010-11-10
Did you try

```
sudo apt-get remove --purge firmware-b43-installer
```

Please post the output.

Once you remove the firmware-b43-installer package, you can remove other packages by apt-get autoremove.

---

