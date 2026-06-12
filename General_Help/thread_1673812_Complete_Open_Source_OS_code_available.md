---
title: "Complete Open Source OS code available?"
date: 2011-01-23
forum: General Help
---

### Post by montraydavis on 2011-01-23
I have been looking forever on creating my own Linux OS. I have been using Linux for a few years now, and would say that I am at an intermediate level. I have gotten as far as creating a bootloader/kernel (printing to screen, and few interaction methods). However, I am stuck, and don't really know what to do next, so, I was wondering if there was an OS that is at least "useable" (with GUI) with all available code, as well as OS files such as configs, system images, (basically everything the typical Linux based OS's have like Ubuntu, Debian.) 

Or anything as close to that would be greatly appreciated. I have tons of books on OS development, but, I think my next step is to actually dive into an already existing OS, and learn how it REALLY works, from the CORE. 

Thanks,

Montray Davis :D

---

### Post by ubudog on 2011-01-23
Maybe this can get you on the right track?

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by Hur Dur on 2011-01-23
Linux From Scratch is about as minimal as you can get. It teaches you a lot about the workings of Linux.

For the love of God, do not make a distro that is absolutely useless. i.e. Xubuntu, Lubuntu, and Kubuntu. 

I also recommend Arch. It just installs what is needed to set up a functional system. Nothing more, nothing less.

---

### Post by montraydavis on 2011-01-23
I have played with it a little bit, but, does Linux From Scratch actually include a complete OS ( Like GUI, images, and all that other good stuff to make an OS actually worth using ? )

