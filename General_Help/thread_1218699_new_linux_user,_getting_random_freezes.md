---
title: "new linux user, getting random freezes"
date: 2009-07-20
forum: General Help
---

### Post by gnomerocks on 2009-07-20
I am dual booting windows and Ubuntu 9.04, and for the most part i am loving linux. But, i seem to have run into a problem, and have no idea how to get it resolved.

My problem, is that my laptop, an acer aspire 5100, suddenly and without warning locks up, the screen goes to either a random solid color, or sometimes weird random patterns that look like areas of "tv static", and areas of black mingled together. I can only guess my video card, a ati radeon xpress 1100m, is freezing up inside linux. In windows it works fine, and i can leave it plugged in doing bit torrent downloads for *days*. I am pretty sure its not video card itself going bad since windows has no issues with it.

If helps to know, i do not, and have not, had desktop effects turned on since i first got Ubuntu installed

release 9.04 jaunty, kernel linux 2.6.28-14-generic, gnome 2.26.1

system:
memory: 3.0 GiB (2 sticks 2 GB DDR2 each, factory matched pair)
processor 0: AMD Turion 64 X2 Mobile Technology TL-50
processor 1: AMD Turion 64 X2 Mobile Technology TL-50

phoenix bios bios 3.13
Ubuntu is running on a primary partition, ext3, 2 GiB swap area primary partition.

Any help here would be great. It stinks that i can hardly use linux becuase of fear of locking up and loosing all my progress. Until i get this resolved, it is back to \/\/|/\/|)()\/\/$ i go.:sad:

---

### Post by philcamlin on 2009-07-20
id say driver issue ?

---

### Post by gnomerocks on 2009-07-20
system > administration > hardware drivers only is showing a alt driver for Atheros "madwifi" driver. No video driver listed.

---

### Post by t4thfavor on 2009-07-20
I have the same laptop, I use it rarely, but I never have an issue, is there a specific thing your doing when this happens?

I would be willing to make changes to my system to help you out with your problem. 

Are you using any external devices?

What extra programs do you have installed?

I run mine with Visual effects enabled and have no problems. 

Please let me know what's going on, and I can look into reproducing some of the problems.


I do know that it took 2 installs for mine to boot right, and I am NOT dual booting with Windows.

---

### Post by gnomerocks on 2009-07-20
> **t4thfavor said:**
> I have the same laptop, I use it rarely, but I never have an issue, is there a specific thing your doing when this happens?

I would be willing to make changes to my system to help you out with your problem. 

Are you using any external devices? _*mi brand wireless laser mouse, maxor OneTouch4Plus usb HHD, usb cooling pad*_

What extra programs do you have installed? _*7zip,rar, ubuntu restricted extras*_

I run mine with Visual effects enabled and have no problems. _*waste of cpu.*_

Please let me know what's going on, and I can look into reproducing some of the problems.


I do know that it took 2 installs for mine to boot right, and I am NOT dual booting with Windows.
one thing i forgot to mention is that it sometimes does this on startup, just as soon as the mouse cursor is visible and the desktop is still loading. Other times i can use linux for upwards of 6 hours no problem. As far as what i am doing when it happens, usually transmission downloads, or browsing in firefox. I keep about 5-8 tabs open all the time. Cpu usage and memory usage are around 20-25% cpu, and 8-10% memory during these "download parties".

---

### Post by t4thfavor on 2009-07-21
I will use mine a bit tonight, and see if I can make it happen, other than that I can tell you I have only factory installed ram, 1GB.

I put 2GB of Samsung pc4200 in it, and its been running for 

21:23:22 up  3:41,  2 users,  load average: 0.62, 0.52, 0.40


Most of the time I was away, but the screen did sleep, and wake up properly. I am using it tonight for general screwing around, I will post back later and let you know if I have issues.


EDIT:
I had one problem, I think it was due to the graphics card overheating while sitting on my lap. It was black and white vertical bars on the screen, I ended up hard rebooting, and then haven't had an issue since then. uptime of

23:33:27 up  2:02,  2 users,  load average: 0.56, 0.94, 1.12

I think if it was sitting on a table that it wouldn't have happened.

Im going to leave it on overnight, and see how it goes.

---

### Post by PiEp on 2009-08-12
I am having the exact same problems with my Acer Aspire 5100 laptop: random freezes, sometimes shortly after booting, sometimes after hours of use. Seems something is wrong in the drivers department.

I have tried turning off Visual Effects, no effect.
I have now set the sound devices to use OSS. Will let you know if it helps.

---

### Post by PiEp on 2009-09-03
OSS did not help. I have tried other distros on this laptop in the meantime. All Ubuntu-based ones had the same problem. Debian did not have it though, but it requires too much configuration for me to get comfortable.

I am still hoping that some update will fix the issues, as it does not seem to be a hardware problem...

---

### Post by Valir on 2009-10-08
I have the same problem on an Aspire 5100 too!

Reported this as a bug. 

System freezes at random. Screen blanks out with striped pattern. It does not respond to any command. Hard reboot required. I haven't identified any running application as the culprit. It happens at random. The graphics card is ATI Radeon xpress 1100. Is this a kernel problem or a graphics problem? I have installed the medibuntu package but the problem existed both before and after.

A serious flaw.:(

---

