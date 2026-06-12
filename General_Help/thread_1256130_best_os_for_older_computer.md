---
title: "best os for older computer"
date: 2009-09-02
forum: General Help
---

### Post by Kristofer Van Orton on 2009-09-02
I'm trying to fix a computer for a friend. This thing is old, I mean really old. It came standard with Windows 98, it only has 4gb hard drive and 128mb of ram. I've tried setting it up using Win2k because when I got it this thing actually had Windows XP on it and ran really slow. I think this thing is kind of hopeless as far but its actually my friends only computer (I feel bad for him If I got my old laptop working I would just give it to him because I feel so bad haha) so I just want to get it working at top speed, what ever that is on 128mb ram haha and I've decided to try some linux distros for it...so what do you guys think?

The old computer:
Dell Latitude CPi
4GB HD
128MB RAM

anyone got any ideas?

---

### Post by aeiah on 2009-09-02
crunchbang. its based on ubuntu, so you should be able to lend a hand. its lighter than xubuntu and in my opinion better than fluxbuntu or other lightweight ubuntu derivatives.

---

### Post by P4man on 2009-09-02
I read about "slitaz" here today, and Im just running it in a VM, and it looks pretty neat for a machine with 128Mb.  After installing, it boots in ~20s on my VM and its actually running in 85Mb with firefox open :D ! Doesn't look too arcane or complicated either.  Just give it a nice wallpaper :p

puppylinux would be another option.

---

### Post by Bucky Ball on 2009-09-02
You might want to look at Damn Small Linux or Puppy Linux. No Ubuntu flavour will run on that (unless you install from a CLI and just get the bits you want, including a resource friendly desktop environment like Openbox).

---

### Post by paradigm2 on 2009-09-02
The memory is the killer.  If it were 256M you could go with Windows 2000, XP, or some linux with fluxbox and still have a responsive system.

You could TRY using Gentoo or Arch and putting fluxbox on there, I don't know how it'd work out but it's your best bet that would still allow a GUI and say be able to run a normal Firefox version.

There's no way Xubuntu would be responsive on that system if you could even install it.

---

### Post by aeiah on 2009-09-02
> **Bucky Ball said:**
> No Ubuntu flavour will run on that (unless you install from a CLI and just get the bits you want, including a resource friendly desktop environment like Openbox).

you did just describe crunchbang lite, you know...

---

### Post by Bucky Ball on 2009-09-02
I sit comfortably corrected.

---

### Post by fela on 2009-09-02
Gentoo; Arch; Linux from Scratch; Debian netinstall; Puppy Linux; Knoppix.

I advise you to use Puppy or Knoppix, as you can easily get them running straight from RAM (which will make the system much more responsive by not using the harddisk much at all).

You might want to try debian though, it's very customizable and one of the oldest linux distros; it's very very stable aswell and has a superb package manager (apt, the same one as Ubuntu).

Gentoo, arch and LFS are all extremely customizable, you compile everything from source code in Gentoo and LFS. You sort of have to be a bit of a geek to use them though.

The system in question has a massive amount of computing power compared with what you actually need to do basic tasks like getting onto the web, checking email; etc. and there are tonnes of linux distros that will work great on it.

EDIT: you also might want to try getting an alright video card for it and running compiz. I'm being serious, it takes load off the CPU. Forget about the desktop cube and burning windows though.

---

### Post by snowpine on 2009-09-02
Hi there, I have a similar computer (Dell Latitude Cpx, 128mb ram, 6gb hard drive). It's currently running SliTaz, which works ok for light web browsing (forget about streaming flash videos though). (note: you need to use the SliTaz 'loram' installer; the regular one is optimized for 256mb)

Tested Xubuntu, CrunchBang, Fluxbuntu, etc., and they are all painfully slow on this machine. Anything based on Ubuntu needs at least 256mb in my experience. SliTaz and Puppy are the only distros I would recommend.

---

### Post by gordintoronto on 2009-09-02
> **Kristofer Van Orton said:**
> 
The old computer:
Dell Latitude CPi
4GB HD
128MB RAM

anyone got any ideas?

Puppy Linux, which should run fine on that configuration, and has a decent set of applications.

---

### Post by Kristofer Van Orton on 2009-09-02
wow im happy to see so many people reply so fast thank you call ill have to expiriment with some of these

---

### Post by Augsburg on 2009-09-02
I've run a very nice Damn Small Linux Install on a similar computer. It's a great Distro, taking up very little hard drive space. It's also debian-based like Ubuntu, so it will be easy to use if you know your ubuntu. In addition, it all has a nice X interface, and Joe's Window Manager (which in my opinion looks a lot more professional than ICE, etc). If you want help with a basic install and setup, I created a blog last year that I have posted [here]("http://web.augsburg.edu/~brownp/download/dsl.pdf").

---

### Post by Kristofer Van Orton on 2009-09-02
im definetley gonna have to try that one thanks alot

---

### Post by matsuzine on 2009-09-02
Here's what I would do:

use a minimal install ubuntu disk to install the base system (text only) then install a lightweight wm like jwm.  Actually, I'm posting this from a 10-year old computer that runs as fast as my new machine for most tasks using that setup.

---

### Post by Kristofer Van Orton on 2009-09-02
> **matsuzine said:**
> Here's what I would do:

use a minimal install ubuntu disk to install the base system (text only) then install a lightweight wm like jwm.  Actually, I'm posting this from a 10-year old computer that runs as fast as my new machine for most tasks using that setup.


well the minimal install on ubuntu is 3GB (hard drive:4GB) but maybe not in older versions
i think im gonna try dsl and see how that goes

---

### Post by matsuzine on 2009-09-02
My ubuntu with everything installed (core, wm, apps but none of my dev stuff) weighs in at 1.1 GB!

If small and fast are more important than number of packages, configurability, then puppy also is great.  Plus, DSL is pretty cool as you said, and I've got an even older machine running it...  Lightweight distros are a lot of fun.

---

### Post by marshmallow1304 on 2009-09-02
> **Kristofer Van Orton said:**
> well the minimal install on ubuntu is 3GB but maybe not in older versions

No, that's the minimum size requirement to install with the full CD.  The minimal CD installs just a base system with no extra packages, so once it's installed it's very small (easily less than 1 GB).

If you're good with command line, you can use it to install from scratch.  I recommend [lxde]("http://www.lxde.org") and [slim]("http://slim.berlios.de/") for older hardware.


Puppy is nice also.

---

### Post by snakepit # on 2009-09-02
Look at Absolute.

[I]Absolute is a x86 Linux distribution based upon Slackware. It concentrates  on "desktop" use so that it is ready for internet, multimedia, document and   general home use as much as possible.  Absolute is lightweight -- meaning 2 things: that it  can run on on older hardware and that the OS interface stays out of your way. 
[/I] 
[http://www.absolutelinux.org/](http://www.absolutelinux.org/)

---

### Post by BitJunkie on 2009-09-02
You might also want to look at antiX. It ran OK on an old laptop of mine.

---

### Post by Kristofer Van Orton on 2009-09-02
i installed dsm and the display looks very pixely and you cant really see anything so i guess i need to go for something else

---

