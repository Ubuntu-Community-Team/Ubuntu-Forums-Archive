---
title: "Xorg crashing"
date: 2006-05-11
forum: General Help
---

### Post by bernardfrancois on 2006-05-11
Hi,

Since today, every few minutes I get logged of and I see the login screen again.

Right after that, I notice the following lines added to dmesg:

```

[26153.238138] Xorg[13004]: segfault at 00002aaaab5a2e5c rip 0000000000c7c733 rsp 00007fffffadae18 error 4
[26154.955040] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[26154.955064] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[26154.955093] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[26155.367202] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[26155.367226] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[26155.367255] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

I have an nvidia geforce ti4800se (agp 8x, as you can see). I have the binary nvidia drivers from the nvidia website. I didn't update them lately. Few days (weeks?) ago, there was an update for Xorg.

Anyone who has a clue on how to resolve this problem?

---

### Post by Ramses de Norre on 2006-05-11
You'll need to reinstall the drivers, a kernel upgrade has been applied a couple of days ago.

---

### Post by bernardfrancois on 2006-05-11
Oh, thanks! Now I know why Xorg crashed every few minutes; that was when trying to load an OpenGl screensaver. Fortunately I'm not using something like XGL, or I probably wouldn't even have been able to start X.

I installed the latest nvidia driver using the [howto](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+latest+nvidia+drivers), and now everything works fine again.

I didn't know the driver wouldn't work any more after installing a new kernel. This seems to be a major disadvantage of automatic kernel updates.

I'm not into kernel compilation and stuff like that, and I don't know much about how drivers are managed in Linux... I thought the nvidia driver would run in user-space, not in kernel-space (it should be, I don't want 3rd-party drivers to endanger my OSs stability).

Couldn't it be the latest X update that caused the problem?

---

### Post by bernardfrancois on 2006-05-12
(i accidentally double posted, and I would like to remove this post, but I can't)

---

### Post by Hairy_Palms on 2006-05-12
if you use the nvidia drivers in the repositories then the drivers get automatically updated along with the kernel.

---

### Post by tseliot on 2006-05-12
[QUOTE=Hairy_Palms]if you use the nvidia drivers in the repositories then the drivers get automatically updated along with the kernel.[/QUOTE]
That's true but if the xserver is updated (of course it does depend...) the OpenGl can break but the nvidia driver might keep working (crashing whenever you use OpenGL)

---

### Post by bernardfrancois on 2006-05-12
I still don't understand how come it made Xorg to crash. Was the OpenGl library (libglut I guess) library updated while the nvidia programmers didn't follow the standard strictly enough and made that the nvidia driver crash ?

I wonder if the problem would have been resolved if I installed the same nvidia driver (version 8178 ) again (now I already installed version 8756).

Whatever the reason is, it should not cause a segmentation fault in Xorg. This might be a bug in Xorg. I would at least expect a little more error handling.

---

