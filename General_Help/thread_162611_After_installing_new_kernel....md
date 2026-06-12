---
title: "After installing new kernel..."
date: 2006-04-19
forum: General Help
---

### Post by PriceChild on 2006-04-19
Hi, installed the 2.6.16-cks6 kernel using the following post:
[http://ubuntuforums.org/showthread.php?t=157560]("http://ubuntuforums.org/showthread.php?t=157560")

However, my xserver isn't starting properly and crashes to terminal.

I've tried removing my conf file and doing "sudo configure xserver-xorg" But that doesn't work. (including changing my graphcis driver to nv instead of nvidia)

I'm guessing its something to do with my having 
the latest nvidia drivers installed using method 2 from the following howto:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=update+nvidia]("http://ubuntuforums.org/showthread.php?t=75074&highlight=update+nvidia")

Anyone any ideas?

Ive been able to get back into the latest standard breezy terminal by doing "sudo configure xserver-xorg" by restoring my original conf file. ((backed it up before deleting it earlier in the post ;))

---

### Post by PriceChild on 2006-04-19
sorry... *bump*

---

### Post by Stormbringer on 2006-04-19
Re-run Method 2 of the "Latest NVIDIA driver HOWTO" to get your Nvidia module compiled for Kernel 2.6.16.X.

- Log in on the console prompt
- Go into interactive sudo mode (sudo -i)
- Set the environment variable for gcc (CC=gcc-3.4; export CC)
- Re-run the NVIDIA installer
- (Re)start GDM and you are all set

Storm.

---

### Post by Rizado on 2006-04-19
[QUOTE=Stormbringer]Re-run Method 2 of the "Latest NVIDIA driver HOWTO" to get your Nvidia module compiled for Kernel 2.6.16.X.

- Log in on the console prompt
- Go into interactive sudo mode (sudo -i)
- Set the environment variable for gcc (CC=gcc-3.4; export CC)
- Re-run the NVIDIA installer
- (Re)start GDM and you are all set

Storm.[/QUOTE]Why would he want to set the enviroment variable for gcc to 3.4? The kernel is compiled with gcc 4.

You can skip almost everything in method 2, It's for the older ubuntu kernel and you have a new one. What you want to do is make sure you keep the kernel source in /usr/src and don't change it after you've compiled a kernel. Download the latest Nvidia installer and run it. Don't change any enviroment variables or install any kernel images/headers because you already have everything you need.

Make sure you haven't enabled nvidiafb in the kernel too because it breaks the binary NVIDIA driver. In graphics support make sure all nvidia options are not enabled. You probably only want VESA enabled (and maybe one of the first options.)

If it still doesn't work post your /var/log/Xorg.0.log after trying to start X.

---

### Post by PriceChild on 2006-04-19
Hey... i'm now running 2.6.16.6 perfectly :)

I got a scare when the installer got angry about gcc 3.4 but that was quickly sorted out :)

Oh and restarting GDM didn't work, i had to reboot.

Thanks for help :)

---

### Post by Rizado on 2006-04-19
[QUOTE=PriceChild]Hey... i'm now running 2.6.16.6 perfectly :)

I got a scare when the installer got angry about gcc 3.4 but that was quickly sorted out :)

Oh and restarting GDM didn't work, i had to reboot.

Thanks for help :)[/QUOTE]You should know that you're using the server version of con kolivas patches. The normal ones are named ck. 
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)
The good thing is that now that you have compiled one working kernel you won't have much problem (Hopefully) compiling a new one. It's the first one that's hard to do :)

---

### Post by PriceChild on 2006-04-19
He he yeah i'd noticed... Will it make that much of a difference?

Think i should redo it?

---

