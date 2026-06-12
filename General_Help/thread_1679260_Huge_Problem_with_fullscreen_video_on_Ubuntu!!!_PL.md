---
title: "Huge Problem with fullscreen video on Ubuntu!!! PLEASE HELP!!!"
date: 2011-01-31
forum: General Help
---

### Post by gokuman56 on 2011-01-31
Hello,
I have a HP DV5-1002nr running the latest 32 bit edition of Ubuntu. I have a huge problem with playing fullscreen videos. They work when I am not fullscreen, but as soon as I click fullscreen, rainbow colors show up and I have to close the screen or turn off the computer to make it better. Lets say I am on youtube and I click a video, it works until I press the fullscreen button, the video sound is still playing, but the display turns rainbow colors.
Can someone help me?
Thanks

---

### Post by slooksterpsv on 2011-01-31
Have you installed the ATI Drivers for your video card? If not click on Settings -> Administration -> Hardware drivers -> After a moment you can click on Activate.

After that installs, open up a terminal via: Applications -> Accessories -> Terminal

When that window appears type in:
gksudo aticonfig --initial -f

Reboot and let us know if that helps any.

---

### Post by gokuman56 on 2011-01-31
Thanks, I just removed the Driver and everything works.

---

### Post by slooksterpsv on 2011-01-31
> **gokuman56 said:**
> Thanks, I just removed the Driver and everything works.

Sadly, that does not surprise me, the drivers seem to be hit or miss. Even if I install the driver, it really doesn't do anything unless I run aticonfig --initial -f to create the xorg file for me.

---

### Post by number nine on 2011-06-21
I'm seeing this same issue: "rainbow" colours on video (which, after it happens, affects some text and graphics as well) with the only solution being a restart.

Unfortunately the suggestion here won't work for me because I have Intel graphics using the standard kernel driver:

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

Does anybody have any suggestions as to what I can do to resolve this?

Edit: system is 32-bit Maverick, Intel i915 graphics driver.
$ uname -a
Linux [[hostname]] 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

---

### Post by slooksterpsv on 2011-06-21
Not sure, I'd create a new thread with your specific issue e.g.

Intel 945GM Graphics color issue

Other than that I'm not sure, I don't use Intel so I'm not experience in that area.

---

### Post by el_koraco on 2011-06-21
I have the same thing on my machine with ATI drivers. A workaround for me has been to go to tty1 (CRTL ALT F1), and back to GUI (CTRL ALT F7). 

I've reported the bug, but it doesn't seem to be fixed yet.

---

