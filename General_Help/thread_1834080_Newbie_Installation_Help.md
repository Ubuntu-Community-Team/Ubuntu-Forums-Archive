---
title: "Newbie Installation Help"
date: 2011-08-27
forum: General Help
---

### Post by katsuexe on 2011-08-27
Hi, this is my first time using Linux ever. And I have a problem and no clue of what to do.

I have a Compaq Presario SR1720NX. It was given to me with Windows XP. It worked fine in that I could use the Internet, use flash and play games, create documents and save etc...

Except for some reason it would download to another partition on the hard drive and say that I didn't have any space to download stuff, even though the drive had plenty of space. Also I couldn't connect to windows update. Moreover when it booted it had 2 versions of Windows XP but only one version worked.

I thought it was a virus but Microsoft Security Essentials was running fine.  I was able to update MSE by transferring over the update files on a flash drive.

I emailed a Windows tech and they gave me a few solutions to try but nothing worked. My solution was to just delete everything by doing an a clean OS installation. I had (have) no money or a recovery disc, so I choose Ubuntu Linux of course. 

I followed the instructions on the site and created a live CD. It worked, booted, and installed just as planned.

I updated the computer and restarted again.

I gave it a few minutes to load. Then I clicked on the Libre Office App. My computer instantly froze. After a hour of waiting, i held the power button and manually turned off the computer. When it restarted, without the CD, it went directly to the Grub Rescue prompt. 

I restarted again and the same thing.

I figured I would just reinstall the OS, but when it boots from the CD it gets stuck at the Ubuntu screen and appears to be loading forever, or at least over an hour.

I tried pressing a bunch of keys to see if options or another menu would pop up but nothing. So basically I get the grub rescue prompt or Ubuntu screen, even though everything installed fine.

 I've been at this for hours already searching these forums and online for help.

What the hell is going on?!!

Any help or advice would be much appreciated.
Thanks a lot in Advance

PS: Without this OS, the computer cannot be used at all.

---

### Post by artantaaa on 2011-08-27
I hate to break it to you, but your onboard graphics chipset, the ATI Radeon Xpress 200, is not supported by Ubuntu. You can read about it at:
[https://help.ubuntu.com/community/RadeonDriver ]("https://help.ubuntu.com/community/RadeonDriver")
To get this computer to run Ubuntu, you will need a new graphics card. It doesn't have to be anything new or expensive, just compatible with Linux. I would get the cheapest Nvidia PCIExpress card I could find for it. Maybe a 8400gs (about 20$)

---

### Post by Quackers on 2011-08-27
You could try the nomodeset boot option as described below

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

