---
title: "Issues with 'fresh' install of Ubuntu 10.04"
date: 2010-07-26
forum: General Help
---

### Post by wambuntu on 2010-07-26
Machine:

Acer Aspire x1300 - small form-factor PC
AMD 64-bit Dual Core Processor
3GB of RAM
nVidia-based graphics

The following distros work:

openSUSE (Time w/ distro 3 weeks)
Fedora (Time w/ distro 4 1/2 weeks)
Linux Mint (Time w/ distro 2 weeks)
Mandriva (Time w/ distro 2 months)

and Ubuntu 10.04 (Time w/ distro 2 months)

Issue # 1 - graphics

Each distro correctly notifies me that there are proprietary drivers available for my hardware, and each distro seemingly installs the drivers correctly and I reboot.  In three out of the five, the graphical boot into Linux is broken and I have to fix Plymouth.  

(No worries, I've learned how to do this) 

From here, it's usually business as usual on four out of the five distros.  Ubuntu is the only booger at this point that I cannot figure out, and it is frustrating because this is one of the easier environments to work out of.  

What it is doing, from time to time, is not rendering the desktop panels correctly and I get a white rectangle next to the desktop button.  Sometimes I'll have a 2nd destkop button that is slightly off-center and super imposed over the original (and working) desktop button.  In the upper right-hand corner of the screen in the "Me" section I'll have portions of that panel super imposed as well, but usually this eliminates all functionality of that section and I have to kill the panels.  

This isn't too big of an issue for me.  However, it does frustrate my children when it screws with the "Me" panel and they cannot shut off the machine properly.  My wife isn't too impressed, either.  I'm using the recommended driver for my graphics card, and I don't have snazzy desktop effects enabled.  Is there a setting that I need to tweak in the nVidia control panel?  


Issue # 2 - mouse


Sometimes I'll be in the middle of a game of Sauerbraten and my mouse will fail.  I cannot move in any direction and I have to type /quit and exit the game, depress the power button once on my machine and arrow down on the keyboard to restart my machine.  Once I restart, all is fine and dandy.  

This does not happen on:

openSUSE
Fedora
Linux Mint
Mandriva

I tried another mouse and I encounted the same issue, but not with any of the other builds.  

Because I needed something that just worked, I have Windows 7 on the machine.  For ethical reasons, I'd rather not keep using this copy of Windows and go back to Linux.  I want to know, though, if I will be able to fix the issues I have with Ubuntu or if I will need to migrate over to Fedora, openSUSE or Mint.  

Anyone else experience these issues?

---

### Post by wambuntu on 2010-07-27
OK, so there is a bug out there for my problem:

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/544962](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/544962)

[IMG]http://launchpadlibrarian.net/41705818/show_desktop.png[/IMG]

If I use the Human theme (from 9.10) I don't encounter this issue.  


:popcorn:


Now I wait to see if there is an update / fix.

---

