---
title: "Smallest unit of a working Linux o/s??"
date: 2011-07-06
forum: General Help
---

### Post by ClientAlive on 2011-07-06
I'm wondering what the least err . . . unit/ units are for a working Linux. For instance. Is a kernel + a window manager enough? Then let's say you install one app on top of that - now you have one app you can use, right? But is that right (kernel + window manager)? Do you even need a window manager for a functioning system? Do you need more than the window manager?

I'm asking because I'm fixing to build something from the ground up but it isn't a regular Linux thing and I want to approach if from the direction of adding just what I need not taking away what I don't.

Thanks in advance for any info.

Jake
:)

---

### Post by idoitprone on 2011-07-06
ubuntu is not a recommended distro for bare bones install. If you are ok with command line, then try arch linux. You do not need a window manager. However, you do need a command line as it is more bare bones then a window manager.



 [http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch)

Recommendation: if you have wifi, you should install the wireless-tools, so you can connect to the internet as you configure your system

To run gui apps, you require the x server. I am not sure if you need a window manager Openbox is as barebone window manager as you can get. You can try ratpoison, a window manager that do not require a mouse

---

### Post by nothingspecial on 2011-07-06
> **idoitprone said:**
> ubuntu is not a recommended distro for bare bones install. 

Who doesn't recommend ubuntu for a bare bones install? 
I certainly do.

You can accomplish a lot without X at all. Obviously you are going to struggle to edit videos, but browsing, email, music, even watching youtube is perfectly possible on a cli only install.

---

### Post by ClientAlive on 2011-07-06
> **idoitprone said:**
> ubuntu is not a recommended distro for bare bones install. If you are ok with command line, then try arch linux. You do not need a window manager. However, you do need a command line as it is more bare bones then a window manager.



 [http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch)

Recommendation: if you have wifi, you should install the wireless-tools, so you can connect to the internet as you configure your system

To run gui apps, you require the x server. I am not sure if you need a window manager Openbox is as barebone window manager as you can get. You can try ratpoison, a window manager that do not require a mouse


Thanks. My next project will be Xen. But Xen requires a host o/s to run on top of (sort of). Well, without getting too carried away about it, it does have some management tools that I'll need to have. What's more important though is all the things I don't need to have. Basically that's anything that would come along with any conceivable Linux distro. So my idea was to compile a kernel (what is it 2.6.39 stable) and whatever next, absolutely critical to function thing is (if that's a window manager), then Xen on top (which modifies that kernel, I think, then what handful of apps for Xen (the management tools for it). Personally, I don't care if there is a gui but that depends on the usability of the Xen apps and how they work.

Anyhoo . . . maybe that gives a better idea why I'm asking. I'm not really thinking about a minimal install, I'm thinking about an actual ground up build but I need to understand what the real bare-bones is.

---

### Post by ClientAlive on 2011-07-06
> **nothingspecial said:**
> who doesn't recommend ubuntu for a bare bones install? 
I certainly do.



.  :)

---

