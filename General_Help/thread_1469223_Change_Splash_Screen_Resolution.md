---
title: "Change Splash Screen Resolution?"
date: 2010-05-02
forum: General Help
---

### Post by sting547 on 2010-05-02
I've recently upgraded to Ubuntu 10.04 LTS. When I boot up I see this:

[http://jantechblog.files.wordpress.com/2010/03/ubuntu1004branding-large_004.jpg](http://jantechblog.files.wordpress.com/2010/03/ubuntu1004branding-large_004.jpg)

in a very low resolution

At the login screen and on the desktop my resolution is 1680 x 1080

Is there a way to make the splash screen that resolution as well?

Thanks in advance

---

### Post by WorMzy on 2010-05-02
Have you installed propriety drivers for your graphics card? If so, disable them, then plymouth (the new boot splash) should automatically detect your resolution. Disabling the propriety drivers will disable any desktop effects you have running (such as anything graphical to do with compiz).

Otherwise, try running 'sudo dpkg-reconfigure plymouth'.

---

### Post by Ginsu543 on 2010-05-02
If you are running nVidia graphics, there is apparently a bug with the nVidia video drivers which lowers the resolution of Plymouth. This is how I got around it:

1) Open Terminal
2) Run: sudo gedit /etc/grub.d/00_header
3) Go to line #103, which should read: set gfxmode=${GRUB_GFXMODE}
4) Add the following to the next line (#104): set gfxpayload=*length*x*width* (where *length* and *width* are the dimensions of your screen)
5) Save
6) In Terminal, run: sudo update-grub

That should do it. If set gfxpayload=*length*x*width* doesn't work, then try set gfxpayload=keep.

---

### Post by sunk8 on 2010-05-02
I think u can change it using the GUI app:

startup-manager.

;-)

---

### Post by WorMzy on 2010-05-02
Just to clarify, by length you mean height, right?

I'll try this.

---

### Post by WorMzy on 2010-05-02
It certainly seems to have improved things, (using set gfxpayload=1440x900), but the quality still looks awful. I wonder if sticking x32 on the end of that would make any difference.


EDIT: It didn't.

---

### Post by lavinog on 2010-05-02
> **sunk8 said:**
> I think u can change it using the GUI app:

startup-manager.

;-)

I don't think startup-manager has been modified for plymouth yet.

---

### Post by Ginsu543 on 2010-05-02
@WorMzy
By *length* and *width*, I mean *width* and *height*, respectively (sorry about the confusing language). Also, I forgot to ask whether you have already changed the GRUB_GFXMODE setting in your /etc/default/grub file.

My grub file looks like this:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXMODE=1600x1200**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Notice the section in bold. The resolution of the grub splash screen must be in 4:3 ratio. I'm wondering whether that is why your splash doesn't look as nice since 1440x900 is in 16:10 ratio. I'd try maybe 1200x900. I set my gfxpayload to the same resolution as my GRUB_GFXMODE.

---

### Post by WorMzy on 2010-05-02
I'm using grub legacy, and I think it only supports vga modes. Unfortunately, using vgamodes makes plymouth look even worse.

I'll try 1200x900 though. For the two or three seconds that Ubuntu is booting, it'd be nice to have something pretty to look at.

EDIT: Nope, same. I'm starting to wonder if this change really did make any difference, or whether I just thought it had due to sleep deprivation.

I think I'll head to bed and see if I can find a solution this afternoon.

---

### Post by Ginsu543 on 2010-05-02
I didn't know you could even run Plymouth with grub-legacy. Are you sure the two are compatible? Maybe Plymouth looks bad for you because you only have vga modes available in grub-legacy.

---

### Post by lavinog on 2010-05-02
If you are using grub-legacy, you must have upgraded from 9.04 to 9.10 to 10.04...in which case you likely didn't start with ext4 file systems.  You could get a speed boost if you do a clean install...which should address the grub-legacy issue.

---

### Post by Ginsu543 on 2010-05-02
That's a good point. I always do a clean install whenever I upgrade, so I didn't even think about problems that could occur from dist-upgrading.

---

### Post by godsiem on 2010-05-02
Hi,

I have also come upon this problem... I managed to solve it following this tutorial, the first approach:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

I hope it helps you!

Cheers!

---

### Post by meho_r on 2010-05-02
> **lavinog said:**
> I don't think startup-manager has been modified for plymouth yet.

But it still works though. After unsuccessfully trying to sort this issue out, at the end I used startup-manager for setting plymouth resolution (not 1440x900, which I use, but 1280x1024: not ideal since this is not a right ratio, but still better than 640x480). If someone finds out how to use native ratio (16:10 for 1440x900) or tested this resolution with the approach by softpedia godsiem mentioned in the previous post, please post here.

---

### Post by olalaaa on 2010-10-12
I have in that _line 103_ of the file **00_header** something slightly *different* :

```
set gfxmode=1024x768
```

so I will change it here into

```
set gfxmode=1366x768
```

because my laptop screen has native resolution 1366x768.

If I have thereafter better boot screen resolution I will post again here for you.

My system is Lucid Lynx x64, and I have a NVIDIA GeForce on it ( with Lynx updated from Ubuntu Hardy, not a clean install ).

---

### Post by olalaaa on 2010-10-12
Everything is almost fine (the image with "loading" points seems to be a little bit too wide, and the list with kernels installed became somehow narrowed...)

---

