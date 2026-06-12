---
title: "Which Linux is best for REALLY old computer?"
date: 2010-11-14
forum: General Help
---

### Post by Thecovester on 2010-11-14
Hello all, I have a '98 computer, and I'm wondering if there's ANY possibility of putting a form of Linux on it. It only has 64 mb of RAM :P so it can't do much. I was looking at Puppy Linux and SliTaz, would either of those work? If not, are there any other choices? Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-11-14
If the distros you mentioned won't work, then your only alternative will be [TinyCore]("http://www.tinycorelinux.com/").

---

### Post by Thecovester on 2010-11-14
Ok, I'll try that. I have two questions, though. The old CD drive won't read anything (something that has to do with the I/O ports) so I'll have to use a Flash Drive. I'm supposing that my computer has USB 1.0, would a normal flash drive work with USB 1.0? 

Also, in Smart Boot Manager, can SBM boot to a flash drive? (Not from a flash drive, boot to a flash drive) If not, what other program can boot an OS from a flash drive? (My BIOS is too old to do pretty much anything)

---

### Post by arvevans on 2010-11-14
I usually install *_[Vector Linux]("http://www.vectorlinux.com/")_* on old machines.  It takes forever to install, but once installed it is pretty fast, even on older hardware.  
Note that Vector Linux is based on Slackware, and not on Debian as is Ubuntu, so there will be some differences in how things are done.

---

### Post by Thecovester on 2010-11-14
Ok.....thanks for all the suggestions of Linux for old computers (i'll look into Vector) but could someone please answer my questions about SmartBootManager, USB, and SliTaz?


EDIT: Vector Linux won't work for my computer. It needs at least 96 mb of memory; I only have 64 mb.

---

### Post by Thecovester on 2010-11-17
Ok, so I have one last question. Will a USB drive that was made recently work with USB 1.0?

---

### Post by Miyavix3 on 2010-11-17
What is your experience with configuring things on Linux? Requirements are mostly dependent on window manages and/or desktop environments.

If you feel comfortable with a moderate amount of editing: Openbox, Fluxbox or IceWM for a window manager. [IMO, icewm is really nice. Editing menus is super easy even though it's done in a text editor]

If you are adventurous, you can try a tiling WM like AwesomeWM, DWM , wmii or xmonad. If you go this path, make sure you try this type of setup before you realize you don't like it.

If you can, try LXDE. It's pretty low resource and very functional.


[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information)

[http://en.wikipedia.org/wiki/Comparison_of_X_window_managers](http://en.wikipedia.org/wiki/Comparison_of_X_window_managers)


With this being said
[http://en.wikipedia.org/wiki/SliTaz_GNU/Linux#System_requirements](http://en.wikipedia.org/wiki/SliTaz_GNU/Linux#System_requirements)
[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

or you can pick from these:
[http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

---

### Post by Jerry N on 2010-11-17
> **Thecovester said:**
> Ok, so I have one last question. Will a USB drive that was made recently work with USB 1.0?

Everything I have seen is backwards compatible so the answer is (probably) yes.

Another OS you might try is Legacy OS.  This is based on an older version of Puppy Linux and was originally called TeenPup Linux.  It is made specifically to work on older machines with limited resources and is a lot less weird than Damn Small Linux.  I have it running on a 1998 era machine and it runs fairly well but I haven't made it print over the network yet.  It is not Debian based like the newest versions of Puppy Linux.

A couple of years back I spent a lot of time trying to make numerous so-called "light" versions of Linux work acceptably (to me) on old 300-400 mhz class computers and have yet to find one that performs better than Windows 2000 with SP4.

Jerry

---

### Post by Thecovester on 2010-11-19
Thanks Jerry. Legacy OS looks like it should be great, but the system requirements are:
At least 500mhz CPU
192 mb RAM
20x CDROM (testing shows 4x may work)
To Play DVDs, you need a good 256 mb RAM and a good Ghz (not Mhz)processor.

Too bad :(

But I'm looking at DSL right now. It will work well with my old computer. Also, I might try a distro called CTKArchLive which is a light version of Arch. Thanks for all of the help!

---

### Post by snowpine on 2010-11-19
DSL is a defunct project and obsolete by a few years (Firefox 1.0 for example), not recommended.

SliTaz on the other hand is fantastic and very much an active project, but you'll need to use one of their 'loram' versions (64mb is not very much, even for SliTaz). They have a new spin called 'SliTaz Tiny' that supposedly fits on a floppy and runs with only 8mb! (Haven't tried it personally, I don't have any hardware that old...) Also SliTaz has good documentation for alternate boot methods since your CD-ROM doesn't work.

Tiny Core is also popular (never tried it) and Puppy is fantastic, though maybe a little heavy for only 64mb of RAM.

Is there a reason you can't upgrade to newer hardware? If you could find, say, a Pentium 4 with 512mb RAM, you would have a lot more options. Even if your budget is very limited, you can often find a decent computer for cheap/free on Craigslist, thrift stores, recycling centers, etc. A good article on the subject: [http://kmandla.wordpress.com/2010/10/30/howto-find-an-old-computer/](http://kmandla.wordpress.com/2010/10/30/howto-find-an-old-computer/) Linux on older hardware can be frustrating and challenging for new users, much easier to install on capable hardware so you can get right to the fun stuff. :)

---

### Post by Rubi1200 on 2010-11-19
Another possible option is antiX:
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by Miyavix3 on 2010-11-20
> **Rubi1200 said:**
> Another possible option is antiX:
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

Yes! I couldn't remember the name before. Thank you.

---

### Post by Alexcelbun on 2012-09-30
Try ConnochaetOS It has EXTREMELY low sistem requirments(pentium1MMX,32mbRAM)as far as i know tomorow im gona install it if it dosen't comes on something.

---

### Post by overdrank on 2012-09-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

