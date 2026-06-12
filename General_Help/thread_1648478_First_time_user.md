---
title: "First time user"
date: 2010-12-18
forum: General Help
---

### Post by crownclown on 2010-12-18
This is my first time to use ubuntu...
well after the ubuntu installation at the boot screen it seems that i got so many thing that be boot..i think it is call grub or something.
how can i remove those thing and just have 2 boot o.s...
1st is for w7
2nd is for ubuntu
and how do i rename it ?
myne is the ubuntu 10.10
i just finish my update manager and now dont know what to do with it ?
any suggestion?
thx:D

---

### Post by chicoharv on 2010-12-18
did you install inside windows or did you have Ubuntu partion your HD?  If you partioned your hard drive you must use GRUB to go to either OS. Grub is your new start up instead of MBR, you can't delete it and if you do you can not start any OS. If you installed inside windows then windows will show up at the top. Hope this helps, if you have multiple Ubuntu 's listed , once you learn to use the treminal you can delete old Kernels but not GRUB.

---

### Post by crownclown on 2010-12-18
> **chicoharv said:**
> did you install inside windows or did you have Ubuntu partion your HD?  If you partioned your hard drive you must use GRUB to go to either OS. Grub is your new start up instead of MBR, you can't delete it and if you do you can not start any OS. If you installed inside windows then windows will show up at the top. Hope this helps, if you have multiple Ubuntu 's listed , once you learn to use the treminal you can delete old Kernels but not GRUB.

thx for reply well i got ubuntu by its own partition and how to get this configuration on grub ?
isit need to be install ?
so if after i get this grub so i can rename the long name boot to shorten ?

---

### Post by BicyclerBoy on 2010-12-18
Grub is a bootloader.
It tries to support all OS.
You must have it for current linux/Ubuntu.

Windows uses similar tool (ntloader) but it is normally hidden.
The windows bootloader will not support linux/ubuntu AFAIK.

Both can provide a startup user interface /menu to allow you to choice which OS kernel version etc to load.

The window installer will break it by trying to replace it with a m$ tool.

Once you have a stable system you can edit the grub menu to reduce the clutter.
You can this info on Ubuntu website.
Don't be tempted to fix things that are not broken until you understand how to fix it.

What do you mean by:  "i just finish my update manager and now dont know what to do with it ? any suggestion?"

close it ?

Grub will search all HDD & partition for any OS installations.
It will find your ubuntu install partition. It does not need to be primary partition like windows.

Is that what you are worried about ?

---

### Post by crownclown on 2010-12-18
> **BicyclerBoy said:**
> Grub is a bootloader.
It tries to support all OS.
You must have it for current linux/Ubuntu.

Windows uses similar tool (ntloader) but it is normally hidden.
The windows bootloader will not support linux/ubuntu AFAIK.

Both can provide a startup user interface /menu to allow you to choice which OS kernel version etc to load.

The window installer will break it by trying to replace it with a m$ tool.

Once you have a stable system you can edit the grub menu to reduce the clutter.
You can this info on Ubuntu website.
Don't be tempted to fix things that are not broken until you understand how to fix it.

What do you mean by:  "i just finish my update manager and now dont know what to do with it ? any suggestion?"

close it ?

Grub will search all HDD & partition for any OS installations.
It will find your ubuntu install partition. It does not need to be primary partition like windows.

Is that what you are worried about ?

About the finish update ,nope it just after update i dont know what to do next.it means that what should i do more is there any application that i should install ?

after google about the grub, to edit it i need to go to my menu.1st..
but when i go to dir boot/grub there's no such file ?
or it was at other dir?

---

### Post by Sealbhach on 2010-12-18
> **crownclown said:**
> 
well after the ubuntu installation at the boot screen it seems that i got so many thing that be boot..i think it is call grub or something.
how can i remove those thing and just have 2 boot o.s...


That's how it's supposed to be. Are you able to get into Ubuntu and Windows by choosing things from the grub menu?

If you can, then you don't have a problem.  Just leave it as it is until you learn a bit more about how to customize it.

.

---

### Post by crownclown on 2010-12-18
> **Sealbhach said:**
> That's how it's supposed to be. Are you able to get into Ubuntu and Windows by choosing things from the grub menu?

If you can, then you don't have a problem.  Just leave it as it is until you learn a bit more about how to customize it.

.

isit..ohhh....
okay then i will not edit it...
but may i ask u 1 things...
why i can't change anything in menu.1st (i found the menu.1st after remove something at synaptic package manager)
it say that i'm not the owner for root.
:cry:

---

### Post by Sealbhach on 2010-12-18
> **crownclown said:**
> 
why i can't change anything in menu.1st (i found the menu.1st after remove something at synaptic package manager)
it say that i'm not the owner for root.
:cry:

It's called menu.lst

That is an L, not a one.

The answer to your other question is:

> it say that i'm not the owner for root.

That is why you can't change it, and this is why you need to learn about root and sudo permissions before you try to change anything.

