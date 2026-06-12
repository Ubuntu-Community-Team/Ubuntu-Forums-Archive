---
title: "How do you install programs in Ubuntu?"
date: 2006-03-23
forum: General Help
---

### Post by vidorTX405 on 2006-03-23
I am a Windows user running Ubuntu in emulation using VMware Player. I am trying to install programs manually and cannot figure out how to do it. I am completely new to the terminal in Linux. ](*,) May I have some help?

---

### Post by bbzbryce on 2006-03-23
I'm not sure if there is a difference when using vmware however, the typical way to get a program is to type

sudo apt-get install packagename

For example to install firefox one would type

sudo apt-get install firefox

Hope this helps.

---

### Post by DeusEx on 2006-03-23
you could go to System - Administration - Synaptic

---

### Post by barthel on 2006-03-23
[QUOTE=vidorTX405]I am a Windows user running Ubuntu in emulation using VMware Player. I am trying to install programs manually and cannot figure out how to do it. I am completely new to the terminal in Linux. ](*,) May I have some help?[/QUOTE]

In Ubuntu, the preferred method is via the Synaptic Package Manager (System->Administration->Synaptic Package Manager from the menus). It will take care of all the dependencies and the basic configuration for you.

From the command line, "aptitude" will give you a somewhat similar interface, but you can also use "apt-get" and "dpkg" directly. There's a greate reference to ap-get at [http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html") which I found to be very helpful. I'd also suggest looking at the man pages ("man apt-get" or "man dpkg" from the terminal).

Hope this helps.

---

### Post by damu on 2006-03-23
You also have the basic way : Applications/Add applications
You will also find it under System/Administrations/Add applications

Just browse the list , tick the sotwares that you want Ubuntu to download and install, adn click apply...let Ubuntu do the job...that's it. Now they are in the menu, ready to work.

Another easy way to install some softwares is to use Automatix (do a search on this forum). It makes it as easy as "Add applications" for softwares and funtionnalities that you probably look forward to have ( multimedia codecs, DMA on, skype, etc)

---

### Post by bionnaki on 2006-03-23
read this: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Blunts on 2006-03-24
I hate to be link repetitive but this will tell you 90% of what you need to know [http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

---

### Post by frodon on 2006-03-24
And if it's not enought ;) : [http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)

---

