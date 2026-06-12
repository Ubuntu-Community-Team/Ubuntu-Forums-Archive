---
title: "Missing GNOME on my install? (I'm new, please help)"
date: 2006-05-10
forum: General Help
---

### Post by Claire on 2006-05-10
Okay, so, here's how the story goes.  I got really mad at windows, did some research, and decided on Ubuntu Linux.  I completely deleted windows (bah, long story behind it too), then downloaded and installed Ubuntu Linux using instlux ([http://sourceforge.net/projects/instlux)](http://sourceforge.net/projects/instlux)).  Everything went just fine until I rebooted the computer and it was loading.  At first, everything seemed to be loading fine, I got a nice little screen and messages under it OKing all the systems.  And then it went to the text prompt screen.  As far as I can tell, I am somehow missing the GNOME desktop.  Now, I'm usually pretty computer-savvy.  I tried rebooting.  I tried typing help and looking through the commands they listed, trying to run some of them.  I tried to find help online (obviously on another computer).  Ran some of the commands through that they suggested.  (Including (but not limited to): sudo dpkg-reconfigure xserver-xcrg, sudo dpkg-reconfigure gdm, sudo apt-get install ubuntu-desktop, sudo update-alternatives --all.)  I just kept getting back something along the lines of:

Reading package lists... Done 
Building dependency tree... Done 
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
(Then a couple lines really similar to that one.)
W: You may want to run apt-get update to correct these problems 

Tried running apt-get update, same problem.  I'm kind of frustrated.  (](*,) seems about right.)  Am I just missing the GNOME desktop?  How can I remedy this?  Is it even possible to remedy it if the only operating system on that computer is now the faulty linux?  Do I have to reinstall windows onto it?  Help . . . please . . .

---

### Post by lorne_kun on 2006-05-10
It would help if you posted your hardware profile so that we can see if its a hardware problem, some hardware is unsupported, now Im no linux expert, I think some of the more experienced people can help you with that. Im just lucky that it worked on the first try. Something you can also try is simply reinstalling ubuntu if all else fails.

---

### Post by WildPenguin on 2006-05-10
I can't say I have heard of instlux before, so I'm not sure exactly how reliable it is, but it does seem to have given you a very minimalistic Ubuntu install.

Is the machine connected to the internet when you run apt-get? If not, it may be easier to download the .iso (using another computer, of course), and reinstall Ubuntu using a bootable CD. Since configuring everything solely via the command prompt can be rather difficult to if you are new to Linux (or even if you have been using it for awhile).

---

### Post by z_diver on 2006-05-10
This is an interesting issue.  I've never tried instlux but I assume it starts a default breezy(5.10) install.  

You said it starts booting OK, which means you get past the grub bootloader section.  You mention a "text prompt screen", and it seems you are running lots of command line options so I'm guessing it has installed something along the lines of a basic server install which is probably not what you wanted anyway.  On top of that, it seems the network is not configured properly.  

I would recommend downloading and booting from the newest Dapper Live CD, and then if you are happy with the way it works, clicking the Espresso install icon on the desktp and it will be a very straight forward and fast installation.  Then you will be able to reboot and have a fully functioning desktop.

Dapper is still beta right now so you may or may not want to keep up with all the updates they are currently going through.  After June 1st, developement should slow down and the updates will be much lighter and smaller.

[http://releases.ubuntu.com/6.06/]("http://releases.ubuntu.com/6.06/")
I'd get the LIVE cd that is appropriate for your hardware and it has a nice fully graphical installation program built in.

---

### Post by Maureen on 2006-05-11
This is probably a foolish question, but what happens when you type "startx" at the command prompt? Perhaps for some reason X-Windows simply isn't launching at startup?

---

### Post by Claire on 2006-05-11
I already tried "startx" (thanks for the tip anyway though because I am *completely* new to Linux).  Yesterday, I was fiddling around some more, and I managed to run aptitude (though I'm guessing an abbreviated version) so that allowed me to look through the packages, and there wasn't even an "installed packages" section, just "global and locally created packages" and "virtual packages," and looking through there, I could see that certain things were missing, but they were all cited as "unavailable for install."  I reran the base configuration, but when it came to getting the packages, none of the https or ftps worked (again, all unavailable, although I know the computer is connected to the internet).

Currently I am trying to just burn a CD with an iso image to boot from (but now *this* computer is having problems with iso recorder).

As far as my hardware goes, it's a 2000 IBM ThinkPad laptop with an intel processor and a 20gb hard drive (not sure about that much more than that, it's actually my dad's old work laptop), and I have a wireless internet connection.  I read somewhere that sometimes Ubuntu has issues recognizing the internet connection from laptops, so maybe that's the problem?

Anyway, thanks for all the help, and I'm hoping to get this sorted out today . . .

---

### Post by Al3xanR0 on 2006-05-11
[QUOTE=Claire]Okay, so, here's how the story goes.  I got really mad at windows, did some research, and decided on Ubuntu Linux.  I completely deleted windows (bah, long story behind it too), then downloaded and installed Ubuntu Linux using instlux ([http://sourceforge.net/projects/instlux)](http://sourceforge.net/projects/instlux)).  Everything went just fine until I rebooted the computer and it was loading.  At first, everything seemed to be loading fine, I got a nice little screen and messages under it OKing all the systems.  And then it went to the text prompt screen.  As far as I can tell, I am somehow missing the GNOME desktop.  Now, I'm usually pretty computer-savvy.  I tried rebooting.  I tried typing help and looking through the commands they listed, trying to run some of them.  I tried to find help online (obviously on another computer).  Ran some of the commands through that they suggested.  (Including (but not limited to): sudo dpkg-reconfigure xserver-xcrg, sudo dpkg-reconfigure gdm, sudo apt-get install ubuntu-desktop, sudo update-alternatives --all.)  I just kept getting back something along the lines of:

Reading package lists... Done 
Building dependency tree... Done 
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
(Then a couple lines really similar to that one.)
W: You may want to run apt-get update to correct these problems 

Tried running apt-get update, same problem.  I'm kind of frustrated.  (](*,) seems about right.)  Am I just missing the GNOME desktop?  How can I remedy this?  Is it even possible to remedy it if the only operating system on that computer is now the faulty linux?  Do I have to reinstall windows onto it?  Help . . . please . . .[/QUOTE]

This sounds like a connection issue, post the output of 

ifconfig and route if it is not a connection issue then you may need to update your /etc/apt/source.list [here]("http://www.ubuntulinux.nl/source-o-matic") is a great place to get updated sources.

---

### Post by IYY on 2006-05-11
> I already tried "startx" (thanks for the tip anyway though because I am completely new to Linux).

And what happened then? Did just Gnome fail to start, or the entire X server?

---

### Post by Claire on 2006-05-11
Thanks everyone for the help; I finally managed to fix the iso recorder, burn the iso image to CD, and boot from that, reconfiguring everything, and now it works (I think something was just wonky with how it was connecting to the internet before because I had to fix the internet connection now too from within gnome).  I'm pretty excited now!  So far, I like it.

---

### Post by Bloch on 2006-05-11
Be sure to read about and install easyubuntu to get all the propietory codecs.

> [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

That link you gave to "instlux" goes to a page headed INVALID PROJECT

As Dapper Drake is out soon you might like to play around for the next two weeks and then download and install afresh.
Good luck with your new system.

---

