---
title: "newest nvidia driver"
date: 2012-05-03
forum: General Help
---

### Post by ahso4271 on 2012-05-03
Hi
should I stick with the default that comes with 12.04 or use this?
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

Many thanks
Michael

---

### Post by pqwoerituytrueiwoq on 2012-05-03
I have had no issues with the 295.40 version on my "GeForce 8200M G" or "GeForce GTX 550 TI"
**i use the nomodeset kernel option

edit:
that ppa contains no updates to nvidia-current as of now

---

### Post by Pablo Pablovski on 2012-05-03
295.49 driver relaeased here.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

Works for me, when 295.40 seriously didn't

---

### Post by pqwoerituytrueiwoq on 2012-05-03
i suggest waiting a day or 2 for it to show up in the ppa linked in the OP
unless you want to reinstall the driver after every kernel update

---

### Post by bogan on 2012-05-03
Hi! **Pablo**, you Posted:> **Re: newest nvidia driver**
         295.49 driver relaeased here.

[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html")

Works for me, when 295.40 seriously didn't     Sure it is there, but they do not advise it for 7xxx & 8xxx cards; they say:>  cannot offer driver info: Try again later.But Ive downloaded it and we shall see.
Edit: Though their NVNews says of version295.49: > **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!. **bogan**.

---

### Post by bogan on 2012-05-03
Hi!,** All**,

I downloaded the nvidia 295.49 driver from the Nvidia Web site, and installed it;  everything I have tried up to now, is running AOK - Ubuntu 3D & 2D, Gnome, Gnome Classic with & without Effects. I have not tried any Movies or complex Videos.

That is with a GeForce 7650 GTS: It shows none of the symptoms I associate with running 295.40 with this or other cards.

Running:```
 sudo nvidia-installer --latest
``` still returned 295.33, so I could not install it with```
  sudo nvidia-installer -f 
```and had to use```
 sudo chmod a+x NVIDIA-Linux-x86-295.49.run 
 sudo sh NVIDIA-Linux-x86-295.49.run
```to execute the .run file. 

If only 12.04 could be put right as easily!

Chao!, **bogan**.

---

### Post by ahso4271 on 2012-05-04
Thanks, for the driver from Nvidia's website, do I need to preinstall kernel sources or alike?
How to later update that? 

I guess with ppa there's someting alike a update command?

After install of the default can I do?

sudo nvidia-installer -f

seems the easiest way...

---

### Post by markbl on 2012-05-04
> **bogan said:**
> Hi!,** All**,
I downloaded the nvidia 295.49 driver from the Nvidia Web site, and installed it;  everything I have tried up to now, is running AOK - Ubuntu 3D & 2D, Gnome, Gnome Classic with & without Effects. I have not tried any Movies or complex Videos.

I installed the 295.49 driver version from nvidia web site and have had 3 xorg server seg fault crashes in the 4 hours I have been using it. Just using the browser and terminals in gnome-shell, nothing fancy.

Backtrace is:
```

..
[ 13205.989] (II) Module glx: vendor="NVIDIA Corporation"
[ 13205.989] 	compiled for 4.0.2, module version = 1.0.0
[ 13205.989] 	Module class: X.Org Server Extension
[ 13205.989] (II) NVIDIA GLX Module  295.49  Mon Apr 30 23:52:01 PDT 2012
..

Backtrace:
[ 19140.851] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb775f627]
[ 19140.851] 1: /usr/bin/X (0xb75d7000+0x18c3aa) [0xb77633aa]
[ 19140.851] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb75b440c]
[ 19140.851] 3: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0xb482e000+0xd4b39) [0xb4902b39]
[ 19140.851] Segmentation fault at address 0xb47dc000
[ 19140.851]
Caught signal 11 (Segmentation fault). Server aborting

```

So still looks broken. Guess I will try 302.07 next.

---

### Post by markbl on 2012-05-04
Ok, I have installed 302.07 and running ok atm. Will report back later how it goes. I am just running the beta driver from nvidia site which I installed by running the shell script installer, not xorg-edgers or x-swat ppas.

---

### Post by markbl on 2012-05-05
Nvidia driver 302.07 seg faults for me as well, running gnome-shell. One instance today of:
```

686CCB40771CDF520.xkm
[  2262.128]
Backtrace:
[  2262.128] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb7719627]
[  2262.128] 1: /usr/bin/X (0xb7591000+0x18c3aa) [0xb771d3aa]
[  2262.128] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb756e40c]
[  2262.128] 3: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0xb479b000+0xcfc74) [0xb486ac74]
[  2262.128] Segmentation fault at address 0xbf93
[  2262.128]
Caught signal 11 (Segmentation fault). Server aborting
[  2262.128]

```

Surely I can't be the only one this is happening to?

---

### Post by markbl on 2012-05-06
This time I added the xorg edgers ppa and updated to 302.07 that way (instead of just using the nvidia script from their download site). However, just got a segmentation fault again. Anybody else seeing this? I have dual monitors and using gnome-shell.

---

### Post by ahso4271 on 2012-05-06
running fine with default 12.04 driver but wondering about the newest:

michael@ubuntu-michael:~$ sudo nvidia-installer --latest
sudo: nvidia-installer: command not found

Am I missing something?
Thanks

---

### Post by smurphy on 2012-05-06
If all the drivers are core-dumping, I suspect that the fault is somewhere else to look at. Not the driver.

You sure you have all the correct sources etc. installed ?
Make a kernel build (compile, make -j to span as many processes as there is memory) and stress the system to make sure it's not a hardware issue.

What I'd try too, is to set the BIOS to default fail-safe settings for testing the driver.

---

### Post by Macfunky on 2012-05-06
I had problems with 295.40 running gnome shell and unity. I have been using Xfce since the problem cropped up. I'm not sure how to install the driver and don't want to try in case i mess something up. What's the easiest and safest way for me to get the update? Will it be pushed through in the repos shortly? If so i'd preferably wait for that.

---

### Post by smurphy on 2012-05-06
That's the point. If it is a hardware issue, whatever update you get won't fix it. Reason to test for it ...

---

### Post by dino99 on 2012-05-06
you need to:

- purge (via synaptic) the nvidia installed packages
- have dkms installed
- the kernel headers (2) installed
- the xorg-edgers ppa activated : after updating, select xserver-xorg-core 2:1.12.1 & nvidia-current for installation
- then deactivate edgers ppa and update again

- log out/in

does not get trouble here with a 8500gt on Precise i386

---

### Post by markbl on 2012-05-07
> **smurphy said:**
> If all the drivers are core-dumping, I suspect that the fault is somewhere else to look at. Not the driver.

Didn't have these problems on 11.10. I have switched to the nouveau driver and all is well now. Seems to work very well in 3D etc actually. I have xorg-edgers enabled so I will wait until I eventually see another nvidia update and maybe try that.

---