Also, I downloaded the LiveCD, but, for some reason, it seems like the whole Chapter one is missing from the disk ( not that I really need it too badly, but, it would help; I believe it's the actual manual and building LFS ).

---

### Post by ubudog on 2011-01-23
> **montraydavis said:**
> I have played with it a little bit, but, does Linux From Scratch actually include a complete OS ( Like GUI, images, and all that other good stuff to make an OS actually worth using ? )

Also, I downloaded the LiveCD, but, for some reason, it seems like the whole Chapter one is missing from the disk ( not that I really need it too badly, but, it would help; I believe it's the actual manual and building LFS ).

No, LFS is really, really basic.  Teaches you the deep inner workings of Linux, which may help you to create a full blown OS.

---

### Post by ubudog on 2011-01-23
> **Hur Dur said:**
> Linux From Scratch is about as minimal as you can get. It teaches you a lot about the workings of Linux.

For the love of God, do not make a distro that is absolutely useless. i.e. Xubuntu, Lubuntu, and Kubuntu. 

I also recommend Arch. It just installs what is needed to set up a functional system. Nothing more, nothing less.

Arch is pretty cool too.  :)

---

### Post by Hur Dur on 2011-01-23
I thought you meant building a Linux distro from scratch.

I recommend Arch Linux and Debian Net Install. You install everything yourself. It's simple, though. Getting from CLI to GUI is as simple as apt-get install xorg icewm and then editing .xinitrc. Or in Arch Linux, pacman -S xorg icewm and then editing .xinitrc. AFAIK, Debian does have a tool that allows you to make an iso image of your current OS. I'm not sure if there is one for Arch, though.

You should also focus on what you are making the distro for. Stability, ease of use, and decent performance? Debian.
Speed, and newer software? Arch.

---

### Post by montraydavis on 2011-01-23
What I am trying to do is obtain the source code an already existing OS based on Linux, and modify it myself to fit my needs ( as a learning experience in case I do decide to take on the challenge of creating a full blown Linux OS ).

---

### Post by Verbeck on 2011-01-23
> **montraydavis said:**
> What I am trying to do is obtain the source code an already existing OS based on Linux, and modify it myself to fit my needs ( as a learning experience in case I do decide to take on the challenge of creating a full blown Linux OS ).
then, [http://www.gentoo.org/](http://www.gentoo.org/)

---

### Post by SeijiSensei on 2011-01-23
The source code exists for every piece of software in the Ubuntu repositories because of its licensing.  That's true for every other Linux distribution as well.

The "OS" as you call it is actually composed of a variety of pieces.  There's the Linux kernel which sits between applications and the hardware, then there's everything else including GUIs, programs, etc.  If you're really interested in the "nitty-gritty" of the Linux kernel, you might start by [downloading the most recent stable kernel source from kernel.org]("http://kernel.org/") (2.6.37 as of tonight) and reading the included documentation to see how to build a kernel from scratch.  Just walking through the hundreds of configuration options will give you a sense of the complexity that's involved.

---

### Post by montraydavis on 2011-01-23
I can't happen to find the source code.... Could you point me to the link ?

---

### Post by ubudog on 2011-01-23
> **SeijiSensei said:**
> The source code exists for every piece of software in the Ubuntu repositories because of its licensing.  That's true for every other Linux distribution as well.

The "OS" as you call it is actually composed of a variety of pieces.  There's the Linux kernel which sits between applications and the hardware, then there's everything else including GUIs, programs, etc.  If you're really interested in the "nitty-gritty" of the Linux kernel, you might start by [downloading the most recent stable kernel source from kernel.org]("http://kernel.org/") (2.6.37 as of tonight) and reading the included documentation to see how to build a kernel from scratch.  Just walking through the hundreds of configuration options will give you a sense of the complexity that's involved.

That link should help you.  ;)

---

### Post by srs5694 on 2011-01-23
If the goal is to write an OS kernel from scratch, then I'd suggest using a model that's smaller than a current Linux kernel, which is absolutely huge (67 MiB *compressed* for the latest version I've got). A much earlier Linux will probably be more understandable as a starting point, although it would lack drivers for a lot of vital modern hardware so you might need to dig up an older machine or run it in a virtual environment.

There's also MINIX ([MINIX3](http://www.minix3.org) being the latest version), which was written with educational purposes in mind. There's a textbook that describes MINIX, which makes it even better for learning. (Note that I've never run MINIX or read the textbook; I'm just repeating what I've heard.)

To reiterate and expand on some points made by others, the OS kernel (Linux, for instance) handles core tasks like displaying text on the screen, accepting keyboard input, disk I/O, memory management, scheduling processes, etc. It sounds like this is what montraydavis is working on. Everything else we associate with "Linux" today (Web browsers, the bash shell, GCC, GNOME, etc.) is separate from the kernel. In Linux, most of these components are available in other OSes (FreeBSD, for instance). A distribution like Ubuntu is a collection of a specific set of tools, including a kernel and some subset of the available software for that kernel, along with distribution-specific scripts, configuration files, and perhaps even utilities to glue it all together. Writing all of that from scratch would be impossible for one human being. I don't know how many hours of programming time went into building all of Ubuntu, but it's certainly more hours than any of us have left to live (assuming no immortality drugs being invented soon).

Thus, the OP should either concentrate on building a kernel that's compatible with something (probably either Unix, to run Unix-type programs as Linux does, or Windows, to run Windows binaries as [ReactOS](http://www.reactos.org/en/index.html) does); or set his sites much lower, to write something that might be comparable to the OS and core tools of a home computer of the early 1980s, like an Apple II, Commodore 64, or Atari 800. Such an OS could include a handful of very simple applications, and might even be useful for something, but it wouldn't have anywhere near the capabilities of a modern OS. Actually, a third option would be to enlist help. With enough people and time, an OS to rival Windows or Unix/Linux could theoretically be built. I'm skeptical that you could generate enough interest from enough programmers to do this, though. The last remotely successful attempt I can recall was the commercial BeOS, which is now basically defunct, although the current [Haiku](http://www.haiku-os.org) project is an attempt to produce something similar.

Anyhow, this is getting a bit rambling, but for a learning project, creating a Unix-like kernel is probably a good way to go. You can then rely on existing projects, perhaps with a few patches, to provide real functionality. To make this work, you'd need to focus on providing Unix compatibility.

---

### Post by ubudog on 2011-01-23
@srs - Great post!  :o

---

### Post by Hur Dur on 2011-01-23
> **srs5694 said:**
> If the goal is to write an OS kernel from scratch, then I'd suggest using a model that's smaller than a current Linux kernel, which is absolutely huge (67 MiB *compressed* for the latest version I've got). A much earlier Linux will probably be more understandable as a starting point, although it would lack drivers for a lot of vital modern hardware so you might need to dig up an older machine or run it in a virtual environment.

There's also MINIX ([MINIX3](http://www.minix3.org) being the latest version), which was written with educational purposes in mind. There's a textbook that describes MINIX, which makes it even better for learning. (Note that I've never run MINIX or read the textbook; I'm just repeating what I've heard.)

To reiterate and expand on some points made by others, the OS kernel (Linux, for instance) handles core tasks like displaying text on the screen, accepting keyboard input, disk I/O, memory management, scheduling processes, etc. It sounds like this is what montraydavis is working on. Everything else we associate with "Linux" today (Web browsers, the bash shell, GCC, GNOME, etc.) is separate from the kernel. In Linux, most of these components are available in other OSes (FreeBSD, for instance). A distribution like Ubuntu is a collection of a specific set of tools, including a kernel and some subset of the available software for that kernel, along with distribution-specific scripts, configuration files, and perhaps even utilities to glue it all together. Writing all of that from scratch would be impossible for one human being. I don't know how many hours of programming time went into building all of Ubuntu, but it's certainly more hours than any of us have left to live (assuming no immortality drugs being invented soon).

Thus, the OP should either concentrate on building a kernel that's compatible with something (probably either Unix, to run Unix-type programs as Linux does, or Windows, to run Windows binaries as [ReactOS](http://www.reactos.org/en/index.html) does); or set his sites much lower, to write something that might be comparable to the OS and core tools of a home computer of the early 1980s, like an Apple II, Commodore 64, or Atari 800. Such an OS could include a handful of very simple applications, and might even be useful for something, but it wouldn't have anywhere near the capabilities of a modern OS. Actually, a third option would be to enlist help. With enough people and time, an OS to rival Windows or Unix/Linux could theoretically be built. I'm skeptical that you could generate enough interest from enough programmers to do this, though. The last remotely successful attempt I can recall was the commercial BeOS, which is now basically defunct, although the current [Haiku](http://www.haiku-os.org) project is an attempt to produce something similar.

Anyhow, this is getting a bit rambling, but for a learning project, creating a Unix-like kernel is probably a good way to go. You can then rely on existing projects, perhaps with a few patches, to provide real functionality. To make this work, you'd need to focus on providing Unix compatibility.

I hate to bump a thread that hasn't had activity in a few hours, but this is an amazing post. Full of useful information.

---

### Post by ubudog on 2011-01-23
> **Hur Dur said:**
> I hate to bump a thread that hasn't had activity in a few hours, but this is an amazing post. Full of useful information.

Agree.

---

