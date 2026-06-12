---
title: "Total beginner completely stuck..."
date: 2012-09-27
forum: General Help
---

### Post by Kaicul01 on 2012-09-27
Hi,
I apologize in advance for my ignorance, this is my first time trying Ubuntu and I am utterly stuck here, maybe someone can point me in the right direction? (I've tried searching the forums but can't figure this out)
I have installed 12.04 on a Samsung NC10 from a USB using Wubi.
When I installed I overwrote Windows (bad move I guess) and Ubuntu loaded fine. However I am unable to connect to the internet via WiFi and/or ethernet and have tried playing around with network settings to no avail.
When booting I see the following message briefly: 

waiting for /dev/mapper/cryptswap1 is not ready yet or is not present

Then takes me to login and seems to load Ubuntu fine, but can't get online at all. Could this be a driver issue or maybe a bad installation? 

Any help greatly appreciated and thanks for your patience.

---

### Post by jerrrys on 2012-09-27
Wubi runs ubuntu inside windows.  If you wiped windows install from your HDD, this is a regular install and I would worry about getting windows reinstalled first.  Maybe with your restore disk.

---

### Post by jingaling on 2012-09-27
Hi,

Something must have really gone wrong for Wubi yo have removed Windows. If your intention to dual boot? If that's the case then I would install Windows fresh and then Ubuntu next to it (without Wubi as it effects performance). I wrote a guide on how I partition Ubuntu for a dual boot on my blog. Here is a link:

[http://refugeeks.com/RefuGeeks/2012/06/how-to-correctly-partition-ubuntu/](http://refugeeks.com/RefuGeeks/2012/06/how-to-correctly-partition-ubuntu/)

If that isn't what you want then I would suggest a re-install of Ubuntu as it's clearly messed up. However, this may be a driver issue (which I doubt as the Samsung netbooks use a broadcom Wi-Fi chip I believe).

To make sure all your drivers work out of the box with Ubuntu, boot to a live CD. If everything works then you know it's your install that's messed up rather than a driver issue.

Hope this helps, let us know how you get on.

Oh, and welcome to the community! :)

Jing

---

### Post by Kaicul01 on 2012-09-27
Thanks jerrrys & jingaling,
 
Really appreciate you taking the time to reply...
Yeah I think I will try reinstall windows from recovery disc, and start with a fresh Ubuntu install, thanks for the instructions for partitioning as well.
 
I'll post my progress as asap.
 
Cheers

---

### Post by Sonsum on 2012-09-27
I have a Samsung N120 (which is just a slightly newer version of the NC10). Once you get everything installed, I'll be happy to help you get the hotkeys and other stuff working.

---

### Post by Kaicul01 on 2012-10-01
Hiya, so I managed to reinstall Windows (from disc) and then reinstalled Ubuntu (using the Windows installer) as well - I think that when I created the bootable USB that there were issues with that. 
Both boot fine, no issues with Windows, Ubuntu seems to run quite slow though...very slow actually compared to Windows. My NC10 only has 1gb ram which I will upgrade soon, but I wonder if anyone has any ideas as to why this could be?

Sonsum, I would appreciate any help with the hotkey setup if you don't mind, thanks!

---

### Post by mörgæs on 2012-10-01
Ubuntu in a Windows installer (Wubi) is always slow compared to a real dual-boot (having the systems next to each other). Wubi is mostly for short-time testing.

---

### Post by Kaicul01 on 2012-10-03
I have been trying to to set up a dual boot installation without success.
I have downloaded the Ubuntu .iso, and followed the instructions for writing a disc image using Infra Recorder. It seems that the .iso is not being written to the disc (although the process appears to be complete), so when I reboot and try and boot from the disc, it still loads windows. I checked the .iso MD5 hash to make sure it's good and that seems fine. Many thanks for any suggestions...

---

### Post by cway00 on 2012-10-03
Based on your quote

> **Kaicul01 said:**
> 
Sonsum, I would appreciate any help with the hotkey setup if you don't mind, thanks!

This site below will give you a guide on more information on hot-keys setup 
```

http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/

```

---

### Post by lwalper on 2012-10-03
Check your boot sequence in the BIOS. As your machine starts, try pressing the Esc key, or Del key, or as on my Gateway laptop, the F2 key. That will open the BIOS window and allow you to make changes. Look for the boot sequence and change it to boot from CD as the first option - then the hard disk - or if you're going to use the USB stick for booting you might put that one on the top.

---

### Post by Kaicul01 on 2012-10-06
Got it sorted thanks for your advice everyone :-)

---

### Post by Sonsum on 2012-10-07
In case you haven't figured it out already, [this]("https://launchpad.net/~voria/+archive/ppa") is the best way to get a Samsung device working perfectly under linux.

---

### Post by will1982 on 2012-10-07
> **mörgæs said:**
> Ubuntu in a Windows installer (Wubi) is always slow compared to a real dual-boot (having the systems next to each other). Wubi is mostly for short-time testing.

According to Wikipedia, only performance detractor  is a slight hit to disk writing performance.

Not that I actually know, last time I used Wubi was ages ago :3

---

### Post by jingaling on 2012-10-07
I think we all know that Wikipedia is usually as accurate as performing key hole surgery with a chain saw. :)

---

### Post by will1982 on 2012-10-07
> **jingaling said:**
> I think we all know that Wikipedia is usually as accurate as performing key hole surgery with a chain saw. :)

xD

You're right, I checked the sources, and they were dead links -.-

---

