---
title: "Just switched from mac - How do I install softeware/driver upgrades?"
date: 2011-08-26
forum: General Help
---

### Post by Potsoil on 2011-08-26
Hi,
I'm very new at this and switched to Ubuntu this evening.
I can't connect to my wireless network, and I think this might be due to my airport in my macbook (2,1) needing an update (as I needed to do this when I first got it when using Tiger). So I downloaded the driver update for Linux only to find there's no simple 'install.dmg or .exe' and I get a lot of files which I seemingly can't use.
I've skimmed over the pocketguide, which talks about packages etc., but am I on the right track? Do I use Synaptic package manager? Is there a simple program I should be using?

Any advice would be great! I understand how you're generally not meant to download the source code for things unless you're experienced in programming etc., but for this driver update I think this was my only option.

---

### Post by evilscrappy on 2011-08-26
ok I am new but not,
I was doing some reading before I believe you are on right track with synaptic package manager.
[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

---

### Post by searchfgold6789 on 2011-08-26
Software for linux comes in a variety of ways, in order of popularity:

[LIST=1]
[*]**Synaptic** Package manager, or another package manager like the Ubuntu Software Center.
[*]**A .deb file** downloaded from the internet. It's like an .exe file, you just click it and it runs and installs the software.
[*]**An .sh file.** Normally, one would open up a terminal and type the location on disk of the file. Then it would run ans install the software.
[*]**Source code.** This comes in an archive (not a zip or an rar, it almost comes in a .tar.bz2). Once you decompress the archive, the source code is available in the form of C, C++, etc. files on your hard disk in X directory (wherever you decompressed it to.) One would first install all of the packages (synonymous with "software") that is required. Then, one opens a terminal, enters the directory of the decompressed source code, and types in commands according to instructions provided with the source code. Classically, this would be ./configure {to verify that all dependencies are installed and everything is in order}; make to begin the compilation process, and sudo make install to copy a runnable binary and complete the installation. Usually there are detailed instructions that come along with the source code, as I mentioned.
[/LIST]
I believe that using Synaptic is the easiest and simplest way to install a program, but there are thousands of more programs out there that Synaptic can't offer that are only available if you can compile it from source.

---

### Post by Potsoil on 2011-08-27
The driver update doesn't come with a readme :( I have a lot of .c, .o files, then things like wlconfig_lx_router_ap..

---

### Post by searchfgold6789 on 2011-08-27
Where did you get the drivers?

---

