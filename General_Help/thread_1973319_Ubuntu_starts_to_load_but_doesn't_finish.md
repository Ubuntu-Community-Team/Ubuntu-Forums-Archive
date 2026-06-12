---
title: "Ubuntu starts to load but doesn't finish"
date: 2012-05-04
forum: General Help
---

### Post by aldago on 2012-05-04
I have tried to run ubuntu live disk on two WinXP machines with no success. The boot starts (on the start screen I see an image above 4 dots which light up progressively) but then the screen goes dark an nothing happens. I burned ubuntu-12.04-desktop-i386.iso. Is this the wrong version for a live disk?

---

### Post by MG&amp;TL on 2012-05-04
Hardware specifications, please. Also if you saw any errors at all, they'd be useful as well. :)

---

### Post by aldago on 2012-05-04
No error messages. The screen goes black and I have to push the power button on the computer to reboot. 

System specs:

OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
System Type	X86-based PC
Processor	x86 Family 15 Model 6 Stepping 4 GenuineIntel ~3201 Mhz
Total Physical Memory	1,536.00 MB
Available Physical Memory	575.90 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB

---

### Post by MG&amp;TL on 2012-05-04
That should start, if nothing else. 

On my (very similiar) system, a CD takes ages to load. How long have you left it for? (Incidentally, if you do installs a lot, a USB is much better).

---

### Post by aldago on 2012-05-04
I've left it on for a couple of minutes (which seems like ages). I'll run it again, go have dinner, and see if it was just a matter of time.

---

### Post by aldago on 2012-05-04
Had a great dinner but came back to a black screen and had to power-off to reboot the computer. I alsotried to use the disk on the below system:

OS Name	Microsoft Windows XP Professional
Version	5.1.2600 Service Pack 3 Build 2600
System Manufacturer	HP Pavilion 061
System Model	PS583AA-ABA a1020n
System Type	X86-based PC
Processor	x86 Family 15 Model 4 Stepping 1 GenuineIntel ~3065 Mhz
Total Physical Memory	2,560.00 MB
Available Physical Memory	2.00 GB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB

I also downloaded and tried Kubuntu 12.04 with the same result. Could the problem be in the boot options? I'm fairly new to this so I don't know what to do with those. Any other ideas??

---

### Post by layers on 2012-05-04
sometimes I have the same problem in bed




but I've seen a pavilion 061 run 11.04 without any problems.

---

### Post by mansonfan78 on 2012-05-05
Are the two machines you tried it on on the same network?  If so, there might be a problem with ubuntu discovering the network at bootup, causing it to hang (especially if it's a password-protected network).  You could try disconnecting your computer and/or router and then see if it loads any further.

---

### Post by GreatDanton on 2012-05-05
I think you should try to install from USB, because sometimes Cd-s are not properly burned. When I was installing my system I sometimes couldn't install Linux from Cd, because Cd was not properly burned (around 20% of the time), however I was able to install Linux from USB (100% in my case).

Also if you don't know how to make live USB (because of Windows :) ), you can try to burn another CD and see if that solves your problem.

I hope this help.

---

### Post by whiskers751 on 2012-05-05
Yep sounds like a CD problem...

---

### Post by aldago on 2012-05-05
It may be the CD but I've burned live CDs and I've run versions of ubuntu and kubuntu from disk since their inceptions and before that Knoppix. So, I've run many live versions. But, just as an exercize, I guess I'll try the USB approach. I'll be back with the results. Thanks all for the replies.

---

### Post by aldago on 2012-05-05
I guess it is a CD problem. I put kubuntu 12.04 on a flash drive and it works "live" like a charm. Anyone have any ideas on how to troubleshoot the "CD problem?" I boot lots of live disks that I've made the same way (download iso burn with Imgburn)with no problem. I'd sure like to figure out what this problem is.

---

### Post by MG&amp;TL on 2012-05-05
> **aldago said:**
> I guess it is a CD problem. I put kubuntu 12.04 on a flash drive and it works "live" like a charm. Anyone have any ideas on how to troubleshoot the "CD problem?" I boot lots of live disks that I've made the same way (download iso burn with Imgburn)with no problem. I'd sure like to figure out what this problem is.

Have you check and/or md5-summed the images/discs?

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by aldago on 2012-05-06
Well,
I'm happy to report that both CDs suddenly started working and now I get live Ubuntu or Kubuntu. Go figure. Don't know what caused it but all's well and happy now. Thanks everyone for your help.

---

### Post by GreatDanton on 2012-05-06
computer troll ;)

---

