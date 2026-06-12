---
title: "QUESTION REGARDING GRUB AND MULTIPLE UBUNTU LISTINGS [1st time user]"
date: 2009-12-15
forum: General Help
---

### Post by rustyfenix on 2009-12-15
Question Regarding Grub [1st days using Ubuntu] 

Cheers,

I'm new to this cool OS an the forums and I must say I am digging it so far from what I've seen.

I tried to search for my question but I couldn't find at a glance so maybe someone could help me out it's really general I'm sure here it is:

Basically after I installed Ubuntu on a partition (25GB) on my PC alongside my Windows XP partition (125GB) Everything was working great and I could boot both OS's from the Grub no problem.

It's only after that I updated Ubuntu that I know seem to have 2 versions showing up on the GRUB loader where before I only had 1. It really doesn't bother me much as I just use the top listing but I would like to know if it is possible to only have 1 listing of Ubuntu show alongside my windows XP listing on the boot loader.

I've attached the pic of what the GRUB looks like when I boot up, you will notice the 2 Ubuntu listings and the XP one at the bottom.

Any suggestions would be greatly appreciated, thanks in advance. ;)

---

### Post by darco on 2009-12-15
Your kernel was updated so now it list the previous kernel which is good in case the new kernel failed. If the new kernel is fine, then in synaptic, search for linux-image, and choose to uninstall the old kernel. After, run sudo update-grub in a terminal to remove it from the grub menu.
good luck

darco

---

### Post by rustyfenix on 2009-12-15
:o so that's all there is to it.. what would happen if i chose to boot from the old kernel? will it add a new one after every update?

appreciate it, tks!

---

### Post by scouser73 on 2009-12-15
Hi and welcome to the Ubuntu Forums, I've taken a look at your post, you can remove previous kernels if you wish.

Read through and follow my instructions if you want to.

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Piccy on 2009-12-15
All very good options. But my "preferred" way is using Ubuntu Tweak

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

It not only removes older kernel versions but also a tonne of other stuff as well

---

### Post by rustyfenix on 2009-12-15
Thanks for your prompt replies and instructions I'm learning more everyday now if I could just get that cool looking cube effect on my desktop :D!

> **Piccy said:**
> All very good options. But my "preferred" way is using Ubuntu Tweak

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

It not only removes older kernel versions but also a tonne of other stuff as well

Piccy, I checked this out because I used to use something similar for windows and I just wanted to know what would be the best way to install this program on ubuntu I'm curious about it. Tks!

---

### Post by Piccy on 2009-12-15
OK lesson 2 then :popcorn:

Adding repository sources

As you probably guessed there are a number of ways to do this as well. Adding a repo gives you access to the software available on that particular repo (some repos have lots of software, others have few). In this case we want to add the repo for Ubuntu Tweak. Now I will tell you my preferred way

Go to System - Administration - Software Sources
Go to the other Software tab
Click Add

Now we just need the apt line. This is found on the downloads section of the Ubuntu Tweak site
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Find your version. If you use Karmic then its

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main

Click add source

and

deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main

Click add source


Now it will try to refresh when you close the software sources window, and error. Thats OK we need to add their key

As per the instructions, run this in a terminal
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220

This should import the key. Now go to synaptic and click reload at the top. This will get software info from the repo that we just added and search for Ubuntu Tweak and install

Now this is one method of adding repos but there are others. Another easy method is to just add those two sources to /etc/apt/sources.list

But that can be hard to manage if you are inexperienced. But open it up with gedit and see if you can work it out

These instructions will work for adding any repo to your sources list

---

### Post by miniyak on 2009-12-15
most software in ubuntu is pretty easy to install by opening up the ubuntu software center (or in older versions add/remove)

some of the third party stuff ect. however requires a couple of steps that are probably intimidating for a new user. Ubuntu tweak is definitely worth while for a new user however. Gives one a chance to learn those extra steps. Then after you'll never have to use them again because ubuntu tweak provides easy access to a lot of that other software that the software center misses. 

keep in mind that the "recovery mode" entries can help if something gets hosed, you will want to keep them

also there is a program called "start-up manager" that provides an easy interface to choose the default entry to load

---

### Post by rustyfenix on 2009-12-16
:KS Tweaking is good.

:KS I'm finding myself using Ubuntu more and more now it's good to know these things..
 :KS I know I'm still gonna have to wear the noob hat for now though it's kinda cool actually. 

:KS I would like find out now how activate some kind of pivot feature so I could make use  
:KS of my HP w2207h monitor I'll try searching around the forums tks again guys.

---

### Post by nibirumarduk on 2009-12-17
While I agree with the need to purge the system of unused, outdated kernels to reduce bloat, with Synaptic and all, you may still miss out on a few of the kernel-related packages.

But before we go about the business of purging, do find out what your existing kernel version is. You can remove ***ANY*** kernels ***other*** than the one you are currently using.

Method (A)
Steps
1. 
Find all kernel-related packages installed on your system with either:
dpkg -l|grep linux
or
dpkg --get-selections | grep linux

2. 
Purge all linux-headers-*, linux-image-* and the likes ***for kernels you do NOT want to keep***

e.g.
sudo aptitude --purge remove linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-restricted-modules-2.6.31-14-generic linux-backports-modules-2.6.31-14-generic

3. 
Purging any remaining configs and obsolete packages i.e. housekeeping

sudo deborphan | xargs sudo apt-get -y remove --purge && sudo deborphan --guess-data | xargs sudo apt-get -y remove --purge; sudo apt-get autoremove && sudo aptitude purge '~c'; sudo apt-get autoclean

Method (B)
1. 
For a listing of unused linux headers, image, and modules:

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'

2.
To purge them:
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge


Good luck!

---

### Post by 5ive on 2010-01-15
> **nibirumarduk said:**
> Method (B)
1. 
For a listing of unused linux headers, image, and modules:

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'

2.
To purge them:
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

This method deletes all kernels, but now running Ubuntu. How to do that this method is not deleting two of the latest?

---