### Post by mastablasta on 2011-07-06
> **idoitprone said:**
>  I am not sure if you need a window manager Openbox is as barebone window manager as you can get. You can try ratpoison, a window manager that do not require a mouse
 
 
no, GNU screen is even more barebone
[http://alexandrulazar.com/gnu-screen-window-manager/](http://alexandrulazar.com/gnu-screen-window-manager/)
 
also why not try linux from scratch (LFS) distro then? it's amde to be build from scratch. and it is ment to be a form of learning.

---

### Post by nothingspecial on 2011-07-06
> **mastablasta said:**
> no, GNU screen is even more barebone
[http://alexandrulazar.com/gnu-screen-window-manager/](http://alexandrulazar.com/gnu-screen-window-manager/)
 
also why not try linux from scratch (LFS) distro then? it's amde to be build from scratch. and it is ment to be a form of learning.

Or try ubuntu's nicely setup gnu screen, byobu

---

### Post by Jouke74 on 2011-07-06
If you download the minimal Ubuntu install CD and run through the installation process (assuming that you can have a required ethernet internet connection) it will ask you which packages to install and you can even select an Ubuntu system specifically made to do virtualisation. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by ClientAlive on 2011-07-06
> **mastablasta said:**
> 
also why not try linux from scratch (LFS) distro then? it's amde to be build from scratch. and it is ment to be a form of learning.


Hell yes!! If you're referring to Linux in general that is ". . . made to be buitd from scratch and  . . . meant to be a form of learning.

> **Jouke74 said:**
> If you download the minimal Ubuntu install CD and run through the installation process (assuming that you can have a required ethernet internet connection) it will ask you which packages to install and you can even select an Ubuntu system specifically made to do virtualisation. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ok. Well, I guess there's more I don't know than I realized. I was out on the balcony having a smoke this morning and it occured to me that the kernel probably does not include things like a basic text editor, or even a package manager, or e'ven a shell for that matter. If I'm right about that, then there are a lot of things not included in the kernel that one simply must have to have a functional system. This got me to thinking about what a minimal install might even be - and I realized right there that I don't even know what a minimal install is! I just got on here for the night and all day have been anticipating learning about this, thinking about google and all the search terms I'm gonna put into it, and about you guys and all the great knowledge you might have about this.

Regardless, whether a minimal install or building from the ground up is the best way to go on this - I do know one thing:

I want to be sure that the right things are enabled in the kernel and the wrong things (bloat) are not. Whether that means a minimal install followed by a recompile or a straight up ground up build and adding the necessities on top, I'm not quite sure yet. I'm hoping between us and google and a little courage I'll get it sorted out and on to giten er' done!

:P

Thanks guys

---

### Post by WorMzy on 2011-07-06
> **nothingspecial said:**
> Who doesn't recommend ubuntu for a bare bones install? 

Me.

I recommend Arch.

---

### Post by 1clue on 2011-07-06
You could theoretically boot a linux without even a normal shell.  Linux has been used on embedded devices which have no user input, just a program that runs to perform whatever task the device is designed to perform.  So a kernel, a couple drivers which will probably be built in, a boot loader and some support files, and enough other junk to make it go.

Arch or Gentoo would be good places to start if you want a minimal installation.

Ubuntu Server is a nice reasonable minimal as well, but they do make some choices for you that a more expert distro doesn't make.

Based on your posts, you are what I would call a "newbie" with a few years to go before you figure all this out.

---

### Post by ClientAlive on 2011-07-06
> **WorMzy said:**
> Me.

I recommend Arch.


I thought arch has a real short lifespan. Or is that CrunchBang I'm thinking of. I'm kinda shooting for stability but I think I'm thinking of the other one. I'll get to the Arch site and check it out right now. One of my other tabs is Ubu Mini.

:)
-----------------------

Edit:

> 
You've reached the website for Arch Linux, a lightweight and flexible Linux® distribution that tries to Keep It Simple.



Mmmm hmmm . . . that one perked my ears up! HELLO Arch!!:)

---

### Post by decoherence on 2011-07-06
Unless you want to learn how to build a linux distro, i wouldn't recommend doing the 'ground up' build.

A lightweight install of Ubuntu -- Ubuntu Server, for instance -- plus some carefully selected packages will get you just what you want. After that, you can tweak and recompile the kernel to your heart's desire.

You are correct in your assessment about the kernel. All it does is talk to the hardware and provides things like text editors and xen and so on with a means of accessing the hardware.

When people talk about a minimal linux install, they are still talking about hundreds of programs like text editors, configuration utilities (think ifconfig) and lots libraries and of other things generally referred to as 'userland.' Some of them you may be able to do without but sorting out what you need vs what you don't would be a lot of effort without much benefit (disk space is cheap and additional command-line programs don't 'bloat' the system if they don't run.)

Mind you if you are interested in getting as 'minimal' as you can as an academic exercise, perhaps a ground-up LFS install is the way to go.

Arch Linux is a popular distro for people who want to start with a minimal system, though due to the nature of its package system it won't be super-duper optimized -- this is also true of Ubuntu. If you want to tweak every little thing, try a stage 1 Gentoo install.

---

### Post by oldfred on 2011-07-06
An example, you should only need one video driver. I get 31 as the count in my Maverick. And I am using the nVidia driver I separately installed.

Count of video drivers
dpkg -l|grep xserver-xorg-video|wc -l
List of drivers
dpkg -l|grep xserver-xorg-video

---

### Post by ClientAlive on 2011-07-06
> **oldfred said:**
> An example, you should only need one video driver. I get 31 as the count in my Maverick. And I am using the nVidia driver I separately installed.

Count of video drivers
dpkg -l|grep xserver-xorg-video|wc -l
List of drivers
dpkg -l|grep xserver-xorg-video

33 for me. Guess that's 32 times what I actually need.  :)


> **decoherence said:**
> 
Arch Linux is a popular distro for people who want to start with a minimal system, though due to the nature of its package system it won't be super-duper optimized -- this is also true of Ubuntu. If you want to tweak every little thing, try a stage 1 Gentoo install.

I was reading about Gentoo in some wiki on the Arch site. That's what stood out to me when I read about it - that it's highly configurable.

