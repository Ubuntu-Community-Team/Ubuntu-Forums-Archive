---
title: "A bunch of questions to help a windows power user convert"
date: 2010-04-02
forum: General Help
---

### Post by keljaden on 2010-04-02
I have been playing around with Ubuntu (and its variants) in addition to, fedora, BT3, and Linux mint for a couple of years now.  I have a bunch of questions though which I still need answered so I hope you guys can help me out.

1. Where do installed "applications" go.  EX: I use synaptic or ubuntu software center to download and install wine.  Where are the installation files?

2.  Where are the OS's install files located

3. Can I just download an different desktop environment like LXDE and switch to it from gnome while still keeping all my same apps installed?

4.  I want to make a have the nice ubuntu packages and "features" while using LXDE, keeping everything light.  I was told to use the alternate install disk, which the download links too me to a  "minimal install disk", when i tried and install like this with debian, the thing couldn't even detect my mobo's Ethernet port so i was unable to use it. (so is the minimal install disk what I want, and if so will it detect the Ethernet port on my ASUS P5N-D mobo?)

5.  During an alternate install, do I also get a choice of applications to install? How complex is it, as I will still need my drivers to be auto detected?

6. Battery life, in addition to Desktop I have a laptop.  The battery life in win7 is 4hrs 20min, under Ubuntu 9.10 i get about 2 hours (this is with just using firefox and instant messaging in both)  What am I doing wrong? I was told LXDE helps with power consumption so I think I should try that. (other advice is recommended)

7.  Some people say that have window managers that are not the default to their environment, how do I change it, what is the benefit?

---

### Post by Naggobot on 2010-04-02
1./2. I just realized I have no idea so I Googled this

[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

3. I have both KDE and Gnome installed. You can select session and language from the login screen. 

Hopefully someone else can answer the rest

---

### Post by gsgleason on 2010-04-02
1 - files are all over the place, really.  If you want to know exactly, you can see what files a package has installed in a terminal with 'dpkg --listfiles packagename' or you can use the synaptic package manager, right click, properties.

*nix systems are very different when it comes to applications.  They come in the form of pre-compiled 'packages' which is just like a compressed archive.  Some packages rely on others to work, and these are called 'dependencies.'  Ubuntu's package system will resolve these automagically.

2 - I guess that depends on what you mean by "OS."  Linux itself is the kernel which is generally in /boot.  An OS, I would way, is the assortment of applications that makes a computer work, so really, refer back to the first question.

3 - yes.  there is an lxde package available.  You should get an option on the login screen to choose it.  Maybe this will help.

4,5 - I find that interesting. Once you have booted to the minimal, do 'ifconfig eth0' to see if anything is there.  This would have to be troubleshot I think.  I've used a minimal install only once for my media center with XBMC.  I had no issues.

6 - Make sure you have the various tools set up to do things like CPU frequency scaling, hard drive spin down, etc.  Lower your brightness, maybe?

7 - You probably won't notice a benefit.  Some people use compiz, but it's all for flash and not much for functionality.  I find the default gnome window manager (metacity) to work just fine for me.

---

### Post by Scunizi on 2010-04-02
Much like windows, installed programs have pieces in different locations.  /usr/bin I believe is where the executable is typically located.  With no registry the configuration files are typically in a hidden folder on your /home directory and will occasionally have a system wide configuration file someplace else.

The OS is also spread to different directories.. but / /boot /etc is where most of it is.. root (/) also lists all the directories.

Enjoy the adventure!

---

### Post by keljaden on 2010-04-02
What program can I scale my processor down with (and the 2 hours was with brightness all the way down and my battery is almost perfect still)

I have looked into powertop before, but a lot of linux apps still lack a nice GUI or IMO abnormally difficult terminal commands.

Also I got LXDE to run just fine as well now, thanks for you help so far.

---

### Post by bigsmitty64 on 2010-04-02
This is a good resource to bookmark!

[http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html](http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html)

As is this!

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by 2hot6ft2 on 2010-04-02
1. Has already been answered. There is a picture of the layout but I lost it when I reinstalled.

2. See 1. but most of the configuration files are in your Home Folder they're just hidden, clicking on View  and checking the box for Show hidden files will make them visible.

3. I run Ubuntu Ultimate Edition and can choose my desktop manager at the login screen like gnome, kde, etc..

4. Kinda deletes the #3 answer. Lubuntu is still in beta but I tried it and it seemed very light and stable and it uses LXDE.

5. I don't use the alternate cd, but drivers like graphics would be installed after the OS installation like every other version as far as I know.

6. I don't know.

7. Gnome or KDE, can be installed thru Synaptic Package Manager. Personal taste.

---

### Post by MikeHa on 2010-04-02
[http://www.linuxlinks.com/article/20080621060835773/Portal.html](http://www.linuxlinks.com/article/20080621060835773/Portal.html) has lots of software recommendations

---

### Post by keljaden on 2010-04-03
Thanks so much for all the help everyone.  I think I got all I needed from you guy's posts.  I also got the one thing (ModernWarfare 2) running in crossover perfectly so I say say goodbye to Windows forever and breathe the clean air of Linux.  Thanks again for your help.

---

### Post by nathbfreak on 2010-04-03
I can answer #3.

hit alt+F2
and type:
KDE: apt:kubuntu-desktop
XFCE: apt: lubuntu- desktop
LXDE: Ithink It's apt:lubuntu-desktop

when it done log out and go to "Session" and select the one you want

---

### Post by keljaden on 2010-04-03
thanks again, this was really helpful.

---

