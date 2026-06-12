---
title: "Duel monitors !!"
date: 2010-03-17
forum: General Help
---

### Post by b1gg5y on 2010-03-17
just installed ubuntu as my first ever linux instalation, and am loving it so (bugs and all) but i was wandering if someone can point me in the right direction towards a noobish guide to configuring a duel screen setup !!!

and it has to be a noobish guide....i just about sorted wineHQ out for installing WOW ( witch its doing as i type this ) 

and what is the best firewall and antivirus for ubuntu

and help would be FANTASTIC !!!

DEATH TO MICROSOFT !!!!

---

### Post by linden940 on 2010-03-17
"and what is the best firewall and antivirus for ubuntu"


this is not a windows system...there are very few viruses out that can kill a Linux its a very stable system only thing more stable is Unix anyway the point is...i have been running my ubuntu system for a about a year now and i have not needed a firewall or a anti-virus...but if you wanted one there are a few out there...and any of them would really work..but i have not used one and i have not had any problems

*you'll be shocked at how many window viruses u'll find...funny part is...its for windows..not Linux and so they can not run/work it will give you an error that the "virus" can not run..i just :D butt off and delete it

---

### Post by jrssystemsnet on 2010-03-17
You don't generally need antivirus software on Ubuntu at the moment; there really isn't any Windows-style antivirus software that hooks into the system and scans everything you do while you do it.  At least, not that I'm aware of.  If you want to be able to scan files or directories manually for malware, there's always clamav.

Dual monitors should, for the most part, pretty much Just Work.  If you're using an nvidia card, you'll need to enable the nv drivers from the System -> Administration -> Hardware Drivers, and then use System -> Administration -> Nvidia X Server Settings.

---

### Post by b1gg5y on 2010-03-17
> **jrssystemsnet said:**
> You don't generally need antivirus software on Ubuntu at the moment; there really isn't any Windows-style antivirus software that hooks into the system and scans everything you do while you do it.  At least, not that I'm aware of.  If you want to be able to scan files or directories manually for malware, there's always clamav.

Dual monitors should, for the most part, pretty much Just Work.  If you're using an nvidia card, you'll need to enable the nv drivers from the System -> Administration -> Hardware Drivers, and then use System -> Administration -> Nvidia X Server Settings.


I should of said in my post that im using 2 xfx 9600 gso cards...so i have 1 mohnitor on each card.....tried to mes around with the nvidia x sever settings but something to do with x is going wrong, and being a NOOB i dont know what !!!

---

### Post by scouser73 on 2010-03-17
> **b1gg5y said:**
> just installed ubuntu as my first ever linux instalation, and am loving it so (bugs and all) but i was wandering if someone can point me in the right direction towards a noobish guide to configuring a duel screen setup !!!

and it has to be a noobish guide....i just about sorted wineHQ out for installing WOW ( witch its doing as i type this ) 

and what is the best firewall and antivirus for ubuntu

and help would be FANTASTIC !!!

DEATH TO MICROSOFT !!!!


[COLOR="Red"]**If you don't already have an Xorg.conf, then please follow these instructions**[/COLOR]

Create a new Xorg.conf

Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
**> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

__________________________________________________________________________________________________________________________________________

[COLOR="Red"]**These instructions are for nVidia graphics cards only**[/COLOR]

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by lisati on 2010-03-17
Presumably we're talking du**a**l monitors here, not monitors that have gotten into a du**e**l..... :)

---

### Post by b1gg5y on 2010-03-17
> **scouser73 said:**
> [COLOR=Red]**If you don't already have an Xorg.conf, then please follow these instructions**[/COLOR]

Create a new Xorg.conf

Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.


Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.






Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.


If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

__________________________________________________________________________________________________________________________________________

[COLOR=Red]**These instructions are for nVidia graphics cards only**[/COLOR]

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.





At step 2 i get this warning "

b1gg5y@b1gg5y-desktop:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

i went ahead and done the rest, it alowed me to aply settings in nvserver, but they dont save !!

---

### Post by linden940 on 2010-03-17
two monitors dueling....now..i need to learn how to do that!...*could be fun to watch if i dont have 2 replace them after each match lol*

---

### Post by b1gg5y on 2010-03-17
Just found this [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)...........

will try it after Wow has finished installing, dont want to stop it..

then i will try [B]scouser73's post, witch by the way is a pritty noobish guide..cheers : )

will let ye's all know how it goes !!!
[/B]

---

