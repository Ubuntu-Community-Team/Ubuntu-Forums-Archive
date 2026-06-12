---
title: "LiveCD will not boot, alternate CD installs but new system won't boot."
date: 2010-04-15
forum: General Help
---

### Post by ardchoille42 on 2010-04-15
I have been using Ubuntu since 2005 and I use Ubuntu because it has always been rock-solid and trouble-free for me, I love this distro. I build my own machines because this allows me to pick and choose hardware that I already know works with Ubuntu. My current machine uses an AMD Sempron 2800 CPU, 1gb RAM, 2 x 60gb hard drives, 2 x DVD+/- R/RW drives, nVidia GeForce 6200+ video card. I built this machine and it has been serving me very well since Ubuntu 6.06 (Dapper Drake) and has been able to boot every Ubuntu LiveCD and alternate CD since Ubuntu 6.06 (Dapper Drake).

This is what I get when I boot the current Ubuntu 10.04 b2 LiveCD:
I downloaded Ubuntu 10.04 beta 2, confirmed the downloaded .iso file against the md5sum, burned the image to cd with brasero and check the CD integrity from the LiveCDmenu

Boot from CD
1.Screen with Ubuntu logo in the center and a keyboard looking thing at the bottom.
2. I have to press the ESC key to get to the language screen (took me three reboots to figure this out)
3. I get to the main menu that asks to boot to desktop, install Ubuntu, etc.
4. I chose to "try Ubuntu" and then there is a screen with the Ubuntu logo in the center and five dots below it
5. The dots serve as a type of progress bar but the dots end up all "filling up" and the screen sticks there until I restart the machine (i waited a half hour on two occasions), I can never get to the live desktop session

So, I tried downloading and installing from the alternate CD and the install completed successfully. I kinda like the UI of the alternate CD anyway. Upon reboot, to use the newly installed system, I was taken through the exact same thing that appears in step 5 above.

The LiveCD will not boot to desktop. The alternate CD will boot and install, but the newly installed system will not boot. Once the screen "freezes" nothing on the keyboard works at all.

Is this a known problem that is being worked on? I need to find a way to fix this problem because I flat refuse to give up this awesome distro. I haven't tried upgrading from 9.10 yet because I have a feeling it won't boot either. I'm thinking this is either a kernel problem or an nVidia problem because I just reinstalled 9.10 on this machine last night and it's working fine.

---

### Post by House101 on 2010-04-15
Check the md5sum hash (I'm pretty sure I didn't spell that right), but make a new cd and check it. Also, it's a beta version, it's gonna have problems, report it on the bug site for beta and wait a few more days for the full version to come out bug-free

---

### Post by ardchoille42 on 2010-04-15
> **House101 said:**
> Check the md5sum hash (I'm pretty sure I didn't spell that right), but make a new cd and check it.

Sorry about that, you replied before I had a chance to add that info to my original post. Also, I have tried this from two burned cd's and they both have the same problem. Desktop and alternate cd's all have this same problem.

---

### Post by House101 on 2010-04-15
Go to karmic instead (or go back to dapper) and in a week or two the stable LTS is gonna be released. It's likely to be a nvidia problem, they were messing with the nvidia drivers and integrating extra support, but you're using the beta. How far will it boot? Can you get to the boot menu?

---

### Post by ardchoille42 on 2010-04-15
> **House101 said:**
> Go to karmic instead (or go back to dapper) and in a week or two the stable LTS is gonna be released. It's likely to be a nvidia problem, they were messing with the nvidia drivers and integrating extra support, but you're using the beta. How far will it boot? Can you get to the boot menu?

The process I experienced is outlined in my original post, see the "Boot from CD" section.

---

### Post by House101 on 2010-04-15
Sorry, I meant the alternate boot, you said it installs, but freezes on boot, can you make it to the boot menu for that?

---

### Post by ardchoille42 on 2010-04-15
> **House101 said:**
> Sorry, I meant the alternate boot, you said it installs, but freezes on boot, can you make it to the boot menu for that?

Oh, I misunderstood your reply. The alternate cd installs successfully. But, upon reboot, the new system only shows the boot screen with the Ubuntu logo in the center, and five dots under it, and goes no further than that - GDM never apears. Seems it has the same problems the live session had in trying to get to the desktop session.

---

### Post by House101 on 2010-04-16
Try getting to the boot menu. It's likely a messup of the graphics, I've had nvidia problems and if you you start in recovery mode it should boot.

---

### Post by ardchoille42 on 2010-04-19
> **House101 said:**
> Try getting to the boot menu. It's likely a messup of the graphics, I've had nvidia problems and if you you start in recovery mode it should boot.

Ok, but what do I need to do to get it to boot and work successfully without recovery mode?

---

