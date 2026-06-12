---
title: "Can I get Linux Mint's new back up tool?"
date: 2010-06-17
forum: General Help
---

### Post by Axilus on 2010-06-17
I was reading through the [list of features]("http://linuxmint.com/rel_isadora_lxde_whatsnew.php#mintbackup") for the new Linux Mint release and I found something that I have been looking for on Ubuntu for a while... The New Backup tool.

Is there anyway I can get this on Ubuntu? I mean after all, Linux Mint is built on Ubuntu.

---

### Post by elliotn on 2010-06-17
Just install it, get its name and google it

---

### Post by XubuRoxMySox on 2010-06-17
It's listed in their [software portal]("http://community.linuxmint.com/software/browse/13") but it is not available for Ubuntu. Like many other cool Mint stuff, it has a **.mint** filename extension that will only install on a Mint system.

Just another one of the ways that Mint "gives back" to the people who did most (almost all, actually) of the work that has gone into Mint, which is more accurately termed an *Ubuntu remix* than a "distro." In my opinion anyway.

There are plenty of other backup alternatives that are every bit as easy to use (Google it!).

---

### Post by Axilus on 2010-06-17
> **dixiedancer said:**
> It's listed in their [software portal]("http://community.linuxmint.com/software/browse/13") but it is not available for Ubuntu. Like many other cool Mint stuff, it has a **.mint** filename extension that will only install on a Mint system.

Wait a minute. I can't believe you just wrote that in a casual sentence. With all due respect, what is wrong with you!?

Wasn't the point of me switching over to Linux to not be restricted by what I can and can't install based on what distro (or remix IYO) I'm running?

How do you expect more people to take up an opensource perspective on technology if it is clearly evident that the things that everyone is preaching makes opensource so great (such as  cross platform apps (without building the app from the source again)) is fairly inconsistent between distributions.

The fragmentation and attitudes of some of the distributions in the Linux community disgusts me.

I do agree though, Linux Mint is indeed a very cool, useful, and interesting distro; as are many others, but come oonn...

I thought I got away from all that when I left windows.

---

### Post by philinux on 2010-06-17
Why not just add mint's repos to ubuntu.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9462173](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9462173)

---

### Post by XSAlliN on 2010-06-17
You can, but it also needs some dependencies. 

**[The 1'st files you get from here]("http://packages.linuxmint.com/pool/main/m/")** - and their called:

Mintbackup (this is the backup tool)


mint-info-main **or** mint-info-x64 (if you're on 64 bit)
mintsystem
mintmenu
mint-common
mint-translations


**[...and the last]("http://packages.linuxmint.com/pool/main/f/fortunes-husse/")** fortunes-husse

Just download the latest packages (check build/date) and install them as Deb files.

---

### Post by Axilus on 2010-06-17
> **XSAlliN said:**
> You can, but it also needs some dependencies. 

**[The 1'st files you get from here]("http://packages.linuxmint.com/pool/main/m/")** - and their called:

Mintbackup (this is the backup tool)


mint-info-main **or** mint-info-x64 (if you're on 64 bit)
mintsystem
mintmenu
mint-common
mint-translations


**[...and the last]("http://packages.linuxmint.com/pool/main/f/fortunes-husse/")** fortunes-husse

Just download the latest packages (check build/date) and install them as Deb files.

Will do, hopefully it shall work.

Thanks.

---

### Post by alexandrius on 2010-06-17
@XSAlliN
Works! Thanks for tip

---

### Post by XSAlliN on 2010-06-17
> Wasn't the point of me switching over to Linux to not be restricted by what I can and can't install based on what distro (or remix IYO) I'm running?

How do you expect more people to take up an opensource perspective on technology if it is clearly evident that the things that everyone is preaching makes opensource so great (such as cross platform apps (without building the app from the source again)) is fairly inconsistent between distributions.

The fragmentation and attitudes of some of the distributions in the Linux community disgusts me.

I do agree though, Linux Mint is indeed a very cool, useful, and interesting distro; as are many others, but come oonn...

I thought I got away from all that when I left windows.

No, That's not how it is...

Windows is just **1** distribution.

Linux is just the kernel (an Open Source kernel), on which hundreds (**100+**) of Distributions are made. Some based on source, some on RPM, some on Debian or other distributions (like Ubuntu - > Mint in this case).

For most applications, especially the major ones there is a workaround if not a direct solution to install it on another distributions. But you can't expect even their features to work in same way. 

In this specific case works (mint-backup), cause the tool + dependencies are developed in Deb and there's also the repository option (mint being based on deb/ubuntu). But don't expect AUR to work in Ubuntu, or even Mac application (since some of Windows work with Wine). :)

As for "open source" perspective, as the name implies - it's related to the freedom of "open source" - as in, "*you can take any OSS and use it, enhance it and modify it to your will*". Which is not possible with closed source applications, like most in Windows or Mac (including the OS's), where you take the software "**AS IT IS**". 

Ubuntu being the most popular linux distribution, has many priorities in terms of software development. But, you can't say the same thing about the rest - and not that there isn't will but there is no way to make a software, custom build for all linux distribution - not even for the major ones. Yet most get the source or the rpm package and they can go from that (especially the distributions aimed for advanced users which are not dependent of Windows approach "Click and Install" ...).

> **alexandrius said:**
> @XSAlliN
Works! Thanks for tip

No problem. ;)

---

### Post by XSAlliN on 2010-06-17
This tool may have some decent option, but since it's intended for Linux Mint - the only way to get it work is by faking your Ubuntu credentials to display Mint. Just noticed this after rebooting. My Ubuntu 10.04 LTS was now displayed as Linux Mint 9 Isadora and same goes for all system info. Unfortunately this info is vital for certain components in Ubuntu like "Ubuntu Software Center" and software-proprieties-gtk (software sources) and not GUI related but also functionality.

For me was just a test, to see what's up whit that and then I removed it (dependencies as well). Of course, the problems remains so had to fix those as well. :) I did that by editing the following lines (this is for Lucid only DOH :D ):



**gksu gedit /etc/issue**

> Ubuntu 10.04 LTS \n \l



**gksu gedit /etc/issue.net**

> Ubuntu 10.04 LTS



**gksu gedit /etc/lsb-release**

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION=”Ubuntu 10.04 LTS”

---

### Post by alexandrius on 2010-06-17
@XSAlliN
Mamma mia

You saved me thanks :)


