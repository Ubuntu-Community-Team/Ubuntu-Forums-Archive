---
title: "XPS M1330 with 10.10 Maverick Meerkat"
date: 2010-10-13
forum: General Help
---

### Post by x C0MMAND0 x on 2010-10-13
Before I upgrade, what are some issues anybody has been having with upgrading/installing 10.10? I currently have Dell XPS M1330 running 64bit 10.04, and will be doing an upgrade as opposed to a clean install.

Any issues for anybody out there? I know it just came out, but I am still curious...

---

### Post by transformania on 2010-10-13
I did a fresh install on my m1330, and everything's good except suspend (which is, unfortunately, a deal-breaker for a laptop).

However, I'm going to un-install some junk to make sure it's not just something I'm using that's not jiving with Maverick that was ok with Lucid.

---

### Post by pdbq on 2010-10-13
I did fresh install and webcam is not working


[    8.989309] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[    8.989614] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    8.991353] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    8.991356] uvcvideo: Failed to initialize the device (-5).


it worked normally in lucid

---

### Post by tigang on 2010-10-17
> **transformania said:**
> I did a fresh install on my m1330, and everything's good except suspend (which is, unfortunately, a deal-breaker for a laptop).

However, I'm going to un-install some junk to make sure it's not just something I'm using that's not jiving with Maverick that was ok with Lucid.

I have a quad-core AMD 64bit system that I updated from 10.04 to 10.10. Suspend worked fine until one of the subsequent daily updates installed, now it just hangs on a wake-up.

Also, since the main update, console messages are no longer hidden (quiet). I managed to get rid of the login stuff by installing Startup-Manager, but shutdown looks a mess.

Apart from suspend, the other problems are not too much of a problem, but folk I have only recently converted from Windoze to Ubuntu think it is really unprofessional and are tempted to dump Messy Meerkat and reinstall Windoze 7.

What a shame that a sloppy update from 10.04 to 10.10 has undone all of my good work in trying to convert those folks!

---

### Post by svega85 on 2010-10-17
> **pdbq said:**
> I did fresh install and webcam is not working


[    8.989309] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[    8.989614] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    8.991353] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    8.991356] uvcvideo: Failed to initialize the device (-5).


it worked normally in lucid

same issue here, this fixed it for me, at least till I reboot
$ sudo rmmod uvcvideo
$ sudo modprobe uvcvideo

---

### Post by bro on 2010-10-18
```
$ sudo rmmod uvcvideo
$ sudo modprobe uvcvideo
```

This seemed to have worked for me.

---

### Post by mooselander on 2010-10-19
> **x C0MMAND0 x said:**
> Before I upgrade, what are some issues anybody has been having with upgrading/installing 10.10? I currently have Dell XPS M1330 running 64bit 10.04, and will be doing an upgrade as opposed to a clean install.

Any issues for anybody out there? I know it just came out, but I am still curious...

My fan seems to be running all the time, at mid speed, since upgrading to 10.10.  This has caused my battery time to drop below 2 hours on a 6 cell battery.

According to lm-sensors the cores seem to be running hotter:

Core 0:      +42.0°C  (high = +105.0°C, crit = +105.0°C)  
Core 1:      +42.0°C  (high = +105.0°C, crit = +105.0°C) 

I performed the "copper shim" mod about a year ago and it drastically reduced operating temperatures.  Maybe time to revisit with another application of heatsink grease.

[http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html](http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html)

Has anyone else experienced this?

---

### Post by svega85 on 2010-10-20
> **mooselander said:**
> My fan seems to be running all the time, at mid speed, since upgrading to 10.10.  This has caused my battery time to drop below 2 hours on a 6 cell battery.

According to lm-sensors the cores seem to be running hotter:

Core 0:      +42.0°C  (high = +105.0°C, crit = +105.0°C)  
Core 1:      +42.0°C  (high = +105.0°C, crit = +105.0°C) 

I performed the "copper shim" mod about a year ago and it drastically reduced operating temperatures.  Maybe time to revisit with another application of heatsink grease.

[http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html](http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html)

Has anyone else experienced this?

that happened to me once with a dell 1420. the fix was to update the bios. not sure if it will work for you but it's worth a try.

---

### Post by mooselander on 2010-10-20
Lores' workaround about halfway through fixed me right up:

[http://ubuntuforums.org/showthread.php?t=1592424](http://ubuntuforums.org/showthread.php?t=1592424)

Re-installing pm-utils from the repo now allows my M1330 to suspend properly.  After installing laptop-mode-tools from samwel.tk, rather than the repos, pm-utils remains installed while laptop-mode enables power saving features on Maverick 10.10.

I've also installed Granola from [http://www.miserware.com](http://www.miserware.com) and while I'm still skeptical about it's energy saving potential, my cpu temps have dropped:

Core 0:      +38.0°C  (high = +105.0°C, crit = +105.0°C)  
Core 1:      +37.0°C  (high = +105.0°C, crit = +105.0°C) 

I've configured laptop-mode to spin down the hard drive when not in use and this, in combination with the cpu temp/fan speed drop, has Ubuntu 10.10 reporting 3+ hours of battery life on my 6 cell battery.

Suspend works and battery life has increased.  I'm pretty happy.

---

### Post by svega85 on 2010-10-20
glad everything worked out for you ;)

---

### Post by x C0MMAND0 x on 2010-10-20
Has anybody done an upgrade as opposed to a clean install?

---

### Post by mooselander on 2010-10-20
> **x C0MMAND0 x said:**
> Has anybody done an upgrade as opposed to a clean install?

Yes, mine was an upgrade on a spare hard drive that had an old 9.10 install.

9.10 -> 10.4 -> 10.10

Everything seems to be working fine after a little tweaking:  webcam, fingerprint scanner, wifi, supend and etc.

---

### Post by x C0MMAND0 x on 2010-10-26
I just upgraded.  My temperatures are running significantly higher than they were in 10.04...Around 70C for GPU, when it used to run around 50-55.

---

### Post by transformania on 2010-11-13
> **tigang said:**
> I have a quad-core AMD 64bit system that I updated from 10.04 to 10.10. Suspend worked fine until one of the subsequent daily updates installed, now it just hangs on a wake-up.

Also, since the main update, console messages are no longer hidden (quiet). I managed to get rid of the login stuff by installing Startup-Manager, but shutdown looks a mess.

Apart from suspend, the other problems are not too much of a problem, but folk I have only recently converted from Windoze to Ubuntu think it is really unprofessional and are tempted to dump Messy Meerkat and reinstall Windoze 7.

What a shame that a sloppy update from 10.04 to 10.10 has undone all of my good work in trying to convert those folks!

While I do feel it's unfortunate that in-place upgrades in Ubuntu don't always work flawlessly, to be honest, most OS's in-place upgrades never work flawlessly anyway (in my 15+ years as an admin), whether it's Linux or Windows.

So, I just don't do them.  I always start fresh, and it's an excuse to clean out crud.  At least for Linux, I've been able to bring back most of my customization after the fresh install with a little script I've been refining over the last few installs.

Once every 6-months, though, could be too often to make this worth it for some, but it's fine by me.

I quality-to-cost ratio for Ubuntu is exceptionally high ;P

---

### Post by levymichel on 2012-09-18
two years later. I have the same problem with my webcam on ubuntu 12.04 LTS et with a Dell XPS M1330.
Surprisingly, sometimes my webcam works, sometimes no and, at login, I have the message 'uvcvideo failed'.
I do 'sudo rmmod uvcvideo;sudo modprobe uvcvideo' and the webcam restarts.

---

