---
title: "latest kernel 2.6.31-15 boots me to a command prompt"
date: 2009-11-25
forum: General Help
---

### Post by sdowney717 on 2009-11-25
I have to select 2.6.31-14 to get the gui up.
This am I saw an upgrade and allowed it.
Anyone else notice this?

---

### Post by vy13 on 2009-11-25
Yeah! I have the same problem. I cant boot ubuntu. Can anybody help?

---

### Post by sdowney717 on 2009-11-25
at grub menu, select the 2.6.31-14 kernel

---

### Post by Caraibes on 2009-11-25
I have almost the same problem: In my case, when booting 2.6.31.15, the boot process starts to flicker, and just hangs there...

Of course I am happily using 2.6.31.14 right now, and everything works just fine.

This is on my main desktop, amd64, with Nvidia drivers for the video card...

On my 2 other 32 bit desktops, with Intel & SiS integrated video chipsets, no problem whatsoever with 2.6.31.15...

I guess there's a conflict somewhere with the Nvidia drivers...

-Are you guys using amd64 as well ?

-Do you also have Nvidia video drivers ?

---

### Post by monkeyoutlaw on 2009-11-25
I have the same problem with Intel CPU and ATI GFX.
 
Lots of people have this problem and I am yet to find a solution :(
 
There's another thread here - [http://ubuntuforums.org/showthread.php?t=1307429](http://ubuntuforums.org/showthread.php?t=1307429)

---

### Post by monkeyoutlaw on 2009-11-25
And here [http://ohioloco.ubuntuforums.org/showthread.php?p=8372976](http://ohioloco.ubuntuforums.org/showthread.php?p=8372976)

---

### Post by monkeyoutlaw on 2009-11-25
And my thread...  [http://ubuntuforums.org/showthread.php?t=1337149](http://ubuntuforums.org/showthread.php?t=1337149)

---

### Post by monkeyoutlaw on 2009-11-25
Found a bug report here [https://bugs.launchpad.net/wubi/+bug/484799](https://bugs.launchpad.net/wubi/+bug/484799)
 
Referenced from thread [http://ubuntuforums.org/showthread.php?t=1314064&page=6](http://ubuntuforums.org/showthread.php?t=1314064&page=6)

---

### Post by sdowney717 on 2009-11-25
i am running nvidia 190 driver

---

### Post by vy13 on 2009-11-25
My problem is the same:
[http://ubuntuforums.org/showthread.php?t=1337149](http://ubuntuforums.org/showthread.php?t=1337149)
I cant view the boot menu. I can't load ubuntu.
Heres a picture:
[http://www.flickr.com/photos/vy13/4097234597/](http://www.flickr.com/photos/vy13/4097234597/)

---

### Post by jmask on 2009-11-25
I had this same problem.
Booted to the old kernel and there were still updates pending.
Finished the updates, restarted and all went OK with the new kernel.

---

### Post by Phil M on 2009-11-25
jmask, could you tell us if you're running Ubuntu with wubi or with a direct installation?
Cause I'm running it with wubi and the problem persists.

(Ubuntu 64bit and NVIDIA drivers)
Btw, I'm pretty sure this bug is related to wubi, not to drivers...

---

### Post by arqbrulo on 2009-11-25
Well, I'm pretty sure that it _IS_ related to a driver, to be more specific, Nvidia driver. I selected the *.15 kernel in recovery mode and everything started fine. Once I logged in and typed "startx", it gave me the x11 error message, something to do with the nvidia driver. I changed the setting in the xorg.conf file from "nvidia" to "nv" and it booted fine. went back to "nvidia" and again it failed.

---

### Post by bushtangu on 2009-11-26
try to update your grub from a live cd

---

### Post by sdowney717 on 2009-11-26
for me the problem has vanished. I can now boot into the 2.6.31-15 kernel without issues.
while running the .14 kernel, I installed several programs, ran update upgrade etc... and  who knows why but it is working.

Also I have not been able to startx from the commandline for some time.
I do use the Nvidia driver.
Perhaps you could try going into synaptic and reinstalling or uninstall, install the nvidia driver. it should go thru and recompile itself against the new kernel headers. Then on restarting you have to run sudo nvidia-xconfig.

---

### Post by vy13 on 2009-11-26
I installed Ubuntu with Wubi.

[64 BIT and my videocard is ATI Radeon HD4670]

---

### Post by Levo on 2009-11-27
> **Caraibes said:**
> I have almost the same problem: In my case, when booting 2.6.31.15, the boot process starts to flicker, and just hangs there...

Of course I am happily using 2.6.31.14 right now, and everything works just fine.

This is on my main desktop, amd64, with Nvidia drivers for the video card...

On my 2 other 32 bit desktops, with Intel & SiS integrated video chipsets, no problem whatsoever with 2.6.31.15...

I guess there's a conflict somewhere with the Nvidia drivers...

-Are you guys using amd64 as well ?

-Do you also have Nvidia video drivers ?


I have the same specs and the same problem. Probably the nvidia driver fails to start.

---

### Post by dbrinto on 2009-11-29
> **Caraibes said:**
> I have almost the same problem: In my case, when booting 2.6.31.15, the boot process starts to flicker, and just hangs there...

Of course I am happily using 2.6.31.14 right now, and everything works just fine.

This is on my main desktop, amd64, with Nvidia drivers for the video card...

On my 2 other 32 bit desktops, with Intel & SiS integrated video chipsets, no problem whatsoever with 2.6.31.15...

I guess there's a conflict somewhere with the Nvidia drivers...

-Are you guys using amd64 as well ?

-Do you also have Nvidia video drivers ?


I've got the exact same problem. I'm running 64bit Linux and I have the nvidia drivers installed.

---

### Post by arqbrulo on 2009-11-29
Yep, same here, 64-bit with nvidia drivers. I installed the driver manually from the nvidia site and now I'm booting to kernel 15. So, in my case, it WAS the video driver.

---

### Post by dbrinto on 2009-11-29
> **arqbrulo said:**
> Yep, same here, 64-bit with nvidia drivers. I installed the driver manually from the nvidia site and now I'm booting to kernel 15. So, in my case, it WAS the video driver.

Same here. I booted to 2.6.31-15 recovery mode, and reinstalled the nvidia drivers. Now 2.6.31-15 works.

---

### Post by nickmhalliday on 2009-12-01
> **vy13 said:**
> My problem is the same:
[http://ubuntuforums.org/showthread.php?t=1337149](http://ubuntuforums.org/showthread.php?t=1337149)
I cant view the boot menu. I can't load ubuntu.
Heres a picture:
[http://www.flickr.com/photos/vy13/4097234597/](http://www.flickr.com/photos/vy13/4097234597/)
Hi, I think there is something fundamentally wrong with Karmic and booting. Last week after a month or so of great performance I kept getting totally locked out; or it took 5/6/7 attempts to log on. I then followed some of the instructions to reload grub which has now worked for a few days and then collapsed again. Not making me want to evangelise Ubuntu particularly when I am trying to finish a project and can never log on. My advice at moment would be wait six months before trying an upgrade its fine to have minor bugs but not in parts that stop computer from working

---

### Post by Caraibes on 2009-12-05
Just wanted to say that all issues are automatically fixed for me this morning, with the update to the newest kernel 2.6.31.16.

Up until this morning, I have been running under 2.6.31.14. I never could boot 2.6.31.15. Now, without having to perform any tweak whatsoever, 2.6.31.16 works just fine, and I finally cleaned all older kernels...

---

