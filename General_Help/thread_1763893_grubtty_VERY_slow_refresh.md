---
title: "grub/tty VERY slow refresh"
date: 2011-05-21
forum: General Help
---

### Post by ignavia on 2011-05-21
I'm running Natty on an Nvidia 8200 chipset. I found how to change the grub/tty resolution [here](https://help.ubuntu.com/community/ChangeTTYResolution), but anything I run from tty takes about a full second to redraw the screen. I KNOW this is something simple, but I must be missing it. 

What is it?!

---

### Post by linuxinstalledfromhdd on 2011-05-21
Did you check to make sure you have the video drivers installed?

---

### Post by ignavia on 2011-05-21
Well... I thought I was using nvidia current, but the drivers panel says they're activated but not in use. I have compiz running... so obviously I have some drivers...

Oh, Nvidia server settings says I'm using 270.41.06

---

### Post by wildmanne39 on 2011-05-21
> **ignavia said:**
> I'm running Natty on an Nvidia 8200 chipset. I found how to change the grub/tty resolution [here](https://help.ubuntu.com/community/ChangeTTYResolution), but anything I run from tty takes about a full second to redraw the screen. I KNOW this is something simple, but I must be missing it. 

What is it?!
Hi, first that guide you used is very old, it is not for natty, I do not know if that will make a difference or not. If you are using your nvivia driver then you should see if the other one that is listed works better, for me the current one is not good, I have to use the 173 driver. If you are not using it then go to administration and click on additional drivers and activate it,

---

### Post by ignavia on 2011-05-21
The guide is for grub2, so it worked fine to change the resolution.

I was running the 173 drivers when I upgraded from Lucid, but there was an issue... At the moment, I'm forgetting what it was. I think it was like a static thing when moving windows and things.

---

### Post by wildmanne39 on 2011-05-21
> **ignavia said:**
> The guide is for grub2, so it worked fine to change the resolution.

I was running the 173 drivers when I upgraded from Lucid, but there was an issue... At the moment, I'm forgetting what it was. I think it was like a static thing when moving windows and things.
Hi, and that is just a bug that says you are not using the driver, it really is activated. I am not sure what else to say about the resolution problem though.

---

### Post by ignavia on 2011-05-21
> **wildmanne39 said:**
> Hi, and that is just a bug that says you are not using the driver, it really is activated. I am not sure what else to say about the resolution problem though.

Yeah, I see that now that I removed it and put it back. And I remember that my problem with 173 was that I got no video after coming back from sleep, so that's no good either.

---

### Post by wildmanne39 on 2011-05-21
> **ignavia said:**
> I'm running Natty on an Nvidia 8200 chipset. I found how to change the grub/tty resolution [here](https://help.ubuntu.com/community/ChangeTTYResolution), but anything I run from tty takes about a full second to redraw the screen. I KNOW this is something simple, but I must be missing it. 

What is it?!
HI, is it actually restarting or is it logging you out to the log in screen.

---

### Post by ignavia on 2011-05-21
> **wildmanne39 said:**
> HI, is it actually restarting or is it logging you out to the log in screen.

Huh?

---

### Post by wildmanne39 on 2011-05-21
> **ignavia said:**
> Huh?

Hi, sorry this was meant for another user that is having a different problem.

---