I might end up botching the thing a couple times before I get it right but I'm sure I'll learn. I think it'll be a cool learning exper though, all in all. I'll have to do a little research but I think I'm finding my way.

Thanks guys.

---

### Post by 1clue on 2011-07-06
I was using Linux for almost 10 years, lots of kernel compiles under my belt and all sorts of stuff, thought I was hot $#!+.  Then I started using Gentoo and figured out just how little I knew about it.

With Gentoo, you literally compile every app that winds up on your system.  There are precompiled versions of firefox and other big apps if you really want them, but the general rule is that you compile it yourself.

Before you start adding packages, you compile the kernel.

It's about as opposite of Ubuntu as you can get and still be Linux.

---

### Post by nothingspecial on 2011-07-06
If you would like to use the framebuffer for images and videos etc, you might want the video driver fbdev as well as the one for your graphics card.

---

### Post by WorMzy on 2011-07-06
> **ClientAlive said:**
> I thought arch has a real short lifespan. Or is that CrunchBang I'm thinking of.

Arch is a rolling release distro, meaning that it doesn't have lifespans. You install Arch today, and (assuming you stick with it) you'll still be using the exact same installation five years from now, even though half of the packages you started out with have been replaced along the way.

---

### Post by ClientAlive on 2011-07-06
> **1clue said:**
> I was using Linux for almost 10 years, lots of kernel compiles under my belt and all sorts of stuff, thought I was hot $#!+.  Then I started using Gentoo and figured out just how little I knew about it.

With Gentoo, you literally compile every app that winds up on your system.  There are precompiled versions of firefox and other big apps if you really want them, but the general rule is that you compile it yourself.

Before you start adding packages, you compile the kernel.

It's about as opposite of Ubuntu as you can get and still be Linux.


Uhhh . . .  this thing sounds about like an alien from mars (but in a cool way though  :D ).

I'm reading the wikipedia page on it:  [http://en.wikipedia.org/wiki/Gentoo_Linux](http://en.wikipedia.org/wiki/Gentoo_Linux)

Sounds like there are a lot of very unique qualities about Gentoo. Different package management, different spawning program, even a different shell (which I'm really curious about).

Given that everything is compiled by the user (every package) it sounds like the first thing a foolish newb who want's to mess around with it would do - is find a way to save things as they are before every and any change he is about to make. Maybe in a few years he'll get the hang of it well enough to relax a little.

Sounds really cool and right up my alley. I have that old desktop sitting there that I just got fired up the other day - and it's very purpose in life is to learn with and experiment on. Build it up and take it down, screw it up and then fix it, whatever it takes to get it all sorted out.

Gentoo sounds like a lot of fun.   :)
------------------------\

Edit:

You really made me laugh pretty hard man. How many of us don't think we're "hot . . ." at one time or another. It's those humbling experiences that really open up a whole new world of possibilities though eh?
-----------------------\

Edit:

> 
Following the initial install steps, the Gentoo Linux install process requires that all users compile their own Linux kernel.


Cool . . .

---

### Post by decoherence on 2011-07-07
Since you are so gung-ho I'm gonna throw another two more hats in to the ring. NetBSD and FreeBSD.

Why might you want to learn with one these rather than Linux? Well, if you think about what it is you've decided to study, it's essentially a design for an operating system whose roots date back 40 years. Ubuntu/Gentoo/Arch et al are just the latest hot things in this ancient (in technology terms) lineage. The lessons you learn in any of the BSDs will carry over to Linux. Sure they do some things differently but that is true of Linux distros as well -- there are always going to be thing you need to re-learn either going from BSD to a Linux distro, or from say, Ubuntu to Fedora.

OK fine, but WHY Net/FreeBSD rather than Linux? In a word: documentation. The man pages for BSD userland are extremely well written, in a much more consistent style and format than the mish-mash of docs you see in Linux. You can actually bootstrap yourself completely just by RTFM.

Also, the BSDs place a lot of emphasis on 'correctness' which means that you don't see a lot of the drastic fundamental changes over the lifespan of the distro like you do in linux -- such as ubuntu moving from init scripts to upstart, meanwhile fedora moves from init scripts to systemd, etc. init scripts aren't broken, they just aren't 'exciting.' i mean, who HASN'T wanted to rewrite the init system, right? ;)

Also, the minimal installs for either Net- or FreeBSD make Arch look bloated ;) Anyway, more food for thought! Please keep us posted!

And for the record, I prefer NetBSD but my employer uses FreeBSD.

---

### Post by Jagoly on 2011-07-07
Ive 

I've never bothered with gentoo or lfs, but ubuntu mini and arch are both great. UM is bar far alot more practical, but arch is much more fun:)

