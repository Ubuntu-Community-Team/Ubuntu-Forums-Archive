---
title: "ubuntu random freezes + transitions strange"
date: 2012-09-18
forum: General Help
---

### Post by flyingsliverfin on 2012-09-18
Hey all, I just upgraded from my [very] stable 10.04 to 12.04 hoping to get to know the new HUD etc etc. However, there are random stalls where everything totally freezes. For instance, music stops playing, video stops, I can't move the mouse or enter via keyboard. 

I think this may be related, but sometimes the graphics will turn into lines or blank out. I've attached two screenshots of this happening in different ways. 

I have an old nvidia card:
```
01:00.0 VGA compatible controller: NVIDIA Corporation NV43GL [Quadro FX 540] (rev a2)
	Subsystem: NVIDIA Corporation Device 02d1
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

```

Sometimes when I manage to make it freeze the launcher dock will expand and collapse on its own. Also right now all the things that are normally orange in ubuntuforums and some of the firefox buttons (reload, forward, close tab etc) are yellow. (Took a screenshot of that too).

The frequency of the freezes seems to increase when i use the mouse to interact with the dock. Actually i can't even launch nautilus by clicking the folder launcher... it freezes while i click every time. AH i just realized a pattern: I can use the mouse with the 'Dash Home' but as soon as I flick down to firefox or nautilus nothing happens, then after 2 seconds the mouse freezes for about another 2.

---

### Post by flyingsliverfin on 2012-09-27
Okay so it seems like these effects only kick in after I wake up the computer from suspend (didnt notice before since i do it so much!)

Also if i restart X (sudo restart lightdm) it seems to fix the problem. As a workaround I'll probably just add that command to stuff for it to do upon waking up

---

### Post by flyingsliverfin on 2012-11-26
Okay well if anyone still cares, my final fix for this problem (restarting lightdm is inconvenient because it closes all the programs/applications running) - and that didn't always fix it anyway - was to update to the NVIDIA proprietary driver.

---

