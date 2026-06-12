---
title: "PC from 2003"
date: 2009-07-30
forum: General Help
---

### Post by mavio on 2009-07-30
I've installed Ubuntu 9.04 on a 2003 Dell equipped with 2.3Ghz Intel Celeron and 512 Mb RAM. This because I had heard that Linux is generally faster than Windows, more stable and less hardware-hungry.
I've had problems with the setup of the integrated graphics, intel 845G chipset. Now they are gone :D
At 1024x768, actions like browsing this site or viewing a clip on youtube put a 100% stress on the CPU. At idle the CPU is always on 30%. Glxgears@fullscreen: ~70 FPS. Windowed: 200 FPS.
I've also XP installed on that machine, it seems more responsive, I notice it when scrolling pages in Firefox, it's smoother.
Do I really have to get rid of that old PC?
Or should I use it in command-line mode to do things like moving files, pinging other IPs and so on (useless for me)?
Help me save that old computer!

---

### Post by philcamlin on 2009-07-30
turn it into a web server for all your files :)

thats what i did to 3 windows 98's i have running in my furnace room

---

### Post by castlefox on 2009-07-30
I had better time getting 8.04 to work with my Intel intergraded graphics.  

9.04 has known problems with Intel's graphic solutions.

---

### Post by hibliss on 2009-07-30
Try installing a lighter Desktop Environment.

I recommend LXDE. It will run much better on that hardware than Gnome without too much visual sacrifice.

You can install it to your current partitioned install, then logout, choose session, choose LXDE, and login as usual.

---

### Post by mavio on 2009-07-30
Can you give some tips about converting a PC in a web server? It's very interesting.

I don't mind eyecandy, I would use that PC to surf the web... pretty much like having Damn Small Linux. I tried it, i didn't like it.

---

### Post by earthpigg on 2009-07-30
> **castlefox said:**
> I had better time getting 8.04 to work with my Intel intergraded graphics.  

9.04 has known problems with Intel's graphic solutions.

+1 for this solution

---

### Post by thezood on 2009-07-31
> **castlefox said:**
> I had better time getting 8.04 to work with my Intel intergraded graphics.  

9.04 has known problems with Intel's graphic solutions.

I had the same problem with my integrated Intel chip. Try installing the 2.6.31 kernel. It could give you other headaches since it's still in beta but it's definately worth trying. I got about 150% increase in graphics performance with it.

Download linux-image and linux-header for your architecture and also the _all package from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc4/) and install them. They will create another GRUB menu item so if it doesn't work, you shouldn't have any problems going back to the default kernel.

Also, enable UXA acceleration according to this guide: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
If you want to try the 2.6.31 kernel, you should of course skip the 2.6.30 kernel part in the guide.

---