If I were building a system that I actually intended to use, but still wanted extreme customisation, I'd go with UM. If I were just learning and experimenting, I'd go with arch. In my use UM, being ubuntu, has alot more packages (even taking the AUR into account). In addition, most of arch's packages don't intergrate with San other very well.

Also remember that Linux is just a kernel; the GNU userland is where all the system level applications are. Alot of people stress the point that ubuntu, arch, debian, gentoo, fedora, ect are "GNU/Linux" distributions. Without the GNU userland, you would be restricted to embedded devices.

---

### Post by ClientAlive on 2011-07-07
> **decoherence said:**
> Since you are so gung-ho I'm gonna throw another two more hats in to the ring. NetBSD and FreeBSD.

Why might you want to learn with one these rather than Linux? Well, if you think about what it is you've decided to study, it's essentially a design for an operating system whose roots date back 40 years. Ubuntu/Gentoo/Arch et al are just the latest hot things in this ancient (in technology terms) lineage. The lessons you learn in any of the BSDs will carry over to Linux. Sure they do some things differently but that is true of Linux distros as well -- there are always going to be thing you need to re-learn either going from BSD to a Linux distro, or from say, Ubuntu to Fedora.

OK fine, but WHY Net/FreeBSD rather than Linux? In a word: documentation. The man pages for BSD userland are extremely well written, in a much more consistent style and format than the mish-mash of docs you see in Linux. You can actually bootstrap yourself completely just by RTFM.

Also, the BSDs place a lot of emphasis on 'correctness' which means that you don't see a lot of the drastic fundamental changes over the lifespan of the distro like you do in linux -- such as ubuntu moving from init scripts to upstart, meanwhile fedora moves from init scripts to systemd, etc. init scripts aren't broken, they just aren't 'exciting.' i mean, who HASN'T wanted to rewrite the init system, right? ;)

Also, the minimal installs for either Net- or FreeBSD make Arch look bloated ;) Anyway, more food for thought! Please keep us posted!

And for the record, I prefer NetBSD but my employer uses FreeBSD.


Oh my god! I just saw your signature. LMFAO!!

I can't make it stop! OMG! The laughter is killing me!
-----------------------

Edit:

Ok, sorry. I think I've got it under control now. He he . . .

Yes, duly noted. I kinda like what I see with Gentoo though. I think I'll focus on it for now. I'm just waiting for some RAM to come in the mail for my other machine (the one for this project). It should be here tomorrow or the next day; and, as sonn as I get it, and get er' all upgraded and all, it'll be compiling time for this kid. Oooo . . . it's gonna be so much fun!  :)


> **Jagoly said:**
> Ive 

I've never bothered with gentoo or lfs, but ubuntu mini and arch are both great. UM is bar far alot more practical, but arch is much more fun:)

If I were building a system that I actually intended to use, but still wanted extreme customisation, I'd go with UM. If I were just learning and experimenting, I'd go with arch. In my use UM, being ubuntu, has alot more packages (even taking the AUR into account). In addition, most of arch's packages don't intergrate with San other very well.

Also remember that Linux is just a kernel; the GNU userland is where all the system level applications are. Alot of people stress the point that ubuntu, arch, debian, gentoo, fedora, ect are "GNU/Linux" distributions. Without the GNU userland, you would be restricted to embedded devices.


There's actually a couple reasons, really. Yes, learning is one of them, the other I hadn't mentioned because I'm just not sure how well it's going to work out. The other is more practical. It's to develop technology that fits into a business venture I'm planning. We'll see how things go though. Perhaps, for one reason or another, it turns out to be nothing. I live in hope that isn't the case though.

---

### Post by MiniT on 2011-08-26
When you have time, you might look at Tiny Core and Micro Core Linux.
Their gag is a 10Mb system.  Yep, you read that right.
Almost a waste of a CD.
Their documentation has grown leaps and bounds in the last couple years.
As has their approach to "regular humans" - folks who use human language for thinking.  These folks are pretty smart, I'm telling you.

Microcore seems to be THE smallest, functioning system I can find anywhere.  Throw on a tiny wm and there is Tinycore.

They have a seriously small CD available now which gives you everything you need to install either, plus networking tools, so you can get set up and do the remainder of your build with Wifi.  

They don't stress the "install" like others do.
TC install is ideally just a CD with the base system, plus a file which can be saved to hard drive/usb/whatever, which contains your apps and docs.

Tinycore/Microcore has its own repository and package manager.
Once you figure out the HOw DO, it's blazin fast.

Think "running in ram."  Yeah.

good luck  :)

---