Is there any way to install mintbackup without damaging anything?

---

### Post by XSAlliN on 2010-06-18
Well, there's no damage - just extra work. :) So guess it would be better to use a general tool or one specific for Ubuntu.

---

### Post by nikkpap on 2010-06-18
try my back up tool it isn't with GUI but it run's smoothly and correct it can backup all your app's but not the one you install with a *.deb ;) give a try !!!

[http://www.mediafire.com/?zmmmizymzmh](http://www.mediafire.com/?zmmmizymzmh)

---

### Post by nikkpap on 2010-06-18
and for the lazy ones...

1. mint-info-main
[http://packages.linuxmint.com/pool/main/m/mint-info-main/mint-info-main_9.0.3_i386.deb](http://packages.linuxmint.com/pool/main/m/mint-info-main/mint-info-main_9.0.3_i386.deb)

2. mint-translations
[http://packages.linuxmint.com/pool/main/m/mint-translations/mint-translations_2010.06.12_all.deb](http://packages.linuxmint.com/pool/main/m/mint-translations/mint-translations_2010.06.12_all.deb)

3. mint-common
[http://packages.linuxmint.com/pool/main/m/mint-common/mint-common_1.0.5_all.deb](http://packages.linuxmint.com/pool/main/m/mint-common/mint-common_1.0.5_all.deb)

4. fortunes-husse
[http://packages.linuxmint.com/pool/main/f/fortunes-husse/fortunes-husse_1.0.1_all.deb](http://packages.linuxmint.com/pool/main/f/fortunes-husse/fortunes-husse_1.0.1_all.deb)

5. mintsystem
[http://packages.linuxmint.com/pool/main/m/mintsystem/mintsystem_7.6.8_all.deb](http://packages.linuxmint.com/pool/main/m/mintsystem/mintsystem_7.6.8_all.deb)

6. mintmenu
[http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.9.9_all.deb](http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.9.9_all.deb)

7. Mintbackup
[http://packages.linuxmint.com/pool/main/m/mintbackup/mintbackup_2.0.6_all.deb](http://packages.linuxmint.com/pool/main/m/mintbackup/mintbackup_2.0.6_all.deb)

:lolflag::lolflag:):P):P

---

### Post by Axilus on 2010-06-19
> **nikkpap said:**
> try my back up tool it isn't with GUI but it run's smoothly and correct it can backup all your app's but not the one you install with a *.deb ;) give a try !!!

[http://www.mediafire.com/?yzdwdf2fnmz](http://www.mediafire.com/?yzdwdf2fnmz)

Your backup tool's link appears to be dead.

---

### Post by nikkpap on 2010-06-20
[http://www.mediafire.com/?zmmmizymzmh](http://www.mediafire.com/?zmmmizymzmh)

@axilus  i am sorry i correct the upload sorry again give a try is nice to hear your opinion thanks

---

### Post by XSAlliN on 2010-06-20
There's a CLI way to save a software list:

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

...and add it back later. Which is the same thing Mint back-up does, but with a GUI.

---

