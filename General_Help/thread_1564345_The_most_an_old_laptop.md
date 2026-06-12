---
title: "The most an old laptop"
date: 2010-08-30
forum: General Help
---

### Post by Skriblinmatt on 2010-08-30
Not sure if this is the best place to post this thread, sorry if it's not!
 
I'm new (maybe a month) to Linux and I love it. I love learning it and have read this intro to Linux book (Linux in Easy Steps by Mike McGrath) cover to cover twice and spent about 40-50 hours reading free online stuff. I'm ready for more advanced learning. 
 
**First **of all I got this old laptop from my uncle. It has MS XP (which I intend to wipe off) on it about a 40 gig HD a Pentium (R) 4CPU 1.60GHz and 256 mb of ram. I'd like to install a Linux Distro with little to no GUI. I understand that can be done with any distro, but need to know, does anyone think UBUNTU is BEST for this? I want to do this for three reasons. 
1). I have a desktop with Ubuntu and the laptop will be essentially a toy. 
2). I want to get the most out of this old laptop, so I don't want to waste disk space with OS junk. I do want to be able to launch Openoffice and Firefox and maybe a video player (what's the point of a computer you can't watch Doctor Who on?) but don't need fancy stuff.
3). If I NEED to use the Terminal to navigate it will drastically increase my efficiency and motivate further learning.
 
**Second**, can anyone please suggest books or other reading material that will take me to "the next level". (please hurry will I'm still having fun!):P

---

### Post by bobnutfield on 2010-08-30
This:

> First of all I got this old laptop from my uncle. It has MS XP on it about a 40 gig HD a Pentium (R) 4CPU 1.60GHz and 256 mb of ram. I'd like to install a Linux Distro with little to no GUI. 

and this:

> 2). I want to get the most out of this old laptop, so I don't want to waste disk space with OS junk. I do want to be able to launch Openoffice and Firefox and maybe a video player (what's the point of a computer you can't watch Doctor Who on?) but don't need fancy stuff

Are conflicting.  If you want GUI applications, you must have a GUI.  Almost any distro offer you a minimal desktop.  Openbox, fluxbox, etc.  

If you want to learn classic Linux, I suggest Slackware with a lightweight desktop.  Slackware differs greatly from Ubuntu, but it is the most Unix-like distro out there and the oldest living Linux distro.
I have been using it for years, and it taught me more about Linux in three months than any other distro did in five years.

Check it out.

---

### Post by decoherence on 2010-08-30
Hey there. If you want something like Ubuntu but lighter weight, there is Lubuntu, which uses a basic, stripped down interface while still being easy to use.

My favourite 'fast and light' Ubuntu-based distro is CrunchBang

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Also, if you're enjoying learning and want to take it to the next level, you should look at installing a system that requires more setup (and thus allows more customization.) Slackware is a good suggestion, or a stage 1 Gentoo install.

I would suggest NetBSD based on the strength of its built-in documentation and the fact that it doesn't presume to know what you're going to do with the system. While you don't technically have to build it from scratch, it will seem like you do. But like I said, the built-in docs (man pages) are top-notch so if you don't mind doing a lot of reading, you'll learn a lot and have no problem getting set up.

Almost anything you would learn setting up NetBSD would be applicable to any linux distro. NetBSD is just a bit more 'sane' with less potential for a userland bugs making things that should work, not work.

ADD: If you're looking for a fast, lightweight window manager, once you've got your basic system going, WindowMaker has always been my choice on NetBSD systems. Of course, these days OpenBox or PekWM do just as well (but they aren't as pretty and WindowMaker has a nice preferences program)

---

### Post by jfreak_ on 2010-08-30
+1 to crunchbang. light and responsive.

---

### Post by Skriblinmatt on 2010-08-30
Great!  Thanks so much to all.  I will play with this stuff for a couple days.  Bob, sorry if my post was confusing (to be honest I really don't even know what I said that was conflicting).  I have a LOT to learn and am very greatful for this forum and the quick feedback!!!

---

### Post by borth92 on 2010-08-30
bob was saying that programs like openoffice have a gui, and thus need an os with a gui to function

---

### Post by deserthowler on 2010-08-30
> **borth92 said:**
> bob was saying that programs like openoffice have a gui, and thus need an os with a gui to function

I use Debian without a GUI.  I use fvwm2 window manager and can run Open Office, Firefox, etc.  It will also work with TWM.  They are window managers and not GUIs.

Some of the GNOME and KDE programs will download a lot of extra stuff to support them.

Debian will probably be the most like Ubuntu for you.  You can get the net install and just keep adding things as you want.

Earl

---

### Post by borth92 on 2010-08-30
> **deserthowler said:**
> I use Debian without a GUI.  I use fvwm2 window manager and can run Open Office, Firefox, etc.  It will also work with TWM.  They are window managers and not GUIs.

Some of the GNOME and KDE programs will download a lot of extra stuff to support them.

Debian will probably be the most like Ubuntu for you.  You can get the net install and just keep adding things as you want.

Earl

He was referring to a pure command line OS, which does not naturally run programs with a gui.

---

### Post by bobnutfield on 2010-08-30
> First of all I got this old laptop from my uncle. It has MS XP (which I intend to wipe off) on it about a 40 gig HD a Pentium (R) 4CPU 1.60GHz and 256 mb of ram.

Those specs are plenty for most distros, but I would definitely upgrade ram to at lease 1GB.  You will a lot better performance.

I have a number of laptops with similar specs, all running linux quite nicely, but all have at least 1GB ram.

---

### Post by snowpine on 2010-08-30
Ubuntu can meet your needs (if you do a Server or Minimal) install but IMHO it is not "the best" distro for older hardware.

CrunchBang is my personal favorite, also very nice are AntiX, Puppy, SliTaz, etc.

One option if you are already running Ubuntu on a fast computer is to remotely run "heavy" applications like OpenOffice over the network using SSH or LTSP. I have an old laptop with simliar specs to yours, I use it to log in and access applications and files on my server.

---

### Post by snowpine on 2010-08-30
Ubuntu can meet your needs (if you do a Server or Minimal) install but IMHO it is not "the best" distro for older hardware.

CrunchBang is my personal favorite, also very nice are AntiX, Puppy, SliTaz, etc.

One option if you are already running Ubuntu on a fast computer is to remotely run "heavy" applications like OpenOffice over the network using SSH or LTSP. I have an old laptop with simliar specs to yours, I use it to log in and access applications and files on my server.

---

### Post by Skriblinmatt on 2010-09-02
Please check out this link to a thread on the crunchbang forum.  I posted it to get help with an install problem I am having.  I thought since #! was recomended to me here, it is Ubuntu based and this site gets WAY more traffick I might get the problem solved this way.  [http://crunchbanglinux.org/forums/topic/9344/absolute-beginner-help/](http://crunchbanglinux.org/forums/topic/9344/absolute-beginner-help/) I hope that's OK to do.  Thank you for looking!!

---

### Post by Skriblinmatt on 2010-09-02
I found this guide for a statler usb install that doesn't look like it requires image writing. [http://crunchbanglinux.org/wiki/statler_usb_installation](http://crunchbanglinux.org/wiki/statler_usb_installation)
 
I have never unmounted anything before.  What's the proper syntax? (step 2)

---

