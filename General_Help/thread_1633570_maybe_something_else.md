---
title: "maybe something else?"
date: 2010-11-29
forum: General Help
---

### Post by Askalade on 2010-11-29
hi, i just installed ubuntu 10.04 on my notebook. runs amazing, very  smooth and nice effects. but the thing is : once you get ubuntu you don't  want something else ;P. but i can only use it on my notebook cause my  computer has a amd phenom 2 processor and a ATI hd radeon 5970 video  card. and ubuntu + amd + ATI = crash. it just doesn't work together. **so my question was: is there a ubuntu like OS with compiz or something like that that will work with amd and ati and a 64 bit pc? iv'e searched a bit but i just cant find something, i dont know if fedora is any good or maybe debian or something.**

---

### Post by dino99 on 2010-11-29
what's the truth ? "run amazing" or "crash" ?

for a while now amd=ati

so your question is not one !!!

Open a terminal and run one command at a time, beginning with the first

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

then reboot and check driver activation: system admin additional driver

for more info, see below :)

---

### Post by janpol on 2010-11-29
My PC has an AMD Phenom II X2 550 with an nvidia gtx260 and Ubuntu 10.10 64bits works great.

I think you should look out for issues related with your Video Card (maybe you don't have the best drivers?) and/or your motherboard. 

Linux is Linux, no matter the distro, what changes (basically) are the packets included on each one of them (and also the looks ;)).

You can always try a different distro (maybe Mint, PCLinuxOS, or any other distro oriented to the final user) but, if one of those solves your problem is because they use a different driver version, kernel version, etc.

But, I'm guessing that your problem is drivers(or compiz)-related. 

Have you installed the latest drivers?(see dino99's suggestion) 

Have you tried disabling desktop effects?

Good Luck!

---

### Post by Askalade on 2010-11-29
1. ubuntu was running smooth and is amazing on my notebook and my problem was on my head computer.
2. when i install ubuntu on my head pc it always freezes when it's loading. i have fixed that with booting ubuntu in safe graphic mode. however, i won't get 1920 x 1080p resolution. i will just get crappy resolution and black edges around my desktop (not full screen). and then the Internet doesn't work either. i have wireless Internet btw. and i don't know how to fix internet either. my main question was if there isnt another ubuntu like OS with a compiz like application that may run better on the computer.

---

### Post by TBABill on 2010-11-29
You'll probably face similar issues till you work out the driver issue with the video and wireless. It sounds like you just want it to work without fixing what isn't working in Ubuntu. As far as hardware, Mint probably would result in the exact same problems since its hardware configuration is the same. It's an awesome OS as well, but similar results will just disappoint you again.
 
PCLinuxOS has enabled the Broadcom driver without any additional installation so if that happens to be what you have then perhaps your wireless will "just work". However, I'm not sure what difference there may be in ATi driver versions from Ubuntu to there. You may also be able to get openSUSE running, but it's managed quite differently from Ubuntu. PCLinuxOS still uses Synaptic so if you use it you'll still feel somewhat at home, although the default DE is KDE, which is familiar to Kubuntu, but not Ubuntu.
 
What about a derivative of Ubuntu that may come with more/different drivers? I do NOT know if they do or not, but Pinguy and Ultimate basically run tweaked Ubuntu.
 
Other than that all I can suggest is a separate post for help with each issue till you resolve it. That will teach you along the way and you can print the fixes in case a reinstall becomes necessary. Then you will know how to help when others face similar issues.

---

### Post by Askalade on 2010-11-29
ok ty. i will look

---

### Post by janpol on 2010-11-29
> **Askalade said:**
> 1. ubuntu was running smooth and is amazing on my notebook and my problem was on my head computer.
2. when i install ubuntu on my head pc it always freezes when it's loading. i have fixed that with booting ubuntu in safe graphic mode. however, i won't get 1920 x 1080p resolution. i will just get crappy resolution and black edges around my desktop (not full screen). and then the Internet doesn't work either. i have wireless Internet btw. and i don't know how to fix internet either. my main question was if there isnt another ubuntu like OS with a compiz like application that may run better on the computer.
What I wanted you to understand is that Ubuntu is a distribution of Linux (Gnu/Linux is the OS you are using). There are several distributions out there, and maybe you can fix your problem installing another distro, but that will only mean that the distro you are trying, ships with the appropriate drivers for your computer and you could also install those on Ubuntu.

Other general-use oriented OS's are: Windows or MacOS, and none of them has compiz. MacOS has cool effects but is built for Apple hardware, and is likely that it won't run well on your computer (and getting it to run on a PC requires a lot of tweaking). 

And Windows, I think you know Windows right? :p

Another alternative is BSD (try FreeBSD), but you will find better driver compatibility on Linux (Ubuntu, Mint, PCLinuxOS, Debian, Fedora, etc, etc).

I just wanted to clarify the difference between Linux distributions and Operative Systems :)

My advice: Try to google for issues with Ubuntu and the ATI radeon 5970, if that doesn't work, google for issues with Linux and that video card (like I said: Ubuntu is a Linux distro).

Regards!

---

