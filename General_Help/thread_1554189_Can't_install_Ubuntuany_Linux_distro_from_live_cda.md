---
title: "Can't install Ubuntu/any Linux distro from live cd/alternate cd/usb !!"
date: 2010-08-16
forum: General Help
---

### Post by apoorvumang on 2010-08-16
Since this is a really weird problem, I'll write about it from when it started.
Ubuntu (10.04) was working great on my computer. Then I tried running a game called Unreal Tournament through wine. It didn't run due to some graphics problem, so I tried messing around with *it's* graphics settings (Note: Not the computer's), and was finally able to get it to run. However, the game crashed after about 15 seconds and the computer restarted.

After that, whenever it reached the Ubuntu splash screen with those orange and white dots, the computer would restart again. I tried booting in rescue mode - no luck. Then I tried booting in failsafeX mode with the option "Start Ubuntu in low graphics mode just this once" (not the exact statement, something like that). That worked, and I was able to boot into Ubuntu, but of course without all the nice graphics stuff. 

Then I thought I would just backup my current Ubuntu install and then reinstall Ubuntu. After backing up, I tried booting through the live CD. It booted up, but the computer just restarted after some time - I tried this several times, and each time the computer would restart after some random point. (Another thing to note here might be that if I tried to change the desktop effects in Appearance, it would definitely restart at that point (although it would restart randomly also))

So I tried using the install option of the live CD. I was able to navigate through all of the steps without the computer restarting, but when it came to copying files and stuff, it restarted again. On my second try, I was *almost* able to complete the install - only the last 1 percent or so was left - but ... you know what happened - it restarted. 

My next try was using the alternate CD. It never restarted during the installation. Instead, this error came:
```
file:///cdrom/pool/main/n/newt/libnewt0.52_0.52.10-4ubuntu1_i386.deb was corrupt
```
[NOTE: This was from the 9.1 Karmic CD, but the 10.04 CD also showed the same, or at least similar error]

followed by several similar errors (and then it said Ubuntu couldn't be installed).
So I ran an integrity check on the disc which *failed*(strange, since I had just made the disc), showing the exact same error. However, when I tried using the CD on another computer, it worked flawlessly.

My CD drive has given me problems before(not this kind, though. I've installed Ubuntu from CD before). So I tried booting with a pen drive (which I have done at least a million times), but this time it gave me this error 
```
Boot Error
```
Really strange.

So, I'm out of options now. Need help desperately!!

A few points to note:
1. I tried booting from the live CD after disconnecting the hard drive, but the problem persisted (ie it restarted for no reason after some time).
2. I've tried the same thing with other Linux distros (opensolaris, mandriva), with the same results - random restarting of the computer and inability to install the OS on the computer.
3. My original install got wiped out during one of my tries to reinstall Ubuntu, so I can't boot the computer from hard drive
4. It all started due to some graphics problem (or so I think). Also, changing the desktop effects to normal or high caused an instant restart on the Ubuntu, Opensolaris, Mandriva Live CD.

---

### Post by apoorvumang on 2010-08-16
System specs :
Intel core 2 duo processor, 2gb ram, Intel integrated G45 graphics card, 250 gb SATA seagate hdd

---

### Post by drdanielfc on 2010-08-16
Dumb question perhaps but is your pen drive listed as first boot priority?

---

