---
title: "Minimalist Linux distro."
date: 2011-02-15
forum: General Help
---

### Post by Veren on 2011-02-15
Hello, it's been almost a year since I started using Ubuntu and I reinstalled the system only once since. I think the time to do it again has come, I have residual files all over and I just want to do a usual clean-up. I've never used any other distro than Ubuntu, and here comes my point:
1. I am looking for one that doesn't automatically install stuff like games, printers, pretty much any junk that my asus eee does't use at all, or what's better - one that lets me choose what to install.
2. It should be rather easy to set up. 
3. Could use Gnome as desktop.

I wanted to make a Debian 6 install from a USB stick - the netinst version - though I keep getting "An uncaught exception was raised: Invalid version string 'GNU/Linux'" message.

If you have any idea I'd be more than happy.
Thanks.

---

### Post by FORCEGC on 2011-02-15
There is DSL (damn small linux) and it is pretty minimalist but i dont believe it runs with gnome.

---

### Post by howefield on 2011-02-15
> **Veren said:**
> I wanted to make a Debian 6 install from a USB stick - the netinst version - though I keep getting "An uncaught exception was raised: Invalid version string 'GNU/Linux'" message.

Have you looked at a netboot install of Ubuntu. Start from the ground up and install only what you want.

---

### Post by kellemes on 2011-02-15
> **FORCEGC said:**
> There is DSL (damn small linux) and it is pretty minimalist but i dont believe it runs with gnome.

Latest release 2008, it seems DSL is dead.

If you really want to go minimalistic (50 Mb for the hole OS I believe) an option would be [Puppy Linux]("http://puppylinux.org/"), very small, very complete and very cool!
No Gnome that is..

Also I have good experiences with [Zenwalk]("http://www.zenwalk.org/"), they have a Gnome edition that's just as easy to setup as Ubuntu but much lighter and faster in use.

Browse [Distrowatch ]("http://distrowatch.com/")for more..

---

### Post by kn0w-b1nary on 2011-02-15
tinycore starts at 10.6mb size, then install everything you want only - and you can use Gnome (Default is IceWM). Not easy to setup though, you'd have to take your time with this one. Really nice when finished though.

Hope this helps!

---

### Post by aeiah on 2011-02-15
arch is very popular. i prefer to install ubuntu minimal and then build up from there.

you'll find that installing ubuntu-desktop will pull all the games and apps down as well as gnome. there are ways to stop it doing that though.

---

### Post by cascade9 on 2011-02-15
LOL @ DSL and puppy. Sure, it might be 'lighter' but that wasnt really what the OP is after... 

> **howefield said:**
> Have you looked at a netboot install of Ubuntu. Start from the ground up and install only what you want.

Correct me if I'm wrong, but I thought that netboot worked like netinstall debian? 

Anyway, heres a guide for a minimal install of ubuntu- 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Once you get the system installed (to command line) add GDM and gnome-core (not ubuntu-desktop, if you do that you would end up with the same packages as if you install a normal ubuntu). Minimal install +, GDM + gnome-core, all you will have installed is the base system, GDM and these packages- 

