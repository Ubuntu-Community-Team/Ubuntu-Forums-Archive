---
title: "Blank screen... No distro works!"
date: 2011-09-22
forum: General Help
---

### Post by adie273 on 2011-09-22
Ok so I use to use ubuntu, then the new gnome desktop hacked me off, so I went to opensuse. Worked fine for AGES then all of a sudden I turn on my laptop, it boots to GDM but only shows the background, no login box.

Couldn't fix it at all, grew tired, decided to try Kubuntu for a little change. Used live CD, was impressed, installed it then.... After GRUB's done it's job it sits on a black screen and doesn't respond. Couldn't fix it either, it just wouldn't let me do anything. Decided to try Debian Squeeze as a last resort, thinking to myself, a nice stable distro. 

but guess what?....... Same problem persists here too, GRUB then nothing!


Has anyone any idea what's going on? It's the first I've encountered this. 

Thanks for any help.

---

### Post by Immolatus on 2011-09-22
try installing a new theme for KDM from the command line (Ctrl+Alt+F1) log in there. I think somehow your KDM settings are not static. sometimes INIT scripts can be generated for you unpon install, like xorg.conf is generated auto when you install GPU drivers.

Maybe if you just reinstall KDM from root shell:
(try updating first)
sudo apt-get update KDM

or try:
sudo apt-get remove KDM
then:
sudo apt_get install KDM

---

### Post by adie273 on 2011-09-23
Thanks for your help, I did all that and now instead of. Blank screen it displays the kubuntu 11.04 with the 4 constantly changng colour dots and just hangs there for what is now 35 minutes (left it to make tea incase it was some first time boot thing). 

Needless to say ive no idea how to solve this and I'm that fed up with always taking the lengthy route for a short cut with Linux, that I'm just switching back to good old windows 7 full time.  As much as I love(d) Linux, the cost of windows is dwarfed by this continual random hassle that your presented with all too often now unless it's simple computing your doing.

Thank you for your help, it's greatly appreciated, but for my computer needs and the software I use this constant unreliability to keep functioning normally is too much hassle now. Maybe someday this will stop and Linux distros will have their day.

---

### Post by Quackers on 2011-09-23
Which graphics card are you using?

---

### Post by adie273 on 2011-09-23
It's some old s3g unichrome thing, nothing special. Opensuse, mandriva, ubuntu, kubuntu, Linux mint and fedora all worked up till now. I haven't tried reinstalling opensuse again, I maybe should. But I did try fedora, mint, ubuntu and kubuntu and every single one doesn't work.

Everything was fine until an android app I built and tried test. The emulator randomly stopped working and I got fed up trying to work out why, I shutdown the laptop. Upon turning it on, opensuse stopped working. I wanted a deb distro anyway, so installed kubuntu, mint and Debian to no avail. Tried fedora despite it being rpm. And no joy. I'm stumped as to the problem. I can only imagine it's a hardware issue that's now cropped up.

---

### Post by Quackers on 2011-09-23
It sounds like something is broken, but not sure what that may be.
If you boot from a live cd and select "try Ubuntu" does the desktop load?
If not try some boot options, like nomodeset, for instance.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by adie273 on 2011-09-23
That's the bit that confuses me, every live cd works without problem. I go to install, again without issues. But then when it's done and I reboot, I get GRUB, I select Linux (or it does it itself) and that is where I get a blank screen and nothing else. No response from it, even hitting the keyboard, nor does this hard disk/DVD busy light on the laptop do anything. 

Booting into Windows 7 on the other hand on the other partition is flawless. 

It's the first I've come across this and as a result have no idea how to solve it. I can only figure it's a hard disk thing since that's the only changing factor between a live cd and booting from hard disk. But I can't explain why it's just that partition.

---

### Post by Quackers on 2011-09-23
How far into the disc is the partition for Ubuntu/kubuntu?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dragonbite on 2011-09-23
Can you get an Ubuntu Live CD from pre-10.04?

In 10.04, some graphic chips, specifically Intel 855 and 915, their support was regressed in the kernel.  During bootup it would give a black screen and lock up completely and this hit all of the Linux distributions. Ubuntu was the first hit only because they were the first to release (April, 2010) with the updated kernel. Fedora came out in May that year I think and had at least a basic work-around that didn't black-screen, but didn't offer much.  OpenSUSE came out in June or July that year.

Out of these, I have found Fedora 14 to be the last distribution that handles the Intel chip, complete with Desktop effects.  

Of course what you are describing does not quite sound like that.

It could be that something related to the graphics (xorg? drivers?) is different between the live and the installed versions,, or as mentioned there is a hardware failure somewhere (hard drive?) that is bypassed when running it off of a DVD.

---

### Post by adie273 on 2011-09-23
Ok windows it is. It appears to be getting worse.

I booted the live cd. At the point it asks to try kubuntu or install it, instead of booting into the kubuntu desktop like it used to when I hit try kubuntu..... It now freezes! Again, the computer does not respond.  I'm stumped. Windows works for as long as I need to without error and now Linux just won't do a thing bar install itself!!!

---

### Post by Quackers on 2011-09-23
It may be an idea to try a SMART test on your hard drive or possibly a ram test.

---

### Post by Dragonbite on 2011-09-23
When I run into strange hardware issues, I usually give Fedora a try because it has worked where Ubuntu and openSUSE doesn't, and Ubuntu has worked where Fedora hasn't.

---

### Post by adie273 on 2011-09-23
I'll try a smart test, tried a ram test and all checks out fine.

---

### Post by adie273 on 2011-09-23
Tried fedora, exact same issue. I'll try kubuntu again. If that fails I'll reinstall opensuse 11.4, which is what I was using until everything broke all of a sudden. If that fails then screw it

---

### Post by adie273 on 2011-09-23
Right, reinstalled kubuntu, but changed the partition for kubuntu and the swap partition as well as their sizes, incase it was something to do with where kubuntu was installed exactly on the disk. kubuntu now boots!!! But......

Once I log in on KDM, I then get the background and nothing else.

---

### Post by coldraven on 2011-09-23
Ubuntu 8.04 is the last release which will work on my neighbours PC. It has that Intel chipset mentioned above.

---

### Post by adie273 on 2011-09-23
It's a VIA s3g unichrome pro. Not intel. 

It sounds extremely odd, but I've noticed that if I hold down ctrl and alt, it boots much faster and after logging into KDM it comes up with the splash screen instead of hanging.... But stops and drops back into KDM. As much as I'd prefer a deb distro, I'm gonna try opensuse again and see if that at least works.

---