If you're a new user, just relax and enjoy using Ubuntu before you try changing anything like the grub menu - that is for more advanced users to do.

.

---

### Post by trinitydan on 2010-12-19
Furthermore, it sounds like you are looking at some outdated information.  You can no longer configure grub using /boot/grub/menu.lst in Ubuntu 10.10 which uses Grub 2.

---

### Post by crownclown on 2010-12-19
> **Sealbhach said:**
> It's called menu.lst

That is an L, not a one.

The answer to your other question is:



That is why you can't change it, and this is why you need to learn about root and sudo permissions before you try to change anything.

If you're a new user, just relax and enjoy using Ubuntu before you try changing anything like the grub menu - that is for more advanced users to do.

.

owhh..alright...i will try to enjoy it first...

---

### Post by crownclown on 2010-12-19
> **trinitydan said:**
> Furthermore, it sounds like you are looking at some outdated information.  You can no longer configure grub using /boot/grub/menu.lst in Ubuntu 10.10 which uses Grub 2.

???
Grub2?
so in this 10.10 version its on grub2..
thx man
btw

can some1 help me with this ?

[http://ubuntuforums.org/showthread.php?t=164846](http://ubuntuforums.org/showthread.php?t=164846)

---

### Post by HermanAB on 2010-12-19
Howdy,

Note that Linux tends to work very reliably till people start to change things.  So for starters, leave well alone - don't do updates, don't mess with system things, just try out all the available features and get familiar with the system, before you mess it up and have to re-install to get it working again...

---

### Post by crownclown on 2010-12-19
> **HermanAB said:**
> Howdy,

Note that Linux tends to work very reliably till people start to change things.  So for starters, leave well alone - don't do updates, don't mess with system things, just try out all the available features and get familiar with the system, before you mess it up and have to re-install to get it working again...


owkay...
so i wont install the nvidia first...thx for the info....

---

### Post by trinitydan on 2010-12-19
> **crownclown said:**
> owkay...
so i wont install the nvidia first...thx for the info....

Nvidia?  I don't follow you.  The link posted takes me to an archive about making a live CD.  Maybe there is a different link?

Nevermind, I found the thread.

[http://ubuntuforums.org/showthread.php?t=1648606](http://ubuntuforums.org/showthread.php?t=1648606)

---

### Post by crownclown on 2010-12-19
> **trinitydan said:**
> Nvidia?  I don't follow you.  The link posted takes me to an archive about making a live CD.  Maybe there is a different link?

Nevermind, I found the thread.

[http://ubuntuforums.org/showthread.php?t=1648606](http://ubuntuforums.org/showthread.php?t=1648606)

owhh u found the other link...
well nvm it just the same..so what should i do with it?
u got any solution with that ?

---

### Post by trinitydan on 2010-12-19
I don't have any ideas on that one, but I wouldn't rule out the possibility of someone coming along that does have an answer they can step you through.  As said by others in this thread, just take your time and get familiar with the system a bit and try to learn your way around.  Use the forum, many questions you have will probably already have been asked before so use the search, and in time hopefully some solutions will start to come up for your accelerated graphics and other issues.

---

### Post by BicyclerBoy on 2010-12-19
How did you attempt to install/activate the nvidia driver ?

o   Administration/Hardware drivers

o   synaptic manager

o   nvidia install script ?

Your 310M is the GPU in a laptop or all-in-one mini PC ?

The usually problem with *buntu 10.04 nvidia graphics is that the nouveau driver is loaded first. The nouveau driver is foss & *buntu compliant.

You can check/read the xorg log files to start to debug.

The problem could also be that the package manager nvidia driver is to old for the GT310M. I think you need a more recent version than is available from Ubuntu.

 Solving these problems is not trival for novice user..

Please note that when your PC fails to start the X server GUI it just means there were serious errors loading the X server. The computer is still working & functional if you know how.
You can always use your install CD/DVD as a rescue disk; no damage to your install.

---

### Post by crownclown on 2010-12-19
> **BicyclerBoy said:**
> How did you attempt to install/activate the nvidia driver ?

o   Administration/Hardware drivers

o   synaptic manager

o   nvidia install script ?

Your 310M is the GPU in a laptop or all-in-one mini PC ?

The usually problem with *buntu 10.04 nvidia graphics is that the nouveau driver is loaded first. The nouveau driver is foss & *buntu compliant.

You can check/read the xorg log files to start to debug.

The problem could also be that the package manager nvidia driver is to old for the GT310M. I think you need a more recent version than is available from Ubuntu.

 Solving these problems is not trival for novice user..

Please note that when your PC fails to start the X server GUI it just means there were serious errors loading the X server. The computer is still working & functional if you know how.
You can always use your install CD/DVD as a rescue disk; no damage to your install.


well it's inside my laptop. "[COLOR=Red]You can always use your install CD/DVD as a rescue disk; no damage to your install " [COLOR=Black]so i though there is no other choice so i just reformat..so sad T.T :icon_frown:

[/COLOR][/COLOR]

---

