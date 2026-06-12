---
title: "Slow boot with 10.04"
date: 2010-05-03
forum: General Help
---

### Post by jschille on 2010-05-03
I am getting a much slower boot with the 10.04 upgrade.
After choosing which partition to use I get the blinking white cursor in the upper left hand corner and the "Boot from (hd0,4) ext 3..." sits there for a while before coming to the log in screen.

There have been quite a few posts about this, a lot of people are saying disabling the floppy drive in the BIOS has worked for them.  I don't have a floppy drive on my laptop, so looking for some ideas on how to fix this problem.

Thank you

---

### Post by acejoneyboy on 2010-05-03
if it is the thing about the floppy drive, try disabling it from the BIOS, see if that works

---

### Post by jschille on 2010-05-03
> **acejoneyboy said:**
> if it is the thing about the floppy drive, try disabling it from the BIOS, see if that works

 As stated above I have no floppy drive to disable in my BIOS because my laptop does not have a floppy drive, so I was wondering if there were other fixes to the problem besides disabling the floppy drive.

---

### Post by fooey on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

(the sticky up top) talks about slow bootup issues. may be worth checking out some possible solutions said in that thread link^

---

### Post by jschille on 2010-05-03
> **fooey said:**
> [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

(the sticky up top) talks about slow bootup issues. may be worth checking out some possible solutions said in that thread link^


The only response to the slow boot in the bug threat is to disable the floppy drive.  I read someone that there might be a "hidden" floppy drive somewhere.

Still have no solution to this slow load and am jealous of all these people who disable the floppy drive and boot in < 10 seconds.

---

### Post by techunit on 2010-05-03
Well ok can we know some info on your system so can get an idea of a good boot speed on your system.

---

### Post by techunit on 2010-05-03
Ok so I was facing something similar. I got a blinking curser for say 15 seconds then an instantaneous boot splash then the log in screen. 

See if this sounds like your problem:
[http://ubuntuforums.org/showthread.php?p=9212520#post9212520](http://ubuntuforums.org/showthread.php?p=9212520#post9212520)

---

### Post by jschille on 2010-05-03
Sure, I have a Dell Studio XPS
4 gigs of ram
and a core 2 duo P9600 @ 2.66

I also am using Nvidia drivers

---

### Post by techunit on 2010-05-03
Ah did you install the restricted graphics driver? Please answer first before you go and try to get them because they are messing things up for a lot of people. Please look at my last post.

---

### Post by jschille on 2010-05-03
Hmm.. I don't know.
When I go to System --> Admin --> Hardware Drivers
it shows my NVIDA accelerated driver (version current)[Recommended]
the driver is activated and currently in use.

That's all I can give you, sorry, pretty new to this whole thing.

---

### Post by techunit on 2010-05-03
You may have to disable it because it is causing this problem look at the link I posted if you haven't already started reading.

---

### Post by jschille on 2010-05-03
> **techunit said:**
> You may have to disable it because it is causing this problem look at the link I posted if you haven't already started reading.

Hmm.. if I disable it will I will be running off of on-board video?
What will I lose?

Can it be assumed that in a week a hot-fix will come out for this problem?

---

### Post by techunit on 2010-05-03
it vary much depends on if ubuntu has the preinstalled drivers in it. (probably does) I think that you sould look and see if my link that I provided helps you have not notified me of any thing that would sugest that you have looked at. I hope you do that was how i dealt with problem hope this helps.

---

### Post by jschille on 2010-05-04
> **techunit said:**
> it vary much depends on if ubuntu has the preinstalled drivers in it. (probably does) I think that you sould look and see if my link that I provided helps you have not notified me of any thing that would sugest that you have looked at. I hope you do that was how i dealt with problem hope this helps.

I looked at it.  I am worried about disabling my Nvidia drivers.
Will the commands given for your Radeon be the same for my Nvidia?

I think I have decided to give up on the issue of the slow boot and poor resolution on the splash screen and just pray that the devs bring out a hot-fix in the near future.

---

### Post by techunit on 2010-05-04
I will check for you this is an important question. No I think you need to remove them using defferen't commands... I am sorry I forgot about this. I will try to hlep you further if you like...

I think that just disabling the driver in the HardwaremDrivers application fixed part of the problem then I used a generic command to fix the boot splash... I can repost the code here if you like.

---

### Post by techunit on 2010-05-04
I will post the information that fixed my blinking curser problem soon...

---

### Post by BrokeMahPC on 2010-05-04
@ techunit and jschille
(Don't mind the pm techunit)

The Nvidia drivers do not conflict like the ATI ones do. On the X Troubleshooting page there is a similar code 'recipe' for removing and reinstalling both Nvidia drivers - I recommended it to someone and it didn't work. I think the 1st command is wrong. I found this alternative 1st line but no idea if it works yet:
sudo apt-get --purge remove nvidia-glx-* nvidia-settings
[https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)

Not sure if they entered them correctly but they were left with no drivers at all on the system. I am currently trying to get it back!

The 2 lines that enable the framebuffer work - have you tried them?
 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u

Check here for known bugs and fixes - shows the above:
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

Good info on lucid is a bit thin - I would resist the temptation to fix things - suffer minor inconveniences as Lucid still looks like it isn't finished and requires some fixing and testing. 
Firefox is crashing me at the moment, horizontal scrolling or maximising the window occasionally crashes the video card. I have gotten DVI-No signal, white screen of death and a black screen of death - I have not altered anything! Could be Drivers, Compiz or Firefox (I suspect compiz)

---

### Post by techunit on 2010-05-04
This should help some. Good Luck.

---

### Post by BrokeMahPC on 2010-05-05
[COLOR=Black]There[/COLOR][COLOR=Black] is 1 fix for mentioned in:[/COLOR][B][COLOR=DarkRed]
[/COLOR][/B][COLOR=DarkRed][COLOR=Black]http://ubuntuforums.org/showthread.php?t=1469475[/COLOR][/COLOR][B][COLOR=DarkRed]

[/COLOR][/B][COLOR=Black]Hope it helps[/COLOR][COLOR=Black]!
[/COLOR][B][COLOR=DarkRed]
[/COLOR][/B]**[COLOR=DarkRed]Bootup/Plymouth.[/COLOR] **
Users should experience a much faster boot however some users may  experience problems with Plymouth after the nVidia graphics driver has  been enabled. Users may experience plymouth using lower graphics  resolution. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013")

Graphical solution : [http://news.softpedia.com/news/How-t...4-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
     ```
gksu gedit /etc/default/grub 
``` and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via  VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** Save the file and run:
     ```
sudo update-grub 
```The resolution chosen should be your monitors native resolution.

Other graphics card users may get a black screen with flashing cursor  and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801")
One fix for this is to create this file.
     ```
gksu gedit /etc/initramfs-tools/conf.d/splash 
``` and add this option FRAMEBUFFER=y, save the file.
Then
     ```
sudo update-initramfs -u 
```Plymouth now has a hard dependency on mountall thus trying to  remove Plymouth would remove half the OS. The advice is, if you don't  want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the  floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712")

If the problem is plymouth not displaying, and a black screen from grub  to gdm, this could be due to graphics drivers needing to be loaded  quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787")

Plymouth is installed with 2 themes by default you can install more via  synaptic.
To change themes this code is used.
     ```
sudo update-alternatives --config default.plymouth
```

---

