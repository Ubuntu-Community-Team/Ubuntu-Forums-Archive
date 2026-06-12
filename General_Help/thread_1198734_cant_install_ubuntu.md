---
title: "cant install ubuntu"
date: 2009-06-27
forum: General Help
---

### Post by puppetj on 2009-06-27
when i try to install this os, at a point i get , a error about cant finish install, your cd/dvd drive mush be bad check it out, or clean it...or ill get to install it, but after i reset the os after install it just get stuck right before the boot loader, now i have no issues installing other os's on the pc and with this drive, and i even checked the disc for defects and was good!

---

### Post by ~sHyLoCk~ on 2009-06-27
Can't you do a full format on that drive and then try reinstalling? It's most likely due to bad iso though. Either your disc on which you burnt it had defects or the iso you downloaded was  correupt. Did you download it from an official mirror?

---

### Post by AoSteve on 2009-06-27
Just for the S&G factor.. try installing in safe graphics mode...

During the selection screen after you select your language press F4 and select safe graphics mode.  Then try the install and see what happens.   My brothers Intel G41TY motherboard with the X4500 won't install and gets the disc read error unless it's in safe graphics mode.  Once I install it and enable the "intel" driver through the xorg.conf file it works great!

See if that helps bud!

---

### Post by puppetj on 2009-06-27
ok, so i just tried that, but i get the text [ok] load up, and after that the text goes pretty quick and goes to a command prompt..is that suppose to happen, b/c i dont see anyway to install from there.

---

### Post by philcamlin on 2009-06-27
probably a bad iso:(

are you on a limited plan 

becasue i would recommened downloading another from the ubuntu site :popcorn:

---

### Post by AoSteve on 2009-06-27
Yeah that's what it sounds like.   Try reburning the ISO image or downloading a new one.   When you burn with an older burner, make sure you burn at 8x MAX.  I usually burn at 4x with old burners.  :)

---

### Post by thefunks on 2009-06-27
What release are you trying to install?

I tried installing the latest 9.04 release on two computers just yesterday. One of them worked perfectly but the other had problems installing like you're describing. It would get stuck on part of the installation process and I couldn't complete the installation. I downloaded and tried the 8.04 LTS and that worked fine.

---

### Post by puppetj on 2009-06-28
ok, redownloading didnt fix the issues, i've tried 32/64, i did get one less issue on the 64 bit running live, i didnt get the delete or dont delete some panel it asked me, to... as for burning it at 8x or 4x i cant lowest it support on the medium is 16x..and yes i reformatted plenty or reinstalls still same issues....and as for 8.10 i have issues getting that to load to the desktop on live...and it doesn't support my wifi usb.

@thefunks  are you downloading the release on the torrent or normal way?

---

### Post by AoSteve on 2009-06-28
I'm going to say there's some hardware conflicting somewhere.  8.04 seems to be the most hardware friendly for me as it works out of the box for all of my machines except for my E8400 desktop (The X-Fi doesn't work there either LOL)    But I use 9.04 and find ways to get my hardware working.  

If the 8.04 ISO doesn't work then there's something else at play with your hardware.  I'd run the memtest+ util from the CD, maybe see if something is conflicting?   I know in some motherboards my Sound Blaster Live would cause such a bad IRQ conflict that even windows wouldn't install (and that's horrible LOL).    As a matter of fact, my MSI  KT266a Pro2U motherboard will not work with the SBLive and GeForce 4 Ti-4400 unless the SBLive card is in the fourth slot.  Just doesn't like it anywhere else for some wierd reason.

Also, check your power management settings in the BIOS.  It could have something to do with that also.  I've seen plenty of software problems be sourced from the ACPI of an older system.   

Give those idea's a look through.   I'm thinking something hardware is your issue and not the software.   More times then any, it'll be a driver issue though.  Can you list the full specs of your system so we can better know what you're working with?

---

### Post by puppetj on 2009-06-28
system specs:

amd sempton 2800+

2gb of ddr 333 ram

mb: dfi k8m800-mlvf

onboard sound/video

HERES THE REST:

[more info of the board]("http://www.newegg.com/product/product.aspx?Item=N82E16813136143")

---

### Post by starcannon on 2009-06-28
[LIST]
[*]Chipsets                 North Bridge       VIA K8M800                 South Bridge       VIA VT8237
[*]Onboard Video Chipset       S3 Graphics UniChrome Pro IGP
[/LIST]
With that combo, I'd highly recommend trying with [Ubuntu 8.04 LTS]("http://www.ubuntu.com/getubuntu/download") first. VIA and S3 are in my experience very Linux unfriendly; VIA has made some good solid efforts within the last couple years towards being more Linux friendly, but in my tests, it still takes a bit of tinkering to get things working. Your setup is possible to get working, but you will need to work at it.

---

### Post by puppetj on 2009-06-28
yes but all my hardware only works with 9.04

are the torrent for ubuntu the problem, i get it from the ubuntu site.....
i mean i dunno what i can do here..for now i think ill just go back to windows since that just what works
but if you have any other help please reply
thanks

---

### Post by AoSteve on 2009-06-29
I have to agree here with starcannon.   I think you should download the 8.04LTS from [www.ubuntu.com](www.ubuntu.com) and try it.   If one of my systems have a problem with 9.04, 8.04 always works.  :)

Give that a shot, doesn't look like you have a bad setup for linux at all, so give that a shot!

---

### Post by puppetj on 2009-06-29
that versions dont support all my h/w, so i cant use it..which means i've tried

---

### Post by AoSteve on 2009-06-30
Well, personally I've used both the torrent versions and the website based versions (they are the same I guess?).  I never had any real problems with either one.  Other then that I don't know?  I wish I could be of more help here bud.

The biggest problem I've had on my brothers system and installing was the graphics card wasn't being installed properly and the disc would get a read error during install.  The install option in safe mode for graphics stops me from seeing the error but then I had to go an enable the intel driver manually after the install in which it works great (aside from overscan LOL).

Sorry I couldn't be of more help.

---

### Post by puppetj on 2009-06-30
ok thanks

---