### Post by MiniT on 2011-08-26
One more, dude.
Look at PuppyLinux.
Sounds cutesy, right?
Well the name and sometimes the default look are a little soft for my taste.
But it is darn small as distro sizes go.
And it has a brilliant display detection script . . 
I don't know about these things except what i see, and Puppy is the only one that has gotten my old laptop's screen right on the first try.

Like TinyCore, Puppy can run from CD, or be installed, but the best deal is a system on CD which you tweaked to your liking from the original - then reburned.  That way the base system is basically invulnerable to system rot, and you also have the one file = saved everything.


Both TinyCore and Puppy can be used on a system without installing to the hard drive, yet have a save file, so you have lots of programs and stuff on USB(say) and when finished for the day, the hardware is none the wiser!

possibilities . . :):D

---

### Post by bodhi.zazen on 2011-08-26
The smallest unit of any OS is the kernel.

Most major distros ship a large kernel compiled with many drivers for maximal compatibility.

For your project, I suggest you learn to compile a kernel with only those drivers needed for your target hardware.

---

### Post by deserthowler on 2011-08-26
I started with Linux a few years ago with Debian net install on a Sun Sparc 64 bit.  I worked from the bash shell using apt-get for a package manager and nano as my editor.  Later I installed aptitude as a package manager. Then emacs as an editor. And one of the text based browsers but I don't remember which.  I eventually went to TWM for my window manager which allowed use of several GUI programs.  

Then I went to fvwm which is the **ultimate computer game** as a window manager.  The man page reads like a Russian novel.  I still use fvwm with Ubuntu ... in fact is my WM of choice ... no Gnome 3 or Unity necessary.

Earl

---

### Post by ClientAlive on 2011-08-27
Right on.

I'm surprised to see a reply to this old post. That's pretty cool. :D


This question stemmed from something that's been brewing in me almost since I started with Linux (what, maybe 6 mos ago - if that).

The project I landed on, that I've stuck with, is to compile a Xen system. Got some old hardware (a desktop) resurrected and am, technically, at the point of starting to compile stuff. I decided on Gentoo for my dom0 (a Xen thing). I tell ya' though, I've had a heck of a time clearing certain confusions that arise during this learning process. It's frustrating because I'm sure I could have done this project 20 times over now for the amount of time that's passed - just having to learn about everything under the sun, and it's slow going.

Currently, I'm looking into the disk management scheme I want to use and compiling my kernel. I've got a couple things I'm confused about that I can't seem to find the answer's to and it's been hanging me up. I think it best I start a new thread about it though since it is a different topic. Maybe I can come back here in a few minutes and post a link to that other thread once I make it. If someone has some knowledge about these things maybe you could help me out on that one. I keep researching all over the place and I'm learning a lot but just not getting the answers to my specific questions - has me at a standstill and I would just as soon walk across the room there and start compiling like right this minute.

Thanks in advance. Much appreciated.
-------------------------

Edit:

Link= [http://ubuntuforums.org/showthread.php?p=11193698#post11193698](http://ubuntuforums.org/showthread.php?p=11193698#post11193698)

---

### Post by .... on 2011-08-27
I've run lots of barebones distros and compiled my own kernels too. It's great to learn, but very time-consuming. I guess if you want to use a kernel for a long time, compiling might be worth it. Otherwise, it quickly becomes a pain.

Personally, I would just recommend Debian 6.0 [http://wiki.debian.org/Xen](http://wiki.debian.org/Xen)

---

### Post by Habitual on 2011-08-27
light and fluffy:
[http://distrowatch.com/table.php?distribution=slitaz](http://distrowatch.com/table.php?distribution=slitaz)

---

### Post by jwbrase on 2011-08-28
> **bodhi.zazen said:**
> The smallest unit of any OS is the kernel.

I wonder, though, what the smallest system is that will actually boot and interact with the user (it doesn't have to do anything useful, just A) not panic and B) respond to user input). I suppose you'd need a kernel, init, and a shell. What else?

---

### Post by ClientAlive on 2011-08-28
> **jwbrase said:**
> I wonder, though, what the smallest system is that will actually boot and interact with the user (it doesn't have to do anything useful, just A) not panic and B) respond to user input). I suppose you'd need a kernel, init, and a shell. What else?


Maybe, if a person was ok with it doing only one thing, they could define some things about the hardware that reduce the size dramatically. For instance, maybe all you want it to do is print "hello" when you push the enter key. So you define only 5 bytes of space on the hard drive + whatever the program to print to standard output needs for storage and the min space for you kernel and now you have less to deal with. Same thing for RAM, just define only a tiny portion of it as existing.

I wonder if that would reduce your size a lot. Not that it would be really useful as a system - just for funsies.

:)

---

