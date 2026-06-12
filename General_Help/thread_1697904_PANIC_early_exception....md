---
title: "PANIC: early exception..."
date: 2011-03-01
forum: General Help
---

### Post by kunigami on 2011-03-01
Hi all,

I just ran regular updates. After reboot I got the following error:
 
> PANIC: early exception 06 rip 10?ffffffff8186aa5d error 0 cr2 0

It seems a kernel panic. Any ideas on how to solve it? I can't even login to try any commands...

Thanks!

---

### Post by vivek.pandey on 2011-03-01
have you tried loging in recovery mode?

---

### Post by kunigami on 2011-03-01
Hi,

I managed to invoke GRUB which showed me three versions of kernel with the option to boot in recovery mode. All of them ended up in the same message I posted before.

Afterall it doesn't seem an error related to kernel.

I was to run memcheck selecting the proper option on GRUB, but now not even GRUB is loading anymore :(

---

### Post by vivek.pandey on 2011-03-01
do you have a live cd? try booting in using a live cd.. see if the problem persists

---

### Post by matt_symes on 2011-03-01
Hi

I would start by eliminating hardware issues. Check the drives SMART status, run fsck and memory test from a LiveCD. Make sure there is no overheating and have a physical inspection of the internals of the PC checking for loose cables, unseated boards etc. 

After that i would then check the software.

Kind regards

---

### Post by kunigami on 2011-03-02
That's weird, I can't even boot from the liveCD! The image bellow appears, but after that I get that error message.

I've checked for loose cables, checked the temperature on hardware monitoring at BIOS, and all seem ok :(

[IMG]https://help.ubuntu.com/community/Installation/FromUSBStickQuick?action=AttachFile&do=get&target=Fig02a.png[/IMG]

---

### Post by matt_symes on 2011-03-02
Hi

Can you try the LiveCD on a different computer. That will help eliminate it as a problem. Get it to self check the CD disc for errors.

Also you could try a LiveUSB and see if that boots with Ubuntu and/or a different distribution.

I would be thinking it might be a hardware issue at the moment and investigate that further. However with out further investigation that is all supposition.

Does your PC have any hardware self tests it can run similar to Dell diagnostic partition ?

Kind regards

---

### Post by NZJon on 2011-04-12
Hi there.

I seem to have very similar symptoms. When I boot up my PC (a "home built" machine -- Asus M2N-SLI Deluxe mobo, and Phenom II X 945 CPU) it fails to get (much) past GRUB. I get:

```

PANIC: early exception 06 rip 10:ffffffff81dd5245 error0 cr2 0

```

I have tried the following:

- booting from an Ubuntu 10.10 AMD64 live CD -- failed
- booting from an Ubuntu 10.10 x386 live CD -- failed
- booting from an Ubuntu 10.10 AMD64 live USB stick -- failed
- booting from an Ubuntu 10.10 x836 live USB stick -- failed
- booting from a SysRescueCD -- i386 boots up OK, AMD64 kernel failes to boot
- booting from an Ubuntu 9.04 i386 live CD - boots OK
- booting from an Ubuntu 9.04 AMD64 live CD -- fails

So, it seems to me that, for some reason, my mobo+CPU combination just wont boot AMD64 images/kernels. Seems weird...

I'm going to replace the CPU with an older Athlon I have. 

If anyone has any ideas what could be going on, it'd be great to hear about them!!

Cheers,

   Jon

---

### Post by kunigami on 2011-04-13
Hi,

I decided to send it to the maintenance and they discovered that there was a problem with one of my RAM components. So, If you have more than one module or an spare one, perform some tests to check if without one of the current modules the system boots.

---

### Post by rajan on 2011-05-27
Thanks Kunigami! your post saved me! 

[http://ubuntuforums.org/showthread.php?p=10871078#post10871078](http://ubuntuforums.org/showthread.php?p=10871078#post10871078)

too bad my comp is useless though ....

---

