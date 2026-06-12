---
title: "So how good is kubantu?"
date: 2006-02-28
forum: General Help
---

### Post by snay on 2006-02-28
I am fairly new to linux, and I am using suse linux 10, but I dont really like it. My main problem with it is that it is a pain in the backside to get new programs, and to get them to work. I can compile them from source fine, I just dislike YAST. I dont know if it is the way I am using it or not, but it seems to have problems installing working packages. It missees dependancies, or the official package server just doesnt have the dependancies avaliable. Its a nusance. Ive heared good things about apt-get (kubantu does use this right?) but how good is it really? 
Also, some things I am having problems with at the moment are:
Playing different types of media, including wmv, aac, real, jpeg and I had a bit of trouble getting mp3s to play, so how good is kubantu at all of this stuff?
Can I get kubantu to share an internet connection on my laptops wireless card, to my xbox, which is plugged into the ethernet port?
Also how easy is it to install? I tried debian, but I couldnt get the display to work.
I want to make sure kubantu is right for me. Its currently downloading. Only 7 hours to go.
Thanks. Snay.

---

### Post by gingermark on 2006-02-28
I'll try to answer this point by point. Also I'll not to be petty and tell you that the distro is called Kubuntu, not Kubantu. Oops.

Anyways,
apt-get is excellent. Really. It is.

Getting some media to work takes a little effort initially, but is not difficult. It just involves installing the relevant packages. There is also a tool called Automatix, that installs all that sort of thing for you.

I don't know much about the wireless support.

Kubuntu is very easy to install. The installer doesn't look pretty, but is quite straightforward. If you have another computer with net access forum members will be happy to help if you have any problems.

I had a problem getting x up and running. The magic command you need if you have problems is 'sudo dpkg-reconfigure xserver-xorg' - if all else fails the "vesa" driver will almost always work, and then you can install a proprietery driver if necessary. Maybe check the Linux Questions HCL for your hardware before you install.

You might want to try the Live CD before you install, to see how well your hardware is detected.

Good luck.

---

### Post by FlakJacket on 2006-02-28
So the Xbox is plugged into an ethernet port? does the xbox also have a wireless adaptor? If it does you may be able to set up an ad-hoc network and then use the internet that way.

Flak

---

### Post by Mau on 2006-02-28
Wireless support is great.  A couple of years ago I spent days obsessing over getting wireless to work, which caused me to give up.  A friend recommended me to Ubuntu, and it detected it instantly.  When I booted up, I had a WEP (bad I know, but it keeps my ignorant neighbors out) dialog come up.

---

### Post by tadashi on 2006-02-28
I moved from SUSE v9.3 to Kubuntu v5.1.  I love it.  I get my Wide screen resolution (which did not work in SUSE) and WiFi.  

The install was as simple if not more so than SUSE.  Do not let the text menu installer fool you.

I have had no problem installing using the graphical package managers.  Although I have had to compile my own source code to get the most up to date version.  However, I am reading on how to make my own deb packages once I compile it for easy uninstall should I need to.  It seems pretty simple.

I have heard of some people having problems in Kubuntu that they did not have in Ubuntu.  So if necessary you can load Ubuntu with a KDE windows manager later.

---

### Post by noeluylee on 2006-03-01
Kubuntu 5.10 Breezy is simply great OS. 

Wifi support is good. I had my WPA-PSK working with wpasupplicant. you have to do it manually thought, but it connects pretty well.

---

### Post by metwo on 2006-03-01
[QUOTE=tadashi]I have had no problem installing using the graphical package managers.  Although I have had to compile my own source code to get the most up to date version.  However, I am reading on how to make my own deb packages once I compile it for easy uninstall should I need to.  It seems pretty simple.[/QUOTE]

Have you looked at checkinstall for this? It's easy as pie,

[https://wiki.ubuntu.com/CheckInstall]("https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29")

---

### Post by analyticalman on 2006-03-01
I also used Suse 9.3. Like you I never could get on with YAST (actually Mandriva's URPMI worked better for me than YAST) - but apt-get is better than anything else.  Installing the latest KDE is easier than any other distro and installing multimedia codec's is as good as Fedora core 4 (unless of course you are downloading the AMD64 version in which case forget it);)

---

