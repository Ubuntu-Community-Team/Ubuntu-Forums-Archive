---
title: "Installed nVidea proprietry driver, error on startup"
date: 2010-08-13
forum: General Help
---

### Post by TygerTung on 2010-08-13
Hi,

I just got this high spec computer (Dell Dimension 4550, P4 2.6gHz, didn't come with any ram or HDD, but I pinched the two crappiest 500Mb sticks of DDR400 out of my other computer to give me a whopping 1000Gb of ram, and I whacked in a 40Gb hard drive I had lying around. It has this '	Card, Graphic, NV17, FULL HEIGHT..., COST REDUCED..., DIMENSION...' (That is off the Dell Website).)

The computer was free, and it looks quite good. Since the graphics card has an S Video output I was gonna hook it up to the TV so I can use it to watch video's on demand and DiVX movies and  perhaps DVD's as usually when I'm watching one, halfway through it craps out, and if it's on the computer it will probably be alright due to the better quality drive.

Anyway after all that warble, here is my problem.

I put Xubuntu on it for maximum performance, as it's quite high spec, but not the best spec around.

I hit the button to install the proprietary graphics driver and it installed fine, but when I restarted the computer, it came up with this error:

**Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting***
(EE) Screens(s) found, but none have a useable configuration.

Any help in how to fix this would be great.

Cheers,

Sam

---

### Post by wojox on 2010-08-13
Try

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

Reconfigure from there.

BTW 500Mb + 500Mb = 1Gb (1000Gb had me jealous).

---

### Post by TygerTung on 2010-08-13
Yes, that comes up with the same built in window under the system menu and it comes up withan error box:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

How do I fix that?

---

### Post by TygerTung on 2010-08-14
I thought I'd just bump this thread to give it some more attention as it is probably quite a few pages back by now

---

### Post by wojox on 2010-08-14
Yeah I forgot about ya. :)

When you run 

```
sudo nvidia-xconfig
```

It should recreate a new xorg.conf and then reboot and then 

```
gksudo nvidia-settings
```

Let's you configure everything as root so the settings stay persistent after every reboot.

---

### Post by TygerTung on 2010-08-14
Nah when I create a new xorg.conf file it still has a problem when I restart it.

Is there a problem with the driver somehow and I need to get a different one?

---

### Post by wojox on 2010-08-14
What number driver did you install?

---

### Post by wojox on 2010-08-14
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1468372")

---

### Post by Meizirkki on 2010-08-14
I have had this problem too. It seems that the kernel source doesn't get automatically installed.

These should fix it:

```
sudo apt-get install linux-source linux-headers-`uname -r`

sudo dpkg-reconfigure nvidia-current
```

and reboot

---

### Post by TygerTung on 2010-08-14
Thanks man, The first line worked, but it didn't like the second. However it still fixed the problem!!!

Cheers!

---

