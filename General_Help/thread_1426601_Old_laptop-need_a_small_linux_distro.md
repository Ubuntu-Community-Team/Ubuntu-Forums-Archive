---
title: "Old laptop-need a small linux distro"
date: 2010-03-10
forum: General Help
---

### Post by kevintp on 2010-03-10
I have a Dell laptop with 256mb of memory that I would like to install a linux distro to. I have no need anymore for windows junk. I; however, was trying to use puppy but it kept crashing and would not load the OS after 3-4 days of use. Can you recommend something similar that's easy to use and could be installed with 256mb of memory. P.S. I am an intermediate type "tech".

---

### Post by darolu on 2010-03-10
Can you provide more information about your laptop? what micro processor does it have? video card?
Anyways, technically, with 256MB of RAM you can run Ubuntu 8.04 LTS or even 9.04, if you have ~10GiB for / you can try Slackware, in my experience, is the distro that gives the best performance; I think Debian 5 should run fine too. The "lightest" distro I know is DeLi Linux, in its website they have images of a i486 with 16MB RAM machine running it. [http://www.delilinux.de/](http://www.delilinux.de/)

---

### Post by snowpine on 2010-03-10
Hi Kevin, I have a couple of old Dell laptops (Latitude Cpx and Inspiron 3800, both with 256mb ram). You should post more detailed hardware specs if you want specific advice. :)

I have retired both of these laptops for everyday use, as they are quite slow for everyday purposes compared with the netbooks that replaced them. However, in the past they were my "learning about Linux" computers and I have successfully installed Ubuntu, Xubuntu, CrunchBang, AntiX, SliTaz, CentOS, Debian etc. in search of the perfect distro. 

Puppy is one of the lightest distros there is; if it's crashing, that points to a hardware issue of some kind perhaps. 

If getting advice here on Ubuntu Forums is important, either Xubuntu or the upcoming Lubuntu would be good choices.

---

### Post by river226 on 2010-03-10
Damn Small Linux is another good small Linux distro: [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
as well as Tiny Core: [http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/](http://distro.ibiblio.org/pub/linux/distributions/tinycorelinux/)

---

### Post by kevintp on 2010-03-10
I apologize guys for that. I have 20 gigs on the hard drive and 8mb on video. The rest of the settings are below: 


System Manufacturer: Dell Computer Corporation
       System Model: Latitude CPx H500GT             
               BIOS: Phoenix ROM BIOS PLUS Version 1.10 A12
          Processor: Intel Pentium III, ~490MHz
             Memory: 256MB RAM
          Page File: 176MB used, 826MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.5512 32bit Unicode


I have tried running ubuntu 8.04 and xubuntu but they slow down the machine after all updates

---

### Post by kevintp on 2010-03-10
By the way, did I mention that this was a laptop.

---

### Post by Tahakki on 2010-03-10
Damn Small Linux is very good, but doesn't use standard software.

---

### Post by snowpine on 2010-03-10
Hi Kevin, I have that **exact** computer! :) It will not be "fast" with *any* distro, but you should be able to use it to surf the web (not Youtube or anything), do some light word processing, etc. Mine is currently running a distro called AntiX.

ps I hope you did a full, regular install and that you're not using wubi. ;)

---

### Post by kevintp on 2010-03-10
Did a full install but just like you mentioned snowpine. I need to "max-out" the memory to 512 but I am even wondering if I should do that since it is so old and may totally kill on me in a few weeks to months. Don't get me wrong it has no dents nicks, or scratches just old. And, if I upgrade the memory I might get better options, but right now I think I may stick with the 256mb.

---

### Post by RedSquirrel on 2010-03-10
You could try installing a minimal Ubuntu or Debian system. Add a light window manager such as fluxbox, openbox, or icewm.

Here is one guide for Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you're comfortable doing package management and other tasks on the command line, then you don't need synaptic (or gksu). You can also drop gdm if you don't mind logging in on the console and running 'startx'.

---

### Post by kevintp on 2010-03-10
I thought about damn small linux too but now it's status on distrowatch.com is listed as "dormant." Don't know if that is good or not in terms of security's concern.

---

### Post by kevintp on 2010-03-10
Guys would me booting from a usb of puppy make it a little faster?

---

### Post by snowpine on 2010-03-10
> **kevintp said:**
> Guys would me booting from a usb of puppy make it a little faster?

The Latitude Cpx is not capable of booting from USB.

A faster computer will make Puppy faster for sure. ;)

---

### Post by anticapitalista on 2010-03-10
What are you hoping to do on that laptop?
I ask as people have expectations of what a modern linux can do that doesn't really fit reality.
A 10 year old box is a 10 year old box and even the best up-to-date linux will not perform as well as that box did 10 years ago.

Having said that, try my antiX, or similar light distros such as slitaz, puppy, tinyme, vector, wolvix ...

---

### Post by marshag63 on 2010-03-10
How about Linux Mint Fluxbox:

[http://www.linuxmint.com/rel_helena_fluxbox.php](http://www.linuxmint.com/rel_helena_fluxbox.php)

or you could go without a GUI at all like INX ([http://inx.maincontent.net/](http://inx.maincontent.net/))

MarshaG.

---

### Post by rokytnji on 2010-03-10
Antix ran so good on my IBM 390E with 256mb of ram that I was able to sell it for $100.00 (yesterday) to a person that wanted to run Linux and was impressed with the speed.

I had it set up with 6 gig for root
13.? gig for /home
512 mb for swap partition.

Ran wireless Dlink wna1330 G PCMCIA with Atheros chipset. Runs the 2.6.31 Liquorix Kernel in AntiX 8.2.
The guy likes it.

---

### Post by kevintp on 2010-03-11
Thanks redsquirrel for the article. It helped a lot

---

### Post by kevintp on 2010-03-11
Thanks everyone for the info. As for answering the question for "what do I really expect to do?" I just wanted some options so I know which way to go besides for puppy, xubuntu, or damn small linux. Thanks again everyone.

---

### Post by kerry_s on 2010-03-11
i use debian lxde on 450mhz 256mb ram.
grab the net installer & select advanced-> other desktops-> lxde.

[http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.4/i386/iso-cd/debian-504-i386-businesscard.iso)

---

### Post by darolu on 2010-03-11
Full specs help a lot when recommending a distro. With that processor your options are down to really light distros.

The options most people have made are OK, I'd go with either [Antix]("http://antix.mepis.org/index.php/Main_Page") or [Deli Linux]("http://www.delilinux.de/"). [Damn Small Linux]("http://www.damnsmalllinux.org/index_es.html") is also an option.

Any *buntu won't run at a decent speed regardless of what desktop environment you use, so I wouldn't recommend xubuntu, lubuntu, etc., some 'new' distros may work but without a GUI.

If you have enough experience in customizing kernels and packages, you can try Gentoo or ArchLinux, fully customizing every package to use as few resources as possible.

---

### Post by NightwishFan on 2010-03-11
I would run Debian on such a machine. As was suggested above, try LXDE or XFCE. If you are a real minimalist try Fluxbox. I run the full Gnome desktop in virtual machines that use only 256mb of RAM.

---

### Post by kio_http on 2010-03-11
Try an OS like moblin or anything designed for netbooks. Kubuntu 9.10 with 512 MB RAM runs fine on a laptop with similar specifications (With desktop effects off).

---

