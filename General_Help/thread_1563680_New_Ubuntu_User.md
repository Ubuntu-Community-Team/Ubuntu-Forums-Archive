---
title: "New Ubuntu User?"
date: 2010-08-29
forum: General Help
---

### Post by JWag12787 on 2010-08-29
I am looking to convert my Sony Vaio VGN-NW240F into an Ubuntu system.  But I have concerns regarding drivers, as well as software I use/plan to use.  Can you read below, and help me figure out if it'll be feasible w/ my system specs and software requirements?

Also, is installing the 64-bit version worth any extra hassle?


Specs:
* 2.2GHz Intel Core 2 Duo T6600 Processor   [64-bit]
* 4GB DDR2 800MHz Memory
* 320GB Serial ATA 5400RPM Hard Drive, DVD±R/RW Optical Drive


Software:
* Star Wars:  The Old Republic [coming out next year]
* Digsby [im client]
* Firefox/Thunderbird
* Weatherbug
* Mozy
* Filezilla & Notepad++
* Partition Wizard
* WinRAR
* PowerIso
* Microsoft Visual Studio
* Star Wars:  Empire at War
* C&C Tiberian Sun
* K-Lite Codec Pack w/ Media Player Classic
* AVG Anti-Virus

I'm also looking for software to convert episodes and movies from DVDs to an .mkv format, if anyone can recommend good software for Ubuntu for that [or even Windows 7]




Thanks for your reply!   :popcorn:

---

### Post by DarthScape on 2010-08-29
I have doubts about The Old Republic working on linux right away.

---

### Post by philinux on 2010-08-29
> **JWag12787 said:**
> I am looking to convert my Sony Vaio VGN-NW240F into an Ubuntu system.  But I have concerns regarding drivers, as well as software I use/plan to use.  Can you read below, and help me figure out if it'll be feasible w/ my system specs and software requirements?

Also, is installing the 64-bit version worth any extra hassle?


Specs:
* 2.2GHz Intel Core 2 Duo T6600 Processor   [64-bit]
* 4GB DDR2 800MHz Memory
* 320GB Serial ATA 5400RPM Hard Drive, DVD±R/RW Optical Drive


Software:
* Star Wars:  The Old Republic [coming out next year]
* Digsby [im client]
* Firefox/Thunderbird
* Weatherbug
* Mozy
* Filezilla & Notepad++
* Partition Wizard
* WinRAR
* PowerIso
* Microsoft Visual Studio
* Star Wars:  Empire at War
* C&C Tiberian Sun
* K-Lite Codec Pack w/ Media Player Classic
* AVG Anti-Virus

I'm also looking for software to convert episodes and movies from DVDs to an .mkv format, if anyone can recommend good software for Ubuntu for that [or even Windows 7]
Thanks for your reply!   :popcorn:

Please read this.

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by jocko on 2010-08-29
For the games, wait for someone else to answer, I'm not a gamer.

**Digsby** - according to their home page a linux version is "coming soon"...
But ubuntu comes with the IM client Empathy preinstalled, it handles most protocols, and there are other IM clients available in the repos.
**Firefox/Thunderbird** - Firefox is the default browser in ubuntu, so no problem there. Thunderbird is available in the repos.
**Weatherbug** - They seem to have a linux beta on their home page, but I'm sure there are similar apps available in the repos.
**Mozy** - Online backup? Not sure what's available...
**Filezilla** - Available in the repos.
**Notepad++** - Seems to be a windows-only program, but I'm sure you'll find a linux text editor with similar functionality... Ubuntu's standard text editor is Gedit, but there are others available in the repos or already installed (Kate, emacs, nano, vim, mousepad, Geany ...).
**Partition Wizard** - Gparted is available in the repos.
**WinRAR** - Ubuntu's standard archive manager (file-roller) handles every imaginable archive format you can think of. To get rar-support, you'll just have to install the package "unrar" from the repos...
**PowerIso** - They have a free linux version for download on their webpage, but I'm sure it does not have all the features of the registered windows version. Ubuntu can mount .iso files as if they were CDs/DVDs by a simple right click, and you can also browse the contents of an .iso using file-roller, but I don't think there is any one-in-all tool like PowerIso...
**Microsoft Visual Studio **- Not sure what it is, leaving it for the experts...
 **K-Lite Codec Pack w/ Media Player Classic** - That's windows software. There are lots of good movie players available in ubuntu. Totem is the default, but there are better ones in the repos (mplayer and vlc to mention the top two). You'll get most codecs you can think of by installing the package "ubuntu-restricted-extras" (which also gives you java, flash, unrar and microsoft fonts).
**AVG Anti-Virus** - There are no linux viruses out in the wild, so even the antivirus software that you can install in ubuntu scans only for windows viruses. It may be useful if you dual boot with windows and want to be able to rescue an infected windows system, or if you run a mail server and need to scan incoming and outgoing mails to avoid passing on windows viruses to others. For a linux-only system I can't think of any reason for running antivirus software.

---

