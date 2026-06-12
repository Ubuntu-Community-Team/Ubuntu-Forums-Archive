---
title: "distro choice for a low-end machine"
date: 2010-04-22
forum: General Help
---

### Post by blwizard on 2010-04-22
Hi guys. I've got a machine with P4 1.6GHz and 512M ram. It's a bit laggy when running ubuntu 9.10. Especially after i open up Eclipse, things start to get very slow. I'm thinking about installing Xubuntu, but am wondering if installing debian(or arch) then xfce would be equivalent to installing Xubuntu, or would it be faster when using debian(or arch)+xfce combination?

Reason why I'm thinking about this is that the Ubuntu family including Xubuntu, tendd to integrate too much stuff for ease of use, while installing system from scratch and then building up from that could avoid those unnecessary extra features. What do you guys think?

---

### Post by darolu on 2010-04-22
Xubuntu and Ubuntu are not that different, even when Xubuntu uses XFCE it comes with GNOME apps and libraries, making it almost equally resource-demanding.
Lenny (Debian 5) should work great in that machine, give it a try; if you're used to Ubuntu you won't notice the difference.
If you have enough hard drive (~8GB+ for /) you can try Slackware, it's really neat, I've gotten the better performance from my old machines using it (choosing xfce), it should work great in that machine too.

---

### Post by blwizard on 2010-04-22
Thanks a lot for your reply mate! 

Okay, I'll try Debian then. I was also thinking about installing Gentoo. I used it for nearly two years back in 2005-2006. I was happy with it except that fact that I always had to compile software. I really CBF to compile everything with this piece of crap. I've never used Slackware before. Are there a lot of issues with its package manager? Is it as easy to use as apt, portage, port etc?

By the way, I've got a 40G hard disk, so disk space won't be a problem.

---

### Post by darolu on 2010-04-22
Slackware default package manager is similar to Gentoo's; they have this "[Slackbuilds]("http://slackbuilds.org/")", which are scripts that get your apps and configures them; some times this implies compiling too though; if you don't want to waste time compiling neither slackware nor gentoo are good ideas; when I used Slackware I didn't need to install many apps this way though, you download a DVD and it has pretty much all I needed.
To give you a better idea of how your machine would run, I have a Pentium III @ 650Mhz with 384 of RAM (@ 133Mhz) and a 128MB Nvidia FX 5200; this machine currently has Debian 5 (Lenny) and runs surprisingly well, is not fast but acceptable; it used to have Slackware and it really flew (considering the hardware).

---

### Post by andrew.46 on 2010-04-22
Hi blwizard,

> **blwizard said:**
> I've never used Slackware before. Are there a lot of issues with its package manager? 

A big difference is that there is no dependency checking, not by the package managers themselves: it is actually your job :). The package management tools installpkg, makepkg, explodepkg, removepkg and pkgtool are very robust tools and will never let you down.

Slackware is on the brink of releasing 13.1 so if you can hold off a little while it would be an excellent time to launch into Slackware with a shiny new version. I attach a gratuitous screenshot of Slackware 13.0 on my own laptop running xfce to perhaps whet your appetite...

Andrew

---

### Post by imperius69 on 2010-04-22
hello

see this post (try a  minimal install)

[http://ubuntuforums.org/showthread.php?t=1429832](http://ubuntuforums.org/showthread.php?t=1429832)

:guitar:

---

### Post by blwizard on 2010-05-07
Thanks people! Just before I started to install Debian, the IT department came to us and said they were gonna upgrade our computers! Now we all have Dell Precision 360 workstations. Although Dell computers are from probably 8 years back, they are better than the old pieces of **** we were using before. 

The basic spec is: P4 3.0Ghz with Hyper-threading, 1GB DDR ram with ECC at 400Mhz, 800Mhz FSB, 80GB HD and Nvidia Quodra FX 1000. I stole from one of the older computers two ram sticks and expanded the momory to 1.5GB. Now I'm running Lucid without any problems. Oh I've got dual monitors too by the way!

I'll probably pass on Slackware. Actually I was gonna try it but then heard that it couldn't automatically solve dependencies. This brings back the memory of me trying to install a piece of software on readhat 6.2 but ended up giving up because of the dependency ****. Thanks to you guys anyway!

---

### Post by marcoftheknight on 2010-05-07
From what Ive read, linux masters say Arch linux is  the fastest but also requires better linux skills I think.

---

### Post by warfacegod on 2010-05-07
> **marcoftheknight said:**
> From what Ive read, linux masters say Arch linux is  the fastest but also requires better linux skills I think.

Hands down the fastest I've ever seen is SliTaz. Runs in RAM from a USB, is only 30 MB (yes *Megs*), and has a complete GUI. Even Firefox opens almost instantly.

---