[http://packages.ubuntu.com/maverick/gnome-core](http://packages.ubuntu.com/maverick/gnome-core)

Then you can add whatever you want.

---

### Post by WorMzy on 2011-02-15
I recommend Arch Linux. You'll need to be familiar with the command line in order to start with as it doesn't come with any desktop environment out of the box.

---

### Post by C.S.Cameron on 2011-02-15
Another vote for Tinycore if you want minimal.

---

### Post by snowpine on 2011-02-15
Any distro (Ubuntu, Debian, Arch, etc.) that lets you do a "netinstall." Start with a command-line-only system and then add the pieces you want.

The Psychocats tutorial a couple of people have linked to is excellent if you want to stick with Ubuntu.

---

### Post by debd on 2011-02-15
take a look at [this page]("http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552?artc_pg=2")

you should be happy and installing one of the two listed...I hope.

and dont suggest tinycore ....its kinda unusable..

---

### Post by PaulReaver on 2011-02-15
a minimal install of ubuntu is a good choice

I install just the basics like gdm ubuntu-themes ubuntu-mono ubuntu-artwork dmz-cursors gnome-core network-manager window-picker synaptic chromium-browser abiword jockey-gtk xinit

this looks mostly like a standard ubuntu but without all the crap, and you can always add extra apps later

---

### Post by C.S.Cameron on 2011-02-15
A minimal install of Ubuntu is bigger than an full install of Puppy and way bigger than Tinycore.

---

### Post by snowpine on 2011-02-15
There is a difference between "minimalist" and "small" in my opinion.

Puppy Linux is "small" but it is not "minimalist." It seeks to provide a full suite of pre-installed applications for a complete "out of the box" experience. 

A netinstall of Ubuntu or Debian may not be "small" by Puppy standards, but it provides a "minimalist" base on which to build a completely custom system. It has the added benefit of providing a familiar .deb-based experience to the OP.

I have not used Tiny Core but from what I've heard, it is both "small" **and** "minimalist" to the extreme; good suggestion (as usual) C.S. Cameron. :)

---

### Post by kn0w-b1nary on 2011-02-15
> **debd said:**
> 
and dont suggest tinycore ....its kinda unusable..

I have to disagree. I use on Pentium 3's all the time. Check these vids out:
[http://www.youtube.com/watch?v=0YstiqxFBGM&feature=fvwrel](http://www.youtube.com/watch?v=0YstiqxFBGM&feature=fvwrel)
[http://www.youtube.com/watch?v=2ZD2rK07be4&feature=relmfu](http://www.youtube.com/watch?v=2ZD2rK07be4&feature=relmfu)

---

### Post by PaulReaver on 2011-02-15
> **C.S.Cameron said:**
> A minimal install of Ubuntu is bigger than an full install of Puppy and way bigger than Tinycore.

yeah but tinycore is a bit crap....IMO

puppy is good.... :D  but not a patch on ubuntu or debian....

---

### Post by Brad55 on 2011-02-15
Here is one base on Ubuntu if you want to take a look at it. [[COLOR="RoyalBlue"]Bodhi[/COLOR]]("http://distrowatch.com/table.php?distribution=bodhi")

Bodhi Linux is an Ubuntu-based distribution for the desktop featuring the elegant and lightweight Enlightenment window manager. The project, which integrates and pre-configures the very latest builds of Enlightenment directly from the project's development repository, offers modularity, high level of customisation, and choice of themes. The default Bodhi system is light -- the only pre-installed applications are Firefox, LXTerminal, Elementary Nautilus and Synaptic -- but more software is available via Bodhi Software Center, a web-based software installation tool.

---

### Post by Veren on 2011-02-16
Whoa, thank you all for so many responses.
I was thinking about Arch earlier but the installation scared me out a bit. I finally went with Fedora 14 with Xfce, removed tons of junk and it works wonderful - at least until Ubuntu 11.04 comes out it will :D.
Thanks again, have a nice day.

By the way I worked out Debian too.

---

### Post by kn0w-b1nary on 2011-02-16
> **Veren said:**
> Whoa, thank you all for so many responses.
I was thinking about Arch earlier but the installation scared me out a bit. I finally went with Fedora 14 with Xfce, removed tons of junk and it works wonderful - at least until Ubuntu 11.04 comes out it will :D.
Thanks again, have a nice day.

By the way I worked out Debian too.

Debian is pretty good, now that squeeze is out. XFCE4 is amazing, hope you enjoy it!

---

### Post by Veren on 2011-02-18
Fedora sucked big time, but Crunchbang with Openbox is a huge win :)

---

### Post by YouSmeg118 on 2011-10-21
> **Veren said:**
> By the way I worked out Debian too.

Sorry to bring up an old thread - but i have the same problem. How did you get past this? Thanks

---

