---
title: "Linux on USB problem. Please help..."
date: 2010-09-23
forum: General Help
---

### Post by yes8s on 2010-09-23
Hi all,

I finally decided to give Linux a try, so to test it out I created a [COLOR=Black]U[/COLOR][COLOR=Black]buntu 10.04.1[/COLOR] USB boot drive [COLOR=Black]based on the tools and instructions from [www.pendrivelinux.com]("http://www.pendrivelinux.com/"). I am using an ASUS Core 2 Duo laptop.

Basically I downloaded the ISO from the site and also the installer (* Universal-USB-Installer-1.7.9.8 )*. If I create the boot drive _without _the persistance option (i.e. no casper-rw file ) everything runs fine and I can boot it up, use it and shut it down with no issues whatsover... [/COLOR][COLOR=Black]except I cannot save my settings, files etc.

When I install the OS _with _the persistance option (ie. create a casper-rw file) I can boot and run fine but when I try to shutdown I can't do it successfully. The console spits back errors and even if I wait it just hangs and keeps spitting back these errors

I've taken photo screenshots of whats happening when it's trying to shutdown:

[IMG]http://i51.tinypic.com/28a1fvd.jpg[/IMG]
This part appears to work ok... it kinda stalls a little but I think it is supposed to here (as it says)

[IMG]http://i52.tinypic.com/256uskx.jpg[/IMG]
This is where I start to get the errors...

[IMG]http://i52.tinypic.com/2cpqb1y.jpg[/IMG]
And I keep getting them while I wait...

Only way to get out is force a shutdowm by pressing and holding the power button. Interestingly, when I boot back up the changed settings and files have been saved. 

I've done a search about the error but everything suggests that there maybe something wrong with the USB drive. I really doubt this is the case - the USB drive is 4GB Kingston, it's brand new (literally never used for anything else) and I've checked it's integrety using various test SW.

Any ideas?
[/COLOR]

---

### Post by yes8s on 2010-09-24
Anyone?

I've tried a couple of other dists and I still get the same error... This error has me baffled

---

### Post by aytech on 2010-09-24
Try to recreate the Live USB, I've had problems when creating one with 4Gb persistence, then recreated it with smaller persistence file and it worked then. 
What size of persistence do you choose?

---

### Post by yes8s on 2010-09-24
> **aytech said:**
> Try to recreate the Live USB, I've had problems when creating one with 4Gb persistence, then recreated it with smaller persistence file and it worked then. 
What size of persistence do you choose?


I must of done this a dozen times already... I initially tried it with 2GB persistence. I then tried 1gb and 3 gb. I've tried to create just a live version (no persistence) and then add the persistence later. All result in the same hang up and error.

---

### Post by aytech on 2010-09-24
I'd try a different USB stick and see if the problem will remain.

---

### Post by aytech on 2010-09-25
This same thing happened to me today, I tried to run LiveUSB on a friend's desktop. Only it happened during boot, resulting the system being stuck on welcome screen. I know his PC has problems with video card (bad memory), and this same LiveUSB works fine on my laptop.

---

