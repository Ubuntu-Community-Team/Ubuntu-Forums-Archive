---
title: "Nomodeset"
date: 2012-03-07
forum: General Help
---

### Post by jucestain on 2012-03-07
I recently built a computer with a 580GTX gpu. I installed Ubuntu 11.10 64bit but I had the infamous problem of not being able to boot without changing quiet splash to "nomodeset."  

So here's my question, I have no idea what "nomodeset" and I wasn't able to find (or understand) much from google so I was wondering, what does nomodeset do? 

Also, more importantly, I'd like to do some CUDA programming. I installed the latest drivers from nvidia but the comp still doesn't boot unless I put "nomodeset." Will nomodeset prevent CUDA from working? Or will it slow its performance? Thanks!

---

### Post by Gremlinzzz on 2012-03-07
nomodeset
The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a black screen. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded.

Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent, just for one boot until you installed the nvidia drivers.
:popcorn:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jucestain on 2012-03-07
Yea, I installed nvidia drivers a variety of ways: the proprietary driver way; running the .run file from nvidia's website. All of these caused the boot to fail without nomodeset. 

I ended up trying this:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

And it worked! I can now boot without nomodeset. Not sure what difference it makes but I don't care! From a black box perspective I just wanted the damn thing to work. Hopefully I can get CUDA set up soon. Thanks for the response.

... One of these days I'll read an in-depth book on linux and actually try to understand the inner workings. But I'm just glad it's working (for now at least).

---

### Post by sea7kenp on 2012-08-01
Thank you to everyone who contributed to this  --  especially the part about the kernel itself doing the hardware probing during the bootup process, and how this gets tweaked in new versions of the Kernel.  That explains my mixed experiences with old laptops, frequently with Radeon graphics.  (Note:  Ubuntu 6.06 worked great, Ubuntu 12.0.4 works in text mode, with a fbcon, and only a kernel without pae.  However, ubuntu 10.0.4, as well as Debian 6.05, give only black screens, though I can ssh in).

Question:  can I set up a debugging environment, say via an interactive initrd, so that I can help with the troubleshooting?  I'm interested in a shell before it tries to set up fbcon.

Thank you and best regards,  Kenneth Parker, Seattle, WA.

---

