---
title: "Screen resolution hits rock bottom at Ubuntu loading screen."
date: 2012-05-12
forum: General Help
---

### Post by epikvision on 2012-05-12
:confused:I managed to get my computer to recognize my video card.  For that, I paid a small price: the Ubuntu boot and shut-down loading screens displayed very low resolutions! Before it used to be the same resolution as I had on the desktop: 1920 x 1080.  

How can this be fixed?

---

### Post by Derek Karpinski on 2012-05-12
Do you have nvidia? And I'm guessing you've installed the nvidia drivers?

Open terminal (Ctrl-Alt-T)

```
sudo apt-get update && sudo apt-get install hwinfo
``````
sudo hwinfo --framebuffer
```Pick one of the resolutions and bit depth that matches your native resolution, or at minimum the same aspect ratio.

Copy the 6 character hexadecimal number. ie: 0x0361

```
gksudo gedit /etc/default/grub
```change:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=0x0361"
``` (replace 0x0361 with your hexadecimal number)

Save the file, close the file,

```
sudo update-grub2
```Then reboot, and see how it looks.

This is one way, and there are a few more ways to change the resolution.

---

### Post by epikvision on 2012-05-12
Thanks very much. It has improved the resolution of the boot screen.  Still, it's a great pity that I didn't have 1920x1080 as a supported resolution.

---

### Post by Derek Karpinski on 2012-05-12
> **epikvision said:**
> Thanks very much. It has improved the resolution of the boot screen.  Still, it's a great pity that I didn't have 1920x1080 as a supported resolution.


This is not Ubuntu's fault per se.  when you typed in 'hwinfo --framebuffer' that retured a list of modes the video card can display before loading any drivers.

Now, if your purple splash screen doesn't fill up the screen, and there is a black border around it, we can change that to all black, so you won't notice that you're not running full resolution.

---

### Post by FishboyFive on 2012-05-12
its all a problem with Plymouth 

not sure why ubuntu still uses it for boot up and shutdown

from what i understand Plymouth will never ever work with AMD or Nvidia drivers only open source hacked drivers.

i would have removed this plymouth crap a year ago

---

### Post by epikvision on 2012-07-16
Long later, when I installed the Ubuntu CD I picked up from UDS, I inadvertently installed the Ubuntu x32 on my x64 bit computer.  Sigh.  

Surprisingly, the loading and shutdown screen had the resolution right on, with the purple background. I guess it took a fresh install.

---

