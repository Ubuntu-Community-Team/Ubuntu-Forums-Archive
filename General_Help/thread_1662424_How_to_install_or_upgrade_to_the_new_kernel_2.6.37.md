---
title: "How to install or upgrade to the new kernel 2.6.37?"
date: 2011-01-08
forum: General Help
---

### Post by ayoubson on 2011-01-08
Hi, can someone please explain in simple terms how to safely upgrade to the new kernel (2.6.37)?

---

### Post by Bucky Ball on 2011-01-08
Why would you want to??? That would really not be advisable for a new user unless you intend to go on a very steep learning curve.  The latest is NOT necessarily the greatest in Ubuntu world. That is a Windows myth.

If you REALLY want to upgrade to that kernel there is an extremely easy and safe way to do it, but there's nothing safe about that kernel at the moment as it's still under development! Let me know and I'll let you know but I would seriously think about it doing it unless you are a coding monster or developer looking to actively troubleshoot it, pre-release.

The reason I have not posted you the link is that I don't want to be held responsible for bricking your machine! After this info, if you still want to do that upgrade, then let me know and I'll post you the link. ;)

The Natty Narwhal discussion and testing forum:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by James78 on 2011-01-08
Download the 3 deb packages from these pages and install them. They're originally made for Ubuntu Natty. I'm using them right now and it's working great. :)
```
cd ~/Downloads
sudo dpkg -i *.deb
```

[http://packages.ubuntu.com/natty/linux-image-2.6.37-12-generic](http://packages.ubuntu.com/natty/linux-image-2.6.37-12-generic)
[http://packages.ubuntu.com/natty/linux-headers-2.6.37-12](http://packages.ubuntu.com/natty/linux-headers-2.6.37-12)
[http://packages.ubuntu.com/natty/linux-headers-2.6.37-12-generic](http://packages.ubuntu.com/natty/linux-headers-2.6.37-12-generic)

As previous person said, I am not responsible for anything that happens to you or your computer that results from doing this.

---

### Post by Bucky Ball on 2011-01-08
Much easier here. All debs and a click away. You shouldn't need three packages. Headers and image only for i386 or AMD64.

[http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/)

Good luck cos it might not be working after the next update. And nor would it be expected to. ;)

Word has it the Natty release will be using 2.6.38-**.

---

### Post by ayoubson on 2011-01-08
Thanks very much guys for the quick replies. The Ubuntu community is so helpful :D. Thanks for your advice regarding the risks. Due to this I will not upgrade for now, I may try to do this on a future experimental install which I do sometimes for learning purposes.

---

### Post by James78 on 2011-01-08
No problem! And I'd just like to make a little note to you. If your new kernel (2.6.37) doesn't work for any reason, you should be completely fine. You can have more than 1 kernel installed, and if you do install 2.6.37 and it doesn't work, you can simply boot to the normal one that does work. Not withstanding I'm sure there are other problems that can potentially happen, but you should be fine regardless. I have 3 total kernels (2.6.37, 2.6.36, and the normal one in the repos). If in doubt, you could try it on a virtual machine first.

Note: It's NEVER advisable to 'upgrade' or replace your regular kernel with a new one, or even for that matter to use a new one that's untested with this OS version, hence why the warning. Having 2 kernels, one being a failsafe is usually a good idea if you want to try new versions. 2.6.37 should also be faster than the current 2.6.35, due to internal differences (this is why I installed the new one; the older one was a little too slow and choppy)

Edit: It also appears that 2.6.37 is actually stable now!
[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by Bucky Ball on 2011-01-08
+1 James. I installed 2.6.36 last night and it killed my graphics and wireless. ATI graphics driver not ready yet. Boot back into 2.6.35 and all good. :)

---

### Post by end3rkid on 2011-01-18
Running 2.6.37. Very stable atm :).

---

### Post by zero7404 on 2011-01-23
> **James78 said:**
> Download the 3 deb packages from these pages and install them. They're originally made for Ubuntu Natty. I'm using them right now and it's working great. :)
```
cd ~/Downloads
sudo dpkg -i *.deb
```

[http://packages.ubuntu.com/natty/linux-image-2.6.37-12-generic](http://packages.ubuntu.com/natty/linux-image-2.6.37-12-generic)
[http://packages.ubuntu.com/natty/linux-headers-2.6.37-12](http://packages.ubuntu.com/natty/linux-headers-2.6.37-12)
[http://packages.ubuntu.com/natty/linux-headers-2.6.37-12-generic](http://packages.ubuntu.com/natty/linux-headers-2.6.37-12-generic)

As previous person said, I am not responsible for anything that happens to you or your computer that results from doing this.

i've done this and it appears to have installed properly, updated grub & can start ubuntu with this new kernel.

but x/gnome gui won't start, instead i get a login prompt that's not graphical).

can someone point me in the right direction to get it corrected ? i am running ubuntu 10.10 64-bit, on an HP Envy laptop. i upgraded the kernel to this version because the 2.6.35 kernel doesn't fully support my hardware (usb 3.0, broadcom wireless, ATI 5850 video, core i7), such that i cannot suspend the machine.

i suspend my computer 95% of the time, only shutdown or reboot if i make changes/updates or don't plan on using it for a while.

thanks in advance.

---

### Post by stanca on 2011-01-23
Why not the 2.6.38rc2 already? ;):) 
 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc2-natty/)

---

### Post by Bucky Ball on 2011-01-23
At the command prompt try:

startx

Does that get you to a desktop and if not what happens? If you run the recovery kernel do you get to the recovery options? If so, try the Failsafe X option. That will be low res but might at least get you to a desktop where you can figure things out and possibly download the correct graphics driver.

I'm guessing but the graphics could be the issue.

---

### Post by zero7404 on 2011-01-23
> **Bucky Ball said:**
> At the command prompt try:

startx

Does that get you to a desktop and if not what happens? If you run the recovery kernel do you get to the recovery options? If so, try the Failsafe X option. That will be low res but might at least get you to a desktop where you can figure things out and possibly download the correct graphics driver.

I'm guessing but the graphics could be the issue.

it likely is graphics. but at this point i'm going to back off a manual kernel update until i know more about compatibility issues. i removed the kernel using ubuntu tweak.

i would be better off fixing my suspend issue with workarounds on my current configuration. problem is some resources i've tried in the past don't seem to work ....
i speculate it's either usb 3 or the broadcom wireless, which are configured as out-of-the-box

---

### Post by Bucky Ball on 2011-01-23
Braodcom does work out of the box but you need to connect with a cable to download the firmware.

---

### Post by zero7404 on 2011-01-25
i was able to find a script that fixed my suspend issue ... 

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

content now and don't need to upgrade kernel.

---

