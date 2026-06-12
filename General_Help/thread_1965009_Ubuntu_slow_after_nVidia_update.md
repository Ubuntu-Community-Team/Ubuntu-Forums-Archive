---
title: "Ubuntu slow after nVidia update"
date: 2012-04-24
forum: General Help
---

### Post by Optimised on 2012-04-24
Hi All,

I am running Ubuntu 10.04 and Gnome 2.30.2 on an Intel Q6600 and nVidia EN8800 GTS. This was all running smoothly until after an update the other day (which I am pretty sure included a new nVidia driver). Now Gnome and the rest of the system hangs randomly and the display takes forever to render a window or sometimes doesn't and I have to move my mouse through to refresh that portion of the screen. When moving my mouse across my AWN dock the animations are slow and sometimes take minutes to display - and this usually causes the system to hang.

I tried rolling back the drivers to 173 and 96 however the problem is still existent albeit it occurs less often. The only way to completely stop the problem is to not have a nVidia driver active, however I lose all my compiz, etc. which is also undesirable.

Any help would be much appreciated.

Cheers

Tony

---

### Post by bogan on 2012-04-25
Hi!, **Optimized**,

The problem with the nvidia-current 295.40 update with 7xxx & 8xxx series nvidia cards is very widespread and acknowledged by Nvidia as due a bug in an important security patch.

In the Ubuntu +1 Precise pangolin Forum there are even more reports of nvidia driver update problems:  "**Re: 12.04 -- April 14/15 Updates Nvidia Regression"  **[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

 There are also multiple queries in Nvidia NVnews FAQ's:  [http://www.nvnews.net/vbulletin/sear...archid=4590215]("http://www.nvnews.net/vbulletin/search.php?searchid=4590215")

The symptoms are widely varied, and the treatment varies too. for some 295.33 is OK for others even 290.10 does not work.

What is important is to clear out remove --purge the remnants of any previous drivers and ensure the new or re-installation is to the correct kernal headers.

I have one computer running 295.33 without problems, and another had to regress to 290.10. But really weird is that a version of 11.10 on a USB stick runs both machines OK, even though it has 295.40 installed on it!!

Chao!, **bogan**.

---

### Post by cknight725 on 2012-04-30
Been fighting this NVIDIA issue since 11.04 -- I'm thinkin the best thing to do at this point is bail on NVIDIA hardware sadly.

ATI 6450's are cheap thankfully ...

---

### Post by bogan on 2012-05-04
Hi!,** All,**  There is a new driver, 295.49 available from nvidia downloads
 [http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html)

 Noon Friday May 4th; ```
nvidia-installer --latest 
``` now   returns: v295.49 and     ```
nvidia-installer -f 
``` will install   295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!, **bogan**

---

