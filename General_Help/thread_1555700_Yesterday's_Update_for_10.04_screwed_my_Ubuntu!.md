---
title: "Yesterday's Update for 10.04 screwed my Ubuntu!"
date: 2010-08-18
forum: General Help
---

### Post by ghuqu on 2010-08-18
Hey guys, I'm frantic here. I'm running the 32-bit Ubuntu 10.04 LTS just to start things off here. Yesterday I was notified of an update available, so I ran it never thinking I would ever have a problem. I was away from my computer all day, and when I came back, the screen was black and showed some coding and at the bottom mentioned something about cupsd missing or something...

I rebooted figuring I'd take care of that stuff later. Now instead of going to the splash screen when it comes back on, it's just a blank screen. Sometimes I can hit ctrl+alt+delete and it'll restart, and sometime I have to manually hardboot. Any idea why Ubuntu will not boot as normal? Anyone else's system get screwed after yesterday's update? 

Is there maybe a way to go back to last known working configuration on Ubuntu?

Also, I can access my harddrive with 10.04 installed on a live USB, so if I need to do config changes that is possible. Please help!

---

### Post by clhsharky on 2010-08-18
ghuqu

> last known working configuration
Thats windows, you need to learn the Linux way.
> Is there maybe a way to go back on Ubuntu?
Yes, if you had done a system back up before hand.
Backintime is a good backup app.
I have no ideal what went wrong, hopefully some one can help.

Sharky

---

### Post by malangaman on 2010-08-18
can you see the Grub2 menu?
if so choose an earlier kernel to boot from.

---

### Post by cro_409 on 2010-08-18
I am also having this problem, but I just upgraded to 10.04 late last night after having the same issues with 9.10.

Mine occurs everytime I try to open a program installed off the internet and not the synaptic or software update. Google Earth, for example causes this every time. 

I found a work-around in my BIOS. I put my 9.10 disc in that allows me to boot to the recovery partition and then i command it to reboot, take the disc out and then enter the BIOS and have it boot straight from the largest partition, which is my Ubuntu 10.04. 

Unforunately I doubt anyone still has this BIOS, its a few years old on a Dell desktop I got for free and I doubt has ever had it's BIOS updated.

I don't know if the same update went out for 9.10 but I didn't have this problem before the other day, and this was what prompted me to upgrade to 10.04.

I will try to check my BIOS version in case it will help anyone. If anyone has that BIOS version and wants to know my steps, I can duplicate the problem and write a step-by-step in how I get around it.

---

### Post by ghuqu on 2010-08-18
The Grub 2 menu has not shown ever since I've installed 10.04. It's always gone straight to the splash screen. I've had a feeling it's been the kernel update. I'm going to go into grub and see if I can't force it to load the previous version, and reboot my computer.

---

### Post by ghuqu on 2010-08-18
Well that didn't work

---

### Post by malangaman on 2010-08-19
If you can access the drive through usb, you could try re-installing grub see this link;
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by x C0MMAND0 x on 2010-08-19
You could try installing GRUB from a live CD.  Note this is an older link I'm not sure if it will be current with a 10.04 system, but I don't see why GRUB wouldn't work.   

Link > [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") <

---

